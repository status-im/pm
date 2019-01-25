## Status Devs Meeting 1 Agenda

**Meeting Date/Time: Monday 2018-08-06 at 12:00 UTC (14:00 CEST)
Meeting Duration 1.5 hours
~~YouTube Live Stream Link TBD~~
~Livepeer Live Stream Link TBD~**

## Agenda
0. Introduction
- Purpose of this meeting; format; experiment; feedback (Oskar)
1. Infrastructure updates (infra, p2p, security, testing)
- General infra (Jakub?)
- Hello, Security (Corey?)
- Security champions (Igor)
- Audit update (Adam? / Corey? / Oskar)
- P2P - New Peer Discovery protocol (Adam / Dmitry)
- Testing updates (Anton?)
2. Client updates (mobile, desktop)
- Mobile app (Igor)
- Desktop (Vitaliy / Max)
3. Research updates
- P2P - Whisper node incentivization (Dmitry)
4. Product updates (chat, wallet, dapp)
5. Specific ideas and misc
- Chat / PFS: https://github.com/status-im/ideas/pull/289 (Andrea MP)
- Whisper / Wallet key idea: https://github.com/status-im/ideas/pull/292/ (Andrea F)
6. Meta
- Feedback on this meeting - was it useful? things that went well, things that can improve
- Follow up re notes/stream; next meeting in 2w time

Please provide comments to add or correct agenda topics.

# Notes

Infrastructure: general, p2p, security, testing

## Infrastructure updates

### General infra
Jakub
- New Jenkins Master in place and working
- Jenkins linux slaves ready, need desktop build fix
- Remaking desktop build Jenkinsfile
- Issues with small disc space will go away once done
- Cleaner logs in Kibana
- Add another fleet for Hong Kong—this release or next?

*Has staging fleet been tested?*
Not by test team; no easy way of selecting a fleet right now for testing. Option to select fleet can be created without UI.

### Security

Introduction to Corey, security engineer at Status

*What are the security issues for mobile we're concerned with?*
Reproducible and deterministic builds is one thing; Corey to lead vulnerability/threat modeling sessions with different teams.

Security swarm update: Training phase underway. Igor will start shifting some of the work to Corey. Issues related to wallet and DApps to come. 

Security audit postponed until top issues are resolved. Initial push for security audit was to prepare for a public release. This has been deprioritised in Q3 OKRs.


### p2p

Adam, status of p2p network
- 3 data centers currently
- They are all connected, so it does not matter which one a user connects to
- We have a patch on go-ethereum that creates a different version of discovery protocol. Checks if connected peer matches discovery protocol.
    - Not possible to connect to our network from outside
    - Our cluster forms a **separate** network for those used by the Status app, not connected to Ethereum network
- We maintain our nodes with high uptime
- Drawback: this is still centralized because we run these centers
- We'd like to use new peers discovery protocol in future versions of mobile app
- We'd also like our nodes to support the Ethereum discover protocol and remove the patch; our nodes become part of the network and support the new peer discover protocol
    - Would not require sacrifice in efficiency on mobile
    - Server nodes would become like ethereum nodes
    - Important for LES support, which requires LES servers (more difficult than running Whisper nodes)
        - in v1, we'd like people to find LES servers from Ethereum network, meaning our nodes should also be part of Ethereum network
    - Using rendezvous: this is already in use on some IPFS projects, still undecided if this will become a default peers discover protocol
    - Pros & cons between two protocols?
        - We've tested only on simulated environments, requires real testing on mobile devices

### Testing

Anton
- Focused on increasing coverage and reliability
- Two type of runs: extended build against nightly (100+ of tests - 10% failures), build against PR (50+ tests - 16%)
- Future goal - start implementing blocking merge if tests are failing in a PR
    - Extended tests - we made a survey about this and only one person was against blocking merge in a PR 
    - How this will work:
        - Four types of results in automated tests
            - 50% of failed tests is due to bugs
            - Only 4% when something works in a new way
            - Infrastucture issues 
            - 28% false failures when something is wrong in tests
            - 20% of PRs have no end-to-end test results
                - many of these are from extended contributors
        - How we'll block PR from being merged
            - Fix all known issues from develop
            - Is it a new issue from this PR or known?
                - Increased details on error messages
            - matching failures from a PR with latest nightly build results
            - Feature changes and false failures need to be fixed in the PR
            - Will add an option to unblock merge in a PR manually 

Feedback from Clojure/Go
- Julien: Biggest issues are trust and visibility; Clojure devs aren't always looking at the test results. 
- Pedro: It wasn't clear when something failed on the parent branch or just on your branch. Making the PR fail only when your PR introduced an error is a great step forward.

- Random failures discourage people from taking results seriously
- These tests can't be disabled

Issues to address:
https://github.com/status-im/status-react/labels/e2e%20test%20blocker
These are not flaky tests; these are Status issues. 

Assign blockers to a team. 
Arrange bug-fixing period for these.

Client: mobile & desktop

Igor, mobile
- Prep for ETHIndia 
    - Bounties Network token only available on Rinkeby
    - Using previous release with 2 additional commits for the event
    - Bug fixes for Rinkeby as well
        - Rinkeby can't talk to other networks
    - Running load tests for ETHIndia (500 users anticipated)

Max, desktop
- Nightly builds for desktop
- Will begin chatting internally using desktop
- Issues with Jenkins build for desktop
    - On Linux machines, not enough space and desktop builds are big
    - Once resolved, every PR in status-react will trigger Jenkins builds in both mobile and desktop
- Also resolving blockers from react-native desktop library
- Finishing features for UI, e.g. push notifications


Research updates

Dmitry
- Incentivizing Whisper nodes
- Goal is to base this on reputation system 
    - Distributed reputation systems that can withstand known attacks
    - Get reliable rating from the network
- Can then select peers with best rating
- Payments model requires research
    - Can be done over regular payment channel
    - Incremental payments (10 minutes, then 20 minutes, only one executed on chain)
        - Oskar: this makes sense for computer-to-computer networks but for humans? Higher level payments on top?
            - We can not guarantee that the peer rating will not change over time or that the peer is perfectly trustless
            - Jacek: Same issue if we moved to PSS
            - Similar to real-world, can use oracles etc
            - Ref: swap swear swindle https://swarm-gateways.net/bzz:/theswarm.eth/ethersphere/orange-papers/1/sw%5E3.pdf
            - Ref for interested: https://nakamotoinstitute.org/static/docs/micropayments-and-mental-transaction-costs.pdf
        - More to investigate
        - Fork to Discuss?

### 4. Product updates (chat, wallet, dapp)
#### Wallet
- mostly refactoring, bug fixing
- ENS username registration
- Security champions recap / lessons learned

### 5. Specific ideas and misc
#### Chat / PFS: https://github.com/status-im/ideas/pull/289 (Andrea MP)

- Implement, PFS, follow Signal's Double Ratchet, X3DH
- Persistance with sqlite on status-go side
- Discuss post on initial key exchange, nothing decided yet - how deal with storage? https://discuss.status.im/t/x3dh-and-one-time-key-avoid-smart-server-by-randomizing-the-one-time-key/276
- Desktop relevance? Minimal changes to status-react

#### Whisper / Wallet key idea: https://github.com/status-im/ideas/pull/292/ (Andrea F)
- Security / privacy reasons: extend key store, separate keys
- Security and refactor changes
- Needs a bunch of UX work
- Question: separated wrt seedphrase?
- Use different derivation path

### 6. Meta
- Feedback on this meeting - was it useful? things that went well, things that can improve, add notes to agenda your section

- Corey: Very useful, add in stuff to Hackmd
- Jacek: In terms of keeping time, focus on things that need decision or are about the future. Town Hall about past, for things that have happened

What can improve?
- Issues for this call should be about future
- Understand what we need for each topic, solution/agreement etc
- Really appreciated having something to watch, screen sharing helpful

- Follow up re notes/stream; next meeting in 2w time
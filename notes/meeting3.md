# Status Devs Meeting 3 Agenda

## Agenda

### Part 1 Hot Topics

1. 292 Decouple Whisper key from Wallet (https://github.com/status-im/ideas/pull/292)
    Context: we need to progress on this since this is a dependency for hardwallet light product launch.

    Goals: discuss progress, next steps

    Reading: https://discuss.status.im/t/decoupling-the-whisper-key-from-the-wallet-key/261

2. Status Desktop must-haves

    Context: As we plan on using Status Desktop internally instead of Slack, we need to agree on what features we must have working in order to not have a detrimental impact on team performance.
    
    Goals: Collect a list of features that can be implemented in a reasonable amount of time and will satisfy 90+% of use cases.

3. Web refresh
    Context: explain our infrastructure choices and approach to implementation

    Goals: get engineering input; to get people to join the swarm for implementation

    Reading: 
    [Web Refresh plan WIP](https://docs.google.com/document/d/1IXOyWfx7m3j31GshKPOPXKkLF0-cz_a0hN71TxeWpW8/edit?ts=5b867125) 
    [Content ask](https://docs.google.com/document/d/17ZvEIzBM8avDOkRjbIYcex3jNoeSoNVW5_gntvV-ov4/edit#)
    [Fiddle embed](https://hackathon-status.ghost.io/fiddle-embed/)

4. Infra updates (infra, p2p, security, testing)
5. Client updates (mobile, desktop)
6. Research updates
7. Product updates (chat, wallet, dapp)
8. Specific ideas update
a) 289 Deterministic builds (https://github.com/status-im/ideas/pull/297)
c) 289 Perfect forward secrecy (https://ideas.status.im/ideas/289-perfect-forward-secrecy)
d) 173 Documentation (https://github.com/status-im/ideas/pull/287)


## Notes

### 292 Decouple Whisper key from Wallet

- this is a dependency for the hardwallet project
- this is paused as the work on javacard started
- proposition is to wait for PFS to be finished before resuming this
- keys needs to be decoupled before integrating javacard (for the release; we can continue development though)
- PFS update
    - follow the process described on discuss
    - Go part is implemented
    - there are still some cases when a bundle cannot be exchanged and the UX solution is required
    - docs must be finished yet

### Status Desktop must-haves

- figure out crucial features that needs to be implemented
- objective: use it as a replacement for Slack
- list of features to have the green light to consider replacing Slack:
    - reliable messaging for 1-1 and public chats
    - mentioning users
    - multiple chats open
    - we still need feedback and input from people what is crucial; at the same time we don't want to include features that are hard to implement but not 100% necessary (especially features that touch the library)
    - Pedro: auto-updater is important due to planned frequent changes
    - Pedro: URLs are not clickable
    - Oskar: replacing Slack might not be the best wording, IRC might be a better comparison; we aim for unblocking usage of Status Desktop first
    - Pedro: switching between chat windows is slooow
    - Jacek: a few features that are not necessary related to secure messaging but some improvements for good UX for developers and contributors to open source projects
        - Oskar: these features are not available in the "traditional" tools like IRC
        - Jacek: do we optimize the UX and available features for the right people?
        - Vitaliy: the main objective it's to make it usable internally; phase 2 could be to make it more efficient and appeal to other group of people
        - Jacek: developers might have pretty different requirements than other groups of people
        - Jacek: a bridge between Status Desktop and Riot might be a good feature
    - Oskar: suggested "themes/modes" in the future where one is optimal for developers and another one for another group
    - Oskar: images can also be a limitation (requires IPFS/swarm integration)
    - Jacek: the messaging protocol does not handle mime types

### Web refresh

- exploring Ghost (https://ghost.org/)
- go toward being agnostic and consistent in terms of the design
- building one language which bridges visual design and engineering
- production platform is a development platform (to some degree)
- designing for the future but be backward compatible (using web3.0, ipfs, swarm vs web2.0)
- role out a custom auth integration
    - Ghost does not offer 2FA
    - thus, we will go with self-hosted
    - Oskar: might be some overlap with identity system / discovery
    - Old Discovery work
        - https://docs.google.com/document/d/1J-mZewaD_jOs06m0ljIs-wooL-Tux9bjWI8-mcFQp3o/edit
        - https://docs.google.com/document/d/1sh0gSj0gGWZctXsT2qx8PjMqEWruE-wKj8z7M6Vo5DM/edit
        - https://docs.google.com/document/d/1MQRcv1BmMSl08by7VLGaQArXV-z467PtkwyRpVs7Ok8/edit
        - https://docs.google.com/document/d/1PC4Qu_5qw0OssDptiDiV3qkxkVfaG1DGVHMY7FAy7EM/edit#heading=h.a2z3shua0hvk
    - author vs viewer in terms of IPFS resources
- Jacek, exiled surfer: would it be possible to serve our main page via IPFS before devcon?
    - should it be possible and that would be cool but not really sure what will be a benefit
    - Barry: it's possible to pin down the website to Infura instead of running the IPFS node by ourselves
- (discussion about running our own swarm gateway)
    - it's still attached to the main swarm nodes so if they go down, a lot of our content will do as well
- Barry: ens resolution to swarm hashes
    - this is not clear in swarm in comparison to IPFS

### Infra updates (infra, p2p, security, testing)

- Jakub:
    - the main focus was Jenkins changes
    - there are still some improvements to be done for the release process
    - running small swarm cluster
        - added storage limits
    - Alibaba cloud nodes are up but there are still some connectivity issues (probably on the VPN layer)
- Adam:
    - last week merging Rendezvous into eth.staging fleet
    - next step will be to update eth.beta fleet
    - can test between staging and beta
    - next objectives:
        - incentivization layer
        - spam protection. Jakob looked into some OS level spam protection. Dmitry is working at Whisper level (we can't rely on PoW on phones) https://hackmd.io/CVrdAfo0Sh6da1gGqAfeSw#
        - tested LES discovery last week as first step to reintegrating LES into the app
- Corey:
    - infrastructure audit
    - incident response platform
    - diagram how all the keys work in Status
    - a blog post is planned so that people gets better understanding how the keys work
    - how the hardware is gonna take care of keys to provide better security
    - Company and Personal Security Week ???
        - this is on discuss https://discuss.status.im/t/personal-and-company-security-week/360/1
    - suggestion filling in a spreadsheet comparing IMs security features
    - audit running with hardwerwallet and ens
    - Oskar: secure messenger https://docs.google.com/spreadsheets/d/17s7cMJ61-oYuyiz8cByWH7naZH10FXT3XgrpI-3cBUM/edit#gid=0

### Client updates (mobile, desktop)

- Roman:
    - integration react navigation
    - new release today/tomorrow
- Desktop:
    - fixing scroll views, layout issues
    - performance improvements
    - system warnings/notificastions almost finished
    - Jenkins build fixes
    - unit testing Clojure code

### Research

- TBD

### Chat Team

- Pedro:
    - mostly about PFS implementation
    - we have a build which can be used to test it
    - PFS spec being worked on
    - issue: remembering chats scroll position when switching beteen them
    - private group messaging
        - one message would be sent to each participant (pair-wise encryption); costly as PoW must be calculated for every message
        - Reddit Thread Question needs answering: [Link Here](https://www.reddit.com/r/ethereum/comments/9az1yz/statusim_beta_update_0926_privacy_policy/)

### DApp

- Julien:
    - focused on implementing web3 opt-in mechanism together with MetaMask
    - EIP (link is needed)
        - prevent from leaking too much information to DApps
        - trade-off needed as DApp must know something
    - blog post about being up-to-date with MetaMask is in progress
        - there is a target date but unsure we will make it
    - high-level things related to the extensions in the Status app
        - simple chat command to send CryptoKitty as an extension

### Wallet

- TBD

### 297 Deterministic builds

- Jakub:
    - prepare a PoC with some very simple Go package and get it working with Jenkins
    - later do the same with status-go
    - Oskar: what about Clojure, can it start in parallel?
        - later yes when we have a basic idea how it works and collect more knowledge

### 289 Perfect forward secrecy

- *covered earlier*
- Pedro: would appreciate some feedback on the document (https://hackmd.io/I3jM-rbYRdS3Sqvwu_ATqg)

### 173 Documentation

- basic skeleton that is still fairly basic but sufficient
- more comprehensive, high-level view what we'd like to show
- collect feedback from teams and ask what they'd like to include in there
- focus on building Status and running DApps
- Oskar: what about old wiki?
    - Julien: some were removed because they were irrelevant

## Thoughts

- what about including people from the community?
- advocacy model

## Links

1. PFS doc: https://hackmd.io/I3jM-rbYRdS3Sqvwu_ATqgPFS 
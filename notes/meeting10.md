# Status Devs Meeting 10, Agenda
Meeting Date/Time: Monday 2019-01-14 at 13:00 UTC
Meeting Duration 1.5 hours
YouTube Live Stream Link https://www.youtube.com/c/Statusim/live
Livepeer Live Stream Link TBD

## Agenda

1. Swarm Updates (15-30m)
All swarm leads presenting give brief update.

SNT Utility
- 321-teller-network (research)
- 314-tribute-to-talk (research)
- 313-sticker-market (research)
- 317-dapp-store (research)
- 316-core-network-incentives (research until 31/1)

Essential
- 315-core-improvements (research)
- 311-protocol (research)
- 322-dao (research)
- 312-janitors (research)

Teams (fallback for responsibility)
- 310-core (research)
- 306-core-browser (research)
- 304-core-chat (research)
- 318-desktop (research)
- 319-wallet (research)
- 320-keycard (research)
- Security/Devops
- QA

- Research/Nimbus
- Embark

2. Hot topics. (45-60m)

For each agenda item, please provide context (things non-initiated people need to know, links etc) and goal (desired outcome of discussion) for agenda items.

a) design overview (Hester)

b) react-native-desktop vulnerability (Corey)
    - https://github.com/status-im/react-native-desktop/issues/447

3. Quick announcements (<15m)
- Swarm lead reminder: re swarm updates/budget/link artifacts (done)

## Notes

### Swarm updates

#### Teller Network
- Last session brainstormed on user stories
- Open questions to answer 
    - Crypto-fiat only?
    - Using Teller Network to onboard new users 
    - Dispute resolution, indicators of trust
    - Using DAI as base?
- Basic working DApp for both mobile & desktop
    - User can buy a license to sell
    - There is escrow 
    - UI to query prices for escrow exchange
    - Support for multiple ERC20 tokens
    - Ability to rate transactions for seller ratings
    - Working on UI for arbitration 


#### Tribute to Talk
- Starting UI work 
- Minor changes to mock-ups after design review; linked to "contact request" feature
- Writing specs for contract to prepare for security audit
- MVP: pay tribute with regular transaction, contract only used to register tribuets

#### Sticker Market
- Last week completed research & specs
- Happy with mock-ups after design review
- Open question:
    - ERC721 will not be used in MVP. But is this something we want to use in the future? 

#### DApp Store
- Research phase running til end of month
- P1, fewer core contributors taking part
- Phase 1: Design to discover DApps easily and find DApps that are relevant to you
    - Potentially calling an API to determine relevance in MVP
    - Will build as web DApp
    - In parallel, research around curation mechanism
        - Andy's proposal for bonded curves requires feedback

#### Network Incentives
- Continuing research 
- Taking into account protocol research also happening
- Looking for options more broad, and applicable beyond Whisper

#### Core Improvements
- Implementation underway
- Internal release this week includes [] and save password feature for Android
    - Password storage can be improved - 30% there
- Reliable messaging work is 50%; requires status-go updates to be deployed
- Working on a dependency audit, to ultimately build older versions of the app more easily
- Some work with PFS & device sync. May clash with TtT, coordination required.

#### Protocol Update
- Workshop preparations
    - 5-7 Status CCs meeting end of Jan in Brussels
- Working on POC for a data sync layer, an in between layer that isn't concerned with messages but simply syncing data (to build on top of, featuressuch as public chat, group chat) with flexibility below (e.g. replace Whisper with something else)

- Workshop prep: -- https://www.meetup.com/Pre-FOSDEM-Messaging-Workshop/events/257926909/?isFirstPublish=true 5-7 ppl from Status -- https://medium.com/web3foundation/messaging-for-web-3-0-building-an-anonymous-messaging-protocol-e29db72f4d19
- Data Sync layer PoC1 for 1:1 chat: -- Code: https://github.com/status-im/status-research/tree/master/data_sync -- Protobuf: https://github.com/status-im/status-research/blob/master/data_sync/sync.proto -- Write-up: https://notes.status.im/THYDMxSmSSiM5ASdl-syZg?both


#### DAO
- Liquid Pledging contracts have been deployed to Rinkeby for testing, simulating how UI might act on a real network
- UI is feature complete for the MVP
    - User can create a delegate profile for a project
    - A delegate can fund projects
    - Can withdraw funds from a project
- Now considering path to mainnet, security audit 
    - Overlap with Giveth

#### Janitors
- Still in research phase
- Request that swarm leads... 
    - Continue tracking hours in this spreadsheet: https://docs.google.com/spreadsheets/d/1P4zc6ODJGAY_ErnTHMyHvOSq6NHXnp9VxF3wP6yFPhQ/edit#gid=0
    - Keep Pivotal boards up-to-date
    - Provide work log in swarm repo/weekly updates on what the swarm has accomplished


#### Desktop
- Switched to new version of react-native
- Corey found high severity bug that might also extend to react-native
- https://github.com/status-im/react-native-desktop/issues/447
- Volodymyr: it's a dependency from Facebook react-native; I believe we will get rid of it when we change react-native desktop to another package. It won't contain all react-native code, only desktop related, so the dependency should be removed from dev dependencies list.

#### Wallet
- Redesign issues should be finalized this week
- Thursday call will be prioritizing the next task

#### DevOps
- Looking at the software used
- Can port development locally into dockers soon; will be using exactly the same tooling & versions from then on

#### QA
- Last week set up PivotalTracker project
- Most common tests last week were release testing for internal release
    - Still in progress; waiting for Status-go update
    - Once done, will test battery consumption & performance testing
- For automation, task to automate upgrade on Android
    - First upgrading empty account
    - Next step is to automate an upgrade with real data
- As usual, updating test cases for new features 
- Repetitive tasks for nightly testingitive tasks for nightly testing

#### Research/Nimbus
N/A

#### Embark
All related to Teller Network/DAO. Finding bugs that need fixing and having new feature ideas in developing these DApps. 

#### Design allocation
Hester shared an update on which designers are allocated to which swarms: [LINK]


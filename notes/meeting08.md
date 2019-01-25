# Status Core Dev 8

## Agenda

0. Brief team/swarm updates (5-10m)
- Core
- Research
- Product
- Infra
- Other

1. Decoupling Whisper and Wallet key.

Now that we started the keycard integration with status-react, we are wotking on decoupling the whisper and wallet keys.

Reasons:

1 - privacy (not sharing your wallet transactions in public chats)

2 - security

3 - keycard (wallet keys never leaves the card, transactions are signed by the card. whisper key is downloaded to the client and used to encrypt/decrypt messages).

The wallet key will be derived with the current BIP44 derivation path.

The whisper key will be derived with the path defined in the EIP we proposed: https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1581.md

Desired outcomes:

Deciding how to exchange wallet address for in-chat transactions. Options:

1 - In the current protocol, when Alice adds Bob to her contact lists, Bob receives a messages with Alice’s profile (name and picture). We can send the wallet address as well, allowing Bob to send in-chat transactions only after receiving Alice’s address.

2 - Send a wallet-address-request on demand. When Bob wants to send a transaction to Alice, the protocol sends a request to Alice, Alice accepts, and Bob receives back the address to use in the transaction.    

Links:

1 - Decoupling whisper and wallet keys: https://discuss.status.im/t/multiple-whisper-and-wallet-keys/817.

Work in progress branch: https://github.com/status-im/status-go/tree/experimental/decouple-keys

2 - Steps needed + ideas/help needed on how to exchange wallet address for in-chat transactions https://notes.status.im/xIn9qA-3SWCbp7jkJCJjOg

3 - Our "Non-wallet usage of keys derived from BIP-32 trees" proposal has been accepted (still in Draft). Kudos @bitgamma - https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1581.md

2. Wallet dependency compromised, aka 'could've been us'
Context OP: https://discuss.status.im/t/wallet-dependency-compromised/825 - it's easy to hijack dependencies, this can lead to loss of funds. We have 1k dependencies and little oversight right now.

Desired outcomes:
- What can we learn from this event?
- How will it affect the priorities of what we do? What are we going to do about it?

3. Upgradeable message-ids open forum.

We had problems with message IDs for quite a while and they are impeding the upgrade, let's fix them finally.

More context: status-im/status-react#6956

[also - feedback on time? vs TH, 1h later? local times]

[SKIPPED]

- How to keep track of what artifacts are used in a build?
    - To make debugging easier, we should start logging artifact SHAs (both go and react) every time the app starts up;
    - Currently PR branches are rebased against develop on Jenkins and the respective commit gets lost (i.e. SHA in app doesn't mean anything)
    - Options:
        1. Fail build if PR branch isn't rebased
        1. ~~Push tag of rebased branch~~ (unfortunately this creates GH releases as a side effect, polluting the releases page)
        1. Push temp branch

---

# Notes

## Swarm Updates

## Core Update
(Igor)
-  2 weeks, message reliability, PFS (Group Chats, device sync), and ??

- Screen consisntency channels of mailservers, merged acknowledgments on whisper level, and misc

- group syncing
profile picture and username
public chats and group chats?

- testing ulc and LES, quite a few bugs
finally merged latest go-ethereum and latest release seems to sync but 2 other bugs.


 ## Research

 ### Protocol
 (Oskar)
 validaylabs web3 foundation collaboration
 repo in early stage and also secure messaging companion awesome-secure-messaging
 working with web3 working on time for workshop

focus on:
- distributed state and async messaging
- mixnets

- working on final swarm proposal with rough milestones,
clear seperation and problem statements
1 milestone

### Nimbus / Serenity
(Jacek)

Foundation has cleaned up spec well now
Reading the spec is a great time to get into it

Feel free to ping Jacek if you want to learn more

Team split into two, one focusing on Eth 1.0 and another Eth 2.0
Working on Beaconchain milestone

Goal is March clients should be communicating together in prelaunch testnet

Curious to hear how to proceed with ULC integration
also project to incentivise running nodes

If these interest you talk to Jacek as well

## Product
(Graeme)
### Voting
open create and close function for voting dapp

### Liquid Funding
Migrating Liquid Pledging contracts to Embark

## Wallet
(Goran)

- working on wallet screen designs, expect new ones soon!
prioritising and planning phase same as everyone else

## Chat
(Eric [yenda])

also planning phase
no important updates for now

## Infrastructure
(Jakub)

upgrading a bunch of stuff
Android NDK
Setting up Search for our pages,
plugin for hex..?? to it can index our pages

introduce snake(??)that Corey is leading
new mailserver canaries that check if theres discripenecies (Adam)

checksums for artifacts!

## Testing

automated testing, ready to block PR's that don't pass end to end test, just one last thing.

edit new desktop tests, 2 investigations for automated testing of keycard and for dapps

# New things

## Decoupling Whisper key
(AndreaF)
from a user perspective  **this will be a breaking change for whisper identity**
your whisper identity will change and your random name will change.

2 different keys for wallet and Whisper
- privacy not sharing wallet address
- wallet key should never leave keycard, and having a whisper key that can be downloaded from the card

wallet key will use same
proposing EIP for non-wallet keys, extending BIP43 to have different keys

branch already in status-go (and changes to go-ethereum) that already decouples the keys

how to decide on how we want to exchange addresses
two options
1 when i add you, we are already sending info, so we can send address
or
2 we can have a request on demand when you request to send funds, they can choose to accept or not

for the rest i posted links to discussion and steps we're impmenting

also idea to replace key file storage in go-ethereum with more general storage interface, so it might be a good for keycard

ecrecover can be used to migrate

What happens when we upgrade for the user?
undecided

current idea is to require mstare key and create new leaf off root

concerned about different client compatibility (Metamask, Ledger, etc)
should either allow derivation path / HD structure to end user
and/or
create a standard specification for all clients

Discussions about EthMagicians Wallet and Hardware wallet groups,
no major consensus in either

Ties into a wider discussion Identities, decoupling keys, multiple wallets

## Dependencies being compromised

copay nodejs deps 2 depths deep had an owner change, someone took it over and push new version that obfuscated code, ended up with users of that wallet lost their funds.

How do we fix this before it becomes a problem

(Igor and Jakub)
- Switching to yarn, locks to hashes.
biggest problem with npm, npm never checked what was downloaded what was requested, so an attacker could republish over the same version with different lib.

- Corey's work on auditing dependencies, implementation of snake(??), so we can better audit deps.

Does this really solve the problem?
Need more structured approach to this threat model

PR's can be blocked that have dependencies that change

Also need to be expanded to other langs
gradle, cocoapod, etc.

These things still mitigate
how can we be more than one step away from failure?

no code == most secure so, no deps.
security issues hide in complexity
sounds like we're trying to fix it by adding more complexity
adding more tools to check we're more safe.

A dep you don't have is one you

how can we simplify things, instead of adding things that can lead us to a more secure world?

These things hide in complexity and processes, things people don't understand.
Then falls back onto socially engineer.

Javascript is the biggest issue, many transitive dependencies.

Isolate the key management, and no apis to get the keys.

How do we make this a culture, and ingrained thing in the org?
how did we go with the stride framework? didn't go far.
need to create new security champions?
We started doing them and then our org changed and then things

everything is stored in the same db, so it's possible to accidently change state in chat by working on wallet, segments of the application should be modularised.

create model (for signing) that doesn't touch react at all
native ui components for security critical screens.

Setup seperate call with Core, Wallet & Corey.

last idea, champions for tech (Clojure & go)

## Tracking artefacts of build
(skipping Pedro not available)


## Upgradable Message ID's
(Igor)

We currently have a hash of interpreted version, so hashes change depending on interpretation, so things break.

Instead just Hash message (or id of message)?

Any edge cases?


## Maintaining Compatibility in Protocl Discussion

(AndreaP)
PR out, change message id in format, and this PR adds code to handle it.
If we change again, we need to add code to support 3 versions of message id's

Make a decision of what we want to do PR

(Jacek)
push back idea that maintaining multiple versions
techincally you should be able to isolate that, having different versions is good because you can compare them, this is a problem we'll be facing over and over again
so introduce infrastructure in code to make handling those situations not so costly.

(Multiple People)
at the moment code is not structured to handled this. what makes it difficult?

field names are bad "new-messaging-id" and the next would be "new-new-messaging-id"??
....

Just introduce versioning now.

(Roman)
we can actually do this, but you want to release app in 2 days we can't

(Eric)
migrations are local,
migrations of message-id, send old message id as well for the old versions?
cannot

(Jacek)
make it a backwards compatible way and the cost is near zero, couple of bytes in

(Eric)
Break compatibility to introduce that

(Roman)
nothing prevents us from sending same data

(Igor)
cost of traffic bad

(Roman)
handshake for versioning
how fast we can do this? but for release?

(Oskar)
compatibility is not optional

(AndreaP)
We all agree the thing is that next week we'll have to change format and we're just pushing out a quick fix, seems like a wasted effort.

*** Events are dictating quality ***
The same issue came up with last event, last two releases
Extensions stuff related to roadshow.

Code should always be releasable at any point.

New message id is related to slow signing in, so not easy to remove it

Have code to handle different versions so can downgrade protocol if new one doesn't work,
how do we apply this approach to database?

## OKRs?
Michael mentioned OKR process dur 7th?
Jarrad mucho confused, confirming with Chad

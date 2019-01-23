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

## Notes

Here https://notes.status.im/Z9xG4bACS9WP_9hQtFbVjg
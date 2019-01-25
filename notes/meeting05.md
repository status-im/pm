# Status Devs Meeting 5 Agenda
Meeting Date/Time: Monday 2018-10-01 at 12:00 UTC (14:00 CEST)
Meeting Duration 1.5 hours
YouTube Live Stream Link TBD
Livepeer Live Stream Link TBD

# Agenda

## Hot topics

### 1. Rethinking MailServer v2
Two weeks ago we explored log-based messaging and decetralized storage for MailServers. A few concerns appeared regarding log-based messaging and offloading storing messages on the client though.

This week I'd like to describe a slightly modified approach which is about providing open source tools to create something called Global Whisper Archives. This approach uses decentralized storage and the idea of forking.

Goal: gather feedback and follow-up on the MailServer conversation from the previous Devs Meetings.

### 2. Fork fork fork
We are working towards moving Whisper to a separate package in status-go repository or separate repository. This is because we simply have too many patches and we need to introduce even more after we started working on rate-limiting.

We also want to remove patches from status-go and just maintain our fork of go-ethereum. This will allow us to use status-go as a library in other projects, for example https://github.com/status-im/statusd-bots.

Goal: inform the rest of the core contributors working on status-go repo what is going to change.

### 3. Chat message bridge
3rd parties want to send message to specific chats using external processes. Simplest way to do that is to offer an HTTP bridge that can be used by anyone.
How do we add PN support to this?

@flexsurfer wrote about it here: https://discuss.status.im/t/whisper-api-as-http-service/470/6

and here:

while whisper api is an experiment, and there is no simple solution for services outside status send whisper messages , i see next workflow,
1) dapps ask permission for sending notifications to user (user share his token)
2) dapps server sends notification using FCM SDK and user's token
3) user receives notification in status
4) clicks on it, status opens with some popup message from dapp, something like "CDB is too low in   MakerDAO" and buttons "Cancel' and "Open MakerDAO" ,
5) open MakerDAO dapp if user clicked Open
Is that our best option? How about security concerns?

### 4. ENS smart contract security audit
With Sigma Prime was completed and we are going over their report and collaboratively working on the issues they found. Once completed, we will release the report to the public. Hint, we have awesome solidity developers.

### (10m) Quick announcements and feedback on format

### 5. (NO TIME) Docs and Status Node
First docs how to run Status Node has been prepared. We have a contact to folks running DappNode and Meshbox projects. We want to integrate Status Node with these systems.

Goal: make it clear what the next month P2P Team will focus on.

### (NO TIME) 6. Documentation Update
We have switched our static site generator, are waiting on a design and to implement a global header, and require one person from each team to agree to be the documentation janitor so that we can keep everything ship-shape across the org. We have also set up a proper staging and prod site, so that people can push directly to the develop branch in our docs repo, see their changes live, have it reviewed easily, and then merged into master, which serves to docs.status.im.


## Notes

Agenda was set through a voting Dapp with QV

- Rethinking Mailserver v2
    - Adam:
        - On last call there was talk about log-based messaging
        - On Global Whisper Archives, we would create tools to be able to store messages on IPFS/Swarm, allowing people to retrieve historic messages. Goal is to have single history in IPFS/Swarm in a decentralized way. There would be a way (not clear how yet) to traverse the message history.
        - It would be forkable, so they could run their own service, and they would be able to point to our own message history.
        - Looking to write up more details this week.
        - Although it's easy to run a whisper node, it's much harder to run a good mailserver node, and this initiative hopes to be an answer to that problem.
    - Graeme:
        - Will this architecture facilitate the use case where a user logs on on another device and gets his contacts?
    - Adam:
        - IPFS/Swarm can definitely help with that, but will be an independent solution
        - Regarding PNs, we should keep PN server and mailserver separate
    - Igor:
        - We could do background fetching of messages and show push notifications based on received Whisper messages
    - Ivan:
        - Do we actually need PNs? Wasn't it only required for iOS due to background logic restrictions? Maybe we can do the same, even if not as efficiently.
    - Igor:
        - We can do that on iOS too
    - Oskar:
        - What are the specific next steps?
    - Adam:
        - First, a more formal description/specification

- Fork fork fork!
    - Adam
        - We moved our patches from status-go to our own form of go-ethereum. We no longer need to patch our vendor directory.
        - DmitryS work on moving whisper to its own package. Too many patches to maintain otherwise.
    - Ivan
        - Are we considering how to contribute back upstream? Aren't we risking maintaining our own fork detached from upstream?
    - Adam
        - It's much easier to work without having the workload of creating and maintaining patches.
    - Igor
        - Who will be responsible for upstreaming our patches? Previously it was much more obvious who needed to do it (the author).
    - Adam
        - Good question. We need to figure out a way to do that. We don't have an official process to upgrade geth. We can make a rule, where when we upgrade geth we need to sync our patches upstream.
    - Igor
        - Should we do some kind of tests to ensure that we don't miss any patches along the way, when upgrading?
    - Adam
        - We should still strive to be backward-compatible with upstream.

- [Chat message bridge](https://discuss.status.im/t/whisper-api-as-http-service/470/)
    - Julien
        - The idea is to allow for services/Dapps to be able to send Whisper messages and push notifications to users.
    - Igor
        - How can a Dapp send a message in a simple away autonomously?
            - Using an Infura-like API doesn't work right now, because Whisper communication is stateful.
        - PNs
    - Oskar: we should not consider centralized solutions, the goal is to design a decentralized solution.
    - Ivan: why do we need to add an additional `post` method to Whisper?
    - Igor: for convenience. Otherwise why e.g. would someone need a status-go library?
    - Julien
        - The main use case is having Push Notifications even when the Status app isn't running or the Dapp in question is not running.
    - Ricardo
        - shared https://status.im/whitepaper.pdf
    - Oskar shared screen showing Decentralized Push Notifications market
    - Dmitry
        - Why do we want to provide something that is centralized, instead of Dapp developers running their own node? Isn't it a question of education?
    - Ricardo
        - Status Notifications would be that Status Browser can Subscribe for Status Nodes in Dapps that implement a notification scripts file that Status Nodes understand.
        - Users would need to (initially) Trust the Status Node, and use state channels to make small payments before any notification. If Node dont send notification, user stop making payments
        - Status Nodes would commit to run a script and answer the output of it to the subscriber, and everytime it does, this user would make a payment. 
    - Igor
        - It's a matter of lowering the barrier to adoption. Not everyone will be ready to run their own cluster, with monitoring, etc.
        - Is anyone against us adding two more methods to Whisper RPC API, deployed to our cluster, that then Infura and others can connect to?
    - Oskar:
        - Suggested parking this discussion and continue in discuss
    - Ricardo asked to be invited to future PN discussions
    - Igor
        - What do people most oppose in the ideas discussed?
            - Ivan: having our own cluster
            - Oskar: adding new APIs undecided on implication; hosting our own infrastructure
        - I'm not arguing for relying on centralized infrastructure.
        - We wouldn't use these new endpoints, but Infura could use that to add support for Whisper.

- ENS smart contracts audit
    - Corey
        - We engaged Sigma Prime to audit our ENS smart contracts
        - We're now going over the smart contracts with them to fix discovered issues
        - We're very happy with the quality of their report, and seems like we're in a very good place to start with.
        - People can ask for the report, but it's not going to be public right now.
    - Ricardo
        - Really liked Sigma Prime, they really looked at our application and concept
    - Corey
        - We are signing a contract with Threat Stack to monitor our critical infrastructure. It's a service to monitor who's doing what on that infrastructure to let us know when something goes wrong.

- Documentation Update
    - Cryptowanderer
        - Should be really easy to contribute to the docs now, with a button on the docs to create a PR for changes.

- Announcements
    - Igor
        - Next nightly will contain light node support. Probably poorly performing, but a start nonetheless.
    - 

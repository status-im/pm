# Status Devs Meeting 4 Agenda

Status Devs Meeting 4 Agenda
Meeting Date/Time: Monday 2018-09-17 at 12:00 UTC (14:00 CEST)
Meeting Duration 1.5 hours
YouTube Live Stream Link TBD
Livepeer Live Stream Link TBD

Notes (WIP): https://hackmd.io/oXOKXab8ST-m6-zgVUNE5A

# Agenda

## Part 1 - Hot topics

### 1. Whisper key & other status reserved derivation paths

Context: We have to fix what will be the derivation paths for the whisper key, the database key, and which range of derivation paths we reserve for other status use in the future. See Michele proposal and discussion here in
https://discuss.status.im/t/whisper-and-database-keys-on-the-hardware-wallet/381

Goals: check if we agree with Michele proposal in order to proceed.

### 2. P2P - Rate Limiting
Due to running on a mobile device, we are limited with setting high PoW values. This makes our nodes vulnerable to DoS attacks and spam (in a sense of sending a lot of Whisper envelopes regardless of their content). Even if we were able to set PoW to some high number, it wouldn't mean that spam is completely blocked. Rate limiting allows us to drop peers that send more traffic than we expect or we are willing to handle.

Topic rate limiting will allow users to see which topics generate the most traffic. It can open a way to "unsubscribe" from public channels functionality by recalculating the bloom filter without a particular topic.

Goal: 
- spread information about this idea as it touches chats
- collect feedback

### 3. P2P - Rethinking Mail Servers and log-based communication
Recently, a log-based communication has been discussed. The 10000 foot view of the idea is that each identity is responsible to build its own append-only log and share it somehow with its peers. Scuttlebutt is currently the most advanced solution.

We started thinking about it as a replacement for mail servers. Following decentralization principle, we should be working towards removing third parties and make nodes self-sufficient. The current offline communication solution is a trusted model which is hard to decentralize properly and incentivize people to run it.

The alternative that has appeared on the horizon is to use the log-based communication and swarm. Each node can build its own history of messages and upload it periodically to swarm network. The middle-man in form of special MailServer nodes is removed and the nodes become self-sufficient. The incentivization problem is also removed as it will be built into swarm.

What's the role of Whisper? Currently, it looks like log-based communication trade-off is latency. Whisper can be still used to send messages to provide low latency for online communication. It can also be useful for discovery purposes.

Goal: 
- collect some initial feedback
- should we start working on a POC?

### 4. P2P - Incentivization to run Status nodes
Another topic that we discussed a bit in the last two weeks was incentivization to run Status nodes. As describe above, we'd like to get rid of Mail Server nodes. However, we still need some nodes to pass Whisper messages around. Now, can Status Desktop play this role?

We started working on the documentation that will describe a process to run Status Nodes (as Whisper nodes) by the community members. It will still require some technical knowledge but currently there is zero information how to do that. It's a first step.

Goal:
- informative
- can Status Desktop eliminate a need to run Status Nodes by the community?

### 5. Swarm and PSS integration and Whisper future

Context: During EthBerlin I had the opportunity to talk with Louis, the main pss developer and Guillaume in charge of Whisper at the EF.

Guillaume would like us to try out his branch of go-ethereum where Whisper over libp2p can be tested out with a switch.
Louis was asking if we had any plans for pursuing the development of swarm light client and explained to me how we could start using pss on mobile withtout swarm sync.

As we plan on using Status Desktop internally instead of Slack, we might soon need file sharing capabilities. Desktop having more resources than mobile we will be able to dabble with Swarm and pss to see if it will be a good fit functionnality wise.

Goals:
- Check if we agree on experimenting with swarm and pss on desktop

- Check if we have resources to contribute to swarm light client development (which is almost stalled at the moment)

### 5b. Breaking Whisper

Can we scale to 1M server? #breaking-whisper

- Any specific help needed?
- Next steps? Follow up next call?


### 6. Reproducible builds
The approach of achieving status-go reproducible builds with buildID rewriting in binary. Explained in
status-im/status-go#1185 (comment) and I would love to get some feedback/ideas on it.

### 7. Whisper simulation/visualization toolkit
There was a spike in interest for the Whisper simulation/visualization tool I've been working on for a while, and I started to work on it further: https://github.com/status-im/whispervis I want people to get familiar with it and briefly describe that state it's currently in, and what should be done, and head ideas and suggestions.

### 8. Desktop
**context**
Many features have been requested by Nimbus team and others that are not in scope for Desktop 0.10.0 release yet. These are:

- improve security
- improve performance. This and previous item might be tackled by embedding Node.js/JSCore process into Qt
- private chats
- riot bridge
- address port accessibility issue
- bandwidth issues
- threads, markdown, search, permalinks
- platform issues: Windows not ready yet

goals
- See how these can be addressed or circumvented.

### 9. Chat

#### PFS

- Andrea will be merging the status-go x3dh branch with the functionality locked behind a feature flag, enabled only on nightlies. Group chat will also be enabled;
- No feedback received on [PFS spec](https://hackmd.io/I3jM-rbYRdS3Sqvwu_ATqg#) so far.

### 10. ENS Usernames
Context
Users can register an username in a Dapp
Registered users in this Dapp can be found by typing their username in "add user"
Registered users can use their username to send messages on public chats.

Goals
Define how usernames can be resolved in public chat messages
Define how usernames can enable/disable their username in public chat messages

## Part 2 - Regular - SKIP

Infra updates (infra, p2p, security, testing)
Client updates (mobile, desktop)
Research updates
Product updates (chat, wallet, dapp)
Specific ideas update
Please provide comments to add or correct agenda topics.

## Meeting "Minutes"
- Whisper Key and Status Reserved Derivation paths
    - Michele: How do we want to implement this?  See Discuss topic on this.
        - If we store the keys in diff parts, then we need to modify the applet for special cases (involve cacheing), making it more complex.
        - The main thing is applet complexity growth
        - Only mod is `export_key` command
        - We can't add keys to this list in the future without issuing new cards
        - 2nd alternative is to recognize range of keys that can be exported so that it can be updated 
        - 3rd is to ???
        - Decision: 2nd: https://discuss.status.im/t/whisper-and-database-keys-on-the-hardware-wallet/381/6

- Adam with P2P front
    - Whisper is based on PoW but we make this almost nothing so we can use on mobile
    - Adam: This is typically a defense against spam attacks, but we can't use it because it destroys batter and CPU usage. 
    - This puts our nodes in a position to receive a lot of traffic.  
    - We need something more, another layer of spam prevention.
    - We'll be able to see which room receives the most traffic to help users handle where their resources are going
        - implementation details?? go to Dmitry S
    - Corey: #breaking-whisper channel started to testing scalability of whisper.
    - Oskar: Revisit this topic later for time purposes
    - Adam: We've started looking at log-based communication
        - increased latency, not real time comms
        - `scuttlebutt` is the implementation of this currently
        - this could potentially allow us to remove mailservers
        - each peer would append messages to log and publish to swarm
        - other peers would just sync the log instead of asking mailservers
        - huge point is that we remove a level of centralization within status (kinda)
        - huge drawback is we don't have a light swarm client, it can be hard to do anything without this because we need to use http gateways.
    - Corey: what about Origin
        - Adam: what they're doing is pretty close to log-based comms but using IPFS and using PubSub.
        - We aren't sure about the details of this fof IPFS, swarm has a way to do this that is efficient.
        - these systems don't seem to be useful for realtime comms because latency, it's more for offline comms. We still need something for real time comms, whisper is currentlybest
    - Oskar: Can we do multiple things at once?
        - Adam: I think that is possible because of similarities between implementations
        - Michael: Digital Ocean is planning on load-balancing across traditional infra and swarm/IPFS, it could help here.
    - Oskar: We have no guarantees that content stays online, do we have plan to deal with that
        - Adam: pretty similar to mailservers right now (kinda)
        - Although this is poor for decentralization, even if we ask people to run mailservers because we can't guarantee people keep messages (which lead to incentivization and reputation work)
        - Adam feels as though we won't lose any functionality by moving to Swarm
        - Andrea: It's a pull model, which means I ask for what I'm interested in.
        - This is hard for a chat, and scuttlebutt hasn't work for chat, especially for darkness.
        - Whisper protects the publisher, which is necessary for darkness, which is fundamentally hard to do based on a log-based model.
    - Adam: we also thought about the idea that the head of the log is not attached to an identity, initially share hash using whisper.
        - Andrea: it is the same if that is discovered
    - Iuri: suggestion regarding mailservers.  We could do a service node and allow people to run them.  Implement a promise in a contract and a deposit.
    - Adam: we also had the idea of desktop node that is a mailserver and a reputation system (incentivization).
    - Pedro: concern with moving to swarm is with push notifications:
        - mailservers were supposed to be part of infra for push notifications, swarm doesn't allow for this.
        - Oskar: good point, if we can find a way to spread the data so it doesn't matter which mailserver you connect to then it would be ok
        - Adam: some hybrid solution where mailservers use swarm/IPFS to hold and store data.  Also described in discuss post (PLEASE LINK HERE SOMEONE)
        - Igor: mobile nodes can also write to IPFS/Swarm.  There is an inherent tradeoff between darkness/traffic.
    - Corey: can we have different modes of comms:
        - Oskar: we've thought of this before, but there hasn't been any push to flesh it out. 
        - Ricardo: Maybe just by having the option, we might give info in the use of darkness by traffic analysis
        - Maybe we could try to fake this by randomly sending dark messages/etc
        - Eric: We can experiment with this with Desktop because we don't need swarm light client
    - Andrea: personally, it isn't well suited for what we need in terms of providing a service as Status.  We need an objective, what do we want to do?
        - Adam: We want to get rid of mailservers because they're hard to decentralize and incentivize people to do it. 
        - Maybe building mailservers with swarm maybe makes sense, that's the reasoning behind this convo.
        - Oskar: two different convos here, we should separate them. 
        - Jacek: two things: Andrea started to make the mailserver work with Swarm.  Also log-based comms is a ground up situation that can't be tacked onto how we do things now.  The most imporatant thing about it is that each person stores their own log first.  In order to make comms easier is to might add something like ipfs/swarm/mesh/etc.  Doing this is a diff product.
        - You can get to normal latency by using tricks, and then it degrades gracefully as you lose those tricks. 
        - Andrea: latency can get to something reasonable, but it is a pull model, which makes some things difficult, which needs to be thought out from a product perspective.
    - Oskar: can someone own this and write up a process?
        - crickets
    - Ricardo: The natural solution I always saw about this was that Mailservers would be mostly "notification nodes" as messages would be stored in Swarm. However I also see Mailservers as a "replacement for Swarm" in some cases.
- Adam: working on solution to incentivize people to run status nodes
    - starting with documentation
        - Lot's of work here.
    - also working on mailserver issue
    - status desktop is currently high priority, which could be useful for mailserver issues, but requires people to use Status-desktop
        - Eric: we should have 100 nodes next month... a good start.
- Swarm/PSS integration
    - Eric: 
        - 1. Guillaume (EF) thought we should try libP2P instead of devP2P.  Igor is working on this right now
        - 2. Jacek talked about mutable resources, Louis made a project for a collaborative pong game, look at the code instead of starting from scratch. 
        - If we want to experiement with swarm stuff, we should start with status-desktop.  If we need swarm light client, then we should contribute to its development otherwise it won't happen. 
            - Jacek: They are having trouble defining what an actual light client is, so there is research there.
            - Ivan: There are currently in very first steps towars what that is, but nothing we can use yet.
            - Jacek: maybe we work on it then, isntead of waiting on them
            - Ivan: They want our help, but for us it is much harder to provide the initial client because we don't understand swarm at the depth in which they do.  It requires more time spent by someone to become a core developer for Swarwm, hard with bandwidth. 
    - Oskar: Maybe we don't have resources to contribute, more immediately, we can start to experiment with desktop already, is this reasonable?
        - Ivan: It makes sense.  Light swarm will be available in half a year maybe, we shouldn't wait for that.
        - Oskar: Eric what do you think?
            - Eric: 3 things:  LibP2P switch is an ongoing effort, whisper is the test subject for this, watch Guillaume (EF) for this.  2nd thing, swarm itself.  Sharing files using swarm on desktop client. 3rd thing, consider PSS as alternative to whisper since it is designed for E2E comms.  We can start by trying to use swarm and then we'll see about PSS.
                - Oskar: you want to own this?
                - Eric: Sure, on it.
                - Oskar: can you write up an idea for this, others can help
                - Eric: OK
    - Oskar: other thoughts
        - Corey: if you care about breaking whisper, or know about whisper, please join the channel and contribute.
- Reproducible builds:
    - Ivan: we want to have reproducible builds so people can check if they've built the product correctly from source
    - Slides (PLEASE LINK HERE IVAN)
        - please direct questions to Discuss post (PLEASE LINK HERE IVAN)
        - Corey: can we publish a hash and have people check it easily?
            - I think so (corey's thoughts)
    - Ivan: we need someone to breakdown our build process first, because it is difficult to understand.  Status-react is a hard to get right in comparison to Status-go
        - Oskar: start by building it and seeing what changes at a high level, dep/folder step by step (tree and md5 shell script), attack those first. Should work in parallel with Stasus-go work.
- Whisper Simulation/Visualization Toolkit
    - Slides (IVAN PLEASE LINK HERE)
    - Ivan: Related to #breaking-whisper channel
    - we have poor intuition on P2P and Whisper propagation/load, this is the motivation for this work.
- Desktop
    - Vitaliy: Opinions on further desktop development?
        - we should focus on the security of funcationlity
        - we have issues with performance, this needs priority
        - Status-desktop may be an Eth node
    - How are we going to cope with situations after transition happens?
        - Jacek: a lot of projects can be solved by bridging.  In Nimbus, we have no means to fix the bugs we find.  Dogfooding is to find bugs quickly and then fix them.  
            - we have a lot of community outreach (nimbus) which would be hard to include in Status desktop currently. 
        - Corey: Private group chats, solutions?:
            - email until it's there.
            - Ricardo: release past keys for disclosure
            - Andrea: Some ratchet the key for this
    - Vitaliy: We need to talk about security
        - What happens if we move to status desktop and we don't have spam protection, or private groups?  What do we do?
        - Oskar: Have we considered writing a Nim desktop port?
                - jokes
        - Is there any protection mechanism here?
            - Jacek: that was the original motivation to move to slack
            - one way to handle this is to only use private group chats
                - increases barrier of entry
            - Vitaliy: can you boot people?
                - Eric: No but you can ignore their messages
                - We should have a few weeks before spamming becomes a thing
                - we can use filters and keyword banning, but this only UI banning, and not whisper banning
                - Ricardo: wrote something on this https://discuss.status.im/t/visibilty-stake-for-public-chat-room-governance/133
                - Need to deposit to have messages visable, spammers get slashed.  Also allows to earn SNT by contributing to finding bad actors.
                - We need to decide what kind of enctryption method
                - Corey: look into proxy re-encryption
                - Andrea: suggests looking further into them, it could potentially not help us that much.
                - Jacek: Andrea makes good points here. 
                - We would be very interested in having a meeting to discuss this further with them. 
                - Ricardo: common shared key methodology
                - Jacek: Let's move on
- ENS Usernames: 
    - Ricardo: When you have public chats, users that register might want to have username display, or not.  
    - 1. We need to solve how we can reverse-find the username.  2 problems:
        - 1. ENS usernames are hashed. 
        - 2. Public Keys don't resolve to ENS usernames 
        - Most simple solution to solve is when a user wants to identify themselves in a chat, they send with the payload the username in plaintext so clients can check ENS registry
    - 2. Disabling the username. 
        - I have an idea of just not sending the payload of usernames and acting like not registered user, however users that know that contact username could see the username even disabled.
        - Maybe we can have a "private mode" which not only disable the "ens username" payload, but also use a volatile whisper key - maybe derive a new one each message/minute based on time + whisper seed. (might cpnflict with visibility stake)
    - 3. Discuss how we will implement usernames in Status altogether.  
    - Do we need to start a new swarm?
        - Oskar: We'll start to talk about this in the 151 channel

    END NOTES
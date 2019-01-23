---
tags: core dev call, meeting notes
---

Agenda https://notes.status.im/sSwbEGg9TEWfxpOnLMPE_Q
Swarms https://github.com/status-im/swarms
Recording: https://www.youtube.com/watch?v=HVylXrDBJHg

# Dev Call Notes

## Igor
- not much happeneing today
- heavily in research phase on how to incentivizee new use cases
- set up deadline to finish by end of jan
- more of less asking around at this point
- people
    - andrei
    - igor
    - andrea
- https://github.com/status-im/swarms/blob/master/ideas/316-core-networking.md

## Sticker Market - Julien
- pretty much the same
- had a call earlier to today to kickstart conversation
- plan to have one week research but extend
- just started, not much to share
- https://github.com/status-im/swarms/blob/master/ideas/313-sticker-market.md

## Tribute to talk - Eric
- Chat team update
- plan to TtT 
- right now we have to check contracts and designs
- working on list of top priorities
    - plan to work on them for MVP
    - each to 90% so that only polish left
- before we go to less priority, polish
- high priority features, we put
    - ens name in chat
    - reactions
    - mentions/notifications
    - ????
    - sending images through some extension
- [oskar] notifications, same as core team work?
    - no, more like design of notification of mention
    - replies to posts, people saying your name, etc
- [Julien] are youp lanning to send image as part of message payload or external resource
    - external resource like gifycat 
    - extension comes with warning of metadata guarantees
- [Ricardo] wants to join discussions on TtT
- [Oskar] put meetings from swarms in Status Calendar
- https://github.com/status-im/swarms/blob/master/ideas/314-tribute-to-talk.md

## Dapp Store - Julien
- Not much, hasn't started yet
- Andy should be leading this
- Dapp store implemented as a dapp
- [Oskar] anyone know more details on this?
    - we can wait for Andy
    - [Rachel] Bonded curves and SNT staking
    - [Jarrad] pretty sure no contracts yet
- https://github.com/status-im/swarms/blob/master/ideas/317-dapps-store.md

## Teller Network - 
- No one around to talk about it

## Core Improvements - Igor
- in general, a lot of work, but it's stuff we were working on before
- integrate and fix bugs from mailservers
    - reasons why you would receive PN with no messsage
    - no mailservers that miss messages and we dont know about it
    - created method for syncing mailservers (new and old)
    - found a few bugs like local time and such
- Roman was working quite a lot on slow sign in time
    - he had a list of 12 or so items, there are only 2 left
    - today we should merge 2 or 3 PRs and only a few more things to work on

## Protocol Update - Oskar
- data sync layer discussion 
    - https://discuss.status.im/t/introducing-a-data-sync-layer/864
    - general idea is separate data sync layer to make easier if we move away from whisper
    - should go through post
    - also touches on things that igor was talking about with state of mailservers, this change means we "don't need mailservers"
- working with outside collaborators for a workshop
    - proposal for that is end of Jan 29 to Feb 1 in Brussels
    - Riot chat https://riot.im/app/#/room/!hihNpRPSwQUkWvIJxS:matrix.org and #status-protocol
- [Ricardo] questions on state of mailservers
    - how do you define the state to sync on?
    - [Adam] current state is looking at what IDs those mailservers have
        - there is a crosscheck, if some is missing, sync them. 
        - nothing more advanced than that. 
        - current tests are pretty consistent, new mailservers are mainly the issue
    - [Oskar] The idea we're talking about is not getting rid of them, but not making them so pivotal 
    - [Ricardo] isn't that kind of the reason with PoS and PoW
    - [Adam] We aren't sure about mailservers all together, that's why we haven't spend a ton of time on them. 
    - [Ricardo] so it looks like we need something like sharding, that's what I was thinking about
    - [Oskar] Yeah, this seems like two different timescales on the projects

## DAO - Barry
- Basically we're researching current contracts deployed by giveth
- it implements all functionality at this point with profiles
- implemented insights to see how funds are being moved from pledge to pledge
- working on a dashboaaa

## Janitors - Oskar
- essentially done to figure out state of each swarm
- most everything in pivotal tracker
- if you don't have access to this, ping #312-janitors
- [Igor] who is responsible for keeping backlog/state in this tracker
    - [Rachel] Me and Nabil will try and keep things up to date
    - [Igor] ok
    - [Oskar] if this creates lot of extra work, we can figure something else
        - set tasks and their complication, then get estimates of time constraints
        - [Igor] velocity only works for stable teams, which can become useless in our scenarios
        - [Oskar] one thing to do is try and keep track of who is available, especially during this holiday season

## Browser - Julien
- essentially we finished our sprint we were working on
    - mostly around low hanging fruits around browser issues
    - missing features and broken stuff
        - discovered cookie and local storage persistance ????
- also working on kyber extension to make sure necessary bits were implemented on extension side
    - almost finished but need some lower level stuff to finish
    - shifting to sticker markets, so it won't be prioritized

## Desktop - Volodymyr
- this week we are finished release version of desktop
- most issues have PRs in progress
- team proposals we have prioritized list of tasks for swarm to work on next
    - LINK HERE PLEASE

## Wallet - Goran
- focus is on redesign changes tightened up and merged
- a couple EIPs being finished up

## Keycard - 
- no one around to answer

## Research Nimbus - Jacek
- no updates

## Security - Corey
- I'LL FILL THIS OUT LATER

## QA - Anton
- working on blocking PR to be merged
- one more thing to be fixed by wallet team
- no possible to be done in complete automated way
    - but try to move things to automation as much as possible
- also working on ????
    - didn't get this

## Anything else?
- [Ricardo] would like to hear more about public chats that 
    - [Oskar] like partitioning topics?
    - [Igor] that's my topic, it's group chats all being in single topic
        - this is causing a large data load for a single group chat because you have to partition it somehow, but might have problems with darkness of public group chats
        - probably focus on after xmas holidays
        - I've seen you discuss this with Andrea in dicuss conversations
    - [Ricardo] Also this could be impemented with Status JS to test it or prototype things
        - [Igor] also thing this should be implemented soon as possible because we can't release in public without group chats that are usable. 
        - [Ricardo] Do you think we should have some more definition about these specs?
        - [Igor/Corey] Have swarm to discuss the spec in detail so everyone can be on the same page
        - [Igor] This should be on Core Improvements
- [Oskar] did we figure out what was going on with traffic with mailserver
    - [Igor] if mailserver times out we re-request everything and it times out. this makes a large repeat process.
        - There is a task in message reliability about this
        - hasn't been started but it's there

## Julien
- implemented filtering based on Google API to detect fishing websites
    - discussed with Corey and Igor a couple weeks ago
    - conflicting security with privacy
    - must rely on some API to increase security of browser
    - [Igor] you can always make a wrapper that cuts the headers for the API so they can't see things.  Maybe there is something better
    - [Oskar] would it be possible to make it an option to turn off/on
        - [Julien] yes for sure
    - [Ricardo] What about local storage of websites you visit?  We should try to give the user more control over that. Try and have true anonymous browsing
        - [Julien] It certainly an option but not sure about priority.
- [Corey] set up a call
    - [Julien] the point is the governance of how to come to these conclusions
    - [Igor] there are new versions that have security and privacy updates
        - https://developers.google.com/safe-browsing/v4/update-api
    - [Oskar] we really need to document to make sure we understand tradeoffs and they are made explicit
        - ARD: https://github.com/status-im/status-react/tree/develop/doc/decisions - should probably live in docs

## Anything else?
- [Ricardo] with TtT, I think we should use a captcha for users
    - doesn't rely on API, when user doesn't have contact in list, it should ask for captcha
        - if Alice wants to talk to Bob, Bob gives her a generated Captcha that she has to solve before messages are sent
    - potentially more straight forward than TtT
    - what you can do for free users
    - [Igor] small grayscale images or text.  question is how to generate.  Shouldn't be hard to generate
    - [Ricardo] potentially every user has their own created capture, scanned image and corrupt part of the text
        - I guess implementing this would start with open source implementation if there is one
        - the only hard part is building the captcha system that is inside of the clients
    - [Igor] if implemented in native code, it shouldn't be that difficult, they have good libraries for image and text manipulation.  Different, but relatively simple to do, and openGL if you want. 
- [Ricardo] Status JS noticed a lot of lack of documentation on how things work.  This would also help security quite a bit
    - [Oskar] we have something like this for PFS, and then start working on things like it with PRs to docs site. 
    - [Oskar] for example, I would like to know how ratcheting works in Status, I'm not sure, I want a place to go to figure that out. 

https://github.com/status-im/swarms









- bumper
---
title: Status Devs Meeting 6 Notes
tags: meeting-notes, core-devs
---

# Status Devs Meeting 6 Notes

Meeting Date/Time: Monday 2018-10-15 at 12:00 UTC
Meeting Duration 1.5 hours
YouTube Live Stream Link https://www.youtube.com/c/Statusim/live
Livepeer Live Stream Link TBD

## Agenda

Top 3 issues from voting dapp, ish

### 1. DappNode demo and running a Status node

#### Context

Dappnode.io has setup a status node on their platform. This means that users who have dappnode running may setup a status node at a click of a button.

#### Goal

1. Show how to run a Status node and connect with it
-- which capabilities?
2. At least 5 core devs should be aware of how to do this
3. 5 people commit to trying it out

### 2. Extra: Mailserver availability and responsiveness?

#### Context

Last week we've seen multiple reports of bad availability and slow responsiveness of multiple mailservers. Additionally, there's been a lack of responding to it and serving our users, thus leading to frustration. It also seems qualitatively like we are below our SLA, and if not that we should adjust. E.g. 500 concurrent connections to cluster should be no problem with reasonable responsiveness, and 99%+ uptime of mailservers.

#### Goal
1. Gather information on what the problem is
2. Understand current monitoring and what is lacking
3. Decide on actions and owners needed to ensure we provide a good experience for users, e.g. reasonable uptime and responsiveness


### 3. Status automation

#### Context (saved you a click)
One of the great strengths of Status is it's automation and integration. With transfer to Status me, and other people too miss a lot of the features (kudos, searchable archives, etc).

Let's discuss the way we can implement and deploy these bots.

Also, we might want to provide a simple way to write bots for extenal people too.

- Should it be Go re-implementation of our protocol?
- Should it be a generic Whisper bot?
- Or should the bots be Go+Clojure?
- How do we host them?
- What documentation do you (as a potential bot author) want.

The list of bots we want to have:
* Searchable history of Status channels, later integrated with Slack archives too;
* Zapier integration to post messages to Status from Zapier;
* Kudos bot;
* Github Integration (PRs, issues, repositories notification);
* Fastlane Integration.

See https://discuss.status.im/t/status-automation/545/11 for more

#### Goal

Be on a same page about how these bots should be implemented and how to survive protocol changes. 

1. Decide on how we want to implement these bots
2. Discuss how to ensure they are future-proof
3. Decide on how to scale this effort with the community

### 5. Quick announcements

- Oskar: OKR season have a thinkabout
- Oskar: Whatdoabout next call?
- Andrea: Bus factor Jenkins
- -- also runbooks, monitor basic howto

## Notes

### DappNode demo
Should we skip this one for now. There are some tech difficulties.
Later update:  This would enable an easier starting curve for people to start their own nodes.
  - Graeme: can send an invite for a tutorial on how to get a DappNode up and running on DigitalOcean.
  - Adam: tried it on DO, it's pretty easy. The prerequisite is VPN configuration. Not sure whether the node sync if light or full. Everything runs inside a Docker container.
  - Oskar: is VPN necessary? **Open question**
  - Adam: not sure
  - DappNode are the owners of Status node package, so in order to update the version contained thereid, they should be contacted first. We can work with them to move the ownership of the package to Status.
  - Igor: what exactly does the Status node do?
  - Adam: it's configurable. Right now one can switch between Whisper, relay node, and mailserver mode. Packages are built and configured by a smart contract, so package definitions are stored on a blockchain. A bit bad for the people who want to try it out, because the need to wait.
  - Dmitry: a question - is it possible to make a node discoverable? Is public IP available? If not, it would be of little use.
  - Adam: Whisper node is registered to the cluster by default, so it's a part of the network. Most likely it just uses the server IP. It must be public.
  - Adam: the node can definitely connect to other peers, the question is whether other nodes can connect to the DappNode (in reverse direction)
  - Igor: WebRTC might be worth looking into
  - Oskar: DappNode might be more of an UX thing, if one runs it on a server with a public IP
  - Dmitry: yes, in that case it will be discoverable and there are no problems with that
  - Dmitry: there is Go impl of WebRTC
  - Igor: we could port a C++ impl
  - Graeme: DappNode does not yet work on RaspberryPI

### Mailserver availability and responsiveness
  - Oskar: seeems that we are not meeting our internal goals on availability. Let's find out what our problem is, what can we do about it, setup monitoring, determine owners for subtasks, etc.
  - Eric: last week things have changed. Before the change, app was sending messages to the mailserver, then 'Fetching messages' would appear. Now that we have signals, we see the timeouts that probably occurred before but were ignored. Maybe timeout is too large. One of the things we could do (and Andre is already working on it) is to allow the app to request multiple topics at once. We'll also be looking into sending multiple messages at once. Eric is working on mailserver-related changes (fetch at once instead of consecutively)
  - Oskar: what's the reason for timeouts?
  - Eric: after 10 seconds, if not all messages were received, we get a timeout. We should have received all messages after 10 seconds, so most likely the consecutive sending is the culprit. Maybe the acknowledgement of received messages is the reason, because then we do roundtrips for each messages. Not sure about exact impl.
  - Adam: when sent one-by-one, it should be pretty fast. There is no acknowledgement. Number of messages is not that huge. Hundreds at most. Not sure about the exact reason behind the slow passage of messages. Working on it right now. Whisper always sends one envelope at a time, it was never redesigned.
  - Oskar: are there any availability issues that could cause slowness?
  - Adam: it should be fine. The only thing that changed is number of messages in the channels.
  - Chad: had a lot of messages getting lost. Also got explicit 'could not connect' errors. Very often, 'fetching messages' is visible constantly.
  - Adam: Desktop is indeed slow when downloading messages, but never experienced lost data or errors.
  - Chad: how many chats do you have on desktop?
  - Adam: around 10; Chad: around 50-60
  - Oskar: can we get some monitoring for this?
  - Adam: I'm building this. Need to determine how many concurrent requests we can send. Like stress testing mailserver nodes.
  - Igor: what about peer drops?
  - Adam: most likely not peer drops, potentially a problem in the logic itself. We do not have monitoring yet on the server side to count the number of timeouts. Average response time is monitored on the server side, and in most cases it's <2 seconds
  - Chad: per out stats, we do 2000 messages per day.
  - Adam: we might need to divide it by 3, because we have 3 bots

### Status automation
  - Igor: we lost different types of automation after moving from Slack to Status. We used to have bots that could post to/read from channels. The idea is to create one example bot that would be nicely documented and have a hackathon to evolve this idea to think about kinds of bots we want, and implement them
  - Igor: we have frequent changes in the protocol, this is a hindrance. We'd need to have a more formal spec for protocol, but on the other hand, we need automation now.
  - Igor: need to raise awareness, that if protocol is changed, bots will break.
  - Adam: current StatusGo SDK assumes that there is a Status node running somewhere. Tried to write bots that run a Status node in an embedded fashion. It was pretty nice, but it would imply that bots are written in Go. Maybe a permanent node running somewhere could work
  - Igor: would we then need to have a statusgo_api module? Other langs would provide thin wrapper around it
  - Ricardo: we'd need blockchain/contract support
  - Igor: initially, only Whisper is needed for the API functionality required by bots
  - Ricardo: would be nice to support blockchain events
  - Adam: that's a good point, because without blockchain support in the API it is necessary to use something like Infura whenever blockchain access is needed
  - Eric: what's the status of Node bindings?
  - Igor: haven't heard about Node bindings before.
  - Eric: most probably the swarm has died out. We could reuse a part of Status's codebase
  - Dmitry: don't understand the role of bindings
  - Eric: e.g., create account, something not directly doable via RPC. Dmitry: it's already available in the API.
  - Igor: should bots be Status nodes, or Whisper nodes? Current StatusGo API should be exposed via RPC
  - Ricardo: extensions should be written in a simple languages that is in many other places.
  - Adam: if we decide that Status node is required, it is a shortcut. For the future it is not enough. The API would e.g. allow to replace Whisper with something else behind the scenes. It could be configurable to e.g. use libp2p or Whisper
  - Igor: there should multiple generations of both approaches. Maybe it's too early to start a hackathon. More internal work is needed.
  - Adam: for now we need a working implementation of some functionality for a bot. Agree that we need something very simple.
  - Igor: maybe we can add this as a requirement for the new protocol version
  - Oskar: what about Ricardo's suggestion to provide blockchain support?
  - Ricardo: status node can process a blockchain event and broadcast the message to channel(s)
  - Igor: right now the bot will still need to sit on top of Status node.
  - Oskar: we should assume the current version of the protocol for the initial bot implementation.
  - Graeme: how can one identify the authenticity of a bot? E.g., Status voting dapp bot - how can we validate it?
  - Ricardo: Status node can sign a message with its public key.
  - Graeme: thinking about the user who has no idea about what's happening in the background. In the future we might also get multiple accounts impersonating as bots in order to phish user data
  - Igor: yes, need to have protection against spamming/phishing.
  - Igor: initial bot implementation will start with a Go version. It should operate on a high level, without references to underlying Whisper.
  - Oskar: can we write up some high-quality use-cases for the hackathon?


### Announcements/other
  - Graeme: would love a feedback on the voting dapp
  - Adam: voting is great for e.g. selecting topics.
  - Ricardo: price of ENS names. 10 SNT was suggested. The registration price is just a security measure. It should at least compensate for the gas price. Also, we should know what is the launch timeline, this would impact the price.
  - Eric: who pays for the name (user or contract)?
  - Ricardo: we can discuss this later
  - Oskar: would be useful to think about OKRs prior to the hackathon
  - Let's skip the next call
  - Andrea: we need to think about ownership of build process in Jenkins.
  - Igor: there is no way to debug build process on Jenkins locally.
  - Jacob: yeah, this is mostly a trial-and-error process. One of the pain points is macOS slaves. I'm working on it right now.

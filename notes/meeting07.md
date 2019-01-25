# Coredev Meeting 7 Agenda

###### Tags: `Coredev Call`  `meeting notes`  

#

| Status Devs Meeting 7 Agenda ||
|------------------|--------------------------------|
|Meeting Date/Time | Monday 2018-11-19 at 12:00 UTC |
| Meeting Duration | 1.5 hours |
| YouTube Live Stream Link | https://www.youtube.com/c/Statusim/live |
| Livepeer Live Stream Link | TBD |



### Agenda

1. New teams structure and what it means in technical terms. (Igor) [15-20m]
https://notes.status.im/k0xVSu6nRvS5p0UAWV__BA?both

2. Engineering/Process fails: [15-20m]

- a)   (status-im/status-react#6764)
- b) Automated tests still not reliable (status-im/status-react#6764 (comment) and status-im/status-react#6731 (comment) and status-im/status-react#6752 (comment) for three random PRs that all don't provide 100%, unlikely all of these PRs are broken)
- c) https://github.com/status-im/status-react/pulls too many PRs open - close if open for too long - what happened with ROD? - several PRs from community contributors just dropped ball completely
- d) Also more generally re leveling up engineering practices with PRs (testing changes etc).

3. We can discuss libp2p integration. And making a network from desktop devices. [15-20m]
I tried to summarize why and how in this document https://discuss.status.im/t/libp2p-goals-and-integration-plan/698. I would like to know any concerns around it. [15-20m]

4. Mini announcements [5-10m]


## Notes

### Welcome!


### 1. Need to discuss reorg changes.
 - Igor: there were slight changes. There will be several different areas of responsibility. All core team responsibilities are going to be split across several teams. Need to discuss how it will affect things like codebase, repos, processes, and tooling.
 - Someone said that "code structure should follow team structure". Biggest pain point was during team sync. Need to separate code modules more. E.g., CI is an example. It might ensue in extra effort, but this is needed in order to overcome team sync penalties. What is other folks opinion on this?
 - Oskar: what are other team leads opinions about this?
 - Goran: with respect to CI for instance, problem is not modules, but platforms. Builds sometimes fail for obscure reasons. Perhaps don't understand the whole question.
 - Igor: we know what teams are, we know their responsibilities. But how will it affect their day-to-day development?
 - Pedro: one example would be a separation of chat protocol into separate parts, instead of leaving it inside status-react.
 - Igor: yes, so we need to discuss whether we need to do this, and if so, decide on further steps. 
 - Bruce: there are different degrees of separation. We can take steps towards the separation without it being drastic. Some things are really hard to separate. Even within the same repo, things will need to be pulled apart. It may turn out that some things cannot be separated. Moving things to another repo is a difficult one, it's not an easy lift. Examples are separate some parts into Go modules, or creating React components and extracting them from status-react.
 - Goran: how do we deal with shared stuff? E.g., stuff that is shared between chat and wallet.
 - Bruce: Eric did a lot of work to move subs higher, making components below dumber, they just pass data. They know nothing about re-frame, they just pass data. They are pure stupid components. 
 - Oskar: moving things like Wallet into dapps would be useful. If we have network and people have different abstractions, Wallet then would be just another dapp. What are people's thoughts on that? It could be extension, dapp, RN component. A useful property would be trust minimization
 - Goran: we used to have a great deal of confusion about dapps.
 - Jacek: one of the reasons I've been driving the protocol work so hard is that Status OS should not be doing that much. Lots of principle tradeoffs can be delegated to developers. If you look at Android, you have both FB Messenger which is egregious with regards to privacy, and other better tools. It is essential to develop Status with this OS mindset.
 - Bruce: these things seem to conflict on some fundamental friction points with where we are now. These are far-reaching future ideals, they don't speak to what we are going to do in the next 6 months. Moving to a dapp does not get us closer to a well-behaving wallet for instance, as the technology is not really there. Right now I don't see web extensions or dapp behaving in a way people would want them to behave. It makes me feel uncertain about the goals, what are we trying to do? I don't see those technologies as mature and available. I do see the possibility to make APIs with a solid boundary. Make UIs less knowledgeable. UIs are difficult, they require a lot of code and tweaking.
 - Michael: speaking to the point of general unspecific things. Status as a company with wallet as a product, how do we solve the problem of the need to collect customer data.
 - Goran: what is the definition of a wallet? I've seen 3 definitions. First is safe storage for keys, this is the most minimalistic one. Second one is a client used to access Ethereum and sent transactions (practically, a UI for Ethereum). Third one is a server-side app that manages your account. In a mind of a part of users, wallet is a container where funds are stored. What do we specifically mean when we say "wallet"? We need to set a bar on how much we want to offer natively, and how much we need to provide as an extension. Maybe we'll need to rename some concepts, as names are powerful and concept-defining.
 - Michael: e.g., signing is essentially a notary function without a notary. Maybe we can separate signing/notarization and asset storage as concepts within the application.
 - Corey: a wallet is a password manager. This is a problem with a whole field. Changing names to better match what they actually do is a good idea.
 - Goran: Status needs to have access to the network, so there are keys on one side, network on the other side. If we keep an OS analogy, we'd need to enable file system access, with blockchain being the file system.
 - Corey: the app itself is the access to financial services.
 - Bruce: regulatory bodies will move goalposts continuously. 
 - Nabil: agree with both Bruce and Corey.
 - Jacek: isolate controversial behaviour from the non-controversial. It will move potential attack surfaces to corresponding apps. E.g., Status wallet gets attacked, but not the chat. Bundling everything in a single app will provide multiple simultaneous reasons to shut down the app.
 - Michael: a suite of products. We can return to the roots of Status as a mobile Ethereum OS.
 - Jacek: we need to have a shared understanding of what/how/why we are doing it.
 - Chad: our legal counsel Sonya is working on some of these issues.
 - Oskar: what are people's thoughts on dapp/product discussion?
 - Bruce: would be nice if people drew some whiteboards, so that to present what's on their minds.
 - Oskar: maybe we can have a separate call to continue with this discussion.
 - Igor: any volunteers to write the Discuss post?
 - Oskar: let person who feels like it start conversation

### 2. Engineering/Process failures
 - Oskar: we need to adhere to a higher standard. We can take this opportunity of reorg to set a higher standard for ourselves.
 - Pedro: the person who's writing the issue description needs to think about all the stakeholders down the line. Need to make the description as complete as possible. All the reasons to fail the PR should be contained in the issue description. It might delay us in the short-term, but should increase the team speed in the long run. For instance, push notifications on desktop did not have a descriptive text. It should have been specified in the issue, and could have been caught during PR review. Need to have tests so that we don't have regressions. It's about taking things the whole way to the end.
 - Goran: we need to have screenshots in PRs. Some things become very obvious if they can only see a screenshot.
 - Pedro: I am a big proponent of actually running the code during review.
 - Oskar: I see very few PRs being rejected. Maybe people don't want to be seen as an asshole. But negative feedback applies to the code itself and shows care for the end-users and code quality. We need to change the attitude so that PRs reviews are not treated personally.
 - Oskar: what about reviewer-of-the-day? There are 2 PRs from community members hanging around for a long time. In this case it was us dropping the ball.
 - Pedro: in one of those cases, contributor received an email about failed build, but probably it was not enough. Should we extend the bot filter to close PRs in addition to issues?
 - Goran: if a PR is good, but we want to add something to the PR scope. Not sure if this a fair thing to do for bounties. You get a sunk cost dilemma. In that case a fault is entirely on our side.
 - Goran: PRs in WIP, what to do with them?
 - Oskar: close them 1-2 weeks of inactivity.
 - Goran: probably a good idea. 
 - Vitaliy: what's the point of WIP PRs?
 - Pedro: e.g., checking if there are no issues with Jenkins builds. Also, good to start a discussion.

#### End-to-end tests
  - Anton: PR #6764:cloud infrastructure issue ([Errno 110] Connection timed out), rare occurrence (~3 builds per year were affected) anyway I am going to contact SauceLabs in order to find a way of avoiding such issues
  - PR #6731; #6752: `test_network_mismatch_for_send_request_commands` - is an issue in product 
  - https://github.com/status-im/status-react/issues/5975 `test_back_forward_buttons_browsing_website` and `test_offline_messaging_1_1_chat` - is an issue in tests, tests are disabled in https://github.com/status-im/status-react/pull/6773 until being fixed
  - All tests which are false failures more then once in any PR will be disabled until being fixed
  - Eric: in cases when PRs break the tests due to new functionality, either a commit in a PR to fix test, or a separate PR is needed.
  - Anton: tests can be fixed by QA team, but it would be good to provide accessibility labels/IDs to simplify writing tests.
  - Pedro: then the issue description should specify the need for those additional IDs.
  - Oskar: we need to get to 100%, this needs to be tracked.
  - Anton: PRs should take care of fixing broken tests. Also would be great to have a Github bot posting the results.
  - Oskar: Pedro, can you please help with the Github bot?
  - Nabil: not on the agenda but quite timely are OKRs. Not a lot of visibility how teams are operating, beyond the HackMD doc.
  - Oskar: there was a core call earlier today, meeting notes will be posted to discuss. What about Chat team:
  - Chad: we will have the call tomorrow. We will start looking at OKRs after there is more clarity into team responsibilities.
  - Jarrad: definitely too early to talk about OKRs now. 

### libp2p
  - Dmitry: probably makes sense to skip.
  - Jarrad: a bit unclear on what is the goal.
  - Dmitry: main benefit of using libp2p is using tools that people already have. There is no technical difficulty running libp2p connected to devp2p, and vice versa.
  - Iuri: we also want to integrate libp2p. Hopefully, this way dapps written in Embark could connect to ...
  - Jarrad: are we talking about Status daemon running on a server as opposed to client app? We can consider devp2p to be deprecated in the mid- to long-term. I am concerned about resource consumption.
  - Dmitry: there is no additional overhead in maintaining another Kademlia network. We limit the number of peers we connect to, and we stop discovery once that threshold is reached.
  - Adam: the overhead is marginal. We are collecting metrices on these things.

### Mini-announcements
  - Bruce: it's snowing here :)
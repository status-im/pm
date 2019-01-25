## Status Devs Meeting 2 Agenda

**Meeting Date/Time: Monday 2018-08-20 at 12:00 UTC (14:00 CEST)
Meeting Duration 1.5 hours
YouTube Live Stream Link TBD
Livepeer Live Stream Link TBD**

Notes (WIP): TBD

## Agenda

**Focus on: discuss and decisions about future, as opposed to things in the past**

### Part 1 - Hot topics

1. Light clients: LES and ULC.
Context: Currently there's a bit of a disarray w.r.t these efforts - it isn't clear who or what team is owning it or what our deliverables are. Having 10% of users use LES/ULC in app is a p0/p0 OKR, so we need to be clear about what we are doing here, both on a short and longer time scale.

    Goal: Discuss approach, reach consensus on way forward, and decide who is leading what focus.

Reading:
- https://github.com/status-im/status-go/issues/1025
- https://raw.githubusercontent.com/status-im/status-react/develop/doc/decisions/0003-geth-node.md
- https://github.com/status-im/ideas/pull/295

2. Desktop/Mobile code sharing and automated testing.
Context: We've recently started sharing code base between desktop/mobile, and there are some childhood illness issues related to this.

    Goal: Discuss and outline next steps.

3. Hardware wallet (Javacard, light)
Context: We want to support hardwallet for Devcon. This requires a lot of coordination across HW/dev/security/ux. This is not captured in current OKRs or priorities among teams. Additionally, we also have a HW wallet pro.

    Goal: Discuss roughly what we need, unknowns, and figure out team and point person to this. Rough timeline. Understand relationship with HW pro wallet.

Reading:
-
 https://docs.google.com/presentation/d/1r27RoYKQ1TQtxByGKyFGlLWcb5AtDziXi_1qIqzuQH8/edit#slide=id.p1
- https://discuss.status.im/t/javacard-hardwallet-user-stories/307
- https://github.com/status-im/design/issues/18
(- https://ideas.status.im/ideas/229-hardware-wallet-pro)
(- https://github.com/bitcoin/bips/blob/master/bip-0049.mediawiki#public-key-derivation)

4. Security.
Context: We are starting to take security more seriously with a holistic view and process.

    Goal: Discuss pyramid of pain, etc. Understand current dev/org pain points and next steps.

5. First step towards a DAO. (unconfirmed)
Context: We want to become a DAO. First steps are around voting dapp, liquid pledging, etc. There's also an experiment with Gitcoin.

### Part 2 - fish net (no specific need expressed)

6. Infra updates (infra, p2p, security, testing)
7. Client updates (mobile, desktop)
8. Research updates 
9. Product updates (chat, wallet, dapp)
10. Other specific ideas
- 289 Deterministic builds (https://github.com/status-im/ideas/pull/297)
- 292 Decouple Whisper key from Wallet (https://github.com/status-im/ideas/pull/292)
- 289 Perfect forward secrecy (https://github.com/status-im/ideas/pull/289)
- 173 Documentation (https://github.com/status-im/ideas/pull/287)
11. Automated testing (would be great if issue witnessed in https://github.com/status-im/status-react/pull/5544 and https://status-im.slack.com/archives/C88MZP11P/p1534329878000100 could be caught through automated testing at a PR level)

Please provide comments to add or correct agenda topics.

## Notes

1. Oskar welcomed everyone and went over the Agenda for the call. Lesson learned from last time: focus on things that are future oriented and require people to be here in order to make decisions on things to do going forward.
2. **Light Clients and ULC**
    3. Not clear who is working on it and what the OKRs are.
    4. Igor: still reviewing the draft document and specification for ULC. Have decided to start the swarm next week.
    5. Needs to wrap stuff up on mobile topics (mostly smooth logins etc.) and then get this going next week.
    6. Focus on getting it into the app such that people can see the option and use it.
    7. Then it needs to be tested thoroughly and see what the problems really are. This is the part that makes time estimations really hard.
    8. Until we re-introduce LES, there's not so much to talk about.
    9. So, the first iteration is getting LES as an option inside the application. (If it would only take a day to add ULC inside the application, then that could be done too, but we are unsure about that. It also depends on whether we can get ULC merged upstream.)
    10. Igor: we should use the same cluster: we already have all the connections for the whisper nodes, so using LES on these nodes will save on performance and likely keep regressions a little lower.
    11. First step is to remove Infura from the equation - so we still have our cluster, but will need to run LES on those same machines.
    12. Adam: Dmitry has also started looking into VIPNode - a long term solution as we don't want to be the only people supplying LES nodes. Would be good to not put more pressure on our devops team.
    13. The other thing is that we could get LES servers working on the Ethereum cluster, but there are problems with discoverability there as it can take up to 10 minutes to find a working server.
    14. Jacek said that there is an interesting option in Mist: connect to Infura while, in the background, it starts looking for "good nodes" to connect to the network.
    15. Whatever we want to do with our cluster, Infura is probably doing better right now with a centralized solution. So, redoing their effort seems really inefficient.
    16. Igor: this is just a temporary solution - longer term we definitely need proper discovery. However, we need to start this work now.
    17. Jacek: yes, but this exposes us to a huge amount of risk: attack, being taken down etc. 
    18. Igor and Adam: have this option in releases, but it's not enabled by default. 
    19. Jacek: I don't mind running A cluster, I do mind running THE cluster. It can be a cluster than runs there in order to improve the Ethereum network as a whole because we have an interest in the network running well. Could be used to help testing etc., but if we build too much Status-specific funcntionality in there is when we become the single point of failure.
    20. Oskar: can we parallelize this work? A lot of the problems come from running on a phone, when to sync etc. Another piece of work focussed on discovery, VIPNode etc.
    21. Igor: We can do that. One track - how to make the protocol itself work on mobile devices and how to consume it. How to optimise discovery and aspects within the protocol.
    22. Adam: this will be a bit more work, as we need to set up a few more servers in our cluster. Even if we run these, all the slots will be taken by other peers as Ethereum has too few LES servers - so we need to make sure there are enough slots for Status apps to connect to.
    23. Jacek: wdyt of the idea that we treat Infura as one option amongst many - as Mist does - and the application connects to whatever option it has. Then it can make a smart choice based on how well Infura is working, how many other nodes are running well etc. Same level of trust for Infura nodes as other nodes. Then, when we want to do transactions, maybe we beef up the security requirements, and then when we go back to chat, that changes again.
    24. Adam: VIPNode works this way, but you have to pay for the service and I believe that this will be an option for may alike services in the future.
    25. Oskar, summary: There will be a swarm with the initial focus of getting ULC into the app. The swarm will be Boris, Eugene, Igor - everyone in 293 in other words.

3. **Sharing code between desktop and mobile, and problems resulting from this.**
    4. Max: movement to having one single code base to support different forms of Status. This is similar to other projects that currently exist. This also applies to embedded devices and other things we may have in mind for the future.
    5. Desktop builds have started to fail often, mostly because of lack of unit and end-to-end testing for functionality that they share with mobile builds. It would be great if the mobiel team could suggest, based on experience if we will be able to cover all/most of the functionality for desktop that can be run as unit tests against ClojureScript code against any PR. Is covering ClojureScipt enough?
    6. We also need to have separate end-to-end tests for desktop itself.
    7. Anton: desktop e2e automation research has started. Main goal is to replace main mobile driver with desktop driver. We can reuse the same logic in mobile tests for desktop tests. There are some technical issues with getting this stuff working properly, but should be possible to get it all working with some research. Anyone with experience with this kind of stuff would be welcomed.
    8. Anton: really need to take care with unti tests! Before e2e testing, we really need to fix builds and unit tests (sometimes failed tests show up as green in GH).
    9. Max: sounds reasonable. W.r.t unit tests - will we run the same unit tests for mobile and desktop? We should probably move to some common set of unit tests for both platforms.
    10. Let's prioritise this - it's really essential to work on.
    11. Oskar: is there anything blocking this?
    12. Max: not blocking, but we have failing builds like every 2 days, and this can slow down work dramatically.
    13. Anton: would be great to create a unified pipeline for both desktop and mobile - to reiterate.
    14. Igor: we should also try to merge the build process for these two, as it is currently quite messy and this could help.

4. **Hardware wallet!**
    5. Oskar: We want to support this for DevCon and requires a lot of co-ordination and is not captured in current goals.
    6. We have 2 different versions, so let's figure out goals, unknowns, timeline, and relationship between two wallet products.
    7. Guy-Louis: joined 2 weeks ago and is PM for hardware wallet. We currently have the light version: a java card applet developed by Michele. Starting a security audit by an external company, starting right now. No MMI, contactless, running on NFC, focus on client-integration with phones, then maybe desktop.
    8. It is complete and documented on GH. So, we need to start integration in client. 
    9. We have started to write some of the basic user stories we want to enable: set up (create new Status account or import an existing one), signing txes (user will have to tap his card on the back of his phone and enter PIN rather than pswd), and logging in (instead of selecting account and using pswd, tap card and enter PIN code).
    10. We also need to decide on how the applet is loaded on the java card: manufacturer loads it directly on card, or client uploads through NFC on first set up. Different UI, feature, and security considerations for each option.
    11. Some additional notes: the java card can derive directly on the card the Whisper key, for instance, all of which have implications for the client. We will share a document tomorrow on some further considerations on this and there is already some other documents available in #hardware-wallet
    12. Oskar: did Andrea start looking at this?
    13. Andrea: Yes, started a few weeks ago, but needed to stop to fix a security issue we had. Already a PR open in Geth for this kind of hardware support. Needed to change some stuff there, but am a little unsure how to proceed. Do we work off that PR or start our own fork etc.?
    14. Goran: we need to reuse the scenarios to the bare minimum (applies to both Clojure and overall). Which one of the 3 user stories above are the bare minimum? If you had to remove one from those 3 which would it be?
    15. G-L: probably logging in, but what about the pswd in that case?
    16. Goran: card gets stolen, but not phone - the attacker can't access the PIN (confirmed by G-L). We still need to support both as not everyone will have a card. This adds a fair deal of complexity.
    17. Corey: there are really clear user-flow diagrams which we should add to these notes. Kudos to Denis for those. https://www.figma.com/file/UfQjpWl1hmRchHIyY3Wvu2nW/Hardware-wallet-flows?node-id=0%3A1
    18. Corey: something like facial recognition/finger print log in might help us to unlock some of these problems.
    19. We need to figure out which point we need to enforce hard security at: is it logging in, is it sending a tx, is it sending chat messages? Accessing the wallet should prob require all 3, but sending a public message might not (even though attackers can coerce users if we enable finger prints and Face ID). 
    20. (Miscellaneous comments about torture from tinfoil hat wearing devs, cut short by Oskar ;) )
    21. Goran: we need a timeline with realistic expectations and resource plan - as this is the only way we can actually plan this properly.
    22. G-L: We need to define how we load the applet on the card as this has a direct impact on how we source them. This is the first team discussion we need to have. If the manufacturer loads them, it's almost sure we won't have them in time for DevCon. Regarding the timeline: there's all the sourcing of hardware parts. Then we need to define a list of features and we can create a timeline.
    23. If we don't get the manufacturer to do this, we can maybe make it and just handle it as a sort of workshop with ±100 cards at DevCon.
    24. Andrea: we started talking about decoupling the wallet and whisper keys and we need it for this hardware stuff. Whisper key only in memory in the client. One dependency is therefore starting and finishing the decoupling of keys. This likeyl requires quite a lot of changes in chat and protocol - like asking for the wallet address because it is not derived from the same whisper key anymore.
    25. Goran: If we do the bootstrapping option, we are going to have more custom code on the client side, which can also affect the timeline. Is this something we should be concerned about?
    26. Andrea: Yeah, this will also take more work, for sure.
    27. Oskar: We can go into more detail about this in a separate conversation. Does anyone want to own the swarm on this?
    28. Goran: main work for now is scope definition, happy to help with that. 
    29. Oskar: We still need another Clojure developer - which we can talk about outside this call again.

5. **Security**
    6. Corey: Brought on with the assumption that there aren't any formal methodologies or protocols for doing security.
    7. Have yet to walk into a bunch of landmines, which is awesome. Most people have the base line, but maybe not the confidence to say that they do respect security (because this is a pretty broad topic).
    8. For any questions/comments/quick responses please email security@status.im
    9. The Pyramid of Pain: looking at potential threats to companies and figuring out if we are under attack. Created in 2013 - refer to graphic. Mitigating attacks means forcing the attacker to change his behaviour with Tactics, Tools and Procedures. Think about what gets left out, left over - and applies to everything (UX, design etc, not just devs). Important to have a "back-end mindset" about what the security implications for any action are.
    10. Moving up means an increase in difficulty to change things.
    11. If I can detect these things, how difficult would it be for an attacker? If you force them to change behaviours and tools, they're far more likely to leave you alone.
    12. Worthwhile brainstorming on what we do, and it would be awesome to rebuild the pyramid for what we do specifically. If you have any ideas for how to/ways of doing this, let me know because it;s important that we push this kind of thinking/paradigms across the community.
    13. Security champs went through a threat modelling exercise with ENS name and found some great things. Want to incorprate that into my work and make sure Igor doesn't need to wear that hat and we need to make sure we have robust procedures without them taking too much time/weighing too much on each individual dev. 
    14. Another thing to bring up: a conversation with ThreatStack for cloud infrastructure for monitoring. Because we do rely on some centralized infrastructure, we need to make sure it's clear what is happening on the infrastructure. They will do a demo of what they're capable of and I am curious about who would like to join that call and if it is a reasonable hing for us to do. Jakub is keen to join, obviously. Jacek and Oskar also interested.
    15. There was a social-engineering attack attempted on Kim - someone pretending to be Jarrad asking for her personal phone number in order to transfer the SIM and then access whatever 2FA stuff her mobile had access to. If you see this stuff, please send it to me so I can investigate further. Will do a PSA and write-up about how this works and what it exposes you to.

6. **Voting DApp**
    1. Graeme: not so much about features or do anything new. It's about "What are the reasons that would compel people to vote? Why would you pay gas fees to vote?". Survey being sent out tomorrow through Hutch.
    2. On-chain votes are very expensive, so we need to figure out how to have on chain consequences for on chain votes, as this seems to be the only relevant consideration for incentivizing people to go through the pain of voting on chain.
    3. Trying to avoid complexity for now, before understanding better the incentives.
    4. No update on Gitcoin for this week. Corey has interviewed them for his podcast http://hashingitout.stream (episode will release this week)
    5. Barry: deploying contract on chain for ENS stuff and other work, so have moved to a multisig wallet and some other features that are progressing nicely. However, we're now talking about liquid pledging and the DAO and there is a big gap between where we are now to that. If you could build one feature that moves us from a multisig wallet to a full DAO, what would it be?
    6. We have a WG that is using multisig wallet and seeing what the process is, what the pain points are in bringing people together to actually administer these contracts? There's a fair amount of co-ordination pain there already. Started a Slack channel called #multisig-evolution
    7. Very little feedback because there are not enough people even use multisig wallets yet, so how can we expect people to do more advanced stuff yet?
    8. Jacek: have we looked carefully at Bloom's use of Whisper to gossip around info about identity for the credit service. Maybe we could think of something similar to lower the costs of co-ordination we are already running into.
    9. Graeme: is there any further development planned around the signing of the principles?
    10. Barry: there is another version we can use, which basically signs the document using only web3 as an option. But there are no further plans there for now. We can wait there until Jarrad comes back and then revisit it at a later stage.
    11. Barry: there is an update in Discuss - Jarrad has replied and mentioned there will be an actual SC that validates and stores the signature on chain, so that is likely the next goal.
    12. Oskar: no specific consequences associated with signing the principles as yet, more about getting the cryptograhic signatures going and exposing the whole organisation to actually using at least some of the tech we are building on.

7. **Miscellaneous**
    8. Jacek: Next Ethereum hard fork coming up. Dev call/meeting soon and several important EIPs in there, so make sure to check it out.






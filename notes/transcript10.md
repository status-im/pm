# Intro
0:00-1:00

Oskar: Hello! And welcome everyone to the tenth status devs meeting, the first one for this year. We'll start with some Swarm updates for 15-30 minutes then go through some hot topics. So first there is a design review that Status will go through and then we will talk about a security vulnerability in React Native Desktop. And then at the end if there is any quick/specific announcements. Thank you Igor for hosting this and thank you Rachel for taking notes. So we'll start with the swarms. Maybe we can start with Teller network?


# Teller Network
1:00 - 2:00
Ricardo: Yeah the Teller network, we had a really good brainstorming about it. I think we are heading to a direction where we can have a consistent MVP of what we want and how it will work. We have some open questions... Iuri do you have the documents of the brainstorming there?

Iuri: I dont have it right here...

Ricardo: Ok so we mostly discussed what we wanted to discuss, but some things are open question like if Teller network is only for specific crypto Fiats, or it can be used for something else?

2:00 - 3:00

Ricardo: About reputation, how will we have the reputations? This is something we want to discuss. Something that I found really interesting while brainstorming was we kind of created an idea about onboarding users that don't have any crypto, using Status and even the Teller. You basically ask for someone to be your "lawyer" or "subsidiary".

3:00 - 4:00

Ricardo: This user will take a risk of the gas cost of your operations in the Italian network for example opening an arbitration or even opening the buy requests. These people would be paid by the value that is being brought in that crypto. There is alot of topics to discuss, how are we going to put the dispute resolution, if that's gonna have an indicator of trusts that is part of reputation. If we want to list some tokens, like Petrol that seems like it's harmful for the crypto environment. If we want to support jurisdiction limits like for example for United States people want to support KEYC.

4:00 - 5:00

Ricardo: If we want to deal with the privacy of the transactions, if we want to list prices in DAI or if we want to support DAI as the base. Also we discussed a lot of the user flows and designs, how they should be, but everything right now is still being formed as the first MVP of how it should be and I am excited about it because at first I was a bit lost of how we are going to make this and now I think we have something that we can actually make and will be something good and have some differential and that people will like it.

5:00 - 6:00

Iuri: So with DAI we are basically attacking two fronts. One is the more long term and more complex front which we discussed all out wish list and all the stuff we want to do and how, we want to do it. Another one is the more immediate MVP, we have a basic working DAPP on mobile and desktop. The user can buy a license to sell, theres an escrow mechanism and dispute resolution, you can also write query prices for what the escrow exchange will be, support for multiple ERC20 tokens, we can already rate the transactions and get an overall rating for the seller.

6:00 - 7:00

Iuri: There is stuff that is more code-wise like story book, multiple tasks, good test coverage, and we can list multiple sellers. We just did also to allow users to open arbitrage case and we're working now on the arbitration UI for that arbitration. So that's what we have now for the MVP.

# Tribute to Talk
7:00 - 8:00

Oskar: Let's try to keep the updates fairly brief if it's possible, we have 10-15 people connected. Ok tribute to talk.

Eric: So for tribute to talk we are starting to work on the screens. We are a doing a specification of the contracts. We start for the MVP with a simple tribute to talk where you pay the tribute with a regular transaction so the contract is a very simple contract that manages the tributes and allows one to check what the tribute is for a particular address. That's it for now.

# Sticker Market
8:00 - 9:00

Oskar: Cool, so sticker market?

Julien: Yep, so last week we mostly worked on values documents, like the result document is done, the specification is done. Mostly because Rachel invested a lot of time in this. We are validated the mockup so I think we are done with the mockup themselves. We agree that this is the right directions. Andrei spent some time implementing the mockup, and this week I will try to glue the mockup with contracts, and by the way Ricardo did some work on this contract too. One eventual open question that I would like to raise, for the MVP we probably will not consider ESC721 but it's still open to this discussion so if someone has an opinion around that, that would be appreciated.

# Dapp Store
9:00 - 10:00

Oskar: Cool. Dapp Store?

Andy: Yeah the Dapp Store we have the research phase running at least to the end of this month. There are a few different moving pieces to it and it is only P1 so we don't have many core contributors taking parts. There's two major parts to it we've decided the first is simply design in order to solve some of the most basic user stories about being able to discover Dapps easily, navigate to the one's that you've recently used and ones which might be relevant to you based on what's trending across the network. Which for version one will probably be calling an API seen as it's one of many options, not the only option and it if falls over it won't break.

10:00 - 11:00

Andy: Taken the decision to make it as a web dapp in mind with the sticker markets and whatever other depths like that come out of it, and then in parallel we'll be doing a bunch more research around what exactly the curation mechanism might be for something like this, Ricardo's offered a bit of help there. Yeah I put forward a proposal about using simple bonded curves but that obviously still needs to be validated by others, and like I said we've got a little bit of lack of resources on this swarm so hopefully we can experiment with more bounties and sort of external contributions while the P0 work that everybody else is doing goes ahead full-steam.

# Core Network Incentives
11:00 - 12:00

Oskar: Cool, so network incentives?

Igor: Yeah we are continuing our research like Andrea did research on one of the ideas of incentive of the current infrastructure meaning whisper and mail servers. For the next week we wanna also take a look like taken into account that's there's also a protocol research happening so we want something more broad and applicable and future proof. So people want to have some research on something different and not like whisper side, just come up with something that's more generic and durable so that's essentially it I hope we'll share the documents this week, the drafts of research.

# Core Improvements
12:00 - 13:00

Oskar: You can take improvements as well while you're at it.

Status: For the improvements there's a different situation there, there's no research there we are just implementing things. We implemented a quicker login so it's very very fast on at least my phone and even on the small phones it's very quick and it should be released in an internal release that we will have this week hopefully. We also added added a second password for Android so we have this feature as well as Iris but there is more things to do there so I don't consider it implemented completely because we also need to improve how it stores passwords in both places, so it's about 30% in.

13:00 - 14:00

Status: And also about half done with reliable messages so pruning was I guess already in status go but it needs to be deployed to work properly and there are few things like email confirmations and mail server management in general that needs to be done. We also started our dependency audits so we can build older versions of the application easier than right now but we just use some master or some current version of toolset. The last one is that there is some more work that was done with BFS and device sync and I think we will actually work on it like this week probably because it also might clash with tribute to talk so they need some coordination there, so that's all for us.

# Protocal Update
14:00 - 15:00

Oskar: Cool thank you. I'll do the protocol update. So mainly two things have been done. So one is workshop preparation. We're gonna meet just before Fossdem in Brussels end of January, we'll be fine to seven people from Status. So working on agenda and making as useful to as many people as possible. The other thing is proof of concept for a sort of data sync layer. I've written a post about this before but the idea is that you encapsulate an in between layer that doesn't concern itself with a message per say but instead of just syncing a piece of data and that allows us to build things on top of it. Sort of public chat and group chat and so on, but below it you can swap whisper out and still be able to sync data in a peer-to-peer way. In this proof concept there is a protobuf specification that is wrong in some places but gets the gist across.

# Dao
15:00 - 16:00

Oskar: As well as a sort of basic simulation in Python that has some unreliability assumptions and also deals with mobile node having slightly different characteristics than having something like a desktop note where a mobile node is mostly offline but sometimes goes online. Then sort of for a one-to-one chat and seeing how the system behaves, so I did a short write-up, I'll link to it in the notes, yeah please ask questions or specific things you want me to try to answer with this concept. Please ping me as well. This week we will continue to work from the workshop and looking at what the most useful direction the future proof of concepts will be. dao?

16:00 - 17:00

Barry: So as far as dao based activity, the liquid pledging contracts, they have been deployed to Rinkeby for future testing and actually getting a sense for how the UI that we built will actually interact, to better simulate how the UI might act on a real network as opposed to just in development. But the UI itself is essentially feature complete for the MVP which means you can create a giving profile, a delegate profile, or a profile for a project, and a giver can create a pledge that can fund the pledge and select a delegate, and a delegate can fund projects

17:00 - 18:00

Barry: A giver can veto, and projects can ultimately withdraw those funds after the commit period. So from that perspective it's feature complete, maybe it's not necessarily feature sound in the sense that it may not be the most intuitive UI for some functionality, which is the next steps in iteration, but also we plan to just sync up with Giveth wrote the original pledging contracts to see where there's mutual overlap and think about a path towards to going to mainnet which of course at some point is going to involve a security audit.

18:00 - 19:00

Barry: We were just thinking about sort of what still needs to be done to these contracts from their perspective and from ours where there's mutual overlap and also to see the differences to understand maybe there needs to be like a broader user case to generalize them more to accommodate these sort of broader use cases but that's where it currently stands.

Petty: Hey Barry Corey here, you wanna set up a meeting with me we could go over them to see what kind of, just to talk about that more in depth, the security aspect of these things.

Barry: Yeah sure.

Petty: Thanks.

Oskar: Cool, Jarred or Nabil do you wanna take your time?

19:00 - 20:00

Nabil: Basically we've been meeting regularly. We had two design reviews last week and I think the process was pretty good, we just wanna make sure we have engineers attending each design review to make sure everything being proposed is feasible, it's good for the engineers to give input and have a heads up for what's coming along. Other than that I think the progress is going well in the most part. The one thing that I would like to request from everyone is for all the swarm leads to put in the number of hours that is happening in the spreadsheet that we sent by email just so that we can keep track of budget, so when we give updates at the townhalls. It doesn't need to be to the dot, just a plus or minus ten percent like a rough hourly amount spent is really important for us to make sure that we're assessing things properly.

20:00 - 21:00

In terms of actual engineering progress where everyone's using pivotal tracker, some teams using it more than others, some people are just getting used to using it. The more that we use that the better it becomes and more effective it is and Iuri can probably give a good shpiel on how great it's been especially for his teams. So those two things, one make sure the hourly rates for the swarm leads are coming in just get them at the team meeting it shouldn't take more than like 30 seconds and yeah continuing to use pivotal tracker and making sure the granularities are around the right level so that it's not just one issue that's being worked on for multiple weeks, if the issue is too big break it daon into smaller issues.

21:00 - 22:00

Oskar: Thanks I'll just add one thing to that. It'd be great if we could sort of keep swarm ideas themselves updated in live and for example "we're doing these updates now" and if it's just like a few bullet points it take maybe a few minutes just to write daon "oh here's roughly what we did this week" and just like pointed to some artifact or whatever then just putting it in some workflow in the idea. If you want to do that I think it would be great because it gives sort of other people a very straightforward way of seeing what's happening, it's also a good way of clarifying your thoughts, if you right after beforehand you just put it there and you just say it it makes you think like what's actually changed, so that's just an idea would be great if we can keep them updates so the states care. If it's annoying or if you're doing tracker then fine don't do it but it would be very useful.

# Core
22:00 - 23:00

Jarrad: Yeah a free course on that is to review pivotaltracker and also update it so either way we'll be mindful that. It's also worth noting that we are also in our research phase so if you've got any feedback on how things are going if there's anything that's not smooth or any way we can improve our processes please let us know so we can make adaptations.

Oskar: So just briefly do we have any updates from either Core, Core Browser, or Core Chat that's not covered in the previous updates?

Julien: I can give some updates on that if you want. Yeah so mostly we try to take the number of flow and getting fruits related to what we consider is unsure, so things like fixing universal links in browser or making sure that you can resolve ethereum production URL or whatever something technical.


23:00 - 24:00

Julien: Also we worked on some EIP's because we are browser so we try to work with all the other browser making sure we implement the same set of EIP's, we have the number of rings and chats to dicuss. There are currently two different EIP's that different teams are pushing and mostly metamask that we are also very invested in that. Andrei did a lot of work around that last week. In parallel I'm trying to finish the cable extension and making sure that all the relevant extension changes are being implemented. I'm pretty happy that last week I was able to do my first exchange with the cable extension so hopefully very soon we should be able to even make this a little more public and maybe write a blog post or something.

# Desktop
24:00 - 25:00

Oskar: That's great. Anything from Core or Chat?

Eric: No.

Oskar: Ok. Desktop?

Volodymyr: Hi so recently we launched a new version of react native 0.5.7 in react native desktop. Now there is a PR to move status desktop to this updated version. Also there is a PR in progress, Lynx previews can be enabled from settings in desktop application.

Oskar: Alright. Wallet?

# Wallet
25:00 - 26:00

Goran: I have one update and that's that specifically the wallets and flow pull request is almost ready to be reviewed and tested, so thats something new. It should be ready during this week probably. So yeah that's it. We will probably prioritize the next task on our next calling on thursday so if anyone wants to be in the loop either ping us or join the call.

Oskar: Alright. Key Code?... Anyone from Key Code?... Alright. Security and DevOps?

# Security/DevOps
26:00 - 27:00

Petty: I could take that topic I put up earlier and the process is going through the dependency for React Native Desktop. I submitted a bunch of PR's to fix some of the issues that snake had with the dependencies there but one of them didn't have an automatic fix in terms of just upgrading a dependency is a high severity bug in the yaman generator which allows arbitrary command injection. I have submitted an issue of React Native Desktop and it hasn't gotten much attention but we really need to look into, Paul submitted big mitigations for this and that they involved all input validation to make sure people can't take advantage of this. It probably sims to React Native as well, so if I can get more people looking at this particular issue to find out how we can mitigate it because it's not one of those things where you just upgrade the dependency and it's fixed. The bug is inside the notes here so the more attention we can get on this the more we can realize what implications it has on our application, it has potential to have severe implications based on arbitrary command injection so let's get on it.

27:00 - 28:00

Oskar: Volodymyr do you think you can own that and protest that?

Volodymyr: Did I understand correctly that we are talking about that shell JS library that has vulnerability?

Petty: That's correct.

Volodymyr: Yes so as you mentioned we have it from React Native itself so the dependency is still in Facebook's React Native, under the dev dependency, so it's not the main dependency, so when we will build in production it should not be there. Also I believe we will get rid of it, right now when we switch to React Native 057 we have plans to change React Native Desktop repo and make it separate package that will be out of three platform in terms of React Native so it won't contain all React Native code only desktop related and then I believe the dependency will go from dev dependency list.

28:00 - 29:00

Petty: Can we rewrite the issue and close it?

Volodymyr: Yeah Ok I will comment there.

Oskar: And can we just also verify that it's 100% they won't make it into any nightly builds or anything because if it's actually activated it's pretty dangerous, you can get seed face and everything right.

Petty: I wanna double check triple check that it doesn't make it into production builds.

29:00 - 30:00

Volodymyr: Unfortunately Shell JS library itself does not have the fix for this, I checked and they are not going to fix exactly that API method that is vulnerable to have a backward compatibility but they are going to introduce a new more safe method than this one, and if this depends if Shell JS call to do the function I hope they also take advantage of a new method when it's released, Shell JS.

Oskar: Can we just make sure this week we make this a priority to get absolute clarity on this that it's not something that's affecting nightly builds or anything? And if you need any help you can ask the Core team and they will be able to assist as well.

Volodymyr: Yeah sure no problem.

# DevOps
30:00 - 31:00

Oskar: Great thank you. Ok DevOps

Jakub: So the main work happening right now is on especially looking daon on the versions of software use, so some of that is being done by Pedro, he's right now kind of changing how we build our docker containers on both linux and windaos so we locked daon pretty much everything. Finishing work on almost the same thing for Android, and once both of those things are done we can pretty much port development locally into docker so we are sure that every time we rebuild it on Jenkins or locally it is always using exactly the same tooling and exactly the same library versions, that's probably gonna be finished sometime this week. That's the main thing that's been happening.

Oskar: Ok. QA?

31:00 - 32:00

Anna: Last week Friday we added two pivotal tracker our project called testing and most of the tasks like last week like common tasks for testers were release testing like we had I believe four or five builds to test. Now it's still in progress because we are waiting for status go updates to test with this. As soon as it's done we will also test battery consumptions there and probably performance testing just to make sure that we can measure it automatically. Also for test automation we have task to automate upgrades on Android. For the beginning it will be upgrading this like empty account but the next step would be also to create more charts and see how it goes these upgrades with real data. And as usual writing test cases updates them for the new features or modified features and testing nightly builds so there are like more or less repetitive tasks for like nightly release testing, updating their test cases plus for test automation you'll have like some focus upgrades, battery consumption, performance testing in different scenarios that also will be described. That's it.

# Research/Nimbus
32:00 - 33:00

Oskar: Ok good. Alright research/nimbus? If there is anything... Alright embark?

33:00 - 34:00

Iuri: A lot of stuff we are doing in work is related to the Teller network and the dao in the sense that while doing the Teller network we find bugs that need fixing, or feature ideas and so on, and that's been quite useful. We're discussing a lot now basically redoing the pipeline, making embark much more pipeline agnostic, and that's probably something for embark 5, but that's a very big feature allowing embark to work anywhere including web services and command line applications and so on, and I guess that's the gist of it in some ways.

Oskar: Alright cool. I guess we have the Sun overview and we already talked about the React Native Desktop Vulnerability. Before we go into the design overview, is there something else that someone wants to add to the agenda? Alright cool. Hester?

# Design Overview (Hester)
34:00 - 35:00

Hester: Thanks Oskar.

(Starting to share screen)

35:00 - 36:00

Hester: It's pretty basic but now that we've scoped the design work for at least most of the swarms I've decided to give you a quick snapshot of the current allocation by team, looking at Core, Andrei is the key context for Core, under core there are two swarms currently. Polish/Onboarding/Patient Zero which Andrei is also working on and Network Incentivation which Andrei is also working on. Then similar story for Chat where Maciej is the key contact for the team. Roughly three swarms connected to that although Sticker market is also dapp so it's not necessarily one on one but the swarms that Maciej is responsible for at the moment is Sticker Market, Tribute to Talk and Anti-Spam. For Dapps/Browser story changes slightly as the team contact is and will remain to be Denis who's been working on browser and dapps a lot up until now.

36:00 - 37:00

Hester: Specifically for the dapp store swarm and going into Teller network later, Andrei will be the contact for now. Under Embark because it's a little difficult to connect the swarms to individual teams, for Teller Network the key contact is Denis. There are some other activities going on always that demand the designer's attention but for now the ones that you see on the right are a little bit deep prioritized. There might be time maybe an hour or so every now and then but they're not priority for now as the designers are primarily focused on the white paper use cases.

37:00 - 38:00

Hester: To sum this up, this is the overview of the designers connects the two teams and/or swarms, if you see or submit any change that affects the UI for a particular swarm or team please assign the respective designer on github as well so they can monitor changes that go on that aren't 100% under their control or coming out of design, but at least so they know what's going on. That's it.

Oskar: Awesome. Just a quick question. All the working packages that existed before, have they been either put on hold or are they folded into Polish. What's the status on that?

Hester: Yeah they're folded into Polish exactly. So they're not necessarily on hold because as soon as we would be able to revive them the world would look different, but all the knowledge that has been built up especially regarding profile is picked up in Profile.

38:00 - 39:00

Hester: The dapp discovery is part of dapp store so all the components that were discussed in work packages are finding their place but it's mainly through the designers and not through the process.

Oskar: Cool yeah so any thoughts on this? I guess that's it for updates and hot topics. Any quick announcements?

Jarrad: The ProgPOW year double year discussion topic in the community is worth taking note of if you are not aware of it look into it.

Oskar: Thanks everyone, see you in two weeks. Bye.

0:00 - 1:00

Anna: I'm not sure I will stay to the end fo the meeting so I prefer not to volunteer today.

Oskar: Okay anyone else? Sergei? Come on we're 20 people in the call haha. OK I guess we can get started, are we live on youtube?

1:00 - 2:00

Oskar: Ok welcome to the thirteenth core dev call. We don't have too much on our agenda today. We have follow up on better Pull Request process, and then we have Pedro with state of Nix, and then before we get started is there something else someone wants to talk about, we can add it to the agenda. Alright cool, let's not go through the swarms, you don't have to say anything if you already presented at town hall, but if there's something other people should know about. We can start with Sticker Market.

# Sticker Market

2:00 - 3:00

Ricardo: Yeah I'm here to discuss it as well.

Oskar: Cool is there something you would like to give an update about?

Ricardo: So on my part, I'm researching on... because we have this price that dilemma we have a lot of controller actions in the sticker market contract, and I'm trying to develop a smart contract that can control this in a democratic way, because right now we had a voting dapp to ask people what would be the price, and my idea would be that instead of voting what would be the price, people vote directly what the price will be. I'm currently working with making multiple delegations and changing the architecture of how it works, isolated only for sticker markets it's kind of ready.

3:00 - 4:00

Ricardo: But not like in a multi contract environment that democracy would control multiple contracts, but the main of democracy for sticker markets now, so yeah so then we don't have to discuss the price, let's just let the network decide it. I mean it starts with zero, and if people vote it to change to some value it would happen then.

Oskar: Alright. Tribute to talk, anything you want to update people on that's relevant, if not it's completely fine to say nothing.

# Tribute to Talk

4:00 - 5:00

Eric: Yeah there isn't much, maybe just to mention, the non-native touchpad that is in the designs is also implemented for a keycard, so now we have two implementations of it, so if there is a new design that has a numpad, then please the check the one used for tribute to talk or keycard, and don't do a third one. At some point we should merge them.

Jarrad: There's another thing on tribute to talk, Barry in doing some of the token economy modeling stuff, we kind of realized that as tribute to talk is currently implemented it's very transactional, so in these models you have to assume as soon as it's not locked up, like state or otherwise, you have to assume it's into another token, so there might actually be a better way to slightly readjust how tribute to talk is done.

5:00 - 6:00

Jarrad: Instead of putting up a certain amount of tokens and then having them relieved on initial contact, it might actually be better to have both parties state a certain amount of SNT towards each other until their relationship breaks down. So you would only withdraw your SNT from somebody at the end of a relationship or at the time of blocking them, which might be a bit more beneficial as an anti spam measure, and it's certainly more beneficial in terms of locking out more tokens in the network, because you're essentially moving from a transaction that might take a matter of seconds to a day or so, to the length of human relationships which could be some months if not years, so that's definitely something to think about.

6:00 - 7:00

Ricardo: I think what you described looks like visibility stake but for previous conversation. I think that the current model is good in the way of spam prevention, it might have some overhead, because the smartphones still need to process the message, even if they're blocked they still need to show. But you what you described it's mostly like visibility stake. I was thinking for something like this for the public chats, as well, the governance/democracy would be able to maybe vote/moderate or something like that for the public chats. Because we have this tribute to talk conversation about private conversations about group conversations, and we also have for the public chats.

7:00 - 8:00

Ricardo: I don't know if the correct name is tribute to talk. And also there is something I want to bring on is that tribute to talk should replace patreon. Right now there is a lot of discussion in the internet/youtube, the content creators are getting mad about patreon banning people with a political bias, and I think it's a great opportunity for status to build something that is not able to be censored. Then there is this other version of tribute to talk that is like patreon. So there is this visibility stake way and also this patreon way where you have to pay every month, depends on the content creator configuration, but I guess every month you would need to be.

8:00 - 9:00

Ricardo: There is a little problem on this creator creator approach is that we would be using SNT and there is some volatility on this and maybe the content creator would not want it so we might want to think if we want to use SNT for that, but I guess yes use SNT but if the content creator wants a stable coin he can convert it immediately, but the payment is SNT. So that's what I was thinking for tribute to talk. Right now we are developing this first version of tribute to talk that only is for spam prevention, I'm excited to go to this other version that is maybe for managing a group chat, not really sure how it would look like, we need to discuss is, but that's it.

Jarrad: Yeah cool that sounds great for the second iteration, let's definitely keep that in mind, thanks.

# Dapp Store

9:00 - 10:00

Oskar: Awesome. So dapp store?

Ricardo: So dapp store, I'm also working on this, and I developed this ranking system that is a contract and another contract that feeds this ranking with the subscriptions of the users, for example the dapps I'm building this more generic to be able to be used for the sticker market as well but there is this discussion on this curve or how this would work, so the curve is a burning curve only for selling, only for don't voting sorry, but yeah it's not really clear for me so this is why I didn't on this part of it, I just made a simple down-voting that is more cheaper than up voting, but the idea would be to have these burning curves to give some economic incentive there or...

10:00 - 11:00

Ricardo: I'm not really sure that is why I'm not going further on this maybe, we need to to discuss more this with Andy on exactly how it should work and why it should be like this. I'm also open to other suggestions on how to make this ranking system, the ranking contract is done but the way it's ranking up and down in the system is something we need to discuss. How that would actually, what is the best way to do that?

# Teller Network

11:00 - 12:00

Andy: We're still waiting to do a design review on the first iteration of the dapp store because it's held up by considerations around changing the navigation bar which is still in discussion.

Oskar: Alright thank you. Teller Network?

Iuri: So the teller network we're revamping the UI to try to finalize the first proof of concept. So we did a lot of UI change to make the whole thing really usable, and we are working on the process of re-adding the UI for the escrow part, hopefully after that we will have a full-working dapp, at least for the first approach of the arbitration mechanism. And we are continuing to look at this protocol to support multiple arbiters instead of just one, if that's the fact we go towards.

# Network Incentivization

12:00 - 13:00

Oskar: Alright. Network incentivization? So there is a post in discuss with the current sort of research proposal, Andrei will work on sort of getting a proof of concept of that, we also have designs Andrei has been working on and we will present next Town Hall with what the UI might look like.

13:00 - 14:00

Ricardo: About network incentivization, I think that this should be multiple things, not just one, I said it may that working on single incentivization mechanism -

Oskar: It is, if you want to join the calls we could talk about that more in detail, but yes that was a deliberate choice because we don't want to be tied to whisper when it comes to these things, but we can definitely talk about other methods, it would be best to do it in the swarm calls I think. At this point just want to get through the updates, then we can let everybody because we have 35 people on this call and we have these sort of two points in the agenda. We can add more stuff to agenda or we can talk about it in specific swarms as well to have it maximally useful. So core improvements and open core here?

# DAO

14:00 - 15:00

Oskar: Alright, protocol stuff, ongoing stuff with date synchronization, we are also going to meet at FCC, there's also a conversation with libp2p if that's interesting to someone else, just ping me if you want to talk about something. Dao?

Ricardo: So regarding the DAO I was already talking about that in the sticker market, and my research currently on topic democracy was I'm currently changing the idea of topic democracy to instead of having subtopics, you have subdemocracies, because that's kind of more secure.

15:00 - 16:00

Ricardo: The problem is that if I want to for example, there is this democracy running, then there is sticker market that is a new contract that will have new actions to be done by the democracies, to include these actions, I would have to pass a quorum to be able to create these topics. So in order to not have to do that I'm making it in a way that I can just create a new democracy just for sticker market, and that would have a parent democracy that would be this already running democracy, that people will vote or in this higher or lower democracy that will have a different quorum that if for example, if you want to maybe change some property you don't want to reach the qualified quorum like the absolute majority of influence, so that's my current stake on that. There is a lot of improvements in the proposal system. Like I can create this proposals without a democracy just for testing so that's it for democracy.

# Better PR Process

Document [here](https://notes.status.im/C5pj8g7gQOu9Wo8PtDZsMw#) and in [Discuss](https://discuss.status.im/t/better-pull-requests-process/1044).

16:00 - 17:00

Oskar: Alright cool. Anything from janitors, core, browser, or chat? That's useful for other people to be aware of? Ok anything from desktop, wallet, or key card?

Guylouis: Nothing special I think.

Goran: Also nothing special.

Oskar: Did we miss any swarm or group of people that want to give an update. Alright cool so first one is round following up on better pull request process, this is mostly relevant for status core, we essentially had QA dev's, designers, so on figure out the major pain points we had, then try to figure out things that are relevant in  the short term and the long term.

17:00 - 18:00

Oskar: There's a document, I'll link to it, it's actually in discuss as well, but the specific sort of polished changes that we're proposing is six of them, so one is we should reject PR's that don't have tests as a rule of thumb, and sort of increasing test coverage. Not promoting nightly as something for end users. Reject pull requests that don't write what tests the devs have done themselves and what platforms they used to test, as well as including screenshots when it's relevant. Then running automated tests when a PR is at the review stage already.

18:00 - 19:00

Oskar: Developers asking for limiting, just asking for two three reviewers an this expectation being these reviewers review within a day. And finally stop building all the APKs apps and so on for a PR that only make changes to say test branch. Those are specific ones and then we had things we want to look into more long term, which were integration tests, headless tests, which Andrei is looking into, and address automated tests and supporting more platforms which Anton is looking into. I guess do people have something that were part of this call or not part of this call they wanted to add to this or any questions or thoughts we can talk about it now.

Anton: I had a short conversation with Jakob today and according to him we are not able to stop building that kind of builds for PR's so I don't know if Jakob can elaborate on this if not we can just remove the point.

19:00 - 20:00

Oskar: Cool, does anyone disagree with these points or think they should be phrased differently or there's something missing from these things that we can do on a short-term?

Pedro: My only concern is the first point where we have tests. Hopefully it's easy enough you know, I'm not a Clojures developer, I've been able to contribute to the clojure code base, but yeah I'll have to look into how tests are written, it's not something I've put much thought into, hopefully it's something that is easy to pick up and won't be a blocker from now on.

20:00 - 21:00

Oskar: I would say it's fairly easy to write tests in close script, they're very similar to what you have in different ecosystems, but it's definitely something that we've had as a habit before.

Pedro: The important thing is to have a good reference of existing tests, like there's a single way that tests are implemented and that's the best way to do it, then we can use that as a reference, and that's good. If we don't have like two or three ways and only one of them is the correct way, that's the most important.

Oskar: Cool, on that I imagine it would be sort of basic unit tests that Andrei is looking into, then I guess the third level would be the automated tests which sort of outside of clojure for example and would be more about point-and-click and so on. Those are the three types of tests I imagine that wouldn't be manual. Does anyone disagree?

21:00 - 22:00

Oskar: I guess a question on this note as well is that it's easy to add process and these types of things so is there something that we have right now that people think we should remove in terms of removing complexity in terms of getting rid of existing processes? Alright cool, anything else anyone wants to talk about?

Pedro: Just FYI the end-to-end tests are already being triggered on review, that's been implemented this morning.

Oskar: Awesome. Ok cool so I guess we can go on to Nix?

# Nix

22:00 - 23:00

Pedro: I guess I'll start with a higher level overview of what Nix is, just for people who aren't familiar with it. Basically it's a way of describing packages in a functional way. You have this read-only store which is located at the root of your drive in a slash-Nix folder, and that can only be changed by the admin, so normally it's not something that one package can go and override stuff from another package, or even yourself. That gives us a lot of guarantees of the states in the machine. It also allows us to have this Nix branch for instance running at the same time in the same machine side-by-side with the normal way that we're doing stuff right now which is great for testing.

23:00 - 24:00

Pedro: Because you if want to get into the Nix environment you just type Nix shell then it does all the stuff that it needs to do, defining environment variables and so on, such that you can build on top of the Nix packages. If you're not in this shell then you don't see this stuff, because it's hidden away in this root folder. So in terms of where we are right now, the mobile phase has been done a couple weeks ago, that's finished, and we've been able to remove the usage of like three package managers and replace that with Nix. The hard part now is to replace the desktop part of the dependencies, mostly because of QT.

24:00 - 25:00

Pedro: That last week I was able to do it for linux, so right now we have linux building and packaging, and it even has the webview, which is not something that is present in the original Nix packages. It's only the building of the webview for Mac OS that's giving us problems right now, and that's what I'm currently looking at. Hopefully it's not something too serious and we'll be able to get them unblocked fairly soon. So once that's done we have everything we need in order to phase out the old way of doing this and merge this Nix branch and start doing everything inside Nix. Also changing the CI servers. Yeah that's basically it. I don't know if anyone has questions about it, if they've tried and hit some roadblocks, I'm all ears.

25:00 - 26:00

Oskar: How did things go with the Android SDK?

Pedro: Android SDK for the time being is not taken into account, we still do it the old way. It will get installed automatically, but not inside of Nix. But at least this gives us the advantage that an external contributor will only have to do make setup and he will have everything configured automatically, and we can guarantee the build environment will work. The Android SDK is not something that is a blocker, we can fix it in a subsequent pull request.

26:00 - 27:00

Jacek: I have a question, let's say that a random package is updated by the upstream with the bug fix, and we to incorporate that bug fix, what is the workflow that you imagine, what are the steps?

Pedro: There are some different way you can go about it. You can maintain your own fork, we could have the status fork of the Nix packages repo, some people don't recommend that, just because of the maintenance involved. You could also possibly, in the recipe that you used to import the Nix packages you could possibly patch that there. It's not something that I've gone into depth until now, but it's something in the worst case scenario you just maintain a fork of the Nix packages and you try to keep it as lean as possible, but you could import those newer packages there.

27:00 - 28:00

Jacek: And let's say that it has an upstream version that is good, what are the steps that the developers have to take when upstream is keeping up to date, or when Nix packages is keeping up to date with the upstream.

Pedro: I'm not sure I understand the question, can you rephrase it?

Jacek: Do we lock down the versions that are installed?

Pedro: So the way that the Nix packages work, you clone a specific tag of this repo, so it's bit like... what's the name of the other package manager we just replaced a couple weeks ago? The one we used for Mac?

Eric: Brew,

28:00 - 29:00

Pedro: Yes, so with Brew, it's the same thing, you just clone the github repo, and you're basing yourself on what's described in this repository, it's the same thing with Nix, so as long as we clone this specific tag, or commit SHA, then you know that they are locked down. So if you want to get a newer version of things, you just have to replace this SHA or tag. So if you want to get a specific version of one tool and a specific version of another tool, the workflow is very hard, but I think the important thing for us is not really to have on specific version of each tool, it's mostly to guarantee the specific version of each tool are locked down.

29:00 - 30:00

Pedro: To have known good versions and not really to focus on having one version per tool that is completely made up. Does that make sense?

Jacek: Yeah cool that answers it thanks.

Ricardo: So everything should use the same version that's what you mean.

Pedro: Yeah like if I commit something to status react and then you go in to clone it and you do the Nix shell, it will pull down exactly the same version of the tools and packages that I have on my machine, that's the guarantee that they give you.

Ricardo: Great I got it.

30:00 - 31:00

Pedro: The nice side effect of that is that if I want to build a commit SHA from a release 933 or 932 from one month ago, I can check out that tag, and I'm guaranteed that I get this exact packages and tools that were used at the time to build that version, so even if the tools moved on and maybe they are no longer compatible, I will still get the exact same environments that I had at the time.

Oskar: Yeah that's really useful.

Pedro: Yeah and the tooling is really good around Nix. I had a similar experience with Conan. That was the package manager that I had introduced for building windows desktop.

31:00 - 32:00

Pedro: Nix is actually one layer on top of that. The ideals are the same and part of the way they implement it are the same, but Nix is even more powerful than Conan, so in time it would make sense to replace it as well.

Oskar: Cool anything else on Nix.

Oskar: So that was pretty quick, is there something that people would like to talk about? Any quick announcement or anything like this?

32:00 - 33:00

Oskar: I can share a super small one, there is now a transcript, at least for one of the dev calls, you can add it, thanks to bounty so we have these notes but now also transcript for the 10th dev call, and I have two more bounties for the other dev calls as well, if there's something you're looking for that you would like to refer to.

Pedro: Where are these transcripts stored afterwards?

Oskar: So status-im on github, slash PM and it's in the readme.

Pedro: So normally it's searchable if it's done that way.

33:00 - 34:00

Jacek: So I have a quick thing I saw in my inbox this morning which is that Nimbus just synced block 500,000 which is pretty cool. It's one of our bounty contributors that's been really killing it lately, it's been fixing lots of bugs, so it's going pretty quick now, pretty nice to see.

Oskar: Fantastic. Anything else?

Ricardo: So it's been a little bit annoying for me to use Status lately, I don't know if anyone else having same issues with connectivity?

Oskar: Yeah that would be good maybe some updates on core about the problems with the mail servers and all this stuff? Anyone who wants to give that?

34:00 - 35:00

Pedro: I don't know if Adam is on the call?

Adam: I'm here. Yeah I can give an update about the mail server, but it kind of depends on what kind of connectivity problems you have. Because what we fixed is the problem when you connect mail server and you lose a connection and your node ID stays in the mail server for quite a long time and you cannot connect to that mail server anymore. So if that's the problem then it should be fixed, if it's something different, then I guess it depends on exactly what it is.

Ricardo: I'm not sure but I think there is multiple. That would be one. That is something that is currently running and will be fixed?

35:00 - 36:00

Adam: That's already fixed, because it's only a problem on the nodes running on our servers, mail servers specifically. Some other improvements to the peaking mail server, I know that there were a couple pull requests recently merged to status react but I guess they are waiting for a release that should happen tomorrow I guess, very soon I mean, this week.

Ricardo: I tried to run the mail server myself but I had some problems, it seemed to work but it seemed not to save the messages and delivering, not sure but that would be something interesting to try out in the future.

36:00 - 37:00

Adam: Yeah sure, I'm available so if you would like to get some help with setting up the mail server just debugging it, let me know or generally there is status core infra channel, that usually people hang out there who know what to do. So yeah happy to help with any problems. Recently Yakapolous recently playing with mail servers and providing nice interface using docker and docker-compose, so maybe that will be helpful for you, just to simplify stuff. It's pretty simple and actually makes it much easier to run your own mail server, so yeah there's this new option available since two weeks ago.

Oskar: Is it documented in the running node, running your own node on doc side.

Adam: I think not yet, it has readme and stuff in the repository, but might not have been ported to this run node in our docs. We should do that.

37:00 - 38:00

Ricardo: Yeah I was able to run the node in my own computer and it connected and seemed to work, but it kept connected, like it looked like it was working, but I never received a message, so when I switched to a mail server from the cluster then I got the messages, so that was the problem I was having. I will try to contact you about that. Because I think that maybe if the cluster is overloaded, if I run my own node I could never get these problems, that was my goal, make it work for me at least perfectly, then I don't have to care about the clusters. I was afraid that I was not getting all the messages and I was afraid that people was not getting my messaging so I tried to make it that it's more reliable.

# Chaos Unicorn Day

38:00 - 39:00

Ricardo: Like maybe if I ran the mail server myself maybe that could be better.

Adam: Yeah that's a totally valid assumption, like if you run it on the server and you keep it connected to the network. I mean it generally should be the same using our service because the nodes were not really overloaded, there was just this problem, so if you use the code from like two weeks ago, that problem would also be on your server. Let's talk offline on status and we can figure out what the problem.

Oskar: On that note, we have the chaos unicorn day April 1st, so that's gonna be a day when we shut down things like our cluster and so on.

39:00 - 40:00

Oskar: So that will be fun. It's up to you and your swarm how relevant it is to you, on one end you might not want to prepare at all, and it will just be that day where things are chaotic and we'll see how things work with hosting our own stuff and so on, but maybe it's more relevant to your swarm, in which case this will be a good time to think about maybe what it would look like without it. It's like a fire drill where we're gonna turn off all the things that we should be ashamed of, all the centralized aspects. If we know any projects in this space please let us know.

Ricardo: I think that's a great point because we need to be prepared for that regarding the mail servers.

40:00 - 41:00

Ricardo: From what I noticed it when the mail server is not working properly I still manage to communicate with people which is really cool, just because I'm on the whisper peer to peer network, I'm able to send messages and the other clients are able to receive it, but the only problem is the offline messages that doesn't work. So if that day that we shut down the cluster, we will not be able to read the offline messages. Every message that is sent offline in that period will be lost if no one kept a cache of it.

Oskar: Well even more than that, you need boot node right now, we host most of the boot nodes right now so that's another thing. You can add a custom boot node, but right now it's not clear how closely connected a network is but if we shut down all the boot nodes in the cluster you want be able to talk at all. So that's a good reason to get rid of all centralization in our cluster.

41:00 - 42:00

Oskar: On the note of messages being lost at all, currently yes but this is also something where data synchronization layer would help. We'll see if we get to it before chaos unicorn that would be amazing, but if not yeah.

Ricardo: Do you think it would be interesting to have some group discussions to prepare status for the unicorn day so we are not hit on the face by it.

Oskar: We had a call last week, we don't want it to detract from the focus of shipping the white paper and making status a reliable app for sort of public launch, so that's still priority one and two, but that said to some swarms it might be more relevant prepare for it, but we don't want it to be something where people shift their roadmap, we still are focused on shipping the white paper.

42:00 - 43:00

Ricardo: Ok that makes sense.

Oskar: But if you have ideas on how to survive, a survival guide or whatever, you can post it on discuss and it can be a fun side thing.

Ricardo: Yeah I think the risk of having this centralization problem is only temporary, but it is a risk if we're able to be shut down by an attack, that would be a problem, but I see why it's not a priority right now. But yeah I think it would be a fun experience to show everyone what would be like if we didn't have this driver. Seems like it would just not work, we would just shut down status that day. I think for that not happening that should be at least kind of working, I'm not sure how. The boot nodes problem -

43:00 - 44:00

Oskar: So that's an example, you should be able to run it with your own custom boot node. If that's not the case it might be some small things we have to do on the core side of things to make sure it works but you should be able to host your own boot node. So everyone can host their own boot node then on Twitter or Reddit or Discuss people can say well here let's join the network together and it would be a social experiment to see how quickly that network would deal without our cluster.

Ricardo: Yeah makes sense.

Oskar: Any other thoughts or comment on chaos unicorn day or any other type of announcement before we end this call?

44:00 - 45:00

Ricardo: Regarding the discussion about how the public chats would be, because right now we're not touching that because it's not priority because it's not priority but I think that we can, while we don't develop it, we might be able to discuss how we want that to be for example, because the public chat doesn't have moderation right now and that's bad in my opinion, or just my opinion is wrong, but we should discuss that. Also about the group chats, they currently have this one administrators, so maybe we want in the future more adverse type of group chats that you have a contract that is a small democracy that controls who can enter it or who can use it.

45:00 - END

Ricardo: That's also part of Tribute to Talk in this meaning of replacing patreon.

Jarrad: Let's add this to a discuss post.

Oskar: Yeah a discuss post, and you can add it to the next core dev call. Alright any final words? If not, let's end this. Alright thanks everyone, see you in two weeks, bye.

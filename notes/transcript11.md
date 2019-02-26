# Intro

0:00 - 1:00

Oskar: Welcome to the eleventh Status Core Dev Call. We have quite a lot of things on the agenda today. We did a poll SMT voting to find the things people want to talk the most about. We'll start from the top and see how far we get with the time we have. Also just a small PSA, if you go to the repository, status-im/pm, we have a index of all the previous videos and notes if you want to refer back. Let's get started, so the first topic is Whisper availability inside Status Dapp browser, which is something that will benefit Teller Network as well as Gas Relayer and possibly others. So I guess Richard, would like to elaborate on it if you don't mind?


# Whisper Availability

1:00 - 2:00

Richard: So basically we are going to do the development of the Gas Relayer and Teller Network. We saw that we have a need to have Whisper available in all the apps, mostly because we want all the apps to be able to communicate between each other. What the rest of the team working on the Gas Relayer and Teller Network and I wanted to know is what is the coordinate state of this functionality and what would it take for Dutch to be able to use Whisper in the (Work Tree?) provider that the Status provides?

Status (Dutch?): Well since I've been discussing this before, probably since it's building, I have improved my answer. So first question is, do you need this functionality only when the Dapp is open in the status browser or do you need it to send the synchronous notifications to somewhere.

Richard: Probably what scenarios would be useful?

2:00 - 3:00

Status (Dutch?): So for the first one it's pretty trivial to just allow the namespace and we already blocked the... by default Whisper has a pretty poor API in terms of security, so if we just allow you all the whisper API you would be able to take the private keys and replace them. So we already limit them so we can allow this while the app is running, basically Javascript is being executed in the browser. That will not help you to do anything synchronous while the app is running. So we were discussing things like for instance, you get a notification that you won the bet, and you need to send the notification, for that it is pretty useless to just allow it in status browser.

3:00 - 4:00

Status (Dutch?): For that we thought about different things, and I even had a hacked version of Status Whisper that allows you to in Javascript make a whisper envelope, and just use a HTTP/RPC API to send it. But then the problem is where to host it. I know that there was a huge pushback against hosting our own server with that because of the distance realization reasons, so that's our biggest issue right now. What will be this place where you go and call this RPC API when there is no status client active. That's where we stopped. Otherwise it's a technically solvable issue.

Iuri: So already having the first case supported that will be a huge help.

4:00 - 5:00

Status (Dutch?): So just inside the browser right?

Iuri: Yeah that would already be a big help.

Status (Dutch?): Yeah so just ping me on Status, I will add it to our backlog, and I will try to just make an update to Status GO and it will allow this namespace, it's pretty trivial.

Ricardo: So just a question about this namespace. It needs to be locked because if you allow anything at Whisper you could also make transactions or anything using that?

Status (Dutch?): Essentially you can pretend to be someone else and replace the keys and things like this, so all this API Whisper doesn't split for some reason, like management API vs. normal user API's so if you allow all whisper API's you will have all Admin API's which you dont want. So what we did is we made a whitelist of methods that we can allow. Right now we just block everything Whisper, but we can allow POST, which is probably the method you want if you want to send stuff.

5:00 - 6:00

Status (Dutch?): And also creating filters and reading from filters which is also a question. Do you need to be allowed to read from Whisper, otherwise you will theoretically be able to read all the messages from all the chats.

Jarrad: Is it possible to blacklist the Whisper public key that the user is logged in as?

Status (Dutch?): Yeah it's also possible, we can do whatever we want we intercept all the calls and inspect them at runtime, right now what we implemented is we whitelisted the POST method or something like that, but we can blacklist as well just in case.

Iuri: We would need the public key for identity purposes.

6:00 - 7:00

Status (Dutch?): But you need a seperate, or do you need the same public key as the user? Because you if you use POST it will use keys as a user. Or this is private keys I'm talking about. The public keys you probably can use whatever you want.

Jarrad: Yeah so sorry I meant the private keys from the whisper keychain.

Status (Dutch?): Yeah so I don't know maybe it's worth setting up the meeting with Cory about how to treat those. Maybe we should generate a second key-pair for dapps seperately so you can figure out if a person sent this message or a dapp in behalf of this person.

Jarrad: I think dapps can generate their identities and inject into whisper keychain from the API, unless that's changed? So I think that would be fine as long as we can expose the currently logged in user public key to dapps which doesn't have to be through whisper.

7:00 - 8:00

Status (Dutch?): Yeah isn't this possible already? Just to get the public key from the current account? It's not a whisper API?

Jarrad: Yeah that would be the address, I'm not sure if the public key.

Petty: I want to be real sure on what we're exposing to people, whether or not we're informing the user that that's happening. At least wanna know what we're exposing to people, then informing the user what we expose.

Status (Dutch?): That's what I would like to do, use case by use case, maybe we can just make a diagram for each use case how we think and then you can review it.

Iuri: There is also the question of "would we confirm what the user each post?" or just let that happen? I kinda see that at minimum the user would have to confirm they wanna give whisper access to the dapp? But then the question is if the dapp does a post, do we want a confirmation for that? I'm not sure it would be very helpful, depending on the payloads.

8:00 - 9:00

Jarrad: I don't think it is. I think if we kind of bundle this in, in the same dialogue that allows you to access web3 in the first place. The major concern I have is having the private key of the logged in user in the whisper keychain that is accessible by a dapp. If we can mitigate that, then it's basically down to a responsible disclosure of a public key to the dapp itself.

9:00 - 10:00

Iuri: I think a possible solution for that would be, the user would authorize a public private key generated by the dapp itself as a representative so to speak, and then it gets sent client-side, kind of a like a central transaction in web3, but the thing is that whisper does not support this API, it's kinda of all like server-side so to speak.

Status (Dutch?): That's what we hacked with Andrei actually, I think it was a raw post to post raw, when you can encrypt everything in javascript lets say, then just post raw data that will be transmitted into whisper. That works.

Iuri: That design makes much more sense. I was actually quite surprised whisper designed this way.

Status (Dutch?): That's exactly why there is no whisper on (inFuhrer?)

10:00 - 11:00

Iuri: I think that should be proposed as a standard or extension of whisper.

Status (Dutch?): We did talk to the whisper guys but I dont think it went anywhere. Maybe we should go for another round.

Jarrad: We could propose it as an EIP but I wouldn't put too much love into it. My understanding is that it's better that we focus on our protocol efforts moving forward.

Status (Dutch?): So maybe we should just have a separate discussion on exactly what to do and who will do what in each timeframe, just specifically for that.

Jarrad: Yeah sounds good.

11:00 - 12:00

Iuri: Just a final question, if we do then enable the whisper object, how long do you think that could take, including the release itself?

Status (Dutch?): Well it depends on how we want to enable it. Just enabling the POST message, including the release would probably take a week. If we are talking about also having some UI that shows "this dapp wants to use whisper do you allow" would take more time.

Jarrad: It would be pretty ideal if we could maintain a separate branch that has this trivial version enabled so it doesn't block the Teller Network guys. But we won't merge that into develop any time soon.

Status (Dutch?): That's actually a good idea yeah.

12:00 - 13:00

Status (Dutch?): So the simplest POST that will actually use the privacy of a user, even if it's a separate branch just for testing can be done in a day. Then post raw might take a few days more because I kept this code in a separate branch it might be already outdated after all the guest updates.

Jarrad: That sounds like a good path forward.

Ricardo: I think that this concern about using whisper is actually something in the concern of using the identity of the user because of course there is other problems about the too permissive API of whisper that should be solved, but I think the main concern should be the use of identity and what these apps can do automatically or by requests as someone mentioned.

Jarrad: Yeah that's why it's critical not to allow the dapp to have access to the private key and the whisper keychain.

13:00 - 14:00

Status (Dutch?): Yeah but that's one bailout the whole method that gets private keys is totally blacklisted so no matter what you expose it will be blocked on the integration level. So even if we exposed SSH namespace.

Ricardo: Yeah but what I mean is if you open the app you don't want the app automatically sends messages in your name to your friends because they not only read the message but fake your identity.

Status (Dutch?): That's why when we should release only when it's generates a separate pair of keys so we know it's a dapp on behalf of the user and not the user himself.

14:00 - 15:00

Iuri: So just a quick question regarding what we just talked about, the central transactions so to speak, you're talking about RPC server and all that, but can't we just, the whisper object that we inject into the dapp, can't we put an api that all it does is forward the package?

Status (Dutch?): Yeah I guess the latest idea was like this. Just generate the entire envelope yourself, the api just sends the envelope already encrypted with what you want. That's what we wanted to essentially, we worked on to enable bots on whisper but it didn't go very far so...

Iuri: We actually have all that in GS already with murmur, and then it's just a matter of the transport protocol. That way the injected object would have entry and murmur can just connect to that.

15:00 - 16:00

Iuri: For Teller this would be great, if the browser supports whisper we can use that, if not we could use (lipidTP?) and all that stuff. So we can talk outside the call about how that API could look like.

Status (Dutch?): I'll try to find out where my proof of concept is.

Jacek: One other thing to keep in mind, if you allow to free and access these API so that dapps can basically publish anything they want without any structure, will also be closing the same upgrades path for the future.

Iuri: Closing the what sorry?

16:00 - 17:00

Jacek: The same upgrade paths for the future. So basically if you allow everything, apps will use everything, and we'll never be able to retract that access. Sometimes it's good to release a feature with a little bit of structure in the beginning, because it's always easier to give more flexibility than to take flexibility away.

Ricardo: Yeah you mean with cross-hacking it with the access of accounts, for example we have this peer private mode, some apps with the private mode others not, it's very interesting point to have these well thought before releasing any API.

17:00 - 18:00

Jacek: Yeah it's that, and maybe also some sort of framing of the message so we can change our protocol freely, so thinking a little bit exactly what kind of functionality you offer to dapps, so we can also remain flexible for the future.

Iuri: I think that depends at what level we are talking about the protocol. Because in my opinion whisper should just be the transport and nothing else. Any protocol we do should be within the whisper message. So it shouldn't really matter because the dapp is using that dapp communication part, it shouldn't affect us and how we do our protocol.

Jacek: So I'll give you an example. One thing is that we are not really happy with mail servers. So if we expose mail servers and dapps start using them, we'll have to support mail servers forever. Whereas in the protocol working groups there is some thoughts of offering synchronization basically, or replication as a feature.

18:00 - 19:00

Jacek: Which would not be based on mail servers, so if we want to expose some kind of message streaming or whatever you wanna call it, reliable messaging as a feature, you sort of bake yourself into a corner if you offer mail server support then removing it and try to introduce this other form.

Iuri: I think the issue with the mail servers, I don't mean to derail the discussion, I think the issue with the mail servers is that they look like they are extending the protocol at least for our RPC call, while in practice I think it should just be something that is physically cut like a channel, request within a channel to get the messages, and then the mail server is just like another application that is listening to that channel and responds to it.

19:00 - 20:00

Iuri: That way you don't have that sort of coupling that exists now. So if someone wants to implement like a side chain or something like that that was proposed as a possible solution to a mail server, they just listen to that channel and implement whatever solution, and that's it it works. But if it's something that's not on protocol level or RPC level, then everyone wants to implement a whisper client compatible with series as to implement the same call same extension it becomes really coupled, and then it brings all these that you are saying that dapps rely on something, and because they are done in a certain way we have to support them forever.

20:00 - 21:00

Jarrad: The SHH object that we're exposing here is already defined by web3.js and basically they are in foundation. Even though they were exposing it, it's already box. I don't think that the amount of dapps that even work at the moment or that even exist, or that even use whisper are fewer still. I think practically speaking, we can take these things into consideration when we're working on our own protocol, we may keep this but most likely we'll drop support for this in the future anyway. So as long as that messaging is clear.

21:00 - 22:00

Jacek: It's all about managing expectations and not putting ourselves in an uncomfortable corner.

Petty: Shall we move on to #2?

Ricardo: Regarding mail servers I think that what should happen is that our implementation of EU servers should become something called mail nodes...

Oskar: Let's make sure the conversation's focused, we have quite a few other things to go through. So let's move on to reproducible builds and sort of a quick overview and what's been going on. Pedro?

# Reproducible builds

22:00 - 23:00

Pedro: I just wanted to make sure we're all on the same page. Just to start I'll give an overview of the problem for those that haven't been participating in these discussions in this space. So our goal is to be able to build old commits and be sure that they produce the same binaries. Right now our repo's are not set up for that. They sometimes reference external tools, which can be replaced by third parties at any time, we have no control over that. Or the same for branches in external repos that we reference. So sometimes we fork repos but we still reference the master branch and it's very easy for some other Status contributor to just do a commit on that master branch, that means that we'll never be able to just checkout an old commit and be able to build the same thing.

23:00 - 24:00

Pedro: So what I've been doing to mitigate this is for instance self hosting the external tools which don't have reliable versioning, and replacing the node references that target a branch or a specific commit, with release tags whenever possible. So in order of preference we would like to use as much as possible release tags and if not possible then commit SHA even though the commit SHA has the problem that if someone rebases a branch and force pushes it then that will be broken and we won't be able to build it again, so as much as possible we want to rely on release tags.

24:00 - 25:00

Pedro: Of course last week I did this but in order to make sure that in the future we don't continue to run into these issues I've built a bot to monitor our repos so whenever you do a pull request that touches on package.json or go package.toml for go repositories it will check what kind of reference you're doing, and if it notices you're relying on a branch, then it will prevent you from mergin that pull request and suggest changes. The thing is there are a ton of repos that we rely on right now and it's not easy to go through all of those and make sure that we are in needed shape so I would like to ask everyone if you've forked repos and you added reference to status react or something, if you could go make sure those repos are in good shape and not relying on the master branch or some other branch, just create a release tag on the repo and update status react or whatever other repo.

25:00 - 26:00

Pedro: Just making sure that it's not just a small corner of status that is aware of this, we need to all be working towards this and being on the same page. I don't know if you have any questions?

Petty: Maybe be more explicit on what everyone can do to help this?

26:00 - 27:00

Pedro: Ideally the bot will already catch these situations, but we can also be proactive and like if there's a repo that will never be touched, the bot will not say anything, so ideally we would go to repos that we forked, and create a release if there isn't one already for a specific commit that we want to use, and update that in status react. Sometimes we have two or three levels down, so it's something that everyone needs to be away as they add dependencies to our repos that we might want to build them in the future, not just the current head of the repository, but some other, we might need to build a patch to an old release, and we want to ensure that we are building the same things, not some with some uncontrolled dependencies.

27:00 - 28:00

Pedro: So just be critical of dependencies that you see, and ask yourself if this can be built in the same way in the future. If you know a repo moves and has some new additions to this branch, will I be able to build it in the same way? That's a good reflex to have I think.

Ricardo: I think most things can be written by themselves. But I think some simple things that are only taken for convenience, that if you take like 100 lines to write it, that of course should not be a dependency. But if something very large, also something about the trust, if we do not trust the dependency, we can audit that specific version and get that commit hash of that dependency and lock there. There is this two cases that let's see.

# Fee Structure

28:00 - 29:00

Pedro: If there's no further questions I think that's it.

Oskar: Cool. Awesome. There's been a bit of discussion for fee structures for SNT Utility. Rachel do you wanna give a brief overview?

Rachel: So this is coming up in context of Sticker Market sales because we're doing work to finalize the Sticker Market registry contact right now. Specifically whether we should take a percentage of each sale to fund our project directly or to burn perhaps. I guess the heart of the matter is really about how our project sustains itself financially in the long run.

29:00 - 30:00

Rachel: The predominant hypothesis seems to be that token velocity and value combined with having good open source contributions should eliminate the need for us to ever be charging rent for features but there might be worth burning a percentage of each sale of stickers in the meantime to have a deflationary effect. So I'm not sure if we actually want to get into the debate about these structures overall and financial sustainability of the the project or if they should just stick to the focus of the sticker market registry contract and regarding the fees for that right now, what decision do we take for the contract and how do we future-proof it for any like potentially desired changes in the future.

30:00 - 31:00

Ricardo: I think if we have something like the sticker markets and the Croatian markets then having this operation over the sticker packs, we might have a kind of optional fee and maybe when the owner of that sticker pack can specify how much a fee goes to the Croatian market automatically based on the user buys. It goes slowly rising organically as users buy it. And of course if the sticker market artist want to promote their own sticker pack they could just deposit in the Croatian market.

Rachel: I think that there was also a similar suggestion made that artists when they submit their packs to the registry they could optionally donate some percentage of sales to status.

Jarrad: From an implementation standpoint, going back to this as a registry discussion, from an implementation standpoint many of these look very similar. Basically it's a certain number and sending it to a certain address.

31:00 - 32:00

Jarrad: If we're choosing to burn then it's just zero. Zero otherwise the address be like the Eurasian market or whatever. So we can definitely defer this decision-making while not impeding implementation so much, if we just implement these calls.

Rachel: Yeah, I think that makes sense. Ricardo what do you think.

Ricardo: Yeah I think we can go with free fee or maybe we can settle optional in the smart contracts so if we see any problems we can rise it and start with zero. The question about having the fee is also about the appeal to the artists because then if you have no fee you have a strong appeal for artists joining this system. The competitors they get a lot of higher cuts from the artists.

32:00 - 33:00

Rachel: The competitors I guess in one of two versions of sticker markets, there's much higher fees taken out of every sale, it's much harder to get stickers to get included in the market, it's very hard to even do that in the first place, so it's a huge advantage of our marketplace that creators will be able to do so permissionlessly. But I think when it comes to economic incentives for the artists they have to have an active user base and a product that is accessible to many people in order for them to see sales as well so there's multiple factors there.

Ricardo: Also the problem of introducing a fee with no reason is not exactly moral because you are creating a concentration of powerful there, and it might be unfair. Having optional donation fee there is no problem but having forced fee, I don't agree with it.

33:00 - 34:00

Jarrad: I agree with that, it's definitely a moral question, that's why I agree that if we have such a thing it should benefit everybody who's participating in the network.

34:00 - 35:00

Ricardo: The reason that the ways we can have fees for going to the development is exactly by the idea of slashing bad things on it and having some sort of creation over it, so I think we can go sticker market without these fees maybe introduce some fees like first sticker pack artists create need to commit something but I also don't think it's good but might be interesting because of maybe spam, too much junk going through the market maybe we need to filter it.
But then this fee doesn't go to status it just gets locked there, just like the usernames. And see how maybe we create this in the Croatian markets and see if we can have some kind of trust on the output of Croatian market to actually slash someone's deposits. I think the current way that have on the Croatian market is more like ranking so it doesn't have any consequences besides there is some loss of deposits in case of internal slashing.

35:00 - 36:00

Ricardo: Also we can then just use the Croatian market as this is stated to have a minimal reputations to show to have this filtering. So that's what I think about this whole idea of fees, because that's the only reason to charge a fee morally, is to filter, otherwise we don't have any reason to charge that fee.

Oskar: From an implementation point of view, are there any blockers in terms of if we defer things and just say what's going to some address, is there something that's blocked in terms of when this decision has to be made?

36:00 - 37:00

Rachel: Yeah this is impeding the contract from being completed, so yeah it's important that we decide on it this week ideally.

Oskar: You can just defer to a different contract right and then leave that under specified for now. Is there a problem with that approach?

Rachel: I don't think so, no.

Oskar: Is there any objections to that approach?

Ricardo: So it will be an optional fee in the smart contracts or two versions of the smart contracts, one with the fee and one without the fee?

Jarrad: Optional I imagine, and set it to zero to start with.

Rachel: Yeah I agree.

Ricardo: Ok we will focus in going in that direction in the Sticker Market contract. Maybe we will have some other calls just regarding this sticker market where we make the detail how the user experience over this will be, the optional things.

37:00 - 38:00

Ricardo: Because that should be not only for the (MVV?) but for the whole idea for the final roadmap of sticker market, so take into consideration, we didn't have this decision, and I think everyone mostly agrees with the idea.

Oskar: Alright. So moving on, ULC just got merged upstream after eight months, so that awesome. What does this mean for status and can we integrate it sometime soon? I guess Igor you have the context from the (LESS integration effort?) what's your take?

# ULC

38:00 - 39:00

Igor: Well there is even a PR that integrates ULC but as a separate patch that enables it, but the problem with the ULC is the same as the problem with LESS, it needs servers somewhere. And with all this Constantinople thing there are no reliable servers even on the main nor Rinkeby right because as I understand last time it was tested on Rinkeby. So we need to wait until Constantinople is finally resolved. That's the big blocker, and it was since I started integrating this, because we started doing something then half of the nodes were not Constantinople half were Constantinople. Also you'll see is not a magic thing, so it requires that you trust some nodes, and that means that you kinda need some place, and it's not solved, it's just like this, this PR is essentially technical implementation of what if you know, who you can trust, then you can do this quick sink solution something like this.

39:00 - 40:00

Igor: But the question is how do you know who you can trust, and that's a big question.

Oskar: It's still a step up from only offering (Rivera?)

Igor: Sure but that means we also have to host this trusted servers ourselves and protect them.

Oskar: On that note, Andrei Petro, who's working on webnode, he also reached out and he's looking to integrate the ULC support for webnode, so that would be at least one source for these types of nodes. It's definitely not a general solution but it's a potential start maybe.

40:00 - 41:00

Igor: Yeah but the problem is that you can't validate anything, because what's different from LAS and ULC is that ULC doesn't validate blocks properly. It sort of defers this thing to other nodes that it "trusts". So where will you get these trusted nodes from. Sources of just blocks, you can find them. But which ones you can trust which ones you can't that's the big question.

Ricardo: So might be something that we could make an appeal to someone that is giving bad information about a block and to participate on that you need to have some deposit and then you can learn by giving this ULC responses to the other nodes. So if someone misbehaves they would go to some kind of court system that could be automated because we can probably prove, the nodes could probably do that automatically,

41:00 - 42:00

Ricardo: It's not like something like in the Teller Network that you need human verification if that is an honest claim or not, in this case, all the nodes can just verify from their blockchain if that current state was valid once it was answered.

Igor: Yeah but that makes it a big project.

Ricardo: We can start by being that one entity that does the verification and then decentralize that as a second step. And of course that's step zero which would be everything like maybe the inferior that lists the trusted and then you can register there and these lashes by status if you misbehave.

42:00 - 43:00

Igor: Yeah I'm sure but it's just a full blown project in terms of what I see. We either do everything centralized and then just provide the second centralized solutions solutions like as opposed to inferior which is ULC in our own trusted servers. And sure the blocks will be generated by someone else but the validation will happen on our nodes. Or we just make the whole project with a smart contract and this slashing and whatever else is there because there are multiple ways how we can try doing this.

Ricardo: We can do like a state channel of signatures to do these micro payments between the nodes, so the nodes when they request they need to provide these signatures which then download status remove these tokens from their balances. But of course after many requests, not after every request.

43:00 - 44:00

Igor: Yeah yeah but my point is that it's not a week's worth of a work it's much more.

Jacek: First of all there is a proposal on discuss about this specific thing. Above all I would say that it's a big mistake to run any ULC servers as status. If a user already has a trusted server through vipnode or their own then having access to ULC is fantastic, but us running ULC servers is a big deal.

Jarrad: Agree.

Igor: That's why it's not prioritized.

Jacek: I'd say it's a big no no.

44:00 - 45:00

Petty: A better way to go about this, you think ULC might be allowing someone to run some type of node at their house and then their ULC version attached to it, but us running something is not the right way to move forward.

Igor: But why is it better than somebody runs the nodes and connects with HTTP or json RPC API? So we allow right now if you create a custom network you can still show your custom RPC URL and it will work. It's a different technology but you get the same kind of thing. Is it any better than that?

Jacek: It's the same but it's a stepping stone to something else. Running our own servers is worse. It's a step backwards instead of a neutral step.

45:00 - 46:00

Igor: Yeah that I agree and that's why both LESS and ULC are not that high on the roadmap right now because it's a huge project on how to do the whole crypto economy balance that everyone can run nodes and somehow communicate and validate eacho ther, or maybe it's even worse than inferior.

Jarrad: I agree with both the workload and the secondary step, if there's the ability at least to expose the ability to run ULC even if you bring your own node, that would be a great step in the right direction.

46:00 - 47:00

Igor: Yeah that's possible to implement relatively in the short term. I don't know if the PR was merged or how well tested it was. Because we had problems with ADS and ULC probably has the same issues with chain being too far away from what it actually is and doesn't really handle when the chain forks and then remerges, it didn't handle this well. We can try to enable that as test mode when we upgrade status go next time.

Jarrad: That would be amazing. Let's not worry any further than that for now.

47:00 - 48:00

Ricardo: I think some of the ULC improvements they can also be used for the mail servers improvements, getting rid of the mail servers, because it seems to solve the same problem, but instead of solving the story of messages, this is network, so kind of similar problem in my point of view.

Igor: I don't see how, because essentially what is ALS is, ALS is normal ethereum client but with smaller receipt sizes that you download, you don't download all the data, only selected data, but still verified. ULC is the same as LESS, except verification of blocks code locally you call some RPC method to some other node that returns the hash or something.

48:00 - 49:00

Igor: It's the same blockchain code with some thing disabled or delegated to other nodes. So it's not like something on top of blockchain.

Ricardo: Yeah I agree that there is this difference, in Ethereum you have this linked information because of the blockchain, but in stages you don't have that, we need to solve this problem of having a proof of state sending a message, we didn't solve this, so every message is valid while in Ethereum not.

49:00 - 50:00

Oskar: Just on the topic of what differences between this and having your own remote or whatever, if you're running everything yourself it's just one to one and there's no difference, but this also opens up, because if you ULC you can have multiple nodes right, you can have semi trusted set up, maybe you have multiple friends, and lets say you have LESS service in dapp node you can connect to multiple and you don't need to trust anyone but it's still, if you check that 3/5 still return the same hash and you're still better off, so that type of racing you can't do if you just have someone else's remote servers, so it's slightly more sophisticated as well, which I think is the difference.

Igor: Yeah that's fair.

# Arbitration

50:00 - 51:00

Oskar: Arbitration? So there's a bunch of team that's been thinking of arbitration mechanisms. Seems like a common need so just trying to figure out how this looks like and who will implement this one. I guess Hester you had some points you wanted to discuss more in detail?

Hester: I'm trying to find my list questions. So the intention would be not to go too much in depth it's more to make an inventory of who is concerned about arbitration as in what swarm will need some form of arbitration. It came up in Teller Network, Sticker Market, dapp store, so it seems to be a relevant topic and I'd like to understand for whom it is most relevant. So I'd like to do a sort of round-the-room to the swarm leads to understand has arbitration come up, are you already working on it, do you see any likely forms of implementation?

51:00 - 52:00

Ricardo: I think the most solid implementation of arbitration that I've seen is (collaterals.io?) from consensus. I'm not sure if it's running but I've seen some presentations, it seems like a good solution. They provide examples of user experience, it's mostly like people trusts random other people to deal with their problems. The majority will select the most obvious answer that is the truth.

52:00 - 53:00

Ricardo: It seems like this is something that we want. In the swarms like Teller Network for example the disputing of claims might also be relevant to sticker market like copyright claim, if we want to implement that stuff because copyright is not really nice, maybe we want to have it, just to prevent, removing duplicates inside of our own registry just to have the first there, not like a copyright that you are suing, but something like that.

53:00 - 54:00

Ricardo: Maybe the declaration market could be a way to get over arbitration in the sticker markets case, but not in the Teller Network. Declaration market can solve a different problem, it makes like a ranking of the best, and arbitration is making a decision of who is right and who is wrong.

Hester: So you're saying Teller Network would mostly be in case of disputes around claims, and sticker market would be around copyright issues.

Ricardo: Copyright as an example but we can have other things, like obscene emojis, we don't want that, or maybe we have a rating claim over it, and if someone submits a sexual sticker in a plus 18 claim, the arbitration would kill.

54:00 - 55:00

Ricardo: This is a much more advanced in the roadmap in the sticker market the MVP would not include that, but in the final product we would definitely have that. For example in the MVC we have categories, the controller would be able to move or change the categories of the original sticker back to be sold. This could be done by this arbitration systems.

55:00 - 56:00

Hester: So Teller Network or Sticker Market do you see relevance of arbitration anywhere else?

Julien: In the case of sticker market, as Ricardo said we are considering using decoration market so I'm curious to hear if you think there is some kind of limitation of using decoration market specifically for using sticker market.

Ricardo: It depends on how in the end the decoration market will look like, but in the general sense there is this limitation, because you can not take an action to change something in the decoration market, you can only create, maybe you can create a sticker market over a topic for example, but it kind of gets not consistent with the data set of the sticker market itself that says it has only one category. So the things should make sense in this case.

56:00 - 57:00

Ricardo: So maybe the decoration market would be used in the sticker market but in the sense of the ranking of better stickers, while the arbitration would be used to actually remove a sticker pack from the existence of the dapps. That I think is the difference.

Julien: Ok.

Ricardo: For the closest solution that we have, the MVP's that requires this solution, we are using controller that would be a multi-sig wallet, and later we can decide how the arbitration would look like. In the case of Claros the arbitration actually looks like a governance, and it's basically that if you see the smart contracts.

57:00 - 58:00

Ricardo: So maybe that's a kind of solution, maybe we just go to working to the DOW and set the DOW to do the arbitration.

Hester: It sounds like at least also given the time for Teller Network, you're mostly looking into arbitration now, so it would make sense if it comes up in other projects, to check in with Teller Network to see what the status is there and if something has been developed in that point in time.

Oskar: So I'm not sure if this strictly answers arbitration, there's likely going to be both ULC set ups which is not a priority right now, but network incentivation there might be certain slashing schemes where you put up some stake and if certain conditions are met you slash that state. I'm not sure if you want to have it under the same umbrella but it might come up there. It's slightly different in it's mechanics.

58:00 - 59:00

Ricardo: I agree it's similar. I want to add another thing that we just start implementing these report features while we don't have it, at least sending a mail, but we can send a message inside of status using murmur I think soon, maybe today to someone that is taking care of this. Even if we don't have the perfect solution we need to have that kind of solution because we need to have this expectation of what we need to solve.

59:00 - 1:00:00

Ricardo: Ofcourse we will include that report feature, it will go to the wall of shame, but it's better this way than not having it all. If it doesn't work perfectly, it will at least show us that we need to fix this.

Oskar: Would it make sense to create an interface for this and then you can (ammend?) that whatever contract that deals with this is kind of generic and the specific mechanism that is used depends on the use case or depends on resource we do this on, what sort of abstraction makes sense and will be useful to various products?

1:00:00 - 1:01:00

Ricardo: Yes I think we could have a swarm for opening arbitration case, maybe we can implement that even for files, I don't know it depends on the future of how messaging will be, but for now we only send that message to someone or to some channel, it can be a public channel that receives all the reports, so when you click reports in a sticker pack it will go through a public channel that is reports and it will say "this sticker pack I reported it", then someone would be looking at it and maybe we can take some action if that's relevant.

Oskar: I think there's a interesting parallel to legal systems here because you can look at it like a common law based system, where you say all we know is that there will be conflicts and they might involve these agents, but specifically how this decision is made depends on, right? So if you defer it to some abstract interface and then you can sort of build up this, maybe you start off with the most common offenders whether that's stickers or copyright claims or something else.

1:01:00 - 1:02:00

Oskar: But you start by under-specifying it, and just say there's going to be something like this but it's not clear what the mechanisms are, but you can evolve from there.

Ricardo: I think the problem we want to solve is, if someone like you starts using Sticker Market and starts including a lot of junk or sexual things and it's unpleasant to people to go to the sticker market because there is a lot of junk showing on their screens, it's best interest of sticker to get rid of these things.

1:02:00 - 1:03:00

Ricardo: Now we have this, but in a centralized way, in a multi-sig, what I'm proposing is to having an open channel in the UI to send these messages in the public channel. It's not very well specified how it will be but it's some start that we can then progress in. Later on it will be something just like Claros but optimized for the (entity?) holders.

Oskar: Any other thoughts on arbitration? Maybe people who haven't spoken? Let's move on. Regarding license for our code and moving into DOW and how the relationship looks between the code and the GmbH. I guess Jarrad do you want to?

# CC0

1:03:00 - 1:04:00

Jarrad: Yeah so depending on the regulatory climates, the jurisdictions we have distributed binaries in, and the distribution channels channels policies that we have to adhere to, it seems that the GmbH may be forced to create binaries that's in conflict with the vision of what the community is about. In this case it makes sense for us to move a lot of our codebase into the public domain, which is actually a lot more complicated than it sounds, it's very difficult to waive your copyright.

1:04:00 - 1:05:00

Jarrad: However if we relicense under CC zero it basically waives everything in the public domain however it degrades into a very liberal license in the event that the law does not allow you to put code into the public domain. So in this case that would allow the community to take the source code and create a new source of truth, in which the GmbH would probably maintain a fork of and contribute to. So that requires the participation of every contributor that who's contributed to the codebase. So basically I wanted to see if there's any objections to that. You can mull it over. But then we have to go rounding up people and getting them to sign some basic paperwork allowing us to do that.

1:05:00 - 1:06:00

Oskar: What does this mean for people who have left the product?

Jarrad: That means you need to contact them and get their permission. Same thing for contributors who have never actually joined the project. Any contributor at all basically.

Nabil: Does it have an impact on dependencies too?

Jarrad: Not really, because basically we are licensed under MPL, MIT, and Apache. I think the predominant ones. They're all copyleft in some form, and CC zero is compatible with all that, and any way public domain is more so.

1:06:00 - 1:07:00

Petty: Is there any like statue or timeframe in which we have to go back, is it everyone who's ever contributed to status, or if within a certain amount of time they don't have to?

Jarrad: Everyone owns copyright over their own contributions, so if we're not using that code anymore that wouldn't be relevant, but we'd have to remove that from our history, I think it would be better to just reach out to everybody.

Pedro: I was under the impression that on our contracts we already gave up the rights to our work but maybe I'm wrong.

1:07:00 - 1:08:00

Jarrad: Actually I haven't looked up on that. I did ask (???) advice, but I haven't heard much from her.

Petty: Yeah but if someone doesn't join and sign a contract then they are not part of that set, that might be easier for anyone who has ever worked for us, but any outside contributers would have to be looked at.

Jarrad: Yeah absolutely.

Igor: Also I guess it might lead to revisit of folder dependencies if their licenses are compatible with...

Jarrad: I don't think that's really an issue, if we're using the dependencies and they don't have an issue with GPL or MPL, then they're not going to be an issue with a consumer, because those dependencies still retain their own licenses right, it's only our own codebase that we are waiving the copyrights.

1:08:00 - 1:09:00

Oskar: In terms of practically moving forward with this, what help would you like to see from other people, and if there's some sort of minimal core in terms of this is the most important for example status go and status react, or how do you look at that practically making it happen.

Jarrad: So basically (???) actually put up steps of when they did the relicensing of CPP ethereum. But essentially it's make everybody aware of this, gather everbody's contact details and emails, then email them with the situation, the paperwork, and get as many signatures back as you can.

1:09:00 - 1:10:00

Oskar: I guess practically speaking we might have some issues with bounties and so on, then look at the contributor, see if we can replace it, if not then I don't know. Especially for like designs and so on with, sort of involved with a game with map textures and so on, and there was conflict with one of the designers and he left, and that led to all of the map textures having to be redone. This is also maybe where decoupling the protocol from implementation would also be useful because that way if there's an issue with a specific implementation it would be less severe as well.

1:10:00 - 1:11:00

Oskar: On that note it would be useful to make sure that when we do the specifications and so on, the swarm templates are already CC zero but I don't know if there are other specification documents where this would be applicable as well.

Jarrad: If we're seeing further into the future there's a very real possibility that the reference implementation will be a new code so it's not the end of the world if we can't do it with this one but it's definitely worth trying.

Oskar: Any other thoughts on licenses? Cool alright I guess we're skipping the swarm updates. We recently starting blocking the PRs.

# Automated Tests

1:11:00 - 1:12:00

Oskar: We had some issues with the PRs being merged that broke develop, and we are trying to block them with automated tests and so on and there's been some efforts in that area recently, Pedro do you want to give a brief overview of the state of things there?

Pedro: The issue that we had that there was a period of time during the pipeline of pull requests where we weren't checking if automated tests had been run. What I fixed last week was to ensure that a PR already starts failing, when you create a PR it's in a failed state because there's no automated tests running, and that fixes the majority of the issues. The thing we don't have running yet is actually blocking the PR from being merged, even from a script.

1:12:00 - 1:13:00

Pedro: And to do that we would have to change some other things and the way the repo is set up. I tried to do this with Jakob last week but we had some issues, so we quickly saw that it wasn't an easy solution and that we would need to investigate further in another repo so we wouldn't step on other poeple's shoes while they're trying to do their work and merge PRs, so ideally we would create a replica of status react with all the automations and do the tests there, and once we are sure that everything is working we can deploy that on status react. Right now at least we get a visual indication that the PR is not in a good state, which is already a very good start.

1:13:00 - 1:14:00

Igor: I actually have some addition to that. This issues when develop got broken, there weren't any malicious case, it was because the visual indication in the PR was that everything is ok, and just test didn't run yet, so this thing was actually blocking the script from running is much less of an importance, because if a person just see that the PR checks aren't green yet then it's not safe to merge.

1:14:00 - 1:15:00

Pedro: If we see that in the future we still hit situations where we didn't want to merge and it was done, then we look further into actually enforcing this, but I think we are in a good situation already.

Oskar: On the note of like it's great we have this tool sort of helping us make sure that we stick to protocol. It's important also to remember it's kind of a cultural shift as well, a lot of people work on the code base and so on, people sort of test their stuff beforehand on multiple platforms, just make sure that the PR is in good shape and try to be more hash last few months and reverting things, because breaking develop is a real hit to productivity to everyone else, because they depend on it working, and it can be frustrating for people who are trying to work on something and it doesn't build due to something unrelated. So just test your stuff before you push it, and be mindful of other people and their productivity. If something isn't working don't be afraid to revert it. And code reviews as well, blocking it if it's not good.

1:15:00 - 1:16:00

Oskar: Anything else that anybody wants to add on that area?

Anton: Yes I just want to describe the actual work flow, how it works now. We are not blocking everything from the beginning because it can slow us too much since a lot of tasks need to be merged without testing, even automated tests, in case it's infrastructure or any other PR which is not related to the product.

1:16:00 - 1:17:00

Anton: Right now tests are setting pending status only when they start, it means that they start when PR is into test column, they won't block it or set pending status before PR getting to that column. It's not even forced block, you still can use merge and such, but it's like failed status in the end if any of the tests is failed, or passed status all statuses will be green when all of them are passed.

Pedro: What I did is at check at the beginning of the pull request saying this is failing, the entry tests are failing because they will only be run when this moves to test column.

1:17:00 - 1:18:00

Pedro: So at least it gives explanation, it also makes it easier for people who are not familiar with the process they get an additional explanation on when the actual end-to-end tests will run.

Anton: Also what I can see now each force push removes statuses from the PR, because it's a new commit. Does it set status back Pedro?

Pedro: I don't think so. I could add support for that to listen to force pushes and recreate the status.

Anton: Great.

1:18:00 - 1:19:00

Oskar: We actually managed to go through everything except swarm updates which is pretty impressive. I guess quick announcements then we'll wrap up. So I'll just start with one. Fossdem this week. Nimbus is gonna presenting, hes talking about making an apparent client from scratch, pretty exciting. Then we have the protocol workshop. That's on thursday friday. We'll try to have a hangout, as well as talk about what this means for Core next week. Igor?

Igor: So first we're going to release one more hotfix, but that aside, we are planning to wrap up the next release that's public release 0933 so if you have some PR that absolutely have to be in the next release please tell me or Anna about this until the end of tomorrow essentially working day, if not then we can't guarantee that it goes to the release.

1:19:00 - 1:20:00

Oskar: Cool, anything else?

Jarrad: I'm thinking about how status can self update, there's a thread in discuss, open to ideas and thoughts.

Jacek: I'm participating in an effort right now in San Francisco which is called ETH 1.x, if you're not aware of what that is it's basically an effort an keep the ETH 1 chain alive while and maybe even thriving while ETH 2 is being developed. So there's a couple of proposals going on here.

1:20:00 - 1:21:00

Jacek: They're discussing new sink modes because sink is one of the biggest issues that we have and why people are having difficulty running nodes. Other than that there are chain promotes discussed and so on, but the biggest topic is probably the introduction of certain features that will allow a more nuanced accounting of storage and more nuanced accounted of storage will be used for basically two things. One is the potentially increased gas limit in the future so that you can compote more and sort of store while still keeping storage kept about the same way. And depending if it's necessary also to do storage rents, so if you're interested in these discussions there are recordings and there's going to be lots of discussion on this topic in all Core Devs calls going forward I suspect, so nows a good time to tune in and think about how you feel about these changes and participate in the discussions surrounding them.

1:21:00 - 1:22:00

Ricardo: I think that that's a really important thing to be discussed, all developers should be aware of that because it means using smart contracts becomes more complex, but it's needed, I think everyone in the community agrees with that.

Petty: We're starting a hacker one campaign, probably a private campaign that allows us to work out the details of dealing with incident response, dealing with the disclosures and so on.

1:22:00 - 1:23:00

Petty: Start in about a week and a half when I get back from Belgium. We are going to try to tune the disclosure rate for hacker one packers to about 5 per month, so you can expect 5 bugs from hacker one per month. The scope that we are starting off with that people will be looked at, will be any of our current releases on mobile or desktop, and then whatever infrastructure we have to serve that to the public. If there's problems in any of that that they can find, which there will be, you can expect bugs from them that are well formed because they have a triage service that validates, reproduces, and manages the quality of reports before sending them to us. So just letting you know to be expecting that in about two weeks of time.

1:23:00 - END

Oskar: I would like to ask people to rate this call. I know the core team is doing this so just in terms of how useful it is on a scale from one to ten. If you would just write the number on status core devs on status. If anyone has any thoughts on how these calls can be improved and be more useful. So please put a number 1-10 where 10 is the highest. That's it for now. See you guys in two weeks.

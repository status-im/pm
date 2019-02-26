0:00 - 1:00

Oskar: Welcome to the eleventh Status Core Dev Call. We have quite a lot of things on the agenda today. We did a poll SMT voting to find the things people want to talk the most about. We'll start from the top and see how far we get with the time we have. Also just a small PSA, if you go to the repository, status-im/pm, we have a index of all the previous videos and notes if you want to refer back. Let's get started, so the first topic is Whisper availability inside Status Dapp browser, which is something that will benefit Teller Network as well as Gas Relayer and possibly others. So I guess Richard, would like to elaborate on it if you don't mind?

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

28:00 - 29:00

Pedro: If there's no further questions I think that's it.

Oskar: Cool. Awesome. There's been a bit of discussion for fee structures for SNT Utility. Rachel do you wanna give a brief overview?

Rachel: So this is coming up in context of Sticker Market sales because we're doing work to finalize the Sticker Market registry contact right now. Specifically whether we should take a percentage of each sale to fund our project directly or to burn perhaps. I guess the heart of the matter is really about how our project sustains itself financially in the long run.

29:00 - 30:00

The predominant hypothesis seems to be that token velocity and value combined with having good open source contributions should eliminate the need for us to ever be charging rent for features but there might be worth burning a percentage of each sale of stickers in the meantime to have a deflationary effect. So I'm not sure if we actually want to get into the debate about these structures overall and financial sustainability of the the project or if they should just stick to the focus of the sticker market registry contract and regarding the fees for that right now, what decision do we take for the contract and how do we future-proof it for any like potentially desired changes in the future.

30:00 - 31:00

Ricardo: I think if we have something like the sticker markets and the Croatian markets then having this operation over the sticker packs, we might have a kind of optional fee and maybe when the owner of that sticker pack can specify how much a fee goes to the Croatian market automatically based on the user buys. It goes slowly rising organically as users buy it. And of course if the sticker market artist want to promote their own sticker pack they could just deposit in the Croation market.

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

Petty: A better way to go about this, you think ULC 

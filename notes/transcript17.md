0:00-2:15
Igor: People here, yeah, let’s have one more minute for people to join and then we can start.

Ricardo: There are some people in vacation.

Igor: Yeah some are vacationing, there are some few people who are just ill because of springtime.

Ricardo: yeah, I had my time some weeks ago

Igor: Yeah me too, 

Ricardo: But my problem I guess is too much coffee, not any infections.

Igor: That also happens, so just give me a few more seconds and we’ll start.

Iuri: You guys can hear me ?

Igor: Yeah yeah.

Igor: So yeh, I guess let’s get started then, thank you everyone for joining, it’s meeting number 17, it’s the one that been postponed from the last time and yeah and then yep basically today there are not that many topics to discuss but can start with a swarm updates as usual so just give me a few seconds to open an active swarms list yeah so I guess we can start with the sticker market and yeah, sticker market, If there is

# Sticker Market
2:16-2:52
Julien: I can do that, not a lot of news from sticker market on from development side we’ve done pretty much anything that’s required so not a lot to expect and we are still in the process of doing the audits which I believe started, well I am not very sure because it’s kind of complex to follow the contractor deeds so I'm not quite sure about that but yeah not a lot own on sticker market front.

2:53-3:58
Igor: Yeah Thank you so then the next one is Tribute To Talk but I don't see like Eric or anyone from there here today. Derek’s on vacation right or something like that, yeah then let’s switch to Dapp store, are there any news on this front so I know that we launched the, we released the first version with it but are there any other things, okay and then yeah let's go to the tellar network, yes Iuri’s here atleast

# The Teller Network, Embark, DAO
3:59- 5:42

Iuri: So, supposed to say what to one week two weeks, so with, I mean we did some security audits of our own just like a pre-review so to speak with the different tools of whirlwind and  embark.
 We implemented, we fixed the issues that we were having. We did two RnDs, one was on state channeling  Staters and the other one was in the POA  sidechain to use with the teller network and we also we adopted the whole thing to desktop because it was only mobile before and we had the whole workflow and UI for also the arbiter and we did the first like actual like intensive test of the application like with different people in different parts of the world just you know to see what were the issues on what to improve and so and I guess I can go next to the DAO stuff and with DAO we asked we are (adding) this feature to supporting listening projects and it fetches the project from IPFS and all that we also did like a more intensive test and from the bunch of issues that were currently working on fixing and I think that’s it for now.

# Core Improvements
5:43-6:49
Igor: yeah, cool, thank you, is anyone here from the Token Economics swarm ? Barry here ? Sub sectors..ok next is core improvements that so for the last few weeks we did release new version and we are playing series A follow-up to this with one more bug fix that we feel like its important and status go side as well we are currently, like working on error reporting in a more private way so people can actually send logs and they will be offered to send blogs to status on exceptions and things like that so that's very important for us to actually debug the application and after that we'll do like UI,sware , performance improvements I think. So the next one is the protocol.

Petty: Hey Igor, I have an update for the Token economics forum

# Token Economics
6:50- 7:32
Igor: Oh cool, yeah 
Petty: That’s where we’ve got the build materials I’m working on the initial like introduction blog posts as well as we're playing around with a few different ways to visualize the ENS usernames contract and people's interaction with it so that it can be explained easier to the general  public while also showing like how it captures value and that'll be where I hope to have that at least like majordraft being revised by the end of the week and then from there won't go into each of the individual use cases and notebooks that there's made for additional articles to create kind of a corpus of material to kind of market around.



# Protocol Research
7:33- 9:32
Igor: Cool, thank you so much, now Protocol and Oskar, yes 
Oskar: Yeah sure, so let’s see, last week..ish so we’ve been implementing this minimal viable data sync proof of concept in go and this has been working at, its sort of working interactively but there’s some cleanup that we have to do to get it running in this sort of console client and so we can go, still looking into a bit of the minimal requirements and we’ll make sure we have a way that we can upgrade things which helpful for more efficient sync based on bloom filters and these are the things and that I'm going to research also been looking in sort of , no I don't know if this was talked about last time but one of the things that we need to solve before launching version one is sort of this bandwidth consumption and ideally with compatibility so one step towards that is that we need to have to partition whisper topics soon and we had some discussions with Andreas sort of start sketching out the proposal for moving to device based sync as opposed to suppose to multi cost-based and that will also tie into how we actually adopt the data sync stuff into the app and how we can do later on do protocol negotiation and these types of things adding that we have this ongoing bi-weekly calls and trying to cooperate a bit with this one team it's gonna be a summit in a few weeks that a few of us are going to, yeah and I think that’s mostly it.

I forgot exactly what to be updated last time but something like this.

# Janitors
9:33- 10:33
Igor: Thank you Oskar, and for Janitors ? maybe Hesther or ..
Oskar: yeah
Hesther: Yeah I can...oh Oskar, feel free to go ahead , I was gonna give an update that we made some progress on the critical path that is in right so I do believe most people do have a bank account if you go to the top folder, let’s say projects, you’ll see 8 projects that is called critical path or has some something referring to critical path if you go into that task you can see all the dependencies that we defined so far as being critical I would say that's the main update, Oskar anything to add ?

Oskar: No I think that’s pretty good for now.

# Democracy (DAO)
10:34- 12:22
Igor: Great, so Ricrdo if you can talk... and then topic democracy but if not then we can skip it and not..
Ricardo:  Yeah, I'm doing so more research on (inaudible) because I have two types of quorum that is the simple quorum and the majority quorum and for the wicked  democracy  it seems that it doesn't make sense to have these delegates or at least default to delegate for these simple quorums because they don't require the majority so it's just how you would say they online my majority just the people who voted that counts and so I would I'm removing this part of topic democracy to a later iteration and I will focus only on the majority quorums because that's the.. I think the most important ones and then later on I would derive from that to make a simple quorum I'm also still trying to talk with Aaragon but seems like there is not many interests at their parts or I’m not too really sure so like lot like many answers about my questions but yeah in about today they react components,  that's really being slow and that's so I expect to get in the rhythm back again to make the components this week but I was mostly on this research 

  
# Teams

12:23-
Igor: Yeah, Thank you Ricardo, then then I guess we would do some teams update so for the new core UI is there anyone to talk about ? Looks like there isn’t one 

Oskar: Is (inaudible) or Rachel here ?
Igor: No I don’t see neither of them, I’ll ping Andrea next time probably specifically

Oskar: so just for conext for other people, Core UI is the merging of wallet dapp and chat team into one as well as owning profile and onboarding these specifics for people that are not aware.

Igor: Yeah yesterday I’ve seen Andrea  was creating a lot of tasks related to onboarding, I guess that’s the main goal for them at least for now.

Hester: yeah, maybe to add to that so yes onboarding had a design review end of last week  and we discussed handoff implementation can start this morning, next profile changes is something being worked on as far as I know but we do have some tweaks to make to the design there, I as far as I know those are the big buckets of things going on now.

## Keycard

13:57- 17:37

Igor: great ! cool and the last team like I just call is essentially whatever is core improvements doing so it was already set and now I guess the keycard team.

Guylois: Yeah so for keycard on the Android upfront Dmitri and the test team are working hard to fix a list of bugs that the test team has found during the initial testing of the first MVP app, this will still take a couple of weeks to finish and after that we will need to implement the changes that are coming from the new onboarding flow, on the ledger side, still struggling with getting samples, this is a bit tough here, there’s been some changes in the ledger SDK with regards to how UI is done on the ledger and the mickleA is implementing them. 

And apart from that, Keycard team is also focusing on the multi account feature in the wallet, so we’ve had two or three calls now to kick-off the multi account work, we are in definition phase, we have defined what is the scope of work  what we want to do what to do, what work we’re not currently doing is writing the user stories, so that’s a design we can work on that and also listing the development tasks, with regards to scope, very quickly so that everyone knows what we have in mind that what we’re trying to do for Q2, so the impact is on the wallet side only, we will introduce only later all the matters about the security policy, key-pair and all the specific use cases of key-pairs for dapps and chats like unique keys for dapps and chat group. 

So basically the scope is in wallet , we want the user to be able to create several wallet accounts either on the status hd tree so and either automatically or by manually entering the path they want to use on these tree, we want the user to be able to import any key pair with its private key so outside of our tree of course. We want the user to be able to watch any public address so these are watch only accounts from the wallet and we want the user to be able to export any key-pair also and of course we want the user to be able to browse and explore through these different accounts meaning being able to have another view of all these accounts, get into the details of the specific account and chose from which account they send the transaction from. 

So that’s the scope of what we have in mind and what we are currently writing user stories for. Yeah that’s it for me.

# Discussions on Topics chosen during the meeting

##Discussion related to Gas Abstraction

17:38 - 26:18

Igor: Yeah cokol, thank you, thank you for the update and is there anyone who I forgot to mention, a team or any swarm? so I guess that’s it then. So are there any more topics anyone wants to discuss right now ?

Ricardo: I think that some interesting topics that we could discuss is about gas abstraction in the gas relayer because keycard also implemented that in Hackathon, Julian is asking me about that so to implement this is not exactly gas abstraction but to pay the gas for the users in way to first make easier the onboarding of new users and also the discussion about identity  that is connected to these points and also the discussion about separating the wallets from the shared identities. So I think these topics are important  to be discussed together to be implemented for this change or near changes especially because of keycard and how keycard mentions it I think that separating wallet from the shared key would make things better for keycard and also this would make things easier to implement as an identity contract to make the gas layer possible so I think these topics these are kind of connected and for that I think a good step would be to start thinking in how we can separate a density, sorry the shout in the chat, I think that would be the first thing we need to, I know that this is an ongoing topic for a long time, so I think first big question would be how is this stages of this it’s been working on and there are pull requests about this.

Igor: There is a similar topic that we just discussed about the keycard right ? so its about the separation of ..(inaudible)

Guylois: Yeah, I mean yes within the multi account discussion, well basically about the chat keys, obviously since status needs to work with keycard, what we would need is that the main chat key is not going to get different from the main wallet key, so this will be implemented meaning in particular that on  onboarding or when the user start using status, we need to be made aware that these chats are made with a different key-pair than the wallet so that when he gets some funds on his wallet key pair through kudos or anything else, you get them in another wallet so yes I’m saying he needs to be aware, it needs to be discussed maybe all this can be automatically done in the background for him but basically yes, we’re going to have a different chat keeper, but the other thing we said is that we have not prioritized the fact to use one unique key-pair per chat context at this stage just for planning reasons. That’s what we discussed in terms of specific usage of chat key pairs. 

Igor: Yeah I guess then status go technically it already supports different keys for whisper and for like a serial node but yeah I guess..

Guylois: I don’t know if Andreas is here but he’s really the one that’s worked on this, not sure he’s here because he had to be away from keyboard for an hour but basically yeah Andreas did implement separation of the whisper key and the wallet key and is now working on the, evaluation the efforts on the go status go side when we need several I mean when we need several keypairs for several accounts.

Ricardo: So the current key that we use on the migration would be the wallet key and the we will have a new chat key or will be the reverse ?

Guylois: Yes that’s the way you said it, the wallet key does not change, I think its m/44/6t/000  and we… there’s a discussion on which path we use for the new whisper key, I can share that on the cordova status channel but yeah that’s the way you said it.

Ricardo: Another question so there is a difference from the chat key to the wallet key because the wallet key is not saved inside of the device but the chat key please save it in the device right because you don't want to be hot holding the card so how that changes. may…

Guylois: Yes
 
Ricardo: sorry how that that is the very differentiated ?


Guylois: the thing with implemented is the ability for the key card I mean so here we're talking about when the user is using the key card of course,  when the user is using the key card, his seed is on the key card only and we've implemented on the key code API the ability to export from the key card to the App, one range of paths and we've actually defined the IP for that and the chat key is on these range of paths of course, does that answer your question 

Ricardo: yes so you can you can have like this but then I have another question that is regarding another discussion that is kind of similar because that we have this chat keys that is something far stages like it's not like some or something like any dapp can request the type this type of key because I see that this is kind of useable for some dapps so maybe that dapp wants to use whisper and then they could request this key and when they want to kind of login into the dapp only on the first time you put the card and then it kind of says this guy I'm not really sure but the question is that that's this put this feature is for status only or any dapp can use this type of key that says 

Jarrad: so I mean once we've done the multi account stuff, we'll be able to look at how to use treated in whisper and in dapps so my personal take as I would like to generate a new key pair for every dapp based on like the hash would suppose or something and I definitely think at that point we can definitely request the dapp themselves to request to key pair for whisper, if it only generate them of themselves, it gets a little bit murky when we want to give them the key pair of the users it's already locked in but you know I think we can cross that bridge when we get to it, but first to make sure we have multi-account support well-defined 

26:20 - 28:56

Hester: I have a question Jarrad and Ricardo as well because we've had some back and forth on this if we would enable any dapp to request a key pair like how would you see the process for the ENS dapp to request a let's say a one-time key pair that then also offers gas abstraction so what it like what I would look to enable is for a new user to not require Eth to buy an ENS name and at the same time have the privacy of having a like a one-time like multi account key pair.

Ricardo: yeah so all these surrounds, in this the solution about this I think surrounds the identity contracts because then you can have this single place that you can start this ENS name and these different keys for example the ENS usernames dapp, it can have its own key for accessing but it registers the name for that identity contract and in that, so you can associate new keys for that identity contract and of course remove the keys if you want.

 so, but of course this kind of crude privacy feature of separation of the keys but it would only kill the prior privacy for the selected apps that you want so it's not a default behavior for exposing the dapp so for example maybe you want to use a dapp with a new key because it's only whisper, so if you want you can link to your identity then you could for example let's say that status chat uses a separate key for chat but then we have this identity contract that maybe have badges and have the ENS name, maybe have reputation and then we can link this chat key to his identity by listing this chat key in the identity and then the other users could lease this information from that user to see the profile but of course this is only for a public profile is so it's not private, it's not not for privacy, so we would have, they would have a public profile just for that

28:57- 40:36

Jarrad:  yeah so basically your ENS username will be pointing to a smart contract which would be like your on chain identity or persona, how I personally view this in the future would be that every chat has it's automatically generated key pair and the actual, say identity kay pair would be a parent of those ones that generated, so you generate these child key pairs off this identity public key so that public key would not actually ever be exposed except for to basically sign messages to authenticate these, who that person is on the child keys so I would be an unknown contact to you in a particular chat but if I like if I join a public chat and you join a public chat neither of us would know each other who we are but if we would like to reveal ourselves to each other we could, if it's a private chat of course each private chat with have its own key and you would automatically reveal itself, so in that way you can get some privacy by essentially having a different sort of key pair acting so anyone who's like doing dragnet surveillance would see one identity but it's actually speaking for different identity

Hester: so in that sense it seems like if every chat would have its own key, I'm struggling to understand like how it fits together with ENS, so my line of thinking was is there a way to use the address to, that you use to connect ENS to your let's say public address could we use that same address to also buy the ENS name with gas abstraction 

Jarrad: yeah kind of 

Ricardo: Yeah...

Jarrad: go for it Ricardo

Ricardo: yeah, yes exactly so but there is another feature that about these guys abstraction that I want to mention, that is about the create to opcode from recent hard fork because once we create a key pair we can also create this new identity without deploying it, in it can no it can be deployed on the main only if it's actually use it, so for example you can deposit ERC20 tokens in the in like SNT only SNT in this identity contract that was not even created yet and once you need to use it for example to buy an ENS name then you can use the gas abstraction to deploy it and register your name and then everything is paid in SNT including of course the registration price or stake and value that is 10 SNT more like something 1 SNT for paying the gas, so you can you can show the identity contract address for the user before it's deployed like every key that you create a new key, you can automatically show what would be the contract identity Key address sorry for that key, we can play on that what how do we may imagine so we can do like with one key can have multiple identity contracts if you want but of course something to discuss in future 

I think one per key is enough and then there is another thing that Jarradd mentioned that each key you can review the identity on demand so in the identity contract it can hold the list of the keys but not in plain text, maybe it could be just a hash or maybe you have a specific key that you make a signature to prove that another key is part of that identity so you can you don't need to go to in chain so you don't lose the privacy and but the main concern in all of this is having your public profile mix up with your bank profile maybe like where you store your funds so we should educate users to have multiple profiles so maybe we would have some do something in the UX that the user could enable the like a public profile, the family profile and maybe the work profile we can research on that and then the user select but for the public chat I just mentioned that each chat would have one key, I think that that's really good as well and if we allow the dapp to request a key, a new key I think that's we can make a dapp that is status chat system so we could eventually make the whole chat system dapp itself not part of the core, I think this is a good progress for overall the identity and status as an operational system. 

Igor: actually for multi-account and privacy I have one question or one concern rather so I want maybe someone knows the good answer this so we are trying to make as I understand it we are trying to make this multi account sync to be able to so that the apps don't share the same identity so we are protecting ourselves from being tracked or something like that but if we don't have a private transactions in the ethereum it still will be as soon as you spend some money somewhere it still will be fairly easy to track down and to link those accounts even if there are multiple keys together or is there anything 

Ricardo: yeah to solving that I see that we can have a mixer so maybe we could have a function inside of status or dapp that does that that could allow you to transfer funds in a private manner using a chair in dapp that uses that guys narcs technology just like z cash deposit the funds and this smart contract and it kind of you don't know who ever came that money from that would be a solution but not ideal, we want something on the fly that makes the transaction anonymous but for now we have that

Oskar: Yeah just want to say like we talked to last week that…. 

Igor:  Oskar can you….yeah please continue 

Oskar: can you hear me

Igor: yeah

Oskar: yeah sorry about that… no so we spoke to (inaudible) a while back and they essentially have confidential transactions working already and it's something we could integrate fairly soon if we make it I think it's probably not number one priority for the wallet considering other low-hanging fruit but it's something we can probably get to it like Q3 or so and this was something that key card is looking at as well so it's definitely like a medium term path towards it. 

Igor: okay, cool so are there any other topics to discuss so we can just conclude 

Ricardo: just to conclude this is what I brought here, I brought this here because I wanted to start or integrate these concepts of identity contract and gas abstraction into these updates that are coming in like we have the gas abstraction in a proof of concept working so we could implement that in status already or maybe just in a test net or something like that so it's just a matter of maybe we are really taking ourselves in making this happen because like everyone else is already doing this and we should also do that not only this but also Universal looking so many of other wallets are implementing just gas abstraction what I envisioned here is the universal logins just like I'll explain this in the proposed that is basically the new single sign-on for the web 3 and you're near on this I think would be very good for Status

Oskar: I agree it's something that's been discussed as part of the onboarding work, hester do you know ?

Hester: sorry can you come again Oscar 

Oskar: what Ricardo said about universal logins, how has what's of state of that in terms of onboarding and progress around that 

Hester: no it hasn't hasn't been discussed as part of our boarding which say yes we can look into it but I would wonder if it's a priority for us right now 

Jarrad: we're not gonna get it done Q2 

Oskar: agree 

Ricardo: i think that this is a continuation of this keycard updates or maybe we first have this key card is to make it launch it in working and then we've progress to the universal logins that would bring all these features that we talked it that would be the separation from keys you know maybe perfect way in gas abstraction in everything that makes the UX better for users

Jarrad: yeah i agree mostly account i'm sorry the universal login stuff did come up in multi accounts so we can certainly review that in Q3 depending on how everything goes in Q2

Igor: that makes sense for the future updates of the application, also that starts, like we should probably start thinking like a bit later on having some experimental part of the application like I don't know, like in chrome you can enable some experiments, maybe to simplify these kind of features and testing them we might think about something like that in the future for the application as well

Jarrad: I thought that was developer mode 

Oskar: Yeah don’t we have that already ?

Igor: well i thought developer mode helps you to develop the apps with it but not like new features 

Oskar: like experimental mode yeah shiny new stuff but that will break everything but please try 

Igor: yeah like list of experiments or something like that 

40:37 - 45:18

## Discussion about debugging methods / Obtaining logs

Iuri: yeah on that topic sorry this one is something very important do we have a way to get the console logs from a dapp that's running on the status browser, like if there's any arrows or something 

Igor: Yes, you can just connect to the, like at least if you ran it on the either a connected device to a computer or on iOS simulator you can just look at the logs in safari or chrome depending on  because it will show the webview and all the JavaScript console with it ….

Ricardo: the command I use for Android for my Android is I just connect on the USB and I type adb logcat but this is like not really good because if there is a lot of things I don't want to see there so maybe we should have some kind of filtering command or something like that to show just the app specific because I also like when I develop the app, I want to see the errors in it but I then I have to keep scrolling that screen but maybe someone will have a better solution for that.

Igor: yeah that’s what i’m talking about, if you have a Android studio let’s say and you connect your device with status with USB you should be able to just see there, I don’t know if its only for developer mode but that's for sure but in normal mode maybe also you can just see the list of web views and your application and then just..

Jarrad: when we have the console box you I'm pretty sure console log was hooked to sending messages, so you could like typing commands and get some feedback, I could be mis-remembering that but if we auto generating chats like maybe we can order generate one for like localhost doesn't know that and dump come so loads into chat that way as well I don't know about you but

Igor:  yeah and I think there are some ways on how to do that in react native we should just make sure that they work, I'll try to dig up the article from their documentation because there is a way to remote debug application inside a webview inside...

Julien: it’s already accessible we have certain documentation so what you can do is remote debugging, so it's specific to dapps because what you are referring to before the ADB stuff it's it's every log and probably not Dapp log, actually I'm not sure you can do like regular web remote debugging using Chrome or Safari and it should work out of the box you just you have to make sure that your phone is on the same Wi-Fi as your laptop and then look for your mobile as a remote device or something like that but we have all the information in documentation 

Iuri: alright okay, so as I said you thought the (inaudible) look like a webview so those logs will not be included in that kind of tooling but you say there's a guide I'll give it a try and I’ll talk to you 

Julien: yes sir and I didn't get everything you said that but I think you should get pretty much everything you can even like remote debug you have access to anything that you would have like debugging your dapp inside Chrome for instance 

Igor: the idea but even by you can edit some so much html or something like this inside because I remember testing there was a battle core there, so I was pretty much able to do like anything, with a remote debugger so ….. okay so then let's let's wrap it up thank you everyone for joining today and yeah we'll see you in two weeks.

Nearly everyone: thank you, bye bye


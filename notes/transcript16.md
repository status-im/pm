0:00 -1:00
igorm: yeah but let’s wait for maybe a minute or two for more people, just telling us right now, to actually start

1:00 -1:00
igorm: So yeah, thanks everyone for joining, I’ll lead today’s core dev call and let’s start with the note taking. Eric would you mind taking the notes, I’ll share the link to the chatroom.

Yeah cool, thank you and here today we don’t have a very long agenda so let’s start with a short swarm update and I can start with the network incentives where we started doing first proof of concept where we actually, you can register>>>>2.17>>>

We are adding the first tests that can check for the nodes that they are online and working, that’s what we have been doing lately and now the next one is the sticker market.

2:37 - 2:49
Is there anyone from there ?
2:50 - 3:10
Okay then let’s try tribute to top
3:13 -
can you hear me ? Yes
Eric:
3:31-
Eric To sum up we

4:06- 4:23
Igor: Yeah thank you Eric, and then Dapp store ? Is there Andy or anyone from this forum ?

4:32- 5:04
petty: Igor are you seeing the notes in the chat ?
Igor: Yeah but what do I do, “I’d like to share my screen for the updates” what does it exactly mean ? 
Igor: Now, I thought Barry was asking to share his screen for token economics. Because I don’t have really much to, But yeah Jenna can you please just promote Barry to host as well because I guess only hosts can share the screen. 

Igor: Cool, thank you. The teller network, Iuri ?
Iuri: Alright can you hear me first of all?
Igor: Yep
Iuri: Good morning, first in regards to the dao stuff, we (are) working on creating a project, listing a project, received a notice to create a target profile, reject the commit by delegate, for the teller network, we work on the escrow URL  and also fix some workflows in regards to releasing pumps , when one introduction, when the settlement was made. We fixed various issue related to the screen size. We improved the rating system as well. We fixed the data seeding system, that’s done and it works, we converted the Dapp to use the create react app, great together with the part 4 and we also improved the screen warning the user when a ATM provider was not available.

I can put one in embark too.
Igorm: Yep, Thank you
Iuri: So embark, we’re investigating this race conditions that happens sometimes and we tracking down this issue that turns out to be a geth bug and we pass the transactions that get stuck when running geth with proof of authority which is typically what’s used when doing development. we fixed a bunch of issues in cockpit with regards to pagination, we proved our coveros output, for dapps we did various other improvements in cockpits namely in the IDE and yeah, there’s a bunch of ... we also improve some other stuff but I think that should cover it

7:25- 9:32
igor: yeah, thank you, so now its not written in the Readme but its the democracy, is Ricardo here ?
igor: yes okay, ricardo just joined.
Igor: Hey Ricardo do you have any update for the Democracy ?

Ricardo: Hey, so you were missing me, yes regarding the democracy i had some so I basically I work around the contracts to kind of evolve them because I’m seeing the spec of it so I’m still working on some aspects of it of the governance you know, how it works but then I wanted to start to make the UI but you lean more about Javascript and React and embark, I started to make a multisig that is a very simple application in something that I need so I’m currently working on the multisig and so both of them, then I go back to the contracts of topic democracy so its a...I’m still unsure about all the details but yeah I’m just going to first make the first network configuration so you can set your who you delegate to and later would make it in a way that you can approve, dorry you can vote for approval to reject and also to create proposal ofcourse and yeah that would be then my next steps on top democracy and that’s it.

9:34-13:10
Igor: Thank you. So yeah now I guess barry and token economics.

Barry: Yeah, real quick I’ll share my screen, can you all see it ? Yes Okay, we started a notebook just to figure out you know what are the value drivers of you know ether because, well for one its a big thing, its something that status relies on in a lot of ways right, one  and a big part of our treasury is denominated in ether which as we could see can impact our long term plans based on market gyrations but also the security of the network that we are building a lot of our applications on top off is dependent on ether having long term value but when you look around there’s really not much out there or research being done into what exactly makes you know where ether’s going to derive its value from so this is sort of an investigation, something we started looking into and thinking about and exploring and I just want to put this notebook out there and people stress test some of these ideas because there’s definitely things that we probably are missing and this is not even this is far from a complete model so we really just want to kind of stress test these ideas but I’ll just leave you all with a couple of quick insights that we have so far and maybe in the coming weeks people can expand on this and help drive this research forward but you know in short one thing that we hear pretty often is that ethereum is gonna have all these different industries and replacements built on top of it, you know ranging from financial services to arbitration, legal and because of that you should expect Eth to be very valuable in the future, but you know if we look at that for example, here’s for example one transaction that took place where 1 million dai was wiped in the maker protocol which is built on top of ethereum but if we look at the value it accrued in this one transaction there was 1 mkr that was burned, because it was burned that’s roughly equivalent to 700 something dollars that accrued to the maker protocol and a transaction fee which was roughly equivalent to 9 cents but then that’s not something that was  burnt that’s something that went to the miners so that is something that gets recirculated so you have to divide that by the velocity that Eth has which we talked about in a previous presentation what velocity means but this is basically a value pool of one penny to Eth and 770 dollars to Maker in this one transaction that happened on the network. So you know just because all these services are being built on top of ethereum doesn’t mean the vast majority of that value is gonna accrue to eth, it may actually end up accruing to eth protocols being built on top of ethereum.

13:10-14:08
And then There’s just so, most likely the value driver for eth itself is going to be transaction fees over time and I think this is an important thing in terms of understanding in terms of security we basically just took the history of the dollar value of these transaction fees over time, Just a couple of quick interesting facts about that they’ve been growing since inception at a rate of about 700% a year however, so far, 2019 is the first year since ethereum’s inception is that transaction fee growth is on track to be negative so we’re on to so far things could change but so far this year the growth in transaction fees dollar value is actually on track to be a negative growth rate from what we had in 2018.
 
14:09-15:44
That’s a, you know, one last thing, you could basically if you could estimate what these fees the growth rate for these fees would be over time then you can project that into the future, discount that to the present and then you get the discounted value accrual to eth from transaction fees and the question becomes are transaction fees the only value driver for eth ? are there other things that will drive value for eth and here’s an important, this is an important consideration because the security of the network is backed by right  now miners but in the future it will be proof of stake but there has to be an economic incentive for people to stake, they probably won’t stake or want to stake if the expected value of Eth long term is like negative, they probably have  some kind of positive value accrual expectations for eth in order for the economics of staking to make sense and and so I think that’s also why maybe this research is important not just to status but to the community as a whole because the security of the network, part of it is probably relying on Eth having long term value. So if you want to explore this more you can get a link to this notebook and dig deeper and provide your own insights, fork it comment and go from there.

15:45-
Igrom: Thanks for the great presentation, so 

Ricardo: So I want to give some comments on what Barry told. Regarding the proof of stake, obviously they usage of staking is that you will produce blocks but the blocks they probably don’t give any reward, the reward is only by the transactions and also if you think about the each  value what is the value of ether is actually the power of processing transactions in this decentralized system and so if we achieve scalability in Ethereum, it means that one ethere can do more and therefore it should be more valuable, not thinking about the price, I’m thinking about the value each ether have for me because each ether I have in my wallet is able to change the state of ethereum and that’s the value.

Barry: So I would leave you with one thought on what you just said, if we we have scalability and one ether can do more, has more transactional capacity then wouldn’t the average wallet be actually need to hold less ether because they can do more transactions with less ether.

Ricardo: Yes they need to buy less, they don’t need to buy many, yeah that makes sense. 

Eric: But if scalability means that there is more use cases for which ether is used then you know it may be the offer and demand balance and the value stays the same I mean depends on.

Ricardo: Yeah because it causes less demand because you need less Ether to make a transaction, less demand to ether but at the same time when you have one ether you have more power then to make more transactions. So it's a complex scenario that we are going to get. I don’t understand the outcome but seems like moon 

Igorm: Later on because you had the topic, right now it’s more of a short sync up that at least was envisioned before, but if you want to continue discussing then we can just like discuss it in the end of the meeting if you’re okay with that. Just to keep it a bit, this part a bit short, everyone is present. Cool, yeah thank you. so yeah, let’s continue with the protocol research, Oskar do you have something to say ?


Protocol Research
-21:02
Oskar: Yeah sure, so let’s see, last week, continuance of the doing another iteration of the peer to peer data sync comparison survey paper that we’re building up, I was subtly looking into various types of discovery methods things are looking that we have setup a basic static website that roughly outlines the phases and so on and of the work that’s being done, its big brother is specs the basic static github page. We’re also documenting the current protocol and just not sending PR requests there in the specs repository that Adam’s working on. Priest any feedback on that one ? And then we also had a call with Swarm and a PSS team to say of what the path to getting that into the app or protocol at some point would look like as well as if there’s some kind of collaboration with mix that research and so on and then this week, some people are working on build week but we are doing a brief sort of proof of concept for PSS and feeds. We are gonna have sort of our bi-weekly call tomorrow with web free messaging with the whole team as well and then keep working on discovery and documenting the current protocol as well as exposing JSON RPC through some, this is also part of moving the protocol from closure to go so it’s more self contained and so on. That’s it for me.

21:03-23:11

Igor: Cool, Thank you Oskar and next core improvements forum and the latest weeks were mostly about the incode so first of all we did release the support it, then we were also looking at how could we fight the unicorn  I think it was pretty successful. In there so and then like except the unicorn day. Yeah we also completed some plain maintenance like we upgraded react native in the application c couple of times. Then techniques was merged as well I guess because in the previous call it wasn’t yet which was a huge change and right now there are two follow ups there that helped to improve the whole building pipeline and yeah, a lot of small things under the hood of the application. Maybe not so much visible on the UI level but the, and the biggest one that we are working on right now is to load missing messages from the chatroom which is essentially, which is a big thing because we only load for the traffic reason, we only load 24 hours especially all the private messages so if you happen to join the chat or if you happen to let’s say not go to status, not keep it open over the weekend, you probably will on monday you will lose all the information that was posted on saturday which sometimes looks like a box so we are aiming to fix this as soon as possible.So that’s what we’re working on. So that’s what’s cool improvements. So I guess Dow was already said by Iuri so let’s Janitors, anyone from janitors want to say something? and if not then we can switch to the teams and the core browser team, are there any updates there ?

23:12- 24:14
Oskar: briefly if there’s no one from janitors, I can just there was this survey about and process and tools and so on that went out I think last friday and part of that is also that we are looking to potentially using this rike tool that Jared presented last time well so if you haven’t filled out the process survey please do and a reason for that is because that there’s a tendency to sort of keep adding tools like we have github and we have different product ports and labels and pivotal tracker and so on and we’re going to make sure that whatever tools we use are most useful so if there are tools that people find annoying and so on then we can remove them. So if you’re bothered by some tool, the process or you think something’s are working great then please let us know so we can streamline the process and remove any bits of work and keep just minimal set of tools necessary to streamline work, that’s it. 


24:15- 24:48
Igorm: Yeah, Thank you, cool yeah so the core browser, is there any other using in this front ?
Rachel: I think that the fiddle update that Julien shared and the build we kick off is the main update from past  couple of weeks.

Igorm: Cool yeah thank you and then the core chats ? 

24:49-25:00
Eric: Nothing to say, it's the same as tribute to talk we have worked 100% on tribute to talk closely last week.

25:01- 25:38
Igorm: Yeah, thank you, cool, so the next one is Desktop but desktop was essentially merged to the core team so except what we did for core improvements and core incentivization, there’s also ongoing effort to bring mobile UI, Mobile codebase to desktop and then after that to bring pane view like we have on desktop right now to the mobile client that have big enough screen. That’s essentially for the desktop and then the wallet and key card ?

25:39- 27:22
Guylois: Yeah, I can make an update for keycard first, yeah so we have now done rebuild with all the features for the keycard integration, it’s currently being tested and we’ve raised several issues already so that’s follow up on that I mean most of the issues are user experience related. On the good side, Andreas 26:08 SDK for keycard and is helping to merge the integration of keycard in geth. We’ve been working on the point of sales concept for the past two weeks so we now have a new keycard API that allows a point of sale use cases and the new implementation of the applet and then goes with this new API and the goal is to make during this build week a proof of concept of point of sale transaction with keycard.

The work on ledger, I mean integration of keycard 26:50 is on hold because we need some ledger nano x samples and we still don’t have them and what else ? we also have some suspicion of other issues with the cards which we are mitigating from a software standpoint and we are dealing with 27:10 of the chip on the card to better understand the situation.

Yes, that’s for the keycard, for wallet is Goran here? 

27:23- 27:53
Goran: Hi, from one side we have restarted quality design PR so right now I’d appreciate if you could  give you the PR that brings the redesigned for the main wallet sent flow which after successful merge should be followed up by the same thing for effort at in depth transactions. so hopefully we’ll finally get this merged. Thanks. 

27:54-29:19
Igorm: Cool,thank you and so are there any, oh yeah probably security and devops are the ones that, no Corey,  Jakub ?

Jakub: Can you hear me ?
Igorm: yes
Jakub: all right, I guess from the major things that are happening, we’re switching to victor ops for paging people when there’s problem with infrastructre I mean that’s part of the effort to essentially have a proper setup for the call so we can go in turn fix our infrastructre in cases of any emergencies and I’m actually working on that right now. other than that, the main thing I;ve been focusing on last weekend together with Pedro are Nick’s changes because we are changing quite a lot but this should improve the build process by huge margin and its gonna be both deterministic and reproducible on all environments and I think we’re pretty close, we’re almost there, the last remaining thing is getting the fast lane changes going and I think Pedro is almost there so that’s the main thing really. 

29:20- 31:08
Igorm: Yeah, Thank you, Is there anything from the security standpoint ?
Petty: yeah, trilobites retainer is officially started, we have, they’re focusing on three main things right now, one is looking at starting off thing at the contracts with tribute to talk and sticker market and then they’ll move on to whatever next is prioritized on our release schedule there, we’re also setting up, they’ve finally gotten their tooling to work natively with embark so I mean anybody using embark can have trilobites tooling built into the pipeline that should do checks when they are developing stuff. We’re currently building a tutorial that’s we’re gonna announce here on discuss for everyone to join who does any smart contract work so they can figure out how to integrate that in there quickly and the last thing is, at least the next one that they are working on is probably Dapp curation and I’m setting up like an organizational process that I hope will be a mandatory process for any new project to ping the security team at certain points during their project status initially, once initially so that they can get help assess risk to what they’re doing and then that also informs us and trilobites on how to move forward in terms of how much attention they should be getting based on the project and then the other least second mandatory ping is when they’re winding down to start getting the security team to have a look at it and do audits or whatever necessary based on the project.

31:09- 31:57
Igorm: cool, thank you, is there any other team that I forgot, maybe QA ?
Anton: Yes basically we’ve been the same keycard for last week and for this week we are going to focus on exploratory testing and wallet pairs and also from automated testing I’m focused on bridging IOS tests running, it’s a way like android do we get free open source accounts from browser stack today and I believe that by the end of this week we will get first set of sanity tests for IOS. That’s it.

Igorm: Cool Thank you, is there any team I forgot to host, any swarm that I forgot to ask ? Okay, so then we have a few topics, one is the post that Oskar wrote about the bootstrap node diversity, is there anything you want to discuss there Oskar.
 
Oskar: yeah, I guess I just saw so for context this is something that came out of the chaos unicorn day and just a super brief recap what happens is that how we can shut down, when we shut down our cluster then our users can’t use status but it’s fairly easy to recover when it comes to bootstrap nodes so the actual nodes used to discover dressel on network and so on, so we’re very close to actually being pure peer to peer in that respect so it’s something that’s very simple and there’s lots if cool things we can do in terms of making of decentralized selection of these nodes and so on but what I want to do with this topic and discuss is essentially what the simplest things we could do such that if we have the next chaos unicorn day, people can still actually connect to your network because and I think we are very close and it requires like some very small changes to actually make it impossible for us to shutdown basic communication. So my initial suggestion is very straightforward is to increase diversity of bootnodes, not just of cluster nodes but we include maybe some other core contributor add in other people’s nodes in this sort of static list and that we include it in status go because if we do that then even if a cluster shuts down you can still sort of connect to the network so that’s my specific suggestion maybe people have any faults on that and maybe people have other ideas of simple things we can whereby simple things I mean something that can be done in like a day essentially.

34:12-34:34
Ricardo: So I would like to run a node, can be a boot node main server not just for my own but if other people want to use but I have a problem that is every time my internet connection is reset my IP address changes so there is a problem with that or how can we solve dynamic IPs.

Oskar: Yes that’s a good point, in that case that’s a problem for being included in concept so that would be an additional so yeah requirement I guess for being included in this basic list would be that you have a static IP, if you don’t then as you say you need some kind of dynamic method. There are some ways to do that under which I listed how bitcoin justice there are some bad ideas for doing it in a firm as well that’s based on dns and so on. I don’t know but I feel like there’s some way we can do that as well but it might require bit more work.

Igorm: Yeah, what I thought that it’s pretty, the first node is really tricky ones to discover and they need to have some guarantees because as soon as you have these boot nodes things then you can discover other even dynamic nodes on dynamic gear but for the first few…

Oskar: Yes I mean it’s a solved problem in peer to peer like Bitcoin solved it and talks solved it so it’s not like it doesn’t require crazy research anything like it’s a known problem in peer to peer applications.
Igorm: yeah, since we already have some version of that and code incentivization that’s going into status go fairly soon fairly soon but in a special fleet maybe we can adopt it somehow like but it uses a smart contract registry to get an additional nodes from somewhere.

Oskar:  Well yeah, lying some smart contracts is that, then you have the bootstrap problem because how do you get to the blockchain if you don’t have boot nodes to blockchain so it’s kind of like a catch 22, if you rely on it for the initial bootstrap

Igorm:  Yeah but then you can just think about just adding them to our JSON configuration files because if someone can run a node with the static IP for instance I can run my own digital ocean I still keep writing it from the chaos unicorn day and we can just add you know its node id
because it won’t change IP or anything, it’s a virtual machine and I think a few other nodes from the core contributors would be cool so  maybe we can just gather people who want to run nodes more or less permanently and then just have a one PR to add them to pass additional ones to our fleet files.

Ricardo: So there is a difference from state of vision in these other peer to peer networks is that we don’t want full decentralization so I know that the DNS is really good and I think that it's it's not removing DNS because it's centralized but perhaps allowing multiple solutions and also maybe make it easy to implement your own extension that can allow a different type of boot nodes discovery so maybe if someone else figure out new anyway it's easy to just in this way 

Dean : So one idea I’ve heard of recently or was discussing with someone was if you can remove the need for static IPS and have a let's say an identifier for a boot node and if that boot node is not available the nearest neighbours answer. I don’t know how viable that solution is or if it’s entirely possible possible but that might be an interesting path to look into whereas we don’t have a boot node list whereas an id space and anything within that space or the closest neighbour to that space answers the requests to join the network.

Ricardo : so my IP address it changes but it's in a certain range so maybe I could register my IP in a more abstract way and then maybe they can ping me and  try to find me within that range my internet provider.

Eric: no but the …
Dean :  So instead of going through IPs you go through a node ID and if that node ID is not available the nearest available neighbor to that node ID would respond to the request. it's something that I was recently looking into I don't know if it's possible but I'm gonna like try and expand on that research.

Igorm: But where will the packets go to the first, like are these so will it require some kind of I don’t know sending like messages everywhere to see who replys.

Dean: yeah so hence I don't know if it's very efficient or possible 
Eric: To me it sounds something swarm team is investigating or I think I’ve heard about something similar for PSS delivery.

Ricardo: Eric, do you think that swarm feeds could help in this or its awesome then you we have good nice problem for fleet.

Eric: to connect to the network no

Oskar: So must build in Go ether right and they have the same , its built on dev p2p so you have the exact same booting up start, the only difference has a different network ID and a different capability so it might help in terms of discovery once you are in the general ethereum network but it doesn’t use a different as far as I know it doesn’t use a different bootstrap mechanism than goeth any p2p ethereum protocol as far as I know.

Igorm: Yeah and you still have this zero like the empty state problems because I mean there's not many ways of how can you solve it you can have something like a DNS relay or something like this because unless you have at least one peer, the first peer, you can’t really talk to blockchain well unless you have been fewer or something like that because we don’t want to rely on the other fewer and that’s because..

Eric:  we want to peer 2 peer , the first one should either be hard coded or discovered by DNS which is also kind of hardcoded.

Ricardo: so there is also that the visualization of decentralization and also about the other thing that is decentralization in daenerys just missed the word distribution, so a distributed network or a decentralized network so maybe if the boot nodes they cause this centralization but it’s actually centralize in this boot nodes so maybe we could look forward  in a more distributed way and everyone is a bootnode and maybe somehow that information of your neighbourhood that you’ve seen recently are stored in your device and then you can try them.

42:32- 45:29
Igorm: Well that’s I mean everything is much less of a problem when you already connected to it and you have some history but everything is the biggest problem if you like status network is down, everything is down, you don’t know anything you install the app and start it and what do you do then ? I mean you can always have full scan of IP ranges or something similar to that or you can have hardcoded data inside but otherwise if you don’t connect to any peers you can’t get blockchain data because you …

Ricardo: Yeah I don’t really see that that is an issue, in case of the new user because maybe for that user we can provide a way for that user could like tap the phone of their friend which is in the network and download the bootnodes or some other way they can download through email that from someone so they find another way of finding the new user so I think the problem we need to solve is for the users that are currently not work not being disrupted by any event of a shutdown so if I am already in the network and already know the nodes that are randomly online, maybe I can have better chances on still becoming online.

Igorm: Yeah but that sounds like a more long term plan though but yeah as a long term plan it might be interesting to few

Eric: I think what Ricardo has imagined is what you can… the most important is that there is no disruption for current users and for the new ones in case the network is disrupted it’s just a matter of finding an easy way to share from a usera user that is already connected so like we have with QR codes which I want you to join the network and status’ not going to exist any more, I just along with my contact code I give you a boot node so you can join the network and then there is probably way enough nodes to sustain your good nodes need in the future from the network of users itself.

Ricardo: Yeah that’s what was my idea.

Igorm: Okay

Oskar: So since because there is something broken in design, it was probably a hack but right now when you add a custom boot node you have to restart the app which implies that there is some special thing where you add this node and that’s what you use to connect to network as it was just appending into an array because it should be adding it to some list and then the same thing will be the case that's what you guys just said that when you connect other nodes you can use them as boot nodes potentially and just add it to a list and like it shouldn't have to restart the app or anything ideally, like I'm not sure why it's restarting that

45:30 - 47:14
Ricardo:  maybe it's restarting the gas or the state 

Oskar:  there’s something about the state there maybe there’s some specific reason why its like that but it seems to be broken.

Igorm: Yeah it seems like more like about to the real reason because you can add peers at any point without restarting the home nodes so it’s a bit weird why these peers are treated separately

Ricardo: Yeah it maybe its because its not using the RPC common, its editing the configuration file and then it needs to restart sometime.

Eric: Yeah I think it’s more for ..

Oskar: Is Adma or Dimitry online maybe ? no ? 

Igorm: I mean they still add like they still end up in more or less the same place as the notes that you had with the RPC so it doesn't matter where it reads yo can read the empty list from the config and then add stuff later on.

Eric:  yeah it's probably just a matter of instead of just changing the config for for simply adding a node using their RPC command.

Igorm: Yeah, something like that but yeah it’s probably just a oversight on the geth design.

Eric: I think it’s terrible because for once I suspect it was web3 oriented for 3 months now try to remove web3 and use direct calls to use to the RPC interface so it should be easier now.

47:15 - 52:57
Igorm: Cool so should we move to the next one, I guess the next topic is 

Oskar: sorry one question on if there’s some security considerations, availability considerations so let’s say that we gather this list of additional static nodes so first of all does that expose us to any specific type of attacks and secondly it's a problem if certain notes are just half available.

Igorm: You know the second is probably not big of a deal but the first one  I can see that if let’s say like the default boot nodes aren't working but these nodes are working and are all malicious then they can end up with either DOSing or just plainly if we use like blockchain or so they can point to only malicious nodes in the future so that’s probably that you will end up with this but that's probably it needs to be a threat model so that’s from the tip of my head.

Oskar: my intuition would be that if it's something that we gate keep a bit with github peer process that even if you get like you I don;t think you would be that exposed to eclipse attacks but yeah we useful to just have a sound check out of core, what's your gut feeling right now ?

Eric: My gut feeling is it's not any different than anything else we could do it's I don't see anything extra based on what's been discussed here that would expose us anything that anything else wouldn't expose us to.

Igorm: hmm
Ricardo: So how a node can be identified as an attacking node, it would be delivering messages from like invalid messages or message that are not interesting to anyone in..

Igorm: Yeah that one I mean can always spam Network somehow it can just not do anything to help with communication so that's why and not return any other peers that can do that so it's essentially a denial of service attack and then and probably spend the public chat rooms because well again and then this is too obvious once one on one conversations will probably be safe if you know you have been talking to the right people before, so its a..

Ricardo: Yeah I said that we could probably have some kind of reputation of each node takes care of not something in chain but locally and then if some attack happens they just connect to the nodes they have a good history.

Oskar: That’s how I think that's’ how p2p works to do it there I think eclipse attack vectors there are some basics like that to make sure that you can’t show nodes and so on but that’s more about dynamic adding as opposed to static bootstrap phase I think.

Igorm: Yeah I think I had so far just keeping it with the PR process might be good enough for now especially if it’s just good nodes the ones that just supposed to help discover the you don’t wait for them to be a whisper node or to be whatever node it just only helps with peer discover if I understand p2p correctly.

Petty: Yeah is that process laid out somewhere ? It’s not just the actual code itself that have a spec sheet that explains the process of how it does this local behavior of furiously check nodes 

Igorm: so this you mean the discover itself Or..

Petty: Dev p2p like how it handles those ? 

Igorm: Probably there is something but it’s all the jobs on devp2p its …. are a bit spotty at some topics so that’s why the idea I mean  I guess that’s why it’s peer to peer right because it’s much better documented attempt. 

Yeah

Igorm: So I don’t know, I know that for discovery specifically there is derive few specs and for dev p2p it’s essentially just a messaging like we have for the status spec. That’s all this message means this or something like this I don’t know if it’s but peer discovery, it’s one of the topics to take a look at and how the nodes helps with it.

Igorm: should we talk about the repository of repositories ? Oskar ?

Oskar: That was just an announcement I got a bunch of questions of where to find some repositories and it’s kind of hard to find out yourself unless you know what your repository is if you look it up  you can search stuff is bit annoying so just made this lists of list so if you have a bunch of repositories  that are grouped by something then feel free to add them there and yeah it’s just a list, that’s all.

52:58 - 55:00

Igorm: Yeah.

Oskar: I just copied a bunch of bots and I added all the protocol ones so you can look there if you're not sure of what you look.

Igorn: Yeah, that’s actually a good idea because sometimes it’s very hard to see because we hook a lot of forks and these forks don’t really need so you usually don’t need them IRL but yeah some useful things.

Oskar: Yeah on that note  Goran had a good session as well like if you are owning any repositories and they can  be thrown away and you can just I mean one idea is to do some spring cleaning so you can just archive old repositories because right now we have over 300 repositories, 460 code repos so it’s quite a lot of them.

Eric: Does it include the repository about repositories ? :D

Igorm: Laughter .. :D

Ricardo: Yeah and I have a repository who’s name is contracts that actually have a lot of su projects inside of it so for example there’s an identity inside of there and I’m planning to spawn it into a new repository because some people find it difficult to find it inside of that repository because you need to look into the branches and yeah so there may be we can have your list so if the subcategories that is maybe the apps then things that I only maybe research on contracts so that

Ricardo: Yeah so that whatever there that’s great I would love to just be able to go there and then just search for in it and find whatever or anything and find relevant stuff that would be great.

55:00-59:29

Igorm: yeah cool, so yeah but we should mention this in front of repo in the repo of repos. okay then the next one is that I wanted to talk about a little bit is that just again we had this with retrospective from the chaos unicorn day and yeah there is a link to what exactly was there like the notes and actionable next steps I guess we have all the steps claimed so it's just more or less for your information but we decided that first of all we want to keep doing chaos unicorn day and do it like roughly every quarter so it's important and it might affect everyone but I think it's it was a very good learning experience for us and see how far are we from getting like a real p2p and decentralized messenger. Yeah so that was probably the big one and the other more technical details are in this probably what do you are interested in is the actionable next steps and these documents to see what's there yeah that's that's what I want to bring up also just for information.

Oskar: I guess for people who weren’t there in the retrospective and maybe if you have looked it up is this something else you like to address or do people have any other thoughts on it ? right ?

Ricardo: I think working well and better than I expected and I also.. it seems to work better when I run my mail server like the app is faster so we are going through the effort right direction this chaos unicorn day and we should do it more times.

Eric: For me it was annoying because it showed our development of some features is really relying on the production environment like testnet was really like wallet related features were really undoable at the time.

Oskar: I have a question so do we have any people who would identify as non-technical on the call if you could talk briefly about your experience.

Eric: I sthe devcall really a place for it ?

Oskar: Uh that’s true but I feel like that was the voice that we didn't hear a lot from and and it's probably a different experience so you write this it's maybe a bit but it would be useful for us to hear.

Eric: I know for sure from the chat calls that Hesther Rachael managed to to connect quite easily like we were actually talking on instead of during the day.

Ricardo: so they use the…. other people no ?

Oskar: Rachel and Hesther are you here ? allright.

Eric:  Basically I can say that they followed the gist that was made by Jack and used his main server like probably half of status at least.

Hesther: Sorry I got lost in browsers, yeah I would just to recap I was set up on mobile in ten minutes time maybe desktop took longer but more to do with reinstalling desktop which I've had issues around before but setting up the mail server thanks to Jeff was very straightforward.

59:30- 1:09:00

Igorm: Great so are there any topics that people want to bring up that weren’t reset. So if no then thank you everyone 

Oskar: Sorry what .. One question is if we should have it or if its bad timing for people with I guess there's some kind of holiday

Igorm: Oh yeah I figured it out 

Oskar: would people prefer to have it anyway I don’t know it’s  there’s
 so in two weeks there’s some kind of holiday Easter okay 

Igorm:Yes Easter Monday according to my calendar but do people prefer to either skip it completely or to just have it as a I don't know venue to talk just to have this call but whoever works will join without like real structure or we can skip it completely so let's put it like this we have a chat room so if you if you think that we should keep it then put a plus sign there if we think we should skip put a minus sign and yeah so its a , then we will confirm it.

Ricardo: This happened before from whether you remember people didn't join it the so I was waiting for anyone to join but no one joined.

Oskar: I think the difference is that was a big holiday like that was new year’s eve or something you stay.

Ricardo : yeah exactly 

Eric: not related to the holidays but I was wondering where in the first part of this meeting where we do this sync up wouldn't be more efficient too since it's like right only part of the call maybe we could remove that and replace it by extreme doing that like writing 4-5 lines about their current progress and like all team members agree and then we have a summary of it and maybe people can read it before the call and so if they have questions regarding this then they they can ask during the call but the sync itself can be done before hand.

Ricardo: yeah I agree with you I think that that is exactly this call meeting should be more about like people presenting ideas on what they  need to share with others maybe because they need something for example I'm developing this multi-sig and I need a next way to to load the contact list because if I want to add in new owners to my multi-sig I need to copy paste from it's difficult and I want it to just select the contacts from status for example and I think should be something about these about talking about the ideas we want to share our vision about status or vison of a specific swarm that needs thorough feedback from others and  we have a lot of follow up calls for example I'm not actually late for a call now and I'm just going to give the follow-up from from what I did exactly the same that I told here but more detailed so yeah that was it.

Eric:  so yeah that was it so yeah I stand it up in the in the notes but yeah the idea that it still provides a few lines about the progress and we make summary that is shared before the meeting people read it and instead of this time I rotated to sync up there would be follow-up questions progres some other teams if there is a crystal issues or whatever.

Oskar: Ricardo is there a reason that that agenda doesn't work in terms of adding stuff to that done before.

Ricardo: what I didn’t understand the question sorry 

Oskar: Is there a reason that the agenda format doesn’t work like github issue if you just have specific things you want to talk about 

Ricardo: oh no, I think that that's it's okay like you or the day a demand what what we need but I agree with Eric that I don't see any point of having a meetup sorry a sync like in this shot, just that we should like use we should like use this time for discussion of visions  and what we should do actually not with you well not we don't should not stop what we did but what we should do in this call and let the follow ups for the specific swarms.

Oskar: so what we said before is that we wanted updates to be forward seeking and so letting people know if there's something like a decision to be made or something like this so like something that’s happened since town hall that's relevant for other people to know, do people disagree with that ?

Eric: sorry can you repeat ?

Oskar:  that update should be only if there's something that's new since Town Hall that you think other people should know about and that sort of points to some kind of decision that's relevant for everyone in the column.

Eric: well for me I would still stick to a written form of that so if nothing has happened there is relevant since that there is relevant since that town hall then you shouldn't write anything in your sync but I think everything should be just in written form and people prepare the meeting should be like four to five minutes read and and then they can questions for during the call.

Ricardo: Yeah That’s a good idea.

Igorm: yeah by the way so for the voting in the chat room so if no one will interfere right now we’ll have a meeting on next meeting without skipping but it just who will who will work will join is if that's everything, if that's okay with you then okay cool I see more definitely more plus signs than minuses so great so then with this updates it's yet it's always a tricky thing I mean if we if we just write it then why even like write it for this call I mean . so let's yeah but it might be good point to discuss how not to make it redundant with town hall updates as well because there are updates anyway.

Eric: Well the thing is this call the updates can be more technical and yeah so that would be the difference you may be some details matter for instance if some wallet flows have changed might affect the sticker market and tribute to talk team or that kind of stuff 

Ricardo:  yeah exactly good point Eric that's that's the kind of changes we should talk know not only but anything that that affects others our interests or of others because for example I’m developing specific features on inside of the multi-sig you are it doesn't matter for for other because I’m experimenting with that and anyway if I have something that is cool enough to be shown or it's interesting interesting to other people then I will bring here.

Igorm: Okay so that makes sense, so then its more technical updates here okay let’s keep it that so yeah so I think then we can wrap it up and see if anyone wants to discuss something this call will probably stay open for a little bit for a little while but I guess for those who aren’t don’t have anything to discuss right now feel free to just.. Thanks for joining the meeting today 

Rachel: Thanks guys, happy build week.

Hesther: Thank you everyone, enjoy your week.

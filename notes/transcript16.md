#To Add
##Formatting  + end part

0:00 -1:00
igorm: yeah but let’s wait for maybe a minute or two for more people, just telling us right now, to actually start

1:00 -1:00
igorm: So yeah, thanks everyone for joining, I’ll lead today’s core devcall and let’s sstart with the notetaking. Eric would you mind taking the notes, I’ll share the link to the chatroom.

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
Iuri: Good morning, first in regards to the dao stuff, we (are) working on creating a project, listing a project, recieve a notice to create a target profile, reject the commit by delegate, for the teller network, we work on the escrow URA  and also fix some workflows in regards to releasing pumps , when one introduction, when the settlement was made. We fixed various issue related to the screen size. We improved the rating system as well. We fixed the data seeding system, that’s done and it works, we converted the Dapp to use the create react app, great together with the part 4 and we also improved the screen warning the user when a ATM provider was not available.

I can put one in embark too.
Igorm: Yep, Thank you
Iuri: So embark, we’re investigating this race conditions that happens sometimes and we tracking down this issue that turns out to be a geth bug and we pass the transactions that get stuck when running geth with proof of authority which is typically what’s used when doing development. we fixed a bunch of issues in cockpit with regards to pagination, we proved our coveros output, for dapps we did various other improvements in cockpits namely in the IDE and yeah, there’s a bunch of ... we also improve some other stuff but I think that should cover it

7:25- 9:32
igor: yeah, thank you, so now its not written in the Readme but its the democracy, is Ricardo here ?
igor: yes okay, ricardo just joined.
Igor: Hey Ricardo do you have any update for the Democracy ?

Ricardo: Hey, so you were missing me, yes regarding the democracy i had some so I basically I work around the contracts to kind of evolve them because I’m seeing the spec of it so I’m still working on some aspects of it of the governance you know, how it works but then I wanted to start to make the UI but you lean more about Javascript and React and embark, I started to make a multisig that is a very simple application in something that I need so I’m currently working on the multisig and so both of them, then I go back to the contracts of topic democracy so its a...I’m still unsure about all the details but yeah I’m just going to first make the first network configuration so you can set your who you delegate to and later would make it in a way that you can approve, dorry you can vote for approval to reject and also to create proposal ofcourse and yeah that would be then my next steps on top democracy and that’s it.

9:34
Igor: Thank you. So yeah now I guess barry and token economics.

Barry: Yeah, real quick I’ll share my screen, can you all see it ? Yes Okay, we started a notebook just to figure out you know what are the value drivers of you know ether because, well for one its a big thing, its something that status relies on in a lot of ways right, one  and a big part of our treasury is denominated in ether which as we could see can impact our long term plans based on market gyrations but also the security of the network that we are building a lot of our applications on top off is dependent on ether having long term value but when you look around there’s really not much out there or research being done into what exactly makes you know where ether’s going to derive its value from so this is sort of an investigation, something we started looking into and thinking about and exploring and I just want to put this notebook out there and people stresss test some of these ideas because there’s definately things that we probably are missing and this is not even this is far from a complete model so we really just want to kind of stress test these ideas but I’ll just leave you all with a couple of quick insights that we have so far and maybe in the coming weeks people can expand on this and help drive this research forward but you know in short one thing that we hear pretty often is that ethereum is gonna have all these different industreis and replacments built on top of it, you know ranging from financial services to arbritration, legal and beacuse of that you should expect Eth to be very valuable in the future, but you know if we look at that for example, here’s for example one transaction that took place where 1 million dai was wiped in the maker protocol which is built on top of ethereum but if we look at the value it accrued in this one transaction there was 1 mkr that was burned, because it was burned that’s roughly equivalent to 700 something dollars that accrued to the maker protocol and a transaction fee which was roughly equivalent to 9 cents but then that’s not something that was  burnt that’s something that went to the miners so that is something that gets recirculated so you have to divide that by the velocity that Eth has which we talked about in a previous presentation what velocity means but this is basically a value pool of one penny to Eth and 770 dollars to Maker in this one transaction that happened on the network. So you know just because all these services are being built on top of ethereum doesn’t mean the vast majority of that value is gonna accrue to eth, it may actually end up accruing to eth protocols being built on top of ethereum.

13:10-
And then There’s just so, most likely the value driver for eth itself is going to be transaction fees over time and I think this is an important thing in terms of understanding in terms of security we basically just took the history of the dollar value of these transaction fees over time, Just a couple of quick interesting facts about that they’ve been growing since inception at a rate of about 700% a year however, so far, 2019 is the first year since ethereum’s inception is that transaction fee growth is on track to be negative so we’re on to so far things could change but so far this year the growth in transaction fees dollar value is actually on track to be a negative growth rate from what we had in 2018.
 
14:09-15:44
That’s a, you know, one last thing, you could basically if you could estimate what these fees the growth rate for these fees would be over time then you can project that into the future, discount that to the present and then you get the discounted value accrual to eth from transaction fees and the question becomes are transaction fees the only value driver for eth ? are there other things that will drive value for eth and here’s an important, this is an important consideration because the security of the network is backed by right  now miners but in the future it will be proof of stake but there has to be an economic incentive for people to stake, they probably won’t stake or want to stake if the expected value of Eth long term is like negative, they probably have  some kind of positive value accrual expectations for eth in order for the economics of staking to make sense and and so I think that’s also why maybe this research is important not just to status but to the community as a whole because the security of the network, part of it is probably relying on Eth having long term value. So if you want to explore this more you can get a link to this notebook and dig deeper and provide your own insights, fork it comment and go from there.

15:45-
Igrom: Thanks for the great presentation, so 

Ricardo: So I want to give some comments on what Barry told. Regarding the proof of stake, obviously they usage of staking is that you will produce blocks but the blocks they probably don’t give any reward, the reward is only by the transactions and also if you think about the each  value what is the value of ether is actually the power of processing transactions in this decentralized system and so if we achieve scalability in Ethereum, it means that one ethere can do more and therefore it should be more valuable, not thinking about the price, I’m thinking about the value each ether have for me because each ether I have in my wallet is able to change the state of ethereum and that’s the value.

Barry: So I would leave you with one thought on what you just said, if we we have scalabilty and one ether can do more, has more transactional capacity then wouldn’t the avaerage wallet be actually need to hold less ether because they can do more transactions with less ether.

Ricardo: Yes they need to buy less, they don’t need to buy many, yeah that makes sense. 

Eric: But if scalability means that there is more use cases for which ether is used then you know it may be the offer and demand balance and the value stays the same I mean depends on.

Ricardo: Yeah because it causes less demand because you need less Ether to make a transaction, less demand to ether but at the same time when you have one ether you have more power then to make more transactions. SO its a complex scenario that we are going to get. I don’t understand the outcome but seems like moon 

Igorm: Later on because you had the topic, right now it’s more of a short sync up that at least was envisioned before, but if you want to continue discussing then we can just like discuss it in the end of the meeting if you’re okay with that. Just to keep it a bit, this part a bit short, everyone is present. Cool, yeah thank you. so yeah, let’s continue with the protocol research, Oskar do you have something to say ?


Protocol Research
-21:02
Oskar: Yeah sure, so let’s see, last week, continuance of the doing another iteration of the peer to peer data sync comparison survey paper that we’re building up, I was subtly looking into various types of discovery methods things are looking that we have setup a basic static website that roughly outlines the phases and so on and of the work that’s being done, its big brother is specs the basic static github page. We’re also documenting the current protocol and just not sending PR requests there in the specs repository that Adam’s working on. Priest any feedback on that one ? And then we also had a call with Swarm and a PSS team to say of what the path to getting that into the app or protocol at some point would look like as well as if there’s some kind of collaboration with mix that research and so on and then this week, some people are working on build week but we are doing a brief sort of proof of concept for PSS and feeds. We are gonna have sort of our bi-weekly call tomorrow with web free messaging with the whole team as well and then keep working on discovery and documenting the current protocol as well as exposing JSON RPC through some, this is also part of moving the protocol from closure to go so it’s more self contained and so on. That’s it for me.

21:03-

Igor: Cool, Thank you Oskar and next core improvements forum and the latest weeks were mostly about the incode so first of all we did release the support it, then we were also looking at how could we fight the unicorn  I think it was pretty succesful. In there so and then like except the unicorn day. Yeah we also completed some plain maintenance like we upgraded react native in the application c couple of times. Then techniques was merged as well I guess because in the previous call it wasn’t yet which was a huge change and right now there are two follow ups there that helped to improve the whole building pipeline and yeah, a lot of small things under the hood of the application. Maybe not so much visible on the UI level but the, and the biggest one that we are working on right now is to load missing messages from the chatroom which is essentially, which is a big thing because we only load for the traffic reason, we only load 24 hours especially all the private messages so if you happen to join the chat or if you happen to let’s say not go to status, not keep it open over the weekend, you probably will on monday you will lose all the information that was posted on saturday which sometimes looks like a box so we are aiming to fix this as soon as possible.So that’s what we’re working on. So that’s what’s cool improvements. So I guess Dow was already said by Iuri so let’s Janitors, anyone from janitors want to say something? and if not then we can switch to the teams and the core browser team, are there any updates there ?

23:12- 24:14
Oskar: briefly if there’s no one from janitors, I can just there was this survey about and process and tools and so on that went out I think last friday and part of that is also that we are looking to potentially using this rike tool that Jared presented last time well so if you haven’t filled out the process survey please do and a reason for that is because that there’s a tendency to sort of keep adding tools like we have github and we have different product ports and labels and pivotal tracker and so on and we’re going to make sure that whatever tools we use are most useful so if there are tools that people find annoying and so on then we can remove them. So if you’re bothered by some tool, the process or you think something’s are working great then please let us know so we can streamline the process and remove any bits of work and keep just minimal set of tools neccesary to streamline work, that’s it. 


24:15- 24:48
Igorm: Yeah, Thank you, cool yeah so the core browser, is there any other using in this front ?
Rachel: I think that the fiddle update that Julien shared and the build we kick off is the main update from past  couple of weeks.

Igorm: Cool yeah thank you and then the core chats ? 

24:49-
Eric: Nothing to say, its the same as tribute to talk we have worked 100% on tribute to talk closely last week.

25:01-
Igorm: Yeah, thank you, cool, so the next one is Desktop but desktop was essentialy merged to the core team so except what we did for core improvements and core incentivzation, there’s also ongoing effort to bring mobile UI, Mobile codebase to desktop and then after that to bring pane view like we have on desktop right now to the mobile client that have big enough screen. That’s essentially for the desktop and then the wallet and key card ?

25:39-
Guylouis:

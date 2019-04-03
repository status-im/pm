0:00 - 1:00

Pedro: Welcome everyone to the fourteenth core dev call meeting. The Agenda is pretty light, we will go over the Swarm(former) updates and then we have the Status components discussion and an area for misalliance announcements. I guess we should first get someone to take notes if it's possible.

Rachel: Take that.

1:00 - 2:00

Pedro: Thanks, Rachel. So, who wants to go first with Swarm updates?

# Sticker Market

Julien: I can go first if anyone wants too, maybe I will start with Sticker Market. Essentially, we didn't do a lot like recently because we are mostly done, Andrei did some changes around contracting direction, the idea is to reduce the transaction being perform when you try to buy a sticker pack.

2:00 - 3:00

Julien: Then contract edit front when we ask doing the process of auditing the contract that is essentially the last bit we need to do. So, it is all about Sticker Market. I can continue with the Browser Awesome, actually?

Pedro: Yeah, ok.

# Browser Awesome

Julien: Andrei implemented EIP712, and the goal of this EIP is to provide the different way to sign data from within your dApp, because the previous way to sign data was truly string based but now you can sign like more complex structural information so which is the way something was requested by a number of the external (..). Also is starting on working on separating dApps in separate tab, so because as you know we abuse chats and dApps in the same tab, which is I guess like feedback we have a lot of little bit confusing, so there is a new design to separate this in two different tabs and Andrei has already started and making great for us for that.   

3:00 - 4:00

Julien: A the last bit I'm working on is creating a new Swarm (Aron) extension and the idea is to push and finally (al) extension out of alpha, so we create a Swarm Aron that just to make sure we are agree on the scope and there is a little bit more ownership on this front. That's it.

Pedro: Ok, thanks Julien. Who is next?

# Tribute to Talk

4:00 - 5:00

Eric: I can do it. The tap swarm in general last week we fix the toolbars and there is a pending PR and the next step will be to make it a component and regarding Tribute to Talk we are in the final stage(tash) of implementing the chat UI for Tribute to Talk, the settings are done, but there is a few things that we still need to figure out like if we keep the personalize message are not for now and versioning of Tribute to Talk contract, but we should do the most of the progress this week, we have a call with Ricardo and Richard. So, that's it.

Pedro: Ok, thanks Eric. And anyone up next?

#Dapp Store

5:00 - 6:00

Andy: I can go on the dApp Store staff. So in tandem with Julien Andrei have been doing the staff of browsers changes and we can just detailed now we also slowly moving ahead with implementing messages design for version 1 of the dApps Store that focusing Cape Town who can help us do that the initial thinking we would have managed through (...) bounties but it's a very large project and it's seems better try experiment with a rather subcontracting particular organizations to do the full load of work and you know pay in cryptocurrency and all that kind of stuff which is really cool so (...) should verion 1 of the store which will just be like the suggested home screen icon for a new browser tab.

6:00 - 7:00

Andy: That should be done hopefully in a next two weeks and in the meantime we'll be finalizing the contract and hopefully preparing for orders that we can as soon as navigation PR is been merged and we've got those (4) separate tabs at the bottom of the app, we have the dApp Store up and running and get SNT ranking into it hopefully next month or two depending on how the contract (order) go but that stuff is moving long-lasting.

Pedro: Thanks, Andy.

Iuri: So, I can go next.

Pedro: Yeah.

# Teller Network

Iuri: So, for the Teller Network we are finishing and adding escrow workflow, a lot of other divide details (...) web application. We created the daily (...) system.     

7:00 - 8:00

Iuri: So, when we deploy the dApp or the contracts, you can do the (bondshow) actions automatically which is(mix) much easier to see the dApp in action and testings more easily. We are going be deploying the dApps soon again a new version to Rinkeby. For the DAO, DAO basically going were analyzing to the next steps it's gonna takes two words (...) and a lot more to the next time. In Pack we are working on Tribute mode  which is like fixing any bugs we can find, we are going to release a bit this week and the idea of this thing is the next week the final version and also we are working on a new website which will be release next week as well.

Pedro: Thanks, Iuri. Anyone up next?    

8:00 - 9:00

# DAO

Ricardo: I can go, I'm working on dApp democracy, now I'm making research on how I will implement V2 function and also there is a problem with allocation, but it's not problem, it's a characteristic that is balances that need to be removed from the total quorum because there are like not active balances they are locked balances so these is two things that I'm working on dApp democracy. Also, I'm researching on Ethereum geth, I'm already started to update whisper version 6 from the version 3, that should be easy to build something for Status in Ethereum geth if someone wants too.

Pedro: Thanks, Ricardo. Anyone else?

9:00 - 10:00

Anna: Configure some allocation, I can tell about Status Call, this apart. We have list and whole fix last week mainly about possibility to cancel the pint mail server, so when you selected some mail server as your preferred one you was not able to unselected, now you can, so if for some reason the mail server is not responding or (..) behavior in a long way, now you can just cancel and have the up to select any other mail server that is responding and behaving well.          

10:00 - 11:00

Anna: Also, added some changes to the bottom navigation in the mobile app, so the tabs are now visible there are home, wallet and profile tabs should be visible when you navigate actually in any screen. As I know you, Pedro, you've done a lot of changes to our build system, so you can also update a bit about it.

Pedro: Yeah. Basically we're moving from ad hoc set up to where we download dependencies we need to the next package manager system, so this is been going on for three or four weeks, now when the final stages before merging this to develop will start testing soon.

11:00 - 12:00

Pedro: The last remaining target is Linux which is giving us problems because you can compile it fine on Ubuntu 18, but it doesn't run on Ubuntu 16, so fixing that. Hopefully it should be at the end of this week, so I invite everyone to give it to try and see to find any kind so on the contract everything is working as expected. It shouldn't have any impact on the existing environment you have, so don't be afraid to give it a test. I rather have some feedback from the external developers which talk to me and said they were (..)  after trying this branch they (...) in a few minutes, so that was good to see. That's all I have. Who next?   


12:00 - 13:00

Jacek: Can I ask if you feel like it?

Pedro: Yeah, more and more.

Jacek: The best sign.

Pedro: Yeah, I mean I have the same return from Jacob has been also playing with it and he also has been trying it more and more, so that's a good sign, that's for sure. It's been allowing us to do whenever we've needed gracefully, so that's a sign of material environment when you can do stuff like this gracefully.   

13:00 - 14:00

# Security

Corey: I've got a few fames from a security perspective. This week we will be starting a retainer with Trail of Bits, that gonna be kind of watching over PRs we put do, watching contracts we are going compile. A new product called Critic that basically automatically runs other tools that are smart contracts pull requests and then notifies according whatever issues there are maybe that should help us with the life of beginning stages (avolving..) curly big done around swarms (and if a) we need another third-party a full (..) before after finish over them. Also, today we are launching a private campaign with hacker one, soon we can start to take the same hacks come in, hopefully, not to fast on any the scope of (...) public releases of the application and the infrastructure that serves the application, website basically.        


14:00 - 15:00

Corey: (..) whatever the hackers they invite in the private campaign, doublestole increase so we try to keep akadince of around five valid bug reports per a month (..). So, expect to hear hopefully not to much regulary(..) from hacker one.  

Pedro: Thanks, Corey. Is anyone else have update one a bit?

# Key card

Guylouis: I can give a quick update about key card. So, the almost feature complete for (..) key card integration .. the only thing we are still miss is a transaction signing and this should be ready in about a week rafely.    

15:00 - 16:00

Guylouis: We are also working on improving the login speed key card, and also we are working on developing of a key card app for the Ledger Nano X that is a bluetooth version of the Nano that is coming into market in coming weeks (community channel here). (There is now work before that to go to alpha stage).  

# Components discussion

Pedro: Ok. So, there is more updates or we can move to the discussion of Status components? Does anyone else have updates?

16:00 - 17:00

Pedro: Ok. So, let's move on. Julien, you wanna kick it off, it's yours, or Eric, I'm not sure.    

Eric: Was it mine.

Pedro: Ok.

Julien: Sorry, I was muting somehow. Yeah, I wanted to restart this discussion around components almostly because for now we have a number of different dApps that we are working on in parallel and looks like most of them (..) implementing their own components at least the best (diquence). This would discussion around components (..) lots of people have been involve in it and let's different point of use.

17:00 - 18:00

Julien: So, the one I want initial right now is very fact use and for that why I want to provide some content around I'm thinking about (..) she like most of the very busy component we have so seems like that list item in swarm can be deprecated like at least ones Status React in React Native and the (..) times in a value dApps we have like Tiller Network, ENS Name or dApp Store that we restarted working on (..pretty swim). (..) to rock in this and try to do something a little bit interesting for Status organization.       

18:00 - 19:00

Julien: My idea is just to add extra repository that will contain only these components, it could be some (..) I can extracted from right now, like instances React some components, so they don't really exactly match the fit myself, but still it is something, but yeah I guess we should use Stigma list as source of truth of components. So, if we have a separate repository which just component for both React Soweb and React Native mobile, that we have currently in Status React, I think it would be much easier for everybody to synchronize and interact and just make sure we are all in the same page and if we do that maybe it would make sense to have these component implemented into Javascript actually (..).               

19:00 - 20:00

Julien: So, it would be a single codebase of all components (..similar which) and because Javascript is kind of recommended language right now it would be probably easy to external contributors create these components. Also, if we will move more complex city behind Status React, so thanks to your adwork Pedro, it would be very easy now to compare Status React, but still if we remove all of these complexity, it would be a wind for office. So, these is the whole idea I wanted to discuss and get a feedback like ideas from people working on dApps like Tiller Network, feedback from design team, just to see if it make sense. Yeah, again I train very narrow fixed scope so that actually we can deliver or ship something this time.      

20:00 - 21:00

Julien: When we end all these business stuff we can add other things or think about more component or something web3 orientired bet list. I think it make sense to start with very basic component that we are reused like betams, list items, bages or other things. Once we are there now I think we have strong foundation to simplify and  improve sinargy across teams. The idea to initiate the description and get something back from other people.    

Iuri: Sorry, just speak, do you mean React components?

Julien: Yeah, yeah. I mean like visual components because we are mostly using React, that would be React component and React Native.

21:00 - 22:00

Iuri: We are like a both lot of them now, any bar because a (..). ...for the Tiller too, for the DAO. Yes, it would be nice to standardize all of that, would say potentially a lot of work on creating new application.   

Andrei: Can I come in with the design perspectives of these?

Pedro: Sure.

Andrei: Like Julien said, it's a pretty old discussion. Like speaking on behalf of the design team, we will be happy to turn the starts and discussions into action. So, I'm definitely on the board Julien the narrow of the scope and creating something simple, but usable. On the design side of things as you all know we have a component library for the app, but there is no defined components for web based apps, such as that.

22:00 - 23:00

Andrei: Although, when designing dApps we do follow certain patterns, we do reuse certain things, but there is no centralized serve library that would be a collection of all those reusable elements. So, like I said it's not just other nowhere we do have like singularities and certain levels of re-usability in dApps. So, to kick things off quickly I would suggest starting with basic things such as typography color ballot and icons which are the completely the same on the all platforms app, Native app I mean and the Web based app, such as dApps.

23:00 - 24:00

Andrei: So, if there is any need for assistance I will be happy to help. And if we move for do and serve creating components for web, I would just creating for example one component and defined that Figma and detail have all this specifications, I would work for the list item because it is the most common I guess, or maybe buttons, or maybe text input, something to start with and explore all the problems there would be potentially face. Yeah, that is it for me. What do you think?

24:00 - 25:00

Ricardo: I think that is interesting mentioned about the difference, about the Native app in this dApps, right now we have this difference, but just to mention this I think that in the future everything is going to be the same, everything would be a dApp. Like the (shet) screen and the wallet, the profile, right now we have this Native part build like hardcoded, but in the future for my vision that would be an abstracted out in the dApps. So, it is easier to build, easier to maintain and so on.

Andrei: So, that all the code level, right, but on the UX level would be some differences, because difference in basically user experience with Web based application and Native. The most simple example would be the tab bar.

25:00 - 26:00

Andrei: So, the websites, they don't have any things that is sticking to the bottom, in the mobile app for example, because it works inside the browser window that keeps track of certain limitations. Most common web based app would be a scrollable down, wouldn't have tab bar with text buttons and that create certain differences. The more differences considering the platform with text input, with display arrows in text inputs, so there is the different level of control as far as I know, when we're talking about websites verses Native apps. I'm not saying that it  should be different but I guess they for now just providing a better experience that seems like it would be different.    

26:00 - 27:00

Hester: I think the list item would be really good place to start from like the component side, next colors and bonds, then as you (regest) talking about it comes...    

Andrei: List item, it's really nice example, because these is an example when it's the same on both web and Native. It's gonna be completely the same, and yeah we start with. Also, do reusable fundamental typography color icons which are also gonna be the same.   

27:00 - 28:00

Hester: Yes, I'm totally on board. I think the both are really good place to start and (..) stay away from a... I totally understand concept having components (..) different on web as they are on Native. I think we need to discuss those case by case, because it feels like (..) endless.. should we copy or implement component for both Native and web at the same time always, because it's very difficult to have that ... discuss case by case would be more productive.      

Andrei: I agree.

Rachel: Does anyone have a feedback to the idea of implementing components in Javascript?

Andrei: As for me also just to have something for design perspective I'm all for implementing them in Javascript, because designers are familiar with Javascript, because it is a such popular language these days, so it's gonna also extract more contributors, I mean design contributors.

28:00 - 29:00

Eric: About me it seems like doing animations in library in Javascript is going be a bit a norm.

Andrei: I think we should research the most common modern patterns to use these things, if we are going to use React I'm sure there are plant of good animation libraries there. Let's research some best practices before kicking these off.

Jacek: I have a question. I mean we can offer people build their dApps compatible with better swarm, but how do we be sure that they can visually and design this instead their design .. we don't become to (overvalue)   

29:00 - 30:00

Andrei: Yeah, this is a nice comment by the way. It brings us back to this really long discussion about what we are building and what is the target audience that we are trying to build. So, if we are creating a component library, but we are going to use it inside to build our own dApps this is one thing, but if we are building a component library for third-party developers, it's another thing. And if that true, we should definitely consider some customizable elements, customizable color ballots, all these stuff.  

30:00 - 31:00

Andrei: I would suggest start building component library that we will use for dApps that we build internally.

Julien: Yeah, yeah I'm come back. I think this is a kind of one of the reason like why the original discussion is never ended and never conclude to something already done. (..) all well known in one library. So, personally just like very pragmatically what I need is just component that I will use as a developer and (...) first and make sure we implemented and shipped it. Especially, given that I'm not sure that an external developer are really interested in reusing whatever component we provide, they probably have a fine using something else and actually it would be a kind of complex of the (..median) run in (..) browser.          

31:00 - 32:00

Julien: So, perspective would be doing something simple and actually implementing it. Back to the previous point about dApps and web-dApps I think we are a kind of two different usage of web technologies instead us and for instance something like the dApp Store, well it's almost not a dApp in a sense that it will run directly with instead it will not run as a regular dApp in the browser. So, you don't add the wall browser the correction components and elements (...) kind of change the way those components would behave. So, to me it's almost like in this case the dApp Store is almost like native in sense that you shouldn't be able as a user to (dist..)      

32:00 - 33:00

Julien: In this case I feel like that should be like a common components that we can share like between web and native.

Andrei: Regarding the dApp Store be a basically native, I would suggest not to pretend that it is a native app when it is a web app and to be more transparent (..) and to be ready for it would be used outside of the Status. So, yes, it's most like we are gonna use it inside Status and serve control environment of ours, but it is a dApp, it has url and it is accessible from some other app that try to use a dApp Store as (..).   

33:00 - 34:00

Andrei: I suggest we should be ready for that and just think about it as a regular website (..) not considering what we have in our environment, that is a still a dApp, that make sense.

Rachel: Actually, I think that is not what we are doing, (we are going to represent as a website cannot suggest a webbrowser)... functionality

Andrei: It is. Technically it is. I guess what Julien was saying that how do we think about it like methodology, those kind of discussion, if I understand correctly.   

34:00 - 35:00

Julien: That sounds very smart and I will say: "Yes". I didn't realize that it will be shown as a real web dApp.

Rachel: (.General idea is not..) Actually offering a list of dApps. (...) digital goods for sale. (..) other cases might be actually adding more need feeling more than dApp.

Julien: Ok, yeah, make sense.

Andy: Example of ENS dApp, this is probably in my mind a better example of something that computationally feel more native because it (..) all identity web stuff (..) be doing where is a dApp.

35:00 - 36:00

Andy: Specifically external and it have you know eventually if I get my way the whole (.branch.) features like voting and (..)  complete and complex (..) your own (..) in addition (..)

Rachel: Yeah, sure.

Julien: Right, good points.

Rachel: Maybe worth formalizing this all component discussion

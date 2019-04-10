0:00 - 1:00

Pedro: Welcome everyone to the fourteenth core dev call meeting. The Agenda is pretty light, we will go over the swarm updates and then we have the Status components discussion and then an area for miscellaneous announcements. I guess we should first get someone to take notes if that's possible.

Rachel: Take that.

1:00 - 2:00

Pedro: Thanks, Rachel. So, who wants to go first with swarm updates?

# Sticker Market

Julien: I can go first if no one wants too, maybe I will start with Sticker Market. Essentially, we didn't do a lot like recently because we are mostly done, Andrei did some changes around contracting direction, the idea was to reduce the transaction being perform when you try to buy a sticker pack.

2:00 - 3:00

Julien: Then contract edit front when we are still in the process of auditing the contract, but that is essentially the last bit we need to do. So, that's pretty much it for Sticker Market. I can continue with the Browser, actually?

Pedro: Yeah, ok.

# Browser

Julien: Andrei implemented EIP712, and the goal of this EIP is to provide the different way to sign data from within your dApp, because the previous way to sign data was truly string based but now you can sign like more complex structured information. So which is actually something that was requested by a number of the external dApp developer. Also is starting like working on separating dApps in separate tab, so because right now as you know we have both chats and dApps in the same tab, which is what I guess one like feedback we had a lot, it was a little bit confusing. So, now there is a new design to separate this in two different tabs and Andrei has already started and making great progress on that.   

3:00 - 4:00

Julien: The last bit we are working on is on creating a new swarm around extension and the idea is to push and finally have extension and out of alpha, so we will create a swarm around that just to make sure we are agree in the scope and there is a little bit more ownership on that front. That's it.

Pedro: Ok, thanks Julien. Who is next?

# Tribute to Talk

4:00 - 5:00

Eric: I can do it. For the Tribute to Talk, the trot the chat swarm in general last week we fixed the toolbars and there is a pending PR and the next step will be to make it a component, and regarding Tribute to Talk we are in the final touch of implementing the chat UI for Tribute to Talk, the settings are done, but there is a few things that we still need to figure out like, if we keep them personalized message are not for now and versioning of Tribute to Talk contract, but we should do most of the progress this week, we have a call with Ricardo and Richard this week. So, that's it.

Pedro: Ok, thanks Eric. And anyone next?

#DApp Store

5:00 - 6:00

Andy: I can go on the dApp Store stuff. So, in tandem with the work that Julien and Andrei have been doing on the various different browsers changes and everything that he just detailed now, we also slowly moving ahead with implementing messages designs for version 1 of the dApps Store, there's some folks in Cape Town who are going to help us do that. The initial thinking we would sort of managed it all through bounties, but it's a very large project and it's seems better to try experiment with rather sort of contracting particular organizations to do the full load of work and you know we'll pay in cryptocurrency and all that kind of stuff which is really cool. So, we should have version 1 of the store which will or just be like the suggested home screen icon for our new browser tab.

6:00 - 7:00

Andy: That should be done hopefully in a next two weeks and in the meantime we'll be finalizing the contracts and hope to be preparing it for audits. So, that we can as soon as you know the navigation PR has been merged and we've got those 4 separate tabs at the bottom of the app, we can have the dApp Store up and running and get SNT ranking into it hopefully next month or two depending on how the contracts or let's go, but that stuff is moving along nasty.

Pedro: Great, thanks, Andy.

Iuri: So, I can go next.

Pedro: Yeah.

# Teller Network/Embark

Iuri: So, for the Teller Network we are finishing and adding scroll workflow, a lot of other UI details here and there just to really excite the web application. We created the this data seeding system.     

7:00 - 8:00

Iuri: So, when we deployed the dApp or the contracts, they can do a bunch of actions automatically, which makes it much easier just to see the dApp in action and instead testings more easily. We are going be deploying the dApps soon again a new version to Rinkeby. For the DAO, DAO basically going, when we are analyzing all the next steps that we're gonna takes towards the DAO and a lot more news on that next time. Embark we are what I want to say this we're kind of like in turbo mode, we're just like fixing any bugs we can find, we are going to release the beta this week with the idea of releasing next week the final 4 version. Also we are working on a new website, which should release next week as well.

Pedro: Thanks, Iuri. Anyone up next?    

8:00 - 9:00

# DAO

Ricardo: I can go, I'm working on dApp democracy, now I'm currently researching how I will implement the veto function and also there is a problem with allocation of essence not a problem, but a characteristic that is there is some balances that need to be removed from the total quorum, because there are like not actively been set of balances, they are locked balances. So, there is these two things that I'm working on dApp democracy. Also, I'm researching on Ethereum J, I'm already started to update Whisper version 6 from the version 3, that is returned J to the 6, and with that I think should be easy to build something for Status in Ethereum J if someone wants too.

Pedro: Thanks, Ricardo. Anyone else?

9:00 - 10:00

Anna: Because Igor is on vacation, I can tell about Status Call. We have released the hot fix last week mainly it was about possibility to cancel the tinned mail server, so when you selected some mail server as your preferred one you was not able to unselect it, now you can, so if for some reason the mail server is not responding or whatever behavior in a wrong way, now you can just cancel and have the app to select any other mail server that is responding and behaving well.          

10:00 - 11:00

Anna: Also, we added some changes to the bottom navigation in the mobile app, so the tabs are now visible as a home, wallet and profile tabs should be visible when you navigate actually in any screen. As I know you, Pedro, you've done a lot of changes to our build system, so you can also update a bit about it.

# Nix

Pedro: Yeah. Basically we're moving from our ad-hoc system where we download dependencies we need to the next package manager system, so this is been going on for I believe three or four weeks, now we're in the final stages before merging this to develop, we'll start testing soon.

11:00 - 12:00

Pedro: The last remaining target is Linux, which is giving us problems, because we can compile it fine on Ubuntu 18, but it doesn't run on Ubuntu 16, so we're fixing that. Hopefully it should be ready at the end of this week, so I invite everyone to give it a try and see if they find any kinks or if on the contract everything is working as expected. It shouldn't have any impact on the existing environment you have, so don't be afraid to give it a test. I already have some feedback from the external developers who reached out me and said they were a table for instance to build Androids and after trying this branch they got it up and running in a few minutes, so that was good to see. That's what I have for Nix. Who next?   

12:00 - 13:00

Jacek: Can I ask a people like it?

Pedro: Yeah, more and more.

Jacek: The best sign.

Pedro: Yeah, I mean I've had the same return from Jacob, he's been also playing with it and he's also been enjoying it more and more, so that's a good sign, that's for sure. It's been allowing us to do whatever we've needed gracefully, so that's a sign of maturing environment when you can do stuff like this gracefully.   

13:00 - 14:00

# Security

Corey: I've got a few things on from the security perspective. This week we will be starting a retainer with Trail of Bits, they're gonna be kind of watching over PRs we put do, watching our contracts. We are going to be piloting their new product called Critic, that basically automatically runs integrates with github, it runs all their tool set on smart contracts pull requests and then notifies according to whatever issues there are maybe. That should help with a lot with the beginning stages of all the audits that are currently being done on all the swarms and if we need another third-party audit, a full audit before with that after the initial like overview from them. Also, today we are launching our private campaign with hacker one, so we can extort potentially saying bugs come in, hopefully, not too fast on any and that's the scope of these is any of the current public releases of the application and the infrastructure that serves the applications of the website basically.        

14:00 - 15:00

Corey: We'll see bugs come in from there from whatever hackers they invite and the private campaign, that will still to increase, so we're trying to keep a cadence of around five valid bug reports per a month and then I'll be handling those and dishing them out to whoever needs to mitigate whatever comes there. So, expect to hear that hopefully not to much, but regularly over the next few months coming from hacker one.  

Pedro: Thanks, Corey. Does anyone else have an update you want to give?

# Key card

Guylouis: I can give a quick update about key card. So, we are almost feature complete for an alpha version of the Key card integration with the Stellar as for Android. The only thing that we still miss is the transaction signing and this should be ready in about a week roughly.    

15:00 - 16:00

Guylouis: We are also working on improving the loading speed Key card. Also, we are working on the development of a Key card app for the Ledger Nano X, which is the Bluetooth version of the Nano that is coming on the market in the coming weeks and currently we're implementing using your channel here. And maybe about what it's I think the rain is not here, but there's no one going work, since Garron is working on the Key card to help to get to this alpha stage equity.  

# Components discussion

Pedro: Ok. So, unless there is more updates or we can move to the discussion of Status components? Does anyone else have updates?

16:00 - 17:00

Pedro: Ok. So, let's move on. Julien, do you wanna kick it off for? I think this was yours, or Eric, I'm not sure.    

Eric: Wasn't mine.

Pedro: Ok.

Julien: Sorry, I was muting somehow. Yeah, I wanted to restart this discussion around components and mostly because for now we have a number of different dApps that we are working on in parallel and looks like most of them are kinda free implementing their own components at least the basic ones because, yeah. This word discussion one component is quite old and lots of people have been involving in it and lots of different point of views.

17:00 - 18:00

Julien: So, the one I want to initiate right now isn't is very focused. So, that why I want to provide some context around what I'm thinking about. But essentially I feel like most of the very basic component we have two things like that list item and so on they are kind of duplicated like at least once in Status React in React Native and then essentially probably a couple of times in various dApps we have like Tiller Network, ENS Name or eventually dApp Store one, that we will start working on pretty soon. So, it sounds like an opportunity to work on this and try to do something a little bit like more interesting for Status as an organization.       

18:00 - 19:00

Julien: My idea would be to have like just an extra repository that would contain only those components. So, it could be some more somewhat like extracted from what we are right now, like in Status React we have some components, so they don't really exactly match the Figma ones, but still it is something, but yeah I guess we should use Figma list as a source of truth of components. So, if we have like a separate repository which just component for both React web and React Native mobile, what we have currently in Status React, I think it would be like much easier for everybody to synchronize and interact and just make sure we are all on the same page. And if we do that maybe it would make sense to have these component implemented in Javascript actually and not closure.               

19:00 - 20:00

Julien: So, this way there would be a single codebase of all components in the same language and because now Javascript is kind of common language right now where it would be probably easy to have external contributors create those components. Also, if we remove the world complexity behind Status React, so thanks to your hard work Pedro, it would be very easy now to compile Status React, but still if we remove all of this complexity, it looks like it would be a win for our office. So, that's kind of the eye level idea I wanted to discuss now and get like feedback and ideas from people working on dApps like Tiller Network or feedback from design team, just to see if it makes sense. Yeah, again I'm trying to have a very narrow and fixed scope, so that actually we can deliver and ship something this time.      

20:00 - 21:00

Julien: Then once we have this basic stuff, we can always add other things or think about more component or having something more web3 oriented, but at least I think it makes sense to start with a very basic component that we already used nodes were like button, list items, badges or other things. Once we are there now I think it will be a strong foundation to simplify and improve that synergy across teams. I mean that's the whole idea not to initiate the discussion and get something back from other people.    

Iuri: Sorry, just be clear, do you mean React components?

Julien: Yeah, yeah. I mean like visual components because we are mostly using React, that would be React component and React Native.

21:00 - 22:00

Iuri: We have like a both lot of them now in the bark because of cockpit and I mean studies us as well, we have enough for the Tiller too, for the DAO. Yes, it would be nice to standardize all of that, it would say potentially a lot of work when creating new applications.   

Andrei: Can I comment from the design perspectives on this?

Pedro: Sure.

Andrei: Like Julien said, it's a pretty old discussion. I'll be like speaking on behalf of the design team, we would be happy to turn those thoughts and discussions into action. So, I'm definitely on the board with Julien with narrowing the scope and creating something simple, but usable. On the design side of things as you all know we have a component library for the app, but there is no defined components for web based apps, such as dApps.

22:00 - 23:00

Andrei: Although, when designing dApps we do follow certain patterns and we do reuse certain things, but there is no centralized serve library that would be a collection of all those reusable elements. So, like I said it's not just out of nowhere we do have similarities and certain levels of reusability in dApps. So, to kick things off quickly I would suggest starting with basic things such as typography color palette and icons, which are completely the same on the all platforms: app, Native app I mean and the web-based apps, such as dApps.

23:00 - 24:00

Andrei: So, if there is any need for assistance I will be happy to help. And if we move further and started creating components for web, I would just creating for example one component and define that in Figma in detail I have all the specifications. I would work for a list item, because it is the most common I guess, or maybe buttons, or maybe text input, something to start with and explore all the problems that we potentially face. Yeah, that is it for me. What do you think?

24:00 - 25:00

Ricardo: I think that interesting that you mentioned about the difference, about the Native App and the dApps, right now we have this difference, but just to what you mention this I think that in the future we are going everything is going to be the same, everything would be a dApp. So, like the chat screen and the wallet, and the profile, right now we have this Native part build like hard coded bit, but in the future for my vision I see that this would be an abstracted out in the dApps. So, it is easier to create, easier to maintain and so on.

Andrei: So, that all the code level, right, but on the UX level would be some differences, because of the difference patter a difference in basically user experience between web-based applications and Native. The most simple example would be the tab bar.

25:00 - 26:00

Andrei: So, the websites, they don't have anything that is sticking to the bottom, in a mobile website for example, because it works inside of a browser window and that gives us certain limitations. Most commonly a web-based App would be a scrollable down, it wouldn't have a tab bar that sticks to the bottom and that creates certain differences. There are more differences considering the platform with text temple, would display errors in text inputs. So, there is the different level of control, as far as I know, when we're talking about websites versus Native Apps. I'm not saying that they should be different, but I guess they for now just providing a better experience, they most likely be different.    

26:00 - 27:00

Hester: Just you know some of what you're saying on, I think the list item would be a really good place to start from like the component side, next colors and fonts, then as to what you were just talking about when it comes...    

Andrei: List item, it's a really nice example, because this is an example when it's the same on both Web and Native. It's gonna be completely the same, and yeah we will start with. Also, do reusable fundamentals such as typography, colors palette, icons, which are also gonna be the same.   

27:00 - 28:00

Hester: Yes, I'm totally on board. I think that those are really good place to start and kind of stay away from dApp. I totally understand the concept about having components that might be different on Web as they are on Native. I think we need to discuss those case-by-case, because it feels like otherwise we get into a endless like should we or shouldn't we copy or implement components for both Native and Web at the same time always, because I think it's really difficult to have that to set that rule, but to discuss case-by-case would be more productive.      

Andrei: I agree.

Rachel: Does anybody have a feedback to the idea of implementing the components in Javascript?

Andrei: As for me also just to add something from the design perspective I'm all for implementing them in Javascript, because designers also are familiar with Javascript, because it is such a popular language these days, so it's gonna also extract more contributors, I mean design contributors.

28:00 - 29:00

Eric: About me it seems like doing animations in library in Javascript is going be a bit a norm.

Andrei: I think we should research the most common and modern patterns to use these things, if we are going to use React, I'm sure there is plenty of good animation libraries there. Let's just research some best practices before kicking this off.

Jacek: I have a question. I mean we're asking people to build their dApps compatible with better swarm, but how do we be ensure that they can visually and design this instead their design. So, we don't become to overwhelming.   

29:00 - 30:00

Andrei: Yeah, that is a nice comment by the way. It brings us back to this really long discussion about what we are building and what is the target audience of what we are trying to build. So, if we are creating a component library, that we are going to use inside Status to build our own dApps, this is one thing, but if we are building a component library for third-party developers, it's another thing. And if that's true, we should definitely consider some customizable elements, customizable color palettes, all these stuff.  

30:00 - 31:00

Andrei: I would suggest starting building component library that we would use for dApps that we've built internally.

Julien: Yeah, yeah I completely agree. I think that is a kind of the one of the reason why like the original discussion is never ended and never concluded to something like already done. It that we were trying to serve all the program of the world now in one library. So, personally just like very pragmatically what I need is just component that I will use as a developer and address a focus on that first and make sure we implemented and shipped it. Especially, given that I'm not sure that an external dApp developers, they are really interested in reusing whatever component we provide, they probably of the define using something else and for actually it would be a kind of complex for them I guess if they want to run in other non-Status browser.          

31:00 - 32:00

Julien: So, perspective would be just doing something simple and actually implementing it. Back to the previous point about dApps and web-dApps, I think we have a kind of two different usage of web technologies in Status and for instance something like the dApp Store, well it's almost not a dApp in a sense that it will run directly within Status, it will not run as a regular dApp in the browser. So, you don't have the world browser declaration components and UI elements and probably it's also kind of change the way those components will behave. So, to me it's almost like in this case the dApp Store is almost like Native in a sense, that you shouldn't be able as a user to distinguish that it's web, oh it would be a little bit world.   

32:00 - 33:00

Julien: In this case I feel like there should be some common components that we can share like between Web and Native.

Andrei: Regarding the dApp Store being a basically native, I would suggest not to pretend that it is a Native App, when it is a Web App and to be more transparent and honest about it, and to be ready for it to be used outside of the Status. So, yes, it's most likely going to be used inside Status and in the sort of controlled environment of ours, but since it is a dApp, it has the URL and it is accessible from. Someday some other App would decide to use Status dApp Store as their.  

33:00 - 34:00

Andrei: I suggest we should be ready for that and just think about it as a regular website as a regular though not considering what we have in our environment, as that is a still a dApp, that makes sense.

Rachel: Actually, I think that is not what we are doing. I thought that we were going to represent it as a website, it's gonna to be like home screen in the web browser.. and a new functionality.

Andrei: It is. Technically it is. I guess what Julien was saying that how do we think about it like more of a methodology serve kind of discussion, if I understand correctly.   

34:00 - 35:00

Julien: That sounds very smart, so I would say: "Yes". I didn't realize that it would be shown as a real web dApp.

Rachel: Yeah, part of the ideas that we're not actually offering a list of dApps and thereby we're not violating any dApp Store rules by offering digital goods for sale. So, it's actually an additional inspirated dApp Store but that's just this particular example. In other cases we might be actually animating more native feeling with the dApp.  

Julien: Ok, yeah, make sense.

Andy: Much better example would be the ENS names DF, that's probably back in my mind a better example of something that could potentially feel more native because it plugs into all the identity work and stuff that Andrei has been doing.

35:00 - 36:00

Andy: There's no dApp always specifically external and we'll have you know eventually if I get my way like a whole bunch of features you know like uploading and downloading with SMT and interactions with your wallets and stuff which will make it very, you know, completes and complex, and worthy of its own URL and standing alone in additions all the dApp Store guidelines that Rachel just mentioned.

Rachel: Yeah, sure.

Julien: Right, good points.

Rachel: Might be worth formalizing this whole component discussion in a swarm (..right up..rater) because we've identified some research needs and terms of implementation like definitely different phase into yours and there's a lot sitter in terms of like actually handle the implementation, it'll be really attractive if we can manage to bounty out the whole thing and it seems like something that we should be able to find enough external contributors who would be interested in capable of doing especially for creating goods in Javascript. I could take a start writing up at least like an intro in a few sections for this as a swarm.  

36:00 - 37:00

Rachel: I don't know how many people would have time to dedicate but it's certainly like a shared interest. So, does that sound like a good idea?  

Andy: Yeah, right. So, if we could formalize this, I'm also like a big fan of doing it in Javascript, I'm sorry that I sort of pushed perhaps in the wrong direction last time and I'm more than willing to go along particularly with our designers preferences on this. And, you know, if we do it in Javascript we could potentially reuse like a little bit of the work that we did not a story, but last time if we find any of it to be useful and certainly like the same guys who are keeping on doing the dApp Store work for us have been asking if there's like any other work in between version one of the dApp Store and like implementing the smart contracts, but like laughs. So, they would be keeping perhaps to take on something like that, because they have React experience, if we decide, but doing it in Javascript is okay given the animations and like input for there's anybody else.   

37:00 - 38:00

Rachel: Caveats, okay cool. Yeah, then I'll take a stab at doing a write up, so we can bring that up to other people.

Hester: I know it also, because there is some more time to discuss. I think a write up see great ideas, it's a bit of larger effort altogether just coming back to things like font and color palette and list item are any of those being implemented for React native now that could be expanded, so we have like a start.

Julien: Right, definitely actually list item is probably one of those component that really are very close to what has been designed and things like color typography. Yeah, I think we have pretty much it, so it sounds like a great set of components to start with.

Hester: Is anyone working on those specifically that has time to expand..?    

38:00 - 39:00

Julien: So, this have been implementing like a long time ago. I think I'm the one who created the list items, so I can definitely work on that.

Hester: Ok, yeah, that would be awesome just I wouldn't want to do seem like things that we would need regardless of whatever future system we'd come up with. So, it feels like the sooner we can start on those better. So, if you say you're working on list item, is anyone working on phones at the moment or is that also something that's already happened in the past?

Julien: Yeah, I guess it's part of this component that already existed before the Figma design. So, there are pretty much done.

Andrei: By the way regarding the typography of a typeface we used as you all know it's open source and it's being actually developed and it's being updated once in a while.

39:00 - 40:00

Andrei: So, just to consider this we never discussed that before that this typeface needs updating. So, if anybody could look great, like I don't know sort of a road map or just let's just keep that in mind that it's updated. So, somebody would go to the developers website, download the latest typeface and update it inside the codebase. I'm talking about the interior UI, it's that face right now the one we use on both native app and dApps.

Julien: Okay, I guess we have a plan unless someone wants to discuss something else.

40:00 - 41:00

Hester: Yeah, maybe about the fonts on like we can put it on the core that clock. So, we can see when someone can update that.

Andrei: Yeah, ok. Just everybody knows that it's not like a static thing, it's changing.

Pedro: Does anyone else have any inputs for this discussion or are we done?

41:00 - 42:00

Julien: So, maybe just like one last shot from me is I see this as kind of a collective effort like any team doing something related to UI which should be probably all of us. Well at least the revell they should think component and try know just extra extract whatever behavioral thing they are working on to make sure that they can be reused across the various teams and try to reduce the duplication and that type of thing that would be really great.

Ricardo: Maybe the designers, they can mention to the developer. Look, this component here is probably being reused and also the designers, they can follow up this story book or whatever is the model we are using, to see if the component is actually implemented as the designer expected.

42:00 - 43:00

Ricardo: So, maybe it would be, as you mention it is a team effort, but I guess that the design team should be in charge of taking care of what goes to this package and actually to review if it's correct.

Andrei: Yeah, that sounds great, would be happy to serve to do it, let's just find out what is the best way to make it work. As I said if we start with something really simple it would be easy to find out what is the best way to review components, to define components. I guess after we start with something simple is going to be easier to scale that system.

# Miscellaneous Announcements

43:00 - 44:00

Pedro: Ok, sounds good, sounds like a plan. If we return with (CI) since we know that the next steps looks like we're done this discussion. Should we move on to miscellaneous announcements, does anyone have anything they want to broadcast?

Anna: Yes, I do. I have two small announcements, if I can start?

Pedro: Sure.

Anna: First one actually it relates to anyone who has mobile application installed, if you haven't upgraded from 33 release that is like two readers in the post, please, do upgrade to the waiter stories. The reason is that next Monday, so in a week, they will make changes to the nightly build first and later to the next release and you will not be able to receive messages from this two newer versions in one to one and in the group chats.   

44:00 - 45:00

Anna: So, who wanted to receive messages, please, upgrade to the latest release. If you adventurous to the nightly, but I would as a tester I would recommend to update to the latest through list mobile version. For the desktop we will announce the stable version later this week. So, it was just announcement in short just upgraded to the latest released version, that's it.  

45:00 - 46:00

Anna: The second one is a bit more complex, so if you ever reported issues in Status React Ripple and use to think that your issue is relevant but there were no actions on this like last three months then it will be all closed by bot, but it will be marked for of all this tale label and then it will be closed later. So, if you think that issue is still relevant, please, make a note like: "I can still reproduce", "all these features still needed" and "you haven't added it to the app, but I really would like to see it". So, just add some comment to the issue, so it's open, it's not closed by the bot. If you, for example, got some update, but like notification from github, but missed it and you still remember about such issues, please, go to Status Reactor Apple and just search for issues and reopen them.

46:00 - 47:00

Anna: That will be very helpful and will save a lot of time for testing who will review such issues that were closed and see if they still relevant. That's it.

Pedro: Excellent. Does anyone else have an update to announcements?

Jacek: I can do one. So, for Nimbus I don't know if you guys are following any of that stuff but what's happening with in two words right now is that we're going to be launching a client specific testnet of sorts for the beacon chain. How do we contain doesn't do a lot of things, but it does provide randomness and security to it there's into.   

47:00 - 48:00

Jacek: The part of the testnet is basically that we're going to run a whole bunch of nodes and there're going to be generating a blockchain. The idea is that anybody can connect to this testnet and try out like Nimbus and see if it works. So, if anybody is interested in becoming like playing a validator, basically playing a stakeholder in Eth 2, you get in touch with me, because this is what will be launching like in the next few weeks. So, the workflow is basically that in Ethereum 2.0 you stakes on Eth and then you become a validator and then validators have these duties which are similar to what miners do today and basically we're looking for test bunnies that want to play validators on our own testnet.  

48:00 - END

Jacek: So, this is going to be like a first prealpha launch of the Nimbus testnet and then the next thing that's gonna happen is that once all the client teams have their tests up would be creating a common test that. So, get in touch it's, if you want to try this stuff out.

Pedro: Thanks, Jacek. Anyone else?

Pedro: Ok. Looks like we're done. Thanks everyone for joining, have a great week!

Rachel: Awesome, thanks, Pedro.

Julien: Thank you. Bye.

Andy: Good week, guys!

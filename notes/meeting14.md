# Core Dev Call 11/03/2019

## Agenda

1. Swarm updates
2. Status components discussion
3. Miscellaneous announcements

## Transcript
[Transcript](transcript14.md)

## Call Notes

### Swarm Updates

### Sticker Market
- Mostly done with feature work
- Andrey made a few changes to contract interaction
- Still in process of auditing the contract

### Browser
- Andrey implemented EIP712; goal is to provide a different way to sign data from within your DApp
    - Previous way was purely string based, now more complex information is supported (requested by DApp developers)
- Also working on separating DApps into their own tab
- Working on a new swarm for extensions to move the product out of alpha

### Tribute to Talk/Chat
- Fixed the tool bar and now making it a component
- Finalizing Tribute to Talk chat-side UI (settings already done)
    - Open issues: can we send a personalized message or not with TtT pay wall?
    - Call this week with Ricardo/Richard to discuss contract additions

### DApp Store
- Moving into implementation of Maciej's DApp store designs (web DApp)
- Using an agency in Cape Town
- Version 1 will be a categorized list
- In the meantime, contract will be prepared for audit

### Teller Network
- Finishing the escrow work flow and UI details
- Created a ___ system which makes it easier to see and test the DApp
- Deploying new version to Rinkeby soon

### DAO
- Analayzing next steps here right now

### Embark
- Fixing bugs, planning to release beta this week and final 4 version next week
- Launching new website next week as well

Ricardo - liquid democracy, token balances, Whisper J (version 6 from version 3) - should make it easy to build something for Status in Ethereum J

Anna - released hot fix last week mainly to "cancel" a pinned mail server (and opt back into automated selection). Also added changes to the bottom navigation in mobile - always visible now.

Pedro - we're moving from our ad hoc build system where we download all dependencies we need into next package manager system. This has been on for 3-4 weeks now, we're in final stages before merging to develop. Testing soon. Last remaining items are fixes for Linux and Ubuntu 18. No impact on your existing environment, please to test. External developers are finding it easier to build.

Jacek - do you still like nix?

Pedro - yes.

Corey - starting a retainer with Trail of Bits this week. They'll be watching over our PRs and contracts. We'll be piloting Critic, which integrates with GH and automates all their tool sets on smart contract PRs. This should help with all of the swarm work. We're also launching our private campaign with Hacker 1 today so we can start finding (?) bugs on any public release. Looking for a cadence of 5 valid bug reports per month.

Guy Louis - almost feature complete for a (?) version integrated with Status for Android. The only thing missing is transaction signing; should be ready in a week. Also improving the log-in speed for keycard, and working on the keycard app for ledger, nanox (bluetooth version), etc. Wallet: there is no ongoing work since Goran is working on keycard alpha.

### Discussion Points

### Status Components

We are now working on a number of different DApps and they are re-implementing their own components.

This discussion has been happening for a long time.

Components we do have are duplicated across status-react, react native and in various DApps we have.

Would be interesting for us an organization to create a components repository, which could be extracted from what we have right now and using the figma list as a source of truth.

If we have a separate repo for components (both web and react-native), it would be much easier for everybody to synchronize and interact. It might make sense to have these implemented in JS rather than Clojure.

That way others can contribute more easily.

Iuri - we have a boatload of components in Embark now because of Cockpit. For Teller, DAO, etc. It would be nice to standardize all of that and would save potentially a lot of work when creating new applications.

Andrei - like Julien said, it's a pretty old discussion, and on behalf of design, we'd be happy to turn this into action. I'm on board with narrowing the scope and creating something simple but usable. On the design side of things, we have a component library for the app, but there's no defined components for web-based apps (DApps). When designing DApps, we do follow certain patterns and re-use certain things. But there's no centralized library that would be a collection of all those reusable elements.

I would suggest starting as basic things such as typography, color palette and icons - which are completely the same on all platforms.

Ricardo - difference between native and DApps. I think that in the future, everything is going to be a DApp. The chat screen, wallet, etc. I see all of this being abstracted out.

Andrei - that's on the code level, but on the UX level, there would be some differences. There's a difference between web and native. Most simple example would be the tab bar. Websites don't have anything sticking to the bottom. Most commonly a web based app is vertically scrollable. Etc.

Hester - I echo that list item would be a really good place to start from the component side, next to colors and fonts.

Andrei - List item is a really nice example because it's the same on both web and native.

Hester - totally understand the concern about having components that are different on web and native, but should be discussed case by case.

Rachel - javascript?

Andrei - no pushback, it's easier for designers.

Eric - doing animations in JS is going to be a bit...

Andrei - I think we should research the most common environment patterns. If we're going to use React, I'm sure there are plenty of good animation libraries there.

Jacek - We're asking people to build their DApps compatibly with Status. How do we ensure that they can visually and design wise express what they want?

Andrei - if we're building it for our own DApps, that's one thing. If we're building for third party developers, it's another.

Julien - completely agree. I think this is why the original discussion never ended. We were trying to solve all the problems in one library.

Not sure how interested external developers are in using components that we provide.

Especially if they want to run in other non-Status browsers.

On the point about DApps and web DApps, I think we have two different usages. Something like DApp store is almost not a DApp in the sense that it will run directly in Status, it will not run in the browser. You won't have browser UI elements. It will change the way those components will behave.

You shouldn't be able to distinguish as a user.

I feel there should be components we can share.

Andrei - Would push back on that and presenting it as native.

Andy - ENS DApp is a better example of that.

Rachel - formal swarm proposal?

Andy - all in favor of JS. Could potentially reuse a bit of the storybook. Some of the guys who worked on that are keen.

Hester - write-up's a good idea as it's part of a larger idea. Coming back to ideas like font, color palette, list item. Are any of those being implemented for react-native now that could be expended?

Julien - list item is one that is very close to what has been designed. Color, typography, as well. Sounds like a great set of componenets to start with.

Hester - is anyone working on those specifically who might be able to expand on the work they've already done for react-native?

Julien - those have been done a long time ago. I did list item so I can definitely work on that.

Hester - seems like things we would need regardless of future system. So the sooner we can start on those the better. Is anyone working on fonts at the moment?

Julien - I guess it's part of those that need to be updated.

Andrei - the typeface we used is open source and being actively updated. We'ver never discussed this but the typeface needs updating. If someone could create a roadmap, let's just keep in mind that needs to happen. Interior UI typeface. The one we use on both native app and DApps.

Hester - maybe we can put that on that ___ so we can see when someone should update that.

Andrei - sure, it's not a big thing.

Pedro - any other points for discussion?

Julien - I see this as kind of a collective effort. Any time we do something related to UI, all developers should be thinking component and try to extract whatever behavior or thing they are working on to make sure they can be reused across the various teams, reduce duplication, etc.

Ricardo - maybe the designers can mention to developers, this component here is going to be reused. Check for implementation being as expected.

Pedro - anything else to broadcast?

Anna - I have two small announcements. First one relates to anyone who has the mobile app installed. If you haven't upgraded from 0.9.33 (or earlier), please upgrade. Next Monday, in a week, the nightly build and the next release will not be compatible. You won't be able to receive messages from users on these versions in 1:1 or group chats.

Second, if you ever reported issues in Status-react repo, and you still think that your issue is relevant but there was no action taken in the last 3 months. It will be auto-closed by a bot (first marked `stale`), so if you think something is still relevant, please comment on the issue to keep it open.

Jacek - for Nimbus, we're going to be launching a client-specific testnet for the ___ chain. It doesn't do a lot of things but it does ___.

We're going to be running a whole bunch of nodes that will generate a blockchain. Anyone can connect to this testnet and try out Nimbus. If anybody is interested in playing validator or stakeholder in these two, you can get in touch with me.

You stake some eth and become a validator. They have some duties similar to what miners do today, minus the hardware. This is going to be a pre-alpha launch of Nimbus testnet.

The next thing is that once all client teams have their testnets up, we'll be creating a common testnet.

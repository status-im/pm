# Core Dev Call 25/02/2019

## Agenda

1. Follow up on better PR process
2. Pedro on state of Nix
3. Chaos Unicorn Day

## Transcript
[Transcript](transcript13.md)

## Call Notes

### 1. Sticker Market

(Ricardo) Researching price dilemma; there are a lot of controller actions in sticker market contract and trying to develop SC that can control these mechanism in a democratic way. Could use the voting dapp to get people to vote directly for the price by using multiple delegations and changing the architecture of how it works.

It's "kind of" ready, but not for a "multi-democracy context" yet i.e. it's ready just for sticker market. The price starts at 0, people vote to change it to some value and we can get going.

### 2. Tribute to talk

(Eric) There isn't much, but the non-native touchpad for Keycard is also implemented, so now we have two implementations of it. Let's rather merge the two for Keycard and TtT instead of building others.

(Jarrad) Barry has been doing economic modelling, and as TtT is currently implemented, it's very transactional. There might be a better way to adjust it: instead of putting up X tokens and having them relieved on intitial contact, it might be better to have both parties stake X SNT to each other until their relationship breaks down, i.e. only withdraw SNT at the time of "blocking" someone. More beneficial i.t.o. of locking up tokens in the network (relationships last longer than transactions), and i.t.o of spam mechanisms.

(Ricardo) looks like a visibility staking mechanism. Was thinking of something similar for the public chats and governance of moderators. There are private, group and public chats: so is Tribute to Talk the correct name? TtT should replace Patreon - content creators are mad about patreon burning people due to political bias and this is an opportunity for Status to build uncensorable funding mechanisms. Problem on content-creator approach is in using SNT, which is prone to volatility. Perhaps we can do immediate conversions to stable coins for this kind of problem more generally in the future.

### 3. DApp Store

(Ricardo) Developed ranking systems with a contract that feeds the system with ranking of DApps, which we can use in tandem with the sticker market, potentially. Not sure how to work with the bonding curves and whether that's worthwhile, so haven't done anything there.

(Andy) 1st Design Review delayed by changes to navigation tab in app. Blocked until that is resolved.

### 4. Teller Network

(Iuri) First PoC done with a whole lot of UI changes to make it more usable. We are redoing a few more UI pieces so that we can get to a fully-working DApp which can support multiple users.

### 5. Network Incentivization

(Ricardo) This should be multiple things, not one.

(Oskar) It would be best to discuss further in the swarm calls the exact details of that if Andrea is not around. [link to GH or calendar invite?]

### 6. Protocol

(Oskar) Will meet at FCC and please ping me if you want to talk with specific people there.

### 7. DAO

(Ricardo) Research on topic democracy: changing from sub-topics to have sub-democracies, which are more secure. The problem is: to include new actions/topics I would have to pass a quorum. So now making it such that we can create a new democracy each time, with parent and child democracies that allow you to change ome properties without having to reach a supermajority each time.

We can create propoals without democracies right now for testing, and that's where we are.

## Better PR Process

Document [here]() and in Discuss.

1. All PRs have tests.
2. Not promoting nightly as something for end users.
3. Reject PRs that don't have necessary tests.
4. Running automated tests when PR is marked ready.
5. Ask for 2 reviewers, and reviews done within a day.
6. Stop building the apk etc for all PRs.
7. Andrea looking into integration/headless tests.
8. Anton looking into more automated and iOS tests.

(Anton) After conversation with Jakub, we are not able to stop building the apks for every PR.

(Pedro) Only concern is the first point. I'm not really a Clojure dev so it might make it tougher for me to contribute. Hopefully writing tests in Clojure is easy to pick up.

(Oskar) It isn't that bad, basically ;P

(Pedro) Important to have good reference for tests so that we can use it in the correct way from the get go.

(Oskar) Is there something out there that we think we should remove?

[No response]

(Pedro) Just FYI, the e2e tests are already being triggered on review: that was implemented this morning.

## Nix

(Pedro) High level overview of Nix: a way of describing packages in a functional way. Read-only store located at the root of your drive, which can only be changed by admin. This gives us a lot of guarantees about that state in the machine, and allows e.g. having the nix branch running in the same machine side-by-side with develop. It works by setting up a special shell with the required environment variables that you need to build on top of the Nix packages.

I.t.o where we are right now: mobile phase done a couple of weeks ago. We were able to replace 3 different package managers with Nix. The hard part is to replace the desktop part of the dependencies, mostly because of Qt. Last week I was able to complete it for Linux, so right now we have Linux building and packaging and it's only the webview of MacOS that is giving us problems right now. Can hopefully get that unblocked fairly soon.

Once done, we can completely phase out the old way of doing things, merge the Nix branch and start using that exclusively.

Does anyone have questions/roadblocks?

#### How did things go with the Android SDK?

(Pedro) Not installed inside of Nix atm (installed separately though), but gives us the advantage that external contributor only has to do `make setup` and we can guarantee that it will work. Android SDK not a blocker and can be fixed/included later.

#### (Jacek) Do we lock down the versions that are installed?

Nix works by cloning a specific tag of a given repo. With brew, it's the same thing. As long as we clone specific tag or commit SHA, then you know that they are locked down. If you want a newer version, you replace the SHA. If you want a specific version of one tool and another specific version of another tool, that is hard. But we mostly want to focus on locking down the build environment here, not so much of a handpicking tool versions.

We could also have Status fork of the Nix repos (but not recommended). Or, in the recipe used to import Nix packages, you could possible fix that there.

**So everything uses the same version?**

Yes, basically. It must pull down exactly the same version that is committed on my machine to yours. If I want to build a commit SHA from a month ago, I am guaranteed that I will get the exact packages and tools used to build that version.

Nix is even more powerful than Conan (which I used to build Windows for desktop), so in time we should probably replace that too (though they are built on the same philosophy and way of managing packages, which is cool. Nix is just one layer up, basically.)

(Oskar) Anything else? There is now a transcript for the Dev call (thanks to a bounty!) if there is something you are looking for.

It's stored in the README [here]().

**(Jacek) Nimbus just synced past block 500,000 due to contributions from one of our bounty-based contributors who's been killing it lately. Things are moving along faster now.**

[_General jubilation_]

(Ricardo) It's been annoying to use Status lately, with bad connectivity etc. Why?

(Oskar) Anyone from core? Roman, Pedro, Adam?

(Adam) Update on mailservers depend on what kind of connectivity problem you're having. We fixed the issue with node ID's, but there are rumours of others too.

(Ricardo) Tried to run the mail server myself, it seemed to work, but also like it was saving the messages and not delivering them.

(Adam) I am available, so if you want some help setting that stuff up, let me know or find me and others in #status-infra where the people who know are hanging out.

(Oskar) Is that documented yet?

**(Adam) Not yet, we should do that.**

## Chaos Unicorn Day

(Oskar) We have the chaos unicorn day on April 1st: we shut down our cluster and access to infura etc. to test some stuff and it's up to you how your swarm prepares and handles it. If this is relevant to your swarm, this would be a good time to think about what happens when we fire-drill and turn off all the things we should be ashamed of.

(Ricardo) The mailservers in particular need to be able to handle this! Also, I noticed that other people can still receive my messages when the mail servers are not working, except that offline messages no longer work.

(Oskar) Also, we need bootnodes as well. You can run and add your own custom one, but we're not sure how interconnected the network is. This is also somewhere where a data sync layer could help.

(Oskar) We don't want this to be P0 or P1 such that people shift roadmaps to handle this. It's meant more as a test and a "fun side thing" not to overshadow the main work of delivering all white paper promises.

(Oskar) Anything else?

(Ricardo) We could discuss moderation of public chats, which we don't have. Also group chats: we could have more diverse types of group chats with democracy contracts that can control who can enter.

(Jarrad) Let's put that all into a discuss post...

(Oskar) Thanks everyone.

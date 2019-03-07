# Status Core Devs 11

Meeting Date/Time: Monday 2019-01-28 at 13:00 UTC
Meeting Duration 1.5 hours
YouTube Live Stream Link https://www.youtube.com/c/Statusim/live
Livepeer Live Stream Link TBD
Status Public Channel: [#status-core-devs](https://get.status.im/chat/public/status-core-devs)
Swarm List: https://github.com/status-im/swarms
Previous Notes and Recordings: https://github.com/status-im/pm

## Transcript

[Transcript](transcript11.md)

## Agenda

0. Prios

- Whisper availability (22%)
- Reproducible builds (19%)
- Fee structure (17%)
- ULC (13%)
- Arbitrarion (10%)
- Updates (8%)
- CC0 (8%)
- Automated tests (5%)

****Link to [Summaries & next steps]((https://notes.status.im/nlWvgHqcTR-_IKJEYyLGIw))****

1. Whisper availability inside Status DApp browser, which is something that would benefit the Teller Network as well as Gas Relayer. (Richard)

Current state: why whisper is not available in the web3 provider?
- Discuss post from September: https://discuss.status.im/t/whisper-api-as-http-service/470/8
    - Key comment:
    > On the one hand, providing an HTTP Whisper interface (or WebSocket even) via a web server which would be stateless, i.e. it would not store Whisper keys, is a nice idea. On the other hand, this is actually a solution that brings centralization, as opposed to running independent Whisper nodes. It’s a similar case which we have with Infura: it’s a very nice service from the user perspective but it increases centralization.


Viability for adding this functionality to the dapp browser (through the use of web3 or status_api)



2. Quick overview of the ongoing struggle to achieve reproducible builds, and what's been done in the past couple of weeks to get us closer to that. E.g.: (Pedro)

- the subtle changes to scripts, lock files and things like Docker image tagging, to ensure that artifacts don't get overwritten preventing us from building an old commit.
- the dependencies checker bot and how this will affect our day-to-day going forward, to ensure everyone's up-to-speed and knows what to do when they see an error in a PR? status-go sample

3. Fee structures for SNT utility (Rachel)

- How does Status leverage SNT utility to ensure continuance in the long term?
- Is increasing token price alone enough to sustain the project financially?
- Should Status take fees on SNT utility features such as stickers?
- What should be done with those fees?
- The current proposal is that Status either burn or recycle a percentage of SNT from every sticker sale, while the remainder goes to the artist.

Discuss thread: https://discuss.status.im/t/i-got-2-256-problems-but-a-fee-aint-one/957

4. ULC just got merged! ethereum/go-ethereum#16904

What does this mean for Status? Can we integrate it sometime soon?

5. Arbitrarion
Some teams have expressed need for arbitration mechanisms. What are the needs, what will this look like, who will implement it? Discuss and decide.

- Is arbitration relevant for your swarm?
- To what extend is it relevant? a) required for MVP, b) optimization, c) nice to have at some point
- Where are you at? a) investigating necessity, b) researching arbitration solutions, c) specifying solution, d) implementing
- What is your preferred solution? Why?
- Any relevant EIP's?
- Any potential partnerships?

(Let's skip swarm updates)

6. CC0

7. Automated blocking of PRs

(6 Updates (8%) 7 CC0 (8%) 8 Automated tests (5%))

8. Quick announcements

- Fosdem protocol workshop, Nimbus hackathon, also call next week

- 0.9.33 release — if there is something to add, please ping me until 29th EOD

- Status self update

- eth 1.x effort

- Rank call 1/10, optional comments

## Notes

### Whisper availability in Status Web Browser
- [igor] pretty easy to allow whisper API in browser, but security issues make us limit its availability
- working on other option but we don't know who will host it, if us, centralized
- technically solvable though
- [iuri] if we can get it just in the browser, it would make a big help (trivial part)
- [ricardo] what was the security thing?
- [igor] you can pretend to be someone else, we whitelist methods right now (everything is currently blocked) to keep people from accessing admin API
- [jarrad] possible to blacklist whisper public key of user logged in?
- [igor] sure we can do whatever we want in terms of black/white-list
- [iuri] we would need the pubkey for identity purposes
- [igor] sure, we might want to setup meeting with Corey to see how we want to do that
- [corey] what's being exposed, and is the user being informed
- [iuri] at minimum the user would have to confirm giving access to dapp
   - agreement
- [jarrad] bundle this in the same dialogue to access web3.  My major concern is the private key which is in whisper keychain being accessible by a dapp.
   - agreement
- [igor] these issues is why there is no whisper on infura
- [jarrad] we could propopse EIP but not put too much work into it, and focus on Status
- [ricardo] my concern is the use of the identity and what the dapps can do automatically
- [jarrad/igor] that access will be blocked
- [iuri] can't we just do the whisper object that we inject, and all it does it just forward the package.
- [igor] generate the whisper envelope yourself, and API is just forward envelope
- [iuri] that's what murmur does right now, this would be great for the status teller
- [jacek] if you allow too free access to API, we'll also be closing same upgrade paths for the future.  If we allow everything, we can't pull that back, because it's easier to give more than to take it away.
- [ricardo] yes, this should be well thought out
- [jacek] and making sure we nail down functionality and not do anything else
- [iuri] that depends on what level we're talking.  Whisper shouldn't care what is being sent.
- [jacek] as example, we aren't happy with mailserver.  If people actually start using them, then we'll have to support them forever.  If we change that beforehand, then we can move away from them. Just want to be sure we don't bake ourselves into a corner.
- [iuri] issue with mailservers is that they look like they extend the protocol
- [ricardo] call them mail nodes and treat them like that

### Overview of reproducible builds
- [pedro] our goal is to be able to build old commits and make sure they produce the same binaries.  Right now, our build infra is not setup for that. We have no control of some third part services that we reference for building.  It is very easy to someone to change what we reference, and then our old builds fail
- We can self-host our tools and make sure we host what we depend on with release tags whenever possible, or commit sha
   - commit SHAs fails if someone rebases and force-pushes
- I've built a bot to monitor our repos so if you do a PR that touches on package.json or whatever, it will prevent the PR and suggest what to do.
- There are a ton of repos that we rely on and it is not easy to go through them
- Please everyone, make sure if you touch something that dependson something else, make sure that you set it properly
- [corey] can you be more explicit on what people can do to help
- [pedro] the bot should catch things, but if there is a repo that will never be touched the bot won't touch something.  If you forked a repo, create a release for the specific commit that will be used, and link that in `status-react` with a release tag so it doesn't get changed.
- base reflex for yourself: ask yourself, can this be built this way in the future, if something changes, will the build process break?
- [ricardo] if we have a dependency, audit it and lock it there

### Fee structure for SNT utility
- [rachel] coming up in SNT Sticker market, the question arose if we take a fee for purchases, and what that looks like it.
- do we burn or take as Status to continue development?
- not sure if want to have a broad scoped discussion, or stick to sticker market alone?
- [ricardo] if we hae something like sticker market and curation markets, might have a kind of optional fee.
- [rachel] also have an option to donate % of sales to Status when publishing to market
- [jarrad] all these options are similar in implementation.  Sending some % to an address, so that means we don't have to come to a hard conclusion right now
- [ricardo] fee also has an affect on appeal to artists
- [rachel] huge advantage that people can contribute permissionlessly, but a userbase is important as well.  Multiple factors
- [ricardo] problem with introducing fees with no reason is a moral one. You are creating a concentration of power maybe, and could be unfair.  optional donation fee is reasonable
- [jarrad] I agree with there potentially being a moral problem, if we have something there, it should benefit everyone participating in the network.
- [ricardo] We can only morally charge a fee is if we filter, otherwise we have no reason
- [oskar] from implementation view, are their any blockers if we don't want to decide right now.
- [racher] this is impeding contract from being completed
- [oskar] we can make it optional, and ability to change, setting it to zero initially.

### ULC Release
- [oskar] ULC merged in geth, what does this mean for Status, can we implement soon?
- [igor] The problem with ULC is the same, it needs servers somewhere and who will run them?
- There are no reliable servers because of constantinople bug screwing up all networks
- we need to wait for that to be cleared up
- Also, ULC is not magic, you need to trust some nodes for it to work
- The question is how do you know whom you can trust?
- [oskar] it's a step up from only trusting infura
- [igor] yes but we have to run them
- [oskar] Pedro is working on some helpful solutions
- [igor] problem with validation, as it defers them to other nodes
- [ricardo] might be able to create a market or court system that allows for telling about misbehavior.  Nodes can handle this automatically
- [igor] this makes it a big project
- [ricardo] we can start by being the one that does it, then allow others to do it (decentralize it)
- [igor] yes but this becomes a full blown project
- [jacek] there is a proposal on discuss ([link](https://hackmd.io/6IhsF6zRSqmtggvNnp1sHQ?both#)) about that.  It would be a mistake if we run ULC servers as Status. Us running trusted servers is a big deal
- [igor] how is what we're doing now any different?
- [jarrad/jacek] it's the same but a stepping stone to something else
- [igor] that's why these things are not high on the roadmap.
- [jarrad] agree on workload and secondary step. Maybe just an option to do so if you want, if you're bringing your own node
- [igor] possible to implement in a relatively short amount of time, possibly as a test mode
- [oskar] ULC allows multiple nodes, so you could have semi-trusted setup by connecting to many and validating across them (3 of 5), but you can't do that otherwise

### Arbitration
- [hester] intention is not to go into depth, but making inventory on who is concerned and what swarms may need it.  Who is this most relevant for?
- [ricardo] best implementation so far that I've seen is with a ConsenSys project called kleros.  People trust random people to deal with their problems, answer in numbers
- We might want a copywrite (word choice??) claim to prevent certain behaviors
- Curration market may be a way to get over arbiration, but not in teller network
- [hester] teller network would be disputes around claims, sticker network would be copywrite around material
- [ricardo] also obscenities and material not wanted in the community
- obviously advanced, not in MVP, but end product would have it.
- [hester] anyone else see relevance of arbitration anywhere else
- [julien] [[Corey didn't hear this, reading email]]
- [ricardo] you can't take an action to change something in Sticker market
- maybe we look at kleros more, and set DAO to do arbitration
- [hester] if this comes up anywhere, it seems most reasonable to ask what Teller Network has learned as they've been looking most into it so far
- [oskar] other staking mechanisms could be looked into and be considered
- [ricardo] we should start implementing these report features within the app so at least we can have something.  Have expectation of what we need to solve.  If it doesn't work perfectly, it shows what we need to fix instead of having nothing
- swarm for opening arbitration cases and
- [oskar] common law type interface, start by underspecifying it and evolve from there, maybe

### CCO Re-license
- [jarrad] basically, depending on regulatory climates, distribution policies that we have to adhere to, it seems gmbh may be forced to create binaries in conflict of what our vision is about.
- that means we have to use our codebase into public domain, which is difficult actually
- if we relicense to CC0 it waives all things, but also makes it [[Corey didn't get this part]]
- so we put into public domain, and maintain a fork of it
- This requires **anyone who has contributed to the codebase** might have to sign some paperwork and get their permission to do this.
- [julien] does this have an impact on dependencies?
- [jarrad] not really, they're all copyleft in some form, and CC0 is compatible with that, public domain more so.
- [jarrad] its best if we attempt reach out to everyone, even if they're dead
- [pedro] I thought we already gave up the right to our work in contracts
    - only works for contractors
- [igor] do we need a dependency audit for this?
- [jarrad] naw, don't think so.
- [oskar] what would you like to see to get this done? how do you practially look at doing this
- [jarrad] make everyone aware of this, gather everyone's contact details and emails, then email them with situation and paperwork, and collect signatures as best as possible.
- [oskar] bounties contributors may mean situations.
    - we might have to redo work of these folks
- this is where decoupling protocol from implementation would be useful.
- [jarrad] reference implementation will be new codebase anyway (probably)

### Blocking PRs with automated tests

- [pedro] There was a period of time during pipeline of PR where we weren't checking if automated tests had been run
- I fixed last week that a PR starts in a failed state, and automated tests changes that, which helps a lot
- We need to change some things in the way the repo is set up.  Tried to do this with Jakub last week but we had issues, saw that we need to investigate further to step on other's shoes.
- ideally we would create a replica of status-react with automations, do tests there, and once we're sure it works, then we can deploy it
- right now at least we get visual indication that PR is not in a good state, which is already a good start
- [igor] this issue that when develop got broken, it wasn't maliscious, it was because the visual indication was that everything was OK when it wasn't. Just seeing that PR checks aren't green is quite a bit of movement in the right direction, enforcement can come next.
- [oskar] on this note, important to remember that this is a cultural shift, always make sure PR is in good shape, and please test stuff before you push it. Code review, block if not good.
- [anton] basically, we are not blocking everything from the beginning, it can slow is down.  Some things need immediate merging.  Right now tests are
- each force push removes statuses from PR, does it set things back Pedro?
- [pedro] I don't think so, but I can add support to look for force-pushes and recreate the status

### Announcements
- [oskar] fosdem this week
    - jacek talking about nimbus from scratch
- messeging protocol workshop
    - we'll try to make a hangout to join
- [igor] we are planning to wrap up next public release
    - if you have some pr that needs to be in there, please tell Igor or Anna by EoD tomorrow.
- [jarrad] I'm thinking about how Status can self-update
- [jacek] I'm particiting in ETH1.X, it's basically an effort to keep ETH1 driving while ETH2 is being developed, a copule proposals:
    - new sync mode
    - chain pruning modes
    - introduction of certain features that will allow a more nuanced accounting of storage
        - this will be used for potentially increase gas limit in future and reduce storage rent



    - if your interested, there are recordings and discussions on these topcs in AllCoreDev calls
- [ricardo] I think it is important discussion, that means using Smart contracts becomes more complex but is needed
- [corey] HackerOne campaign.  expect 5 bugs / month in about 2 weeks.





### YouTube

> Scott Stevenson: in California I am using this. http://www.courts.ca.gov/partners/317.htm
> Scott Stevenson: unfortunately its 3000 pages.
> Scott Stevenson: the same rules of laws would apply in an arbitration setting.

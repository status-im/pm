0:00 - 1:00

Oskar: Welcome to the 12th core dev call. I just thought we'd start by letting everyone go around and let everyone sort of speak their mind about what they think the purpose of this meeting is and just make sure we're on the same page so it's as useful as possible for as many people as possible. So maybe we can start with Eric, what's your take on what you would rather talk about and not talk about during these calls and then we can go around.

1:00 - 2:00

Eric: Personally what I like about these calls is that it helps me keep up to date about what the other teams are doing now that there is a bit more separation between the different areas of development. I don't know what I expect more or less from it it's already valuable enough for me. I guess on my side I'm looking into participating more because so far I have not contributed much to these updates, and yeah that's all fine.

2:00 - 3:00

Oskar: Alright cool. I guess Julien? Someone have something specific they want to say? Just speak up especially if you don't usually speak up.

Julien: I will say something, I was supposed to talk. So yeah I feel like there is kind of a redundancy between the various calls we have and channels, so I guess what I expect from this call is to have maybe a very high level understanding of what every swarms is working on but no so interested in details in general I guess.

3:00 - 4:00

Julien: Eventually if there is some decision to be made across engineering, like things related to pull requests or workflow in general, that type of things, otherwise we already have team calls so we can already discuss technical details per team. So yeah just in general if we could have shorter calls, I think it would make sense.

Oskar: I guess we're too many to go through everyone but does someone else have something, do people generally agree, do we want to have swarm updates in these calls or not or do people have other views on what these calls should be about?

Pedro: I think one area where these calls might be good for is for announcements if something changes, could be something related to continuous integration or some tooling aspect everyone needs to be aware of.

4:00 - 5:00

Pedro: We might discuss this synchronously, both before taking the decision and after to elucidate some aspects. It's nice to have this synchronous aspect as long as people voice their opinions and concerns.

Jarrad: Yeah from my side I completely agree, if there's something that's application wide or something that needs to be discussed or made aware of by all teams this is a great forum for it. Aside from that, any ways that we can improve our workflows or what we know is working well, as well as keeping everybody up to date on the high level is pretty valuable.

5:00 - 6:00

Oskar: Does anyone disagree that we should have high level forum updates in these calls?

Jarrad: I disagree if it's covered in the recent Town Hall or in some other form unless it's absolutely necessary for other people to know.

Rachel: I think it's too repetitive. There's information in a lot of different places, but again if it's something that's like application wide or has an effect on other teams that can be important to bring up.

Oskar: Alright cool any other thoughts? Another question I guess is to what extent do people think people think the focus of this call should be purely technical versus maybe discussing things that might be slightly identical so one example would be things like fee structure and these types of things which might touch more on more product business design kind of things, do people have any thoughts on that?

6:00 - 7:00

Barry: I guess it's more of a question, if we don't discuss those things on this call, where would we have a discussion about them, because the general town halls are not really discussions, they're just sort of an update, so if we don't discuss those things here where would we discuss them?

7:00 - 8:00

Igor: Yeah I agree and one more question, we don't have a lot of things to discuss sometimes so I don't know if we need to filter it that early, because it's not like each dev call is four hours and we can finish it, so everything that seems more sensible and related to these discussions company wide it's okay to be here, as long as the timing is ok.

Jarrad: I really enjoyed most of the previous devs call, where we thought we had too many agenda items, but we kind of compiled them together and voted on them, and then we just went thought them all, I thought that worked really well, unless anyone disagrees?

Igor: Yeah if anything we have too little to discuss, not too much, but the previous one was good yes I agree.

Jarrad: Yeah I agree.

8:00 - 9:00

Oskar: Yeah cool. I guess unless there is any other thoughts we can move on to our actually meeting, if anyone has any thoughts on ways these calls can be more effective, please don't hesitate to raise it and we can talk about it. Does anyone have anything else they want to add before we get started? Ok cool, the first item is around better pull requests. The context here is that we had this discussion a few times, but we tend to have very long lived pull requests and it's kind of problem, because it leads to a lot of rebasing, and you don't have a lot of integration and so on. Previously we decided we want to use feature flags a lot more liberally which means you can hide features and only have one pull request we actually toggle on screens, but it seems like we have fallen out of practice with that. So yeah any thoughts on that or any additional comments.

9:00 - 10:00

Andrea: I don't think we have fallen out of that, it's just sometimes the rule is if it touches existing functionalities then it cannot skip QA and cannot use feature flags, I mean you can use obviously, but if you are fixing a bug you want it to go live straight away, you don't want to keep the bug. And so I feel like the subset of features that we can actually use feature flags is a bit limited, and so I think that's one of the problems. Also another issue is that when there is the release, PR's accumulate very much, for good reasons. I think it's actually the main problem.

10:00 - 11:00

Andrea: If there is a release, you know, all hands on deck. Everyone is testing, you can see now how many PR's there are in the testing queue. That leads inevitably to people adding code to existing PR's rather than creating new ones, because it's so difficult otherwise.

Julien: There's the thing related to big PR is that it then becomes really hard to make a good review of the pull request. If I have a pull request with 35 file changes, I know it will be ready hard to just invest time and energy to make sure I provide good feedback, so eventually I guess most people just quickly glance at the pull request and then accept it or just make random useless comments. So I think that's kind of the main issue here.

11:00 - 12:00

Julien: In my opinion I think it would almost make sense to prevent pull requests bigger than 10 files or something, otherwise it's really easy to create an excuse to just create a bigger pull request. It's kind of a vicious cycle here.

Pedro: I think we should be able to ask ourselves regularly, does this PR need to be this big or can I break it into smaller pull requests. I think there's a lot to be said. If all your colleagues know that your pull requests are small, they will be more keen on quickly responding to pull requests. So if we knew that all those pull requests in the queue are small, I think things would be much more smooth.

12:00 - 13:00

Andrea: But this relies on the assumption that these PR's are merged in a timely fashion. If I split my PR in seven PR's and each PR takes several days to get into the code base, then no one will every do that, because it's so long.

Pedro: Yeah so there's that problem, but maybe at that point maybe we could try to identify where the bottle neck is, and see if we can do anything about that. Whether it's testing or continuous integration or people not responding.

Oskar: I Agree about what you said about small PR's. I think it's also a question about how you code. Maybe the easiest thing to do is to change code. Like you have some function then you make one different argument you want to change the logic of it.

13:00 - 14:00

But there is a different style of coding where you don't remove existing code at least initially, instead you create new code then you can isolate the behavior. Even if it's a long multi screen flow, you can still create new screens and add comments saying these should be gone, then you can have just a simple flag in maybe one or a few places, then it doesn't matter if there's a release as long as everything compiles it's not actually being called anywhere. I feel like we're not being creative enough in terms of adding new code and just isolating this is exactly how it's going to be called, then just having a small PR that just toggles a flag or changes stuff, then you can always remove code after the fact once you know the new path works perfectly.

14:00 - 15:00

Andrea: I don't fully agree with you. I understand what you're saying and I know that's possible. I think any of us have done that to some extent. We discussed this. But the fact that we keep having some problems, certain problems, is also because the system we have in place does not help you with that. I think there are some underlying issues that we are now addressing, now we're getting to where the automated tests are much more reliable. I am for some PR's regardless where it should skip QA, regardless if they have live things or no. For example I fix a bug with the mail servers, and you know it has some impact on the code base, so it should go through manual QA, but it's a super small fix and I don't think it should through manual QA.

15:00 - 16:00

Andrea: So I think we should relax those rules because certain PR's should just go through even without having manual QA because we make the judgement call the impact is so small it's more useful to have inside. Bug's get through I mean we see, like Nightly has loads of bugs, and not because manual QA is doing a bad job, quite the contrary, but bugs do get through. So I think we are being too cautious on that side.

Igor: I tend to agree with Andrea here because if you want small PR's, that means we'll have more PR's, that means if we have manual QA on each PR, it will just take forever. That's one of the reasons you want bigger PR because you want all the feature to be tested once. Yeah instead of five or six times. So maybe we should relax a little bit on the PRs.

16:00 - 17:00

Pedro: I guess those two things go hand in hand. If it they are smaller it becomes easier to understand and to reason about them, and see if it makes sense to do manual QA or not.

Igor: Yeah so we should probably relax on the smaller PRs. If it's just one line change that's regression scope it's pretty obvious, especially if it's already covered. Imagine if you change something that if you do it wrongly then it breaks all the chat functionality then I'm pretty sure auto test will find this.

Oskar: I think we had this discussion a few times, and the conclusion has been that we need automated tests to be baseline reliable and they should block, and once that's done then we can relax this cycle.

17:00 - 18:00

Oskar: Now I believe (automate?) has its own dev state, so I guess what's stopping us from doing that now, being more quick? The goal would be if you have a small PR you should be able as soon as (automate?) has run people make a judgement call and a code review then you should be able to merge it so you should have a quick feedback cycle. Is there anything blocking it? Does QA have any perspective here?

Anton: There is a lot of problem from having a lot of small PRs, when a PR makes some changes into the product I need to update some tests, right now I have a queue of PRs like three PRs because I can't update all of them. It's really hard to update big PRs for example (volume tree design?) PR where you need to update like 100 tests, but it should be easy to update small PRs from after test perspective I agree to have small PRs makes sense.

18:00 - 19:00

Igor: Yeah for some of the smaller PRs they don't touch UI so maybe we won't have to update anything.

Oskar: Maybe I'm naive or something but talking about this specific wallet thing, as an example of a big PR, but to me that's an example where you could leave the thing as it is, and then design the new screens, and literally have a flag that's a dev flag, then all these partial problems would already be in the repo and then it would just have a tiny PR where you would actually activate by default or where you would remove the old screens and that's where this additional work would be, you wouldn't have this 40 file diff and this like huge update job. Is there a reason we are not doing it that way? For this specific example, and I think it generalizes to lots of other PRs.

19:00 - 20:00

Iuri: Can you repeat that part Oskar?

Oskar: No I mean like if we have a PR that changes a lot of UI flows, why are we changing the flows as opposed to adding new flows and then toggling off by default for using these new flows, then you would gradually get the changes in through codebase, and you would decouple these sort of automated testing and you would just have one tiny PR that would toggle the flag on by default, and that's where the QA work would be and so on.

Julien: But I guess that's mostly related to mindsets and changing the way we work but actually yeah it makes sense.

20:00 - 21:00

Iuri: I have some thoughts on this. On the Embark thing, Teller and so on, we really try to keep as few PRs open as possible. One thing I really hate is work in progress PRs, and the reason is because typically those PRs are done to give an illusion of work, and they just tend to hang around and need constant maintenance. We actually have a rule that we don't allow work in progress PRs, the only exception is for things like bounties and things like that. And even those you can see that people would do work in progress PR with something copy pasted from stack overflow to give illusion of work. So if there is a PR open it should be with an intention of merging ideally in the same day or in a few days, depending on what the PR is.

21:00 - 22:00

Iuri: The longer the PR is open the more work there is. If the PR is open for a few months, it becomes very hard to maintain. You need to constantly rebase, constantly keep up with changes, and it becomes more likely that it's not even going to be merged. So if the PR is very old you might as well close it and the person then should open it when they think they are actually ready to be merged. The other things in term of code reviews, it's important that the code reviewer be reasonable. Sometimes the code reviewers have a tendency to ask for changes that are not related to the PR itself. That should not happen. If someone does a PR for example for a feature, the PR should be related only to that feature, so the reviewer shouldn't ask well since you touched this file, you might as well refactor the whole thing.

22:00 - 23:00

Iuri: That shouldn't happen if there's unrelated changes that should just be done in a different PR. Or if an idea feature or even if a new bug is found within the context of that PR that should also be done in a different PR. So it's important to keep things as isolated as possible, just to reduce that mental workload. The more PRs there are the worse it becomes. So ideally the workflow is really to aim for most PRs at least to be merged. Sometimes that's not possible, sometimes there's big changes in the codebase and things got delayed and that's fine.

23:00 - 24:00

Iuri: In my opinion having a PR more than two weeks, you might as well close it, it just becomes a maintenance nightmare. If there's a PR open that have no intention to merge in the same day then it's not really ready to be reviewed in the first place.

Oskar: Definitely agree, just curiously have a look at status react and look at the PRs that are open that have been open for a long time, the longest Embark PR is 11 days old. They have nine open, and they are more active than status react. So I don't see what's so special about status react that we couldn't do the same thing.

Iuri: If I might just add a quick thing, the reason that you see some of them, five days old and eleven, it's because we did a big change by moving to (learner?), and that's one of the examples. There was a big code change so that can delay things, but other than that we really try to keep it even less than that.

24:00 - 25:00

Andrea: I don't think the comparison is a fair comparison. I opened a PR 17 days ago, has been reviewed, and hasn't been selected for QA.

Oskar: This is not like a blame game, it's just the process is wrong, there is something wrong in how we do things.

Andrea: But work in progress PR is not our problem, because we do open it, but I only open it just to create a build so I can get the artifacts, on jenkins, I don't think anyone uses it as a system, like we open a work in progress PR when pushing code, it's just the fact we want to have builds.

25:00 - 26:00

Igor: Yeah it's just the simplest way to get CI builds there. I've been doing different types of CI environments, and it's very hard to compare a dapp or anything written in pure javascript where you can make auto test that run in three minutes. I've been working on like a protocol base that had like three thousand end to end tests, and it was this all cycle of running them for five minutes on my machine, and you can't compare it with like test end to end mobile app that you can only run on simulators or real devices that are run in the cloud so you have to upload it somewhere else, there a lot of things that can go wrong.

26:00 - 27:00

Igor: And our tests, they run like 20 minutes, just for end to end tests. So it's very different, it's very simplistic argument that if it works for some code that it will definitely work for another. Tuning sucks for all the mobile things, all the CI tuning really sucks.

Julien: So actually I think it relates to discipline, if you create a pull request in my opinion it's your responsibility to have it reviewed, to make whatever changes, to have it tested, and ultimately merged, and yeah I guess we are lacking a bit on that side.

Igor: It's not everything that we can do there right now with the current workflow, but I agree that we probably should relax things on manual tests and instead of having the skip manual QA label maybe we should inverse it and just put a label if we think that manual QA is needed for this PR.

27:00 - 28:00

Igor:  And by default just put the small tests passed just merge then and see what happens. But I'm not sure that's exactly viable to just close all the PRs older than two weeks and think that's a viable process here.

Oskar: Could you explain when you think it makes sense to have PRs open for more than two weeks lets say?

Igor: Well when we are trying to release one version for four weeks for instance, and we had to release at least two hot fixes along on the way for different cases so it was like zero QA resources for almost like two weeks. Some of the PRs will definitely stay longer.

28:00 - 29:00

Pedro: That's what I'm curious about. For example you compare to Embark, I'm not sure what the QA process looks like for embark, I don't know if this is also an impediment for them, because for us, at least during these last two weeks, there was a shortage of QA resources for a lot of PRs.

Anton: Basically yeah we've been focused on release for last two weeks for sure, and this is why we have that queue, first it's lack of QA resource, and complexity of our application, when you have iOS Android Desktop and several platforms for desktop right you need to make sure a PR isn't breaking any piece of it. The biggest problem I think here is the complexity of the whole product, the whole set of things that needs to be tested.

29:00 - 30:00

Anton: Of course we can skip manual testing for some PRs if they change little but we should wait for tests to run at least, because we had bad experience with reverting several PRs during these two weeks, so just keep calm and wait for tests to pass.

Igor: One more issue is that our tests are essentially only on android, so if you break something specific to iOS or specific to desktop, looking at manual PRs looking at automated tests we'll probably lose those changes.

30:00 - 31:00

Igor: We also built like, HPR touches usually like five platforms which is well not a very simple thing. We can improve for sure, but it's a very simple point of view to think that will be just the same way just like any web app or even web3 app or something like this, we will never be at the same speed.

Oskar: I feel like that's not really giving embark credit, because, sure it has all it's platforms and so on, but it sounds a bit like there's nothing to learn, which I kind of disagree. If there's something we can learn from how they work, is there something we can change and if so what would that be.

31:00 - 32:00

Oskar: For example in terms of the QA process or how we block things and so on, or related to flags I don't know. Is Goran here maybe?

Barry: I would like to add just one counterpoint to what Igor just said. When you see dapps that are developed quickly, I don't think it's because of the tooling, it's in spite of the tooling. The tooling right now for dapp development, it's still very raw. It's definitely not at the level of more traditional development. So when you see dapps developed quickly I think that's in spite of the tooling not because of it.

Igor: I mean it depends on what you call the tooling. Maybe we have a tooling for iOS and Android to run tests but if this tooling fails 20% of the time for the reason because again vendors platform vendors didn't make a good enough tooling.

32:00 - 33:00

Igor: They might put a checkmark that they have this or that, but trust me the tooling there is just...  if you look at the simplest example of what to test, it's any kind of cloud service, and I don't see any point why there shouldn't be good end to end test coverage that runs very quickly, and the tooling there is super mature. It's a very rare case when you actually have good CI process for mobile apps in general. So the point that we have end to end tests that don't fail all the time is already a huge accomplishment for our team, because I haven't seen this in quite a few companies. We can tell facebook has them. And facebook doesn't have just one automation engineer, they probably have a hundred times more.

33:00 - 34:00

Igor: So of course we can just hire more people, or just focus more on automation and will help, but yeah it's totally different. And also the tools I use for automation are not the same stack that we use for development, so it adds more languages and frameworks to our mix, it's like we don't have enough.

Iuri: So two questions. From what you guys said, the reason for the PRs, one is to trigger the CI and get artifacts and so on, and the other reason that they stay longer sometimes is because they are waiting for release. So they can't be merged because for whatever's in the main branch needs to be released first.

34:00 - 35:00

Igor: No not right. The right thing is that each PR is being tested manually, and if all the manual QAs are busy testing the release, and we have 3 QAs, if everyone is testing the release, 5 platforms, then there is no one to test these PRs. It's not like we don't have a release branch, we don't have a problem of merging something into the develop or master while release is happening, it won't affect it, but we just don't have the human resources to test in our current, probably the biggest thing there is that we don't have any small testing on platforms other than Android, because otherwise if you would have it it would be much easier to just everything like automatically to make that app at least doesn't crash on other platforms.

35:00 - 36:00

Iuri: So on that regard, because when Oskar asked what is the reason for PR stay open for two weeks, and the releases we specifically said was trying to go out for two three weeks, what was this referring then?

Igor: That was referring that for almost 3 weeks there were zero QA's available to test.

Iuri: Ok in that case, can't the PRs just be a smoke test for that particular functionality, or is it already like that?

36:00 - 37:00

Igor: I mean we have for Android but I guess for other platforms it wasn't done just yet. Again we started doing something for iOS but there was this restructure in the middle of this and I think we just ran the first test and the person who was doing this was laid off so there was no on to continue.

Oskar: So how can we have manual QA be less of a bottleneck without adding additional resources, is there anything we can do?

Andrea: Many things. We can move from a model instead of testing each PR separately, we test nightlies.

37:00 - 38:00

Oskar: That's what we decided before when we decided before, when we introduced automated tests. That's why it was such a big push to having them be hundred percent passing, that was the reason first, I agree with you, so the question is why are we not doing that?

Anton: First of all we don't have the capacity to cover every single scenario which is headed by development team. For example when we added the block user, I have three PRs in queue to be reworked in order to be passed the whole set of tests to reflect actual new behavior triggers, and I just don't have any time to cover that feature. These blank spaces might be covered manually, but we are planning two covers of tests in future but that future never comes because more and more PRs are coming.

38:00 - 39:00

Anton: The same for iOS we have started iOS we've been working on it and in future we are going to have iOS support but we also need to add battery consumption support, we need to add network consumption support, extra performance tests, it's just never going to be done because we just getting more and more PRs, we just don't have the capacity to cover everything that flows.

Oskar: We don't have to cover everything. This is also because you have feature flags, because if you introduce a whole new flow and it turns out when you're testing nightleys it's not idea you can turn it off quite easily if you do gradual changes and you don't just change things all the time.

39:00 - 40:00

Oskar: I don't know maybe to me it sounds like an excuse to say we need more resources to make this work I don't know if I'm buying it.

Iuri: I have previous experience working on large project, if there was bugs there would be big consequences, there is money on the line and so on, it can be a big issue, what happened was that that particular type of workplace was kind of like a blame game type of workplace, and as a result the testers were too much, the QA was excessive basically. I'm talking about if we change the color of a button they would still do the whole testing.

40:00 - 41:00

Iuri: That was because there was distrust with the developers and because then the management would blame them essentially if there was a bug. Then they would blame the developers and so on. So to attempt to reduce this I try to break the software more into different pieces and introduce acceptance testing and this kind of thing just to increase the confidence and the trust between the QA and the developers. So my question is is there that sort of blame game here, like if there's a bug is there a blame game that causes the QA a bit more excessive than it should be? Or that's not an issue at all.

41:00 - 42:00

Anton: No there is no blame game and we are not doing regression testing for PR, all the regression testing is done by automated test, we are testing only the feature introduced by the PR and possible errors which might be affected, and we are not spending 5 hours by retesting each possible flaw in order to pass testing for the PR. We are doing regression testing only for releases and automated regression testing only for each nightly, it's a much more extended set of tests than running against PR, but there is no like over QA actions against each.

Andrea: 

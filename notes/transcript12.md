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

# Better Pull Requests

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

Andrea: On a good day, if your PR gets reviewed in half an hour, an hour, its the time to ping the developers. If it goes straight to the QA an hour and it's in.

42:00 - 43:00

Andrea: On a good day it takes very little. It's just sometimes they pile up sometimes especially during releases.

Igor: Maybe the problem is with the releases then and not the PRs themselves, because if they work normally on normal days, then maybe it shouldn't be those all hands on deck release testing maybe it should be just longer, we should expect release testing to be much longer. But then for people to keep looking at PRs... it's also a bit weird because sometimes these releases, why they were hands on deck, because first time there was this inferior issue that they communicated super poorly and it turns out that... we had to upgrade our project IDs essentially like very quickly within a day, but it turns out that it wasn't necessary.

43:00 - 44:00

Igor: The second time there was some crasher if I remember correctly that we found out internally, then we had to fix it before it went to any public channels, so it was our quickest release, it was like six hours between finding a bug and pushing the release button. It was super quick for a mobile app. And then yeah and we were trying to release at the same time another release that was supposed to go with some changes for ETHDenver, so it was a little bit of perfect storm last two weeks, so maybe we should think about releases a little bit more.

44:00 - 45:00

Igor: If we test on the nightlies for instance, then no one should install nightlies for desktop unless they are tested. At least no one should install them and think "oh it crashes and it's best" or something like this because we don't have auto test for desktop just yet. So it's a little bit hard circle to square but yeah.

Oskar: One suggestion because we've been talking about this for quite a while so maybe if someone who hasn't spoken about this topic has something they want to add and I think we'll probably go on for a long time about this but yeah anyone who hasn't spoken and wants to say something about this topic?

Julien: So I wanted to add one small thing, we focus a lot on testing and QA but also realistically we lose a lot of time during the reviews, we need more people doing reviews, and once you create as a developer a pull request it's not done, it's just the beginning, so you have to be on top of things and talk to people and push things.

45:00 - 46:00

Eric: I was thinking something that might help also is to limit the number of requests for review for three or four every time so that it's clear to everyone that when you're asked for review you really need to do it otherwise the PR is going to be stalled. Often there is PR with a lot of reviewers but only two are needed to actually pass, so maybe we just need two or three reviews always instead of six or seven.

46:00 - 47:00

Jarrad: Can we turn this into a Discuss post, just so we can keep this conversation going, if anyone can present any more ideas on how to fix it.

Oskar: Anyone who feels particularly strong about this or has a specific view of how they would want to change things or what the specific problem is that wants to do this?

Andrea: I feel that we should relax minor QA and we should move to a system as discussed, testing in the nightlies or maybe features in batch, essentially give more responsibilities to developers.

47:00 - 48:00

Andrea: To push code without bugs so that, it's on them to make sure the code is up to standard to be merged rather than just throwing the PR to QA.

Igor: So should we write a discuss with at least all the problems we see and all the possibilities and probably come up with ideas and solutions how to fix it and what to choose.

Andrea: Yeah I'm happy to do that.

Oskar: Yeah I agree and it would be interesting if someone wants to argue against that viewpoint because I agree it does make sense to test things in nightly. Especially if you isolate the features so you can turn them off and so on. Anyone else who hasn't spoken?

48:00 - 49:00

Jarrad: Just a question, is it possible to pass arguments to all the platform binaries to essentially switch flags off and on without having to rebuild the entire thing.

Igor: Yes to some extent. We can always do them in settings. Because there is still some code in Clojure that reads this into some kind of console. Maybe with restarting the app it should be possible.

Oskar: I think we did that for some things. You can just force restart the app.

# Acceptance criteria and design review

49:00 - 50:00

Igor: So they are not like C++ macros or C macros when you don't compile some part of code.

Oskar: I don't know if we still those flags but we used to have some flags but I guess most of them aren't.

?: There are flags.

Oskar: Okay cool. Are we happy with the state of the topic and then take it up on discuss as well as next call? Alright, awesome. I guess we had also acceptance criteria and design reviews I don't know if that's under the general banner of better PRs do we want to touch on that or go to the next one?

50:00 - 51:00

Hester: So I'm not originally a person who put it on the agenda but my thoughts are just in general when anything impacts the UI to add one of the designers as a reviewer just to check whether the implementation fits with the original designs, that's all i have to say about it.

51:00 - 52:00

Oskar: I think there's another slight addition to that in the sense that, I'm not sure if in figma we can do responsive layouts or not, and if that would be useful for developers if that's the case, because my understanding is that there's minor design tweaks that might be able to be resolved because they are not entirely pixel perfect in a real world application.

Hester: I don't think that automatically happens in figma, but obviously it's worthwhile for the designers to check the responsiveness, so they can probably create a view for different devices or layouts. That's definitely something that needs to be done. If the designer is added as a reviewer it's a communication thing they'll get a ping so they can check when there are deviations or when something might be different from the original design.

52:00 - 53:00

Oskar: Do we have any specific dev or designer on this call that had some issue that felt there was some friction in the process in the process between PR and design review that wants to speak up?

Rachel: I've just been observing a lot of back and forth on PRs where the design doesn't match exactly with the figma designs, it seems to be taking a good about of time for the designers just to be double checking things and some of it seems to be easy to fix but yeah I'm not quite sure what the friction is.

Oskar: Is there a specific PR you were thinking of, maybe I can help if someone is on the call.

Rachel: No it's more general there's been at least 3 or 4 where there just like long comments from ? it's like things that have been emphasized.

53:00 - 54:00

Hester: I definitely realy hope that the figma workshop helped on that as well, because hopefully it makes it a bit more clear where to find these specifications. I know Eric already did a lot of good work on implementing components, and Andrei as well. I do know the designers try to stick to the components that are already there, and they try to limit introducing new components, so I'm hoping let's say that imbalance between implementation and design will also phase at some point because of the use of components.

Rachel: But if there are no developers or designers who feel like this is a problem right now it's probably not a problem.

54:00 - 55:00

Jarrad: Another potential issue here is, we just spent a lot of time discussing QA sort of contributing to longer PR times so adding design reviews to this we should be mindful of that also, could add more time to these things.

Barry: I sat in on the figma workshop, but one thing that's a recurring theme, there seems to be this continuous recurring thing of this one disconnect between designers and developers which is the components for the way designers lay them out in figma is different from the way developers implement them and so really to developers it seems like figma is really just pictures that they just have to eyeball to come up with responsive designs in the application.

55:00 - 56:00

Barry: To me it's almost puzzling, that there doesn't exist a solution out there, because status is not the only place where this is an issue. There can't just be a solution out there that allows designers to lay things out using responsive formatting so developers can plug that in, it just seems like such a big need I can't imagine it doesn't exist out there.

Igor: Well there is a huge discussion in UX community about loading up HTML, and should the designer use HTML to do that, so regarding what I see. But I've seen these things for mobile before, there used to be this course composer that works quite well if your platform is iOS or Android. I guess your best bet is the Google's responsive toolkit for material design toolkit for like HTML essentially for the web pages.

56:00 - 57:00

Igor: I think this question is very pressing right now, but maybe I'm already outdated on all this.

Barry: Well figma, it feels like the layouts, they already lay it out using CSS, they just lay it out using fixed style css right like exact number of pixels, which if you change the screen it might look bad on a different type of viewport. Figma doesn't let you lay things out using flexbox or grid or something like that so that it always maintains those proportions regardless of the view port that it's displayed on.

57:00 - 58:00

Rachel: Is that definitely not possible on figma, or percentages at least?

Hester: I think there should be a specification in DPs should be possible rather than pixels.

Oskar: Do we have any designers on the call? No, I guess we don't.

Jarrad: I know a line of thought that is worth exploring is maybe how we can reduce the barrier between code and design. So for example many moons ago when Andrei created the fiddle, the Andrei designer got really excited because the Airbnb design house was working on this basically automatic code generation. I realized this out of bounds of our capacity at the moment but it's definitely worth keeping in mind.

58:00 - 59:00

Igor: I mean one of the goals of this component based design was to simplify this process without having the code generation, because if you have 20 standard components then they can be reused in both designs and code, this should simplify things. This is why Andrei had the idea to standardize our designs to sort of reduce them to a small subset of all the components that are reused all over the place.

Jarrad: Forgive me, how far along are we in the process? Is largely the UI component based now?

59:00 - 1:00:00

Igor: I don't know if it's component based yet, but new features that we are implementing, I think it's Roman and Eric and others, they are just trying to also like either tweak or create those components that are in those figma documents. They are usually on the top if you look at the figma layouts and you scroll all the way to the top above the screens they're usually components and their states and things like this. Not that many of them. I don't know how many of them. I know that the bottom sheet was implemented by Romand for the cellular sync options but the other I wasn't tracking as much.

Jarrad: Okay so it sounds like it will naturally improve over time.

Igor: Yeah that's what we thought, we won't have any time specifically to implement those or it would look weird on the roadmap to just spend time to just refactor components, so the most viable idea would be to just whenever there is a new feature that requires some components they should be implemented and then the next feature reused.

Jarrad: Yeah makes sense thanks.

1:00:00 - 1:01:00

Eric: But we need someway to synchronize on which component have been implemented already because I've seen that list items have been implemented twice already. Not necessarily the same aspects of it but there is some overlap.

Igor: Maybe we should just invite Andrey the designer and just talk about it on the next core dev call to just have this discussion and see what's already been implemented and what not.

Eric: Or we can do a conference specific call quite short where people involved so we discuss what has been done and how we could reunite the efforts.

1:01:00 - 1:02:00

Igor: Yeah that would be nice. So yeah we can create a separate call about what's the progress on this and who's doing what.

Rachel: I can set something up.

Igor: Thank you.

Oskar: Alright I'm unmuted ok cool. Anything else on that one or should we move on? Cool so protocol discussion and Q&A and suggestions and so on.

1:02:00 - 1:03:00

Oskar: So the context of this is that we gave a brief presentation at town hall but there might not have been enough time to have a discussion about things and coming with thoughts and questions and so on, so this is just a space where people get some thoughts, feel free to share them now, or questions or anything.

Petty: There's a recent message I think from (Fajma?) at the workshop that says she's gonna have a draft of a summary, I guess a summary article of the whole workshop relatively soon, so we'll make that available to everyone to see what happened there if they're still kind of not up to date on things.

# Navigation/Push notifications

1:03:00 - 1:04:00

Oskar: Alright cool, yeah okay, so we don't have anything specific then to talk about right now. Eric you had some suggestion about push notification navigation, is there something specific you want to talk about.

Eric: Actually it's about notifications and about navigation, not the two together. It wasn't necessary for this call it was just that I need to talk a bit with Pedro to figure out what we can do with notifications especially in the case where you block a contact that was in your contacts and to whom you send your SEM token so you want to be able to block this person so maybe change your token or something. And the other one was navigation.

1:04:00 - 1:05:00

Eric: Maybe just next time, because first I need to look at it myself to see how to do navigation for some screens where the origin is different like the profile depending on whether you come from the chat or from the profile screen, user profile screen, yeah so I don't have much to say for this call.

Oskar: We talked briefly about the push navigation flow on the core backlog call I think.

1:05:00 - 1:06:00

Oskar: It's kind of a bit complex to write because logically what you need is you need functions to register it, because it's tied to device and not to a person per se so really to do it properly you need logic to register and deregister devices, and then that should be triggered when you block someone and also when you log out and all these kinds of things. In a traditional architecture that would require a central server, and previous proposals was based on sort of this all in one mail server which might not be the right abstraction so I think it requires quite a bit of thought to make this in a decentralized fashion. It's not a simple problem.

Pedro: Regarding blocked contacts, we can ignore them at the recipient device. Right now we have complete latitude over what we display in terms of push notifications, so if we receive a push notification and we look up in the database and we see that it's a blocked contact we can decide to just let it fall and not show anything.

1:06:00 - 1:07:00

Eric: Yeah that's what I did already but I think the issue is when the database is locked and then you get a notification and when you log in you have nothing and you don't know why.

Oskar: How does that work on iOS if the process is suspended, how is there full control. I mean it's awesome if that's the case I just don't understand how that...

Pedro: Right now it doesn't. So yeah iOS doesn't have support for at least in the react native firebase documentation, it says iOS doesn't have support for waking up the app and doing that processing so what is recommend is to once you start up the app then you process the push notifications and you show them to the user.

1:07:00 - 1:08:00

Igor: I was trying to take a look on the next iteration that will work on iOS so there is a possibility but it should be rewritten in native. Because obviously the reason they can't wake up the app, well they can wake up the app but for five seconds and it's not enough time to spawn up the javascript engine and load our closure script there and do anything useful there. So this just just be native. Because then you can theoretically open a database or something. I think the list of blocked users, like the blocked keys, we can just store them in whatever shared preferences or whatever, why do we need to encrypt them even.

Pedro: Yeah they are already anonymized, we could just store the anonymized keys.

1:08:00 - 1:09:00

Igor: Yeah and then if they are stored not in the database and some simple place like shared properties that's easy to read from the native code, then you can do what Eric suggest and just ignore the notifications or what you suggested we ignore the client side and that should be simple enough.

Oskar: Would that also handle the case if you have two accounts in the same device?

Igor: Yeah we should do something to store something which account was signed in last, if it wasn't signed out. So if the app was killed but the account wasn't signed out, we should store something that will help us filter messages. It shouldn't be like just public key plaintext, it might be like a hash of hash of hash of hash of public key right so it might work still, or hash of hash of hash of hash of hash of last state symbols of last eight bytes of the public key, we just need something to compare with.

1:09:00 - 1:10:00

Igor: Which is to whom to which public key this was addressed so it should be also. But I guess it's already solved on the current implemented it just doesn't work on background of iOS right?

Pedro: Didn't understand the question sorry.

Igor: If you have two accounts and you signed in to account a but the push notification comes for the account b...

Pedro: Initially when I implemented the pull request it was showing for any account you had on the device but the decision was made to only show for the last active.

Igor: So it's already implemented just doesn't work on iOS in background.

Pedro: Yeah.

1:10:00 - 1:11:00

Oskar: Ok awesome so in that case we don't actually need any kind of registration or flow unless we want to switch out firebase, which we probably wanna do at some point.

Igor: It's probably more related to what we sent inside the push notification.

Oskar: What I mean is if you are on fdroid and you want to use something else then wouldn't you need a different token to be reached and then you would have to communicate that to your contacts.

Igor: Yeah that's true but as soon as we add additional support of something it will still follow the same...

Eric: Yeah I think regarding what you're saying, being able not to use firebase, the first step would be not have to have google notification on your device to run status. I think it's still the case.

Oskar: Yeah Dustin said this in Brussels.

1:11:00 - 1:12:00

Eric: So that would be a more urgent case. And I like the solution, it seems like the simplest one to just maintain the list of banned hashes outside of the DB so that you can filter the notification beforehand. I think it looks simple enough so we can reasonably implement it in a short amount of time.

Oskar: I agree it seems like a good solution. Alright, cool. So next one, this is Jarred's thread on key management and whisper decoupling, I guess do you want to add something to it? If they are any thoughts on this, things that might have been missed, general thoughts on this problem?

1:12:00 - 1:13:00

Andrea: I have a question. So I understand the need of separating the wallet keys, so the wallet keys are separate from the child ID, that I totally get it. In the post it was mentioned that for example you have a different key for each chat, which is interesting, and you know they can explain how to propagate and certain stuff for it, so I was wondering first of all what is the problem we are trying to solve
with having different ID's, and then another which is more of a problem, as I understand is to partially reveal your identity, so you have power who to reveal your identity to.

1:13:00 - 1:14:00

Andrea: Which is good, but this is more general problem that you notice in status that ok so we have all these identities and you don't reveal it to people that are not in contacts. But then again if I'm in a chat then everyone calls me Andrea and chooses to call me Andrea which is a bit of problem. It's understandable that we don't have mentions and so we mentioned you can alleviate that problem to some extent, but I feel like if that is the reason then we need to solve that problem first.

Jarrad: So those are great questions and great points. The reason for separating out the keys for contacts, I think in the general case it makes a lot of sense.

1:14:00 - 1:15:00

Jarrad: Because if you start thinking about these different contacts as their own particular silos whether it's a wallet, chat or a dapp, you might as well have that generic mechanism there anyway. But the real reason I was addressing that in the current post is because there had been a lot of thought and even UI flows to basically reveal an individual identity to a chat so you could have different identities but I think it was done through your profile or your settings or something like this and it would pop up before you enter the public chat. So I was basically trying to mitigate a lot of that UI flow while still achieving the underlying goal of whatever it was. I don't actually understanding the necessary reasons and I agree with you that there is that more social aspect of it where someone might just mention you in passing and if you reply to that then that person glean that identity is so regardless.

1:15:00 - 1:16:00

Jarrad: I'm not sure if that's someone we can solve, barring some kind of censorship, but in any case I do think that having the ability to automatically join a public chat and selectively reveal yourself is probably a mechanism worth having, even if this social aspect is problematic. Because it's not going to be every case that you enter a chat where all your friends are in it. Like you can enter a darknet market chat for example and you would want to have some guarantee that you enter and converse in that and it's not tied back to your main identity.

1:16:00 - 1:17:00

Andrea: I understand it makes sense. Yeah be interested in the UX point of view, because you mentioned that there were some problems, some work done before so that would be interesting, thank you.

Jarrad: I mean so basically what I was putting out is basically an aggregate of everyone else's thoughts with just some slight tweaks with how to think about certain things. The main one was instead of thinking about key pairs in their logical distinction more just thinking about them in terms of their security policies. So for example when we've been talking about whisper decoupling we've been talking about separating a wallet from the whisper key, which is what we currently have at the moment, and that's definitely a noble goal.

1:17:00 - 1:18:00

Jarrad: But there were some paths of thought where we've created backwards compatibilities, because it was a whisper key we are not treating it like a wallet, therefore if someone sent money to a whisper key then it would not be able to be retrieved. There's been this idea of hot wallet versus a cold wallet, it's been around since bitcoin days, but essentially the idea is that if a private key is in memory then it's basically a hot wallet or if it's unlocked in some form, you can unlock on disk if you're feeling crazy, whereas a cold wallet or a cold storage would be a physically separated key pair or air gapped in some way, and you would sign transactions and you'd move it over QR code or by some other means.

1:18:00 - 1:19:00

Jarrad: In status by extension we can use those policies, but there's this sort of intermediary stage where you can have sort of wallets which still gonna be signed relatively easy but the hot wallets in status are purely in memory, so they're all derived off what is currently the whisper key right and the reason we do that is because you don't want to be signing every message that you send in chat manually, but at the same time we want to still be able to access these key pairs if they do hold a balance in any token whether it's ? or C20s. So that's basically the reasoning for separating key pairs into hot warm and cold, so this doesn't actually manage any cold key pairs but it's definitely worth having the ability to receive or create a QR code or request onto cold addresses, yeah that's pretty much it.

1:19:00 - 1:20:00

Jarrad: It's more about derivations, how you derive keys from those. It's pretty simple you use a private key and you do some deterministic thing then you can derive off the public key, so you create a hardened derivation off that original child. I am of the position that we should continue to have the existing derivation of whatever, I think I got in wrong in the post but I think Andreas corrected me, we should keep that as is for now, but then every subsequent chat that you join will be under a new one. We can do a transitionary period where the existing public key is still happy to directly converse.

1:20:00 - 1:21:00

Jarrad: But then we can switch it off after a certain amount of releases and sort of a fanfare and telling our user base that that's the case, and we can still receive messages on that public key but we can also send them out to all the clients and it will just look like a new identity and random response there. This is probably better off for a team discussion but I just wanted to make everybody aware we are thinking about this stuff and I certainly would love more feedback, it's important because key pairs are fundamental to what we're doing and they're going to impact many things within the application. So it's definitely worth thinking about. I also mentioned other suggestions for some other things in the wallets. We could also probably even play around with since we changed out the way that we did our recovery, to make us more compatible with other applications then we should probably continue doing that work to make the derivations we do compatible with other applications.

1:21:00 - 1:22:00

Jarrad: So we should be able to different derivations, every other application has a slightly different structure, and we should be able to support that in recovery and ideally be able to do that automatically. Most of that is in the post, certainly a lot more coherent, I'm currently eating my dinner so I do apologize if I'm all over the place.

Oskar: Cool sort of a random thought or question, would it make sense to have this - um because you can imagine that you have been very tied to trust intelligence as well, so if you meet someone, a close friend, then you would see their identity in multiple sort of contexts but someone who is just a friend, a contact, in a certain context would just be that for that specific child key.

1:22:00 - 1:23:00

Oskar: Then when you for example @ mention them it would just render differently but it would be a UI concern, where you would see this sort of privilege, like the highest up the chain that you have established trust which might be different for different people in different contexts. Maybe that's implicit but yeah.

Andrea: I think that Yun worked on notifications before and that was the idea, that you just @, it's just a code, and then whoever you can see the name if you have in contacts, you don't see the name if you don't have it in contacts.

Oskar: Cool because I think it would be awesome if you could have the same account and you could use the same status account and if you were also in a darknet market you would not know it if you just normally add it, but maybe if someone else was also in this darknet, they would know that this was the same person, potentially I don't know.

1:23:00 - 1:24:00

Andrea: Yeah that works as long as people are disciplined enough to use the @. Basically it's not up to you, that's the problem. It's up to the other person. But as Yun mentioned it might not be a problem.

Jarrad: I think if we make @ work really well, then people would naturally just start using it. And I imagine the more proficient you get with the application the more likely you are going to use it. Which might not be so bad because if you are a new user to status when you first start out you probably don't have that much value and you probably don't have too much exposure to the network either. There's things that we can do on a sociological level where we create this sort of culture or these memes to, like if we end up doing welcome parties for onboarding, you can basically say hey these are some pro tips that we've learnt, and you can get them to sort of pass that on.

1:24:00 - 1:25:00

Jarrad: While we can certainly take the technology to a certain level we can continue writing the human software so to speak.

Oskar: Awesome. I guess anything else on this topic someone wants to say?

Igor: I have one super small topic that I just want to ask for opinion. So we know that status doesn't work on public WiFi's, and that's because the ports are blocked. So I have already a PR and we have an infrastructure done to essentially put all whisper traffic through the typical HTTPS 4.3, is there reason why we shouldn't do that?

1:25:00 - 1:26:00

Oskar: Can it be an option?

Igor: We'll have both ports but yeah all our whisper notes and mail servers and boot nodes they all reply on both ports. But right now this PR is super simplistic they just replace the ports with 4.3 but we don't have anything else on these servers ofcourse and discovery if it finds something on the port that's not 443 so this will add it still, there is no limit if it is accessible.

Adam: One point on discovery I'm not sure if you can use low ports on discovery protocol, it might just not pass the nodes which has lower parts, has it been tested?

1:26:00 - 1:27:00

Igor: Well, it works. It's in testing right now but I tested it on a few devices and I blocked ports on my local firewall and it works like it works.

Adam: Yeah I just wanted to confirm whether it's discovery version 5 that provides those nodes or it's just our rendezvous on discover protocol.

Igor: I mean some of them are from our fleet config.

Adam: I just confirm that this is working but thats cool.

Oskar: Awesome. Any other announcements?

Jarrad: I've been working on that self update thing on the weekend and I decided to turn it into a showing points game so that's kind of cool, I don't know when I'll announce probably a couple weeks.

1:27:00 - 1:28:00

Jarrad: The idea is that you basically, everyone commits a hash of what they think is the latest release when we're cutting a new release, and once everyone's committed and staked a certain amount of SNT towards it, then we all do a reveal and everyone's kind of rewarded or penalized depending on who has the majority votes and who committed and revealed the fastest. Meaning whoever pushes the release out fastest would probably profit. So yeah it's a little coordination game and that should be kind of fun to play. It also incentivizes getting lots of signatures on releases.

1:28:00 - END

Oskar: Good stuff. Alright, anything else? Cool so yeah thanks so much for joining the call, if you have some thoughts on ways we can improve it just add it in status core devs. Cool thanks everyone, see you in two weeks.

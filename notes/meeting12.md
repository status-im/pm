# Core Dev call 12
Meeting Date/Time: Monday 2019-02-11 at 13:00 UTC
Meeting Duration 1.5 hours
YouTube Live Stream Link https://www.youtube.com/c/Statusim/live
Livepeer Live Stream Link TBD

For each agenda item, please provide context (things non-initiated people need to know, links etc) and goal (desired outcome of discussion) for agenda items.

Please comment below with things you want to discuss, together with context and desired outcome.

## Transcript

[Transcript](transcript12.md)

## Agenda

0. One feedback that's worth re-iterating. These meetings should probably focus on matters that:

    are technical in nature
    would benefit from sync conversations
    can be decided upon during the meeting, i.e. doesn't require a lot of async research etc

Do people generally agree with this or are there other viewpoints?



1. Better PRs
    a) how can we avoid long PRs? the use of feature flags
    b) acceptance criteria and design review

2. Protocol discussion and Q&A
    Some time to ask questions and discuss protocol workshop etc

3. There was a suggestion by Eric on the chat sync to discuss push notification navigation.

With both deleted chats and old PNs from blocked users (PR just merged), the PNs open into an Unknown chat. Not sure if this is affected by Pedro's recent work to improve PN navigation.

4. Is it worth discussing https://discuss.status.im/t/musings-on-key-management-aka-whisper-decoupling/1034 would love feedback and any issues I may have missed, it probably requires async research, but everyone should be aware of the potential changes

    Status.im
    Musings on Key Management (aka 'Whisper Decoupling')
    Finally had a few hours this Sunday to think about the Key Management stuff. Background We strive to be a private means of communicating, whether that is via text, media or transactions. However currently, it is easy to see a user’s entire transaction history (public blockchain’s yo) based on whisper identity. To improve this there is a desire to generate new keypairs for both on-chain transactions and communication. Previous discussions have been thoughtful & fruitful, but have had some issue...

5. Announcements
6.

## Notes

- Oskar: How do you see these meetings, and what are they good for?
- Eric: These meetings help me keep up to date with what other teams are doing, now that teams work more separately from one another
- Julien: I expect to have a very high level overview of what each swarm is doing, but not too much detail.
- Pedro: nice to have a sync place to discuss org-wide changes, announcements
- Oskar: is it worth it having high-level swarm updates?
    - Jarrad: not if it is repeating what was covered in TH
- Oskar: to what extent should this call be purely technical, or also product?
    - Barry: if not on this call, where should we discuss those things? It doesn't seem to fit the TH.
    - Igor: agree, it's not like the call is growing too long.
    - Jarrad: I really enjoyed last call, where it seemed like we had too many things to discuss, but we managed to compile them down together.

### Better PRs

- Oskar: we tend to have too long-lived PRs. Previously we decided to use feature-flags much more liberaly, but it seems we have fallen out-of-practice with that.
- Andrea P.: In some situations we don't want to use feature flags. When we near releases, testers are too busy testing the release, which leads to people adding code to existing PRs.
- Julien: It becomes hard to do a good review on a huge PR.
- Pedro: there's a lot to be said about breaking PRs into smaller ones, since people will be more keen to act on a PR review if they antecipate it will take a short time. If we see that still doesn't work, we can try to diagnose where the bottleneck is.
- Andrea P.: The system we have in place doesn't help the dev. We should relax rules for manual QA, since some PRs which have big impact are delayed before they reach `develop`.
- Igor: agree we should relax manual QA rule on small PRs, otherwise we'll start having dozens on PRs in testing and be a bottleneck for QA.
- Anton: makes sense to have small PRs, since there's less stuff to update on the tests codebase for each PR.
- Oskar: taking the example of the wallet redesign PR, why do we replace the UI flow, instead of adding the new one behind a feature flag, allowing QA to decide when to move to the new tests?
- Iuri: we have a rule in that we don't allow WIP PRs, with the exception of bounty PRs. If there's a PR open, the idea is that the PR should be merged the same day, or possibly the next. Otherwise there's a lot of churn with constant rebasing. It's important for PR reviewers to be sensible and not ask for changes that are unrelated to the PR at hand (e.g., no asking for bug fixes that were uncovered by the PR work, but unrelated)
- Oskar: we should strive to make status-react have a cleaner PR backlog like with Embark (oldest open PR is 11 days, with 9 open, even though the repo is more active).
- Igor/Pedro: how does the Embark QA process look like? It has been an impediment in recent weeks, since with the focus on 0.9.33 release testing, the resources allocated for PR testing have been almost non-existent.
- Oskar: that doesn't give enough credit to Embark, we shouldn't assume there's nothing to learn because they are too different from status-react.
- Barry: If anything, it's despite of the tooling, not because of the tooling that we manage to be quick.
- Oskar: how can we improve testing speed without adding new resources?
    - this is the reason why we dedicated capacity to automated testing;
    - Anton: we don't have capacity to cover each scenario, so we do it manually. We plan to do it in the future, but the future never comes because there are more and more PRs;
    - Oskar: I have a hard time buying that we need more resources, there must be something else we can do to improve speed;
    - Igor: maybe we can not do all-hands-on-deck for release testing, and then they'll take longer to complete. There were a couple of situations that required this type of organization to be able to respond in time.
- Oskar: this is a long topic, does any one else want to contribute to the discussion?
- Andrea P will start a discuss post about this subject.

### Acceptance criteria and design review

- Rachel: I've been observing a lot of PRs where the implementation doesn't exactly match the design. It's a general problem, not specific to one or two PRs.
- Hester: Eric has done a lot of good work implementing components, so hopefully these issues will be less and less as more things are componentized.
- Barry: Components as laid out by designers in Figma is different than the way that developers implement them. Figma uses fixed styles.
- Can we lay things out in Figma using Flexbox or percentages instead? (To-do: ask designers to follow up)
- Eric: we need a way to sync on what components have been implemented, as I've seen components being implemented twice (not necessarilt the same aspects of it). We could do a separate call to sync up (Rachel will set it up).

### Protocol discussion and Q&A

- Oskar: we did a presentation on TH, but there wasn't enough time to discuss and ask questions.

### Navigation/Push notifications

- Igor: hiding PNs from blocked contacts: we should store some form of hashes of blocked contacts in a separate db so we can filter out those PNs

### Other

- Igor: app will soon be changed to use port 443 to bypass firewalls.
    - Adam: we should test to see if it's working due to discovery v5 or rendezvous.
- Jarrad: working on self-updating mechanism. Each person will vote on what they think it's the latest release.

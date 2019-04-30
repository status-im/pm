# Core Dev 15

Meeting Date/Time: Monday 2019-03-25 at 13:00 UTC
Meeting Duration 1.5 hours
YouTube Live Stream Link https://www.youtube.com/c/Statusim/live
Livepeer Live Stream Link TBD

For each agenda item, please provide context (things non-initiated people need to know, links etc) and goal (desired outcome of discussion) for agenda items.

Please comment below with things you want to discuss, together with context and desired outcome.

## Agenda

0. Brief swarm updates, something new not in TH
sticker; tribute; dapp store;  teller; network incentive; token-economics; core-improvement; protocol; dao; core/browser/chat/desktop/wallet/keycard; qa/janitor; embark;nimbus

oskar: anything new from the TH?

sticker-market:
— waiting for the contract audit
- corey: waiting for coordination with ToB

TtT: 
- the contract was updated so it could be deprecated in the future
- personalized messages was replaces with hash for IPFS

dappstore:
- ...

teller:
- app on rinkeby, deployment issues (debugging);
- an snt token issue fixed; small fixes here and there;

network-incentivization:
- PoC (running a mailserver and using it)

token-economics:
- ongoing work in the notebooks;

core-improvements:
- unicorn prep;
- 0.11.0;
- NO-GO for partitioning topic;

protocol:
- a panel in FCC a few weeks ago, mixnet approach (long-term, regular calls);
- data sync research, comparison and literature research;
    - after that, resume PoC and get it into the app;

dao:
- liquid funding, done with a project page (kickstarter-like format);
- stretch goal: project creation page & dogfood it (during #STATUSBUIDL week)

others:
- chat: typography module was implemented, each team should use it for CSS (compatible in figma);
- chat: system-tags to have meta-info for contacts;
- extensions: out of alpha, fixing permissions and error handling; improving DX; feedback needed;
- keycard: android integration MVP (dapp tx signing); geth integration is almost done;
- keycard: Point-of-sale use-cases for DApps (brainstorm);
- wallet: re-prioritizing incremental UX improvements; some for Point-of-Sale, some from the prev PR;
- qa: testing PRs for mobile for Chaos Unicorn Days; test automation iOS pending (sauce labs issue);
- embark: a small release last week; new website released;
- design: request - looking for a product designer;

---

1. Partition topic compatibility https://discuss.status.im/t/partitioned-topic-post-mortem/1107

- ideas:
    - use old mailservers to transfer messages to the old topics;
    - allow to send second message in the old topic;
    - longer period of time to do transitions;
        - eth2 ~ 6 month transition

- lack of engagement issue:
    - improve the process and culture around protocol changes;
    - use change proposals (SIP /status improvement proposals/);
    - (idea): give power to the users;
    - give power to client implementations;
    
- extracting protocol to another repository:
    - document-first approach;
    - (idea): java implementation;

- steps to do:
    - if there is a breaking compatibility;
    - proposal for the "last breaking change"
    - creative solution not to have it a breaking change;
   
- jacek: it is a stand and not a feature?

- jakub: does it worth it for our current userbase?

- qa: if that helps reliability, it might be worth doing? what is it from the user perspective?

- andrea: we only fetch 24 hours of data because of lack of partitioning, it affects perceived reliability.


1. (Missed it) Announce 172 topic democracy

- tomorrow is a meeting for a Swarm; how it works and why it works like this.
  +----------------------------------------+
  |  172-topic-democracy: swarm startup    |
  |  Tuesday, March 26 1:05 - 1:55pm       |
  |  https://meet.google.com/rft-uazf-mem  |
  +----------------------------------------+


2. Topic suggestion: exposing status-go as a nix package.

   We'd gain 3 things:
    - status-go repo would be consistent with status-react in using Nix (reproducible builds)
    - status-react would consume status-go as just another Nix package, instead of ad-hoc solution we have now;
    - unified hosting since we already host a nix cache.
    
questions:
    - how to update versions? local installs? built if hash is not found, so solved
    
    
3. Chaos Unicorn update
- mobile apps (almost ready, simple message)
- desktop: not sure now, but no need any approvals

- will people be able to chat with old versin? with cluster - nope, we will forbid trafic there


4. Quick follow up to better PR process
    - better? difference?
    - Andrea/Anton follow up quick
    
- issue: no automatic test running
    - issue with permissions for running auto-tests
    
- being able to test the app w/o UI code:
    - possible, but requires refactoring (detaching components from re-frame DB)
    - bounty or a core backlog thingy? write a bounty issue?

- ios e2e testing; issue with SauceLabs provider, it doesn't work there (app launch takes 8 minutes);

- looking into an alternative to SauceLabs (like BrowserStack);
    - make a topic on Discuss;
    

5. Announcements
    - if you are a European, ask to vote against article 13! https://saveyourinternet.eu

    - please rate call 1-10 with comment #status-core-devs

## Notes

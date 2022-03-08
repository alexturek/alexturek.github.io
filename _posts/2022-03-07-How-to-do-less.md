You probably need to do fewer things right now.

# Prioritization, the other definition

There's two loose definitions of prioritization.

1. **`Prioritization(1)`**: _Ordering a todo list._ You make a giant list of things you could do, things you should do, things you'd like to do... and then you put a unique number next to each item. Now it's an ordered list.
2. **`Prioritization(2)`**: _Only doing the top item on the list._ You already have a giant todo list. Which thing are you actually going to finish?

| Prioritization(1) | Prioritization(2) |
| <img src="../images/prioritization-1.png" alt="Prioritization: Ordering a todo list" width="200"/> | <img src="../images/prioritization-2.png" alt="Prioritization(2): Only doing some of the list" width="200"/> |
|:--:|:--:|
| _Why isn't this working?_ | _Get ready to disappoint some people!_ |

You've already done (1). You've done (2) ... sort of. But somehow you're still underwater.

- Your reports are complaining that nobody can do their code reviews.
- Project leads are asking for opinions from their coworkers, and hearing crickets.
- Cowboys are running off grabbing new tech that might be a bad idea, and nobody is stopping them.
- Maintenance costs of "already shipped" features keep surprising your team.
- Senior engineers are acting passive during planning sessions.
- There's a bunch of P1s that aren't getting done, or even worked on. And now you're spending a lot of time and energy on managing perceptions upward and outward, apologizing, trying to figure out how to rearrange the schedule to deliver faster.
- You keep asking your team how to move faster, and they're looking stressed in every standup.
- Engineers are taking dangerous shortcuts to demonstrate progress, and each one is less and less a big deal.
- Management is asking you to prioritize new work, but won't give you a priority to drop.

This isn't a sustainable way to work, but you feel pulled to sacrifice in the short term, and do more of the same things you're already doing.
That uncertainty you feel about the future?
That's a series of impending failures.

**You're stuck in a trap, and thrashing won't get you out.**

You can escape the trap by stopping your current approach, and doing something new.
Take a deep breath, and get ready to finally make those hard decisions.
You're going to deliberately overshoot, cutting down WIP, and then maintaining a healthy amount going forward.

The rest of this post is about how to do that.

# Get out of the trap

First, you need to lower everybody's expectations, ASAP.

## Make and broadcast cuts

You have to get yourself out of a bad state.
There's no point in half measures here.
People are smart and they can recognize hedging.
The folks around you will know if you aren't committed to your plan.
You need to make hard decisions and then do the _really_ hard part, which is stick to them.

Your two meta-priorities:

1. **Keep the lights on, and make keeping them on cheaper.**
   Everything your team already owns (that actually matters to your customers) needs to approach 0 maintenance costs.
   Without minimizing your long term costs, your headcount and time will be eaten up, and every new feature will ship slower than estimates.
   Designate a lead to actively seek out and reduce the highest oncall and support burdens on your team.
   This work is **arguably more important** than any new features - make sure you message it that way.
   It's glorious work, because that lead is maintaining something that is _already valuable today_.
   This looks like e.g. writing docs for users to self-serve, fixing flaky bugs, and adding preprod tests to catch things that cause outages.

   Ask your team what the biggest maintenance costs are.
   Figure out how you can measure them in a way that your team can get behind.
   You can use "number of oncall pages", or "number of support requests that involve more than linking to docs", or something along those lines.
   Dig into your data, figure out where the drag on your team comes from, and drive it down.
   From there, write a Maintenance Roadmap to reduce your team's costs.

2. **Cut the entire roadmap of new features down to one thing at a time.**
   Take the entire list of WIP, and get ready to drop almost all of it.
   I _know_ you're dropping critical things - we've established that you've already dropped every P2+.

   Now it's time to cut the P1s.

   List all the new things you're currently doing or planning to do, and put them in the New Features roadmap doc.
   Do `prioritization(1)` on them, and drop everything except the top item on the list.
   Don't like the result?
   Don't think of it as choosing a bunch of critical things to fail.
   Think of it as choosing one critical thing to actually succeed at.

   You now have a list you can share with people on your team and elsewhere, to explain what's going on.

## Handling Initial Disappointment

**But what about Engineer X**, who was really excited about project Y?

They may be disappointed by losing momentum on their newly cut feature.
But if they actually care about business impact, they'll be solidly behind delivering a single good, long-term useful feature.
If they _don't_ care about it... then they're focused on tech instead of the business problem.
You don't want too many of those people around anyway.

I predict your team will be almost immediately relieved to have a coherent focus.

**But what about Stakeholder A**, who was expecting Feature B in the next few weeks/months?

I expect that your stakeholders _also_ care about the long term health of the business.
They'll be won over, for a little while, by your focus on delivering business impact.
Expect this to fade, and the clamoring to come back.

Defending your team and its roadmap will be a Forever Effort, and I'll get into this in the next section.

**But what about losing momentum, and the effort we've already put in designing and starting other
work?**
You sure did have momentum before - you had lots of little momentums, meaning lots of projects that were going to be delivered late and shoddily.

This is the sunk costs fallacy, and a one-time, short-term problem.
If you can manage to minimize WIP, you won't have to pay it again.
All that work doesn't mean anything if the project wasn't fully finished.
By the way, any partial work that's going to slow down work on the actual committed priority should be considered drag, and removed.
Source control will have it for later.

**What about Feature D, an urgent business need** that the CTO just DMed me about?

Default to No.
Without getting into the politics, I'll just say this:
unless you work at a 10 person company, the CTO has less context than you about reality "on the ground."
You can show them your current new feature roadmap, and explain where the top priority is.
If they want you to insert their new work directly after your current top priority, great.

**Are you really telling me to say no to the CTO?**

Yeah, see above.

> the CTO has less context than you about reality "on the ground."

Good managers know this.
They might ask you for a lot of details, but they won't fire you.
Any manager or C-suite that would fire you for sticking to a plan and actually delivering value to the business isn't worth working for.

# Stay out of the trap

So now, you've committed to a big, one-time effort of saying No to everybody.
You've cut a ton of critical features out of the WIP column, and everybody on your team is starting to get energized at the thought of all working together to achieve a few hard goals.

How do you avoid "WIP creep", and falling back into the trap?

## Say No, early and often

You didn't fall into this do-everything trap in a vacuum.
You did it because there's constant pressure, from yourself and your customers, to deliver everything, immediately.
You can handle that pressure by saying no a lot, up front.
A bunch of small disappointments that you actively seek out and cause are far easier to handle than waiting, and letting them build up to large disappointments.

As early as you hear anybody else's plans that involve your team doing something new, interject with a clear No.
Interrupt the conversation and tell them their plan is going to fail if it depends on your work.
Saying "we'll do this later" is not enough - you have to show all the things that come in front of their ask, and tell them they aren't getting what they want, when they want it.
**If someone isn't at least a little disappointed, they didn't hear no.**
**Keep saying it now and in the future.**

The New Feature and Maintenance roadmap docs you wrote above will be useful here.
You can use them, or something like them, to explain your No.

Don't let expectations creep invade your team's roadmap.
If you aren't going to work on or support Feature X for at least 6 months, _and you really mean it_, then you should feel really comfortable repeating it ad nauseum.

### Copy/paste: How to Say No

Here are some concrete ways to tell management or stakeholders no.

> This isn't `MAIN_PRIORITY`, so we aren't going to do it until at least `ESTIMATED_DONE_DATE`.

> Right now our priority is `MAIN_PRIORITY` because of `ONE_SENTENCE_JUSTIFICATION`, and this is 100% our shipping focus.

> I agree this sounds like a really useful feature - once we finish `MAIN_PRIORITY`, should we consider dropping `SECOND_PRIORITY` and do it?

## A team that helps each other focus

Look, it's not just people outside your team that's causing you distractions.
Everybody on your team, including you, generates them too.
And some people are really good at convincing others that no! This isn't a distraction! It's an important new priority!

So that means that every person on the team needs to be able to help the others recognize and avoid distractions.

What's a distraction? **Anything that doesn't help you keep your existing features running, or deliver your top priority faster.**

A good rule of thumb to recognize a distraction is: it is a significant amount of new work that would surprise the you of N months ago who planned the project.

That might look like...
* Switching a core technology, e.g. your ORM, for a significant sized codebase
* Building a new application to support V2 of a feature that hasn't launched to V1 yet
* "Just experimenting" with one of the above - prototypes that won't lead to immediate migration and use are a waste of time and focus.

Your whole team needs to default to "No, we shouldn't do `NEW_THING`", and have to be convinced.

### Copy/paste: How to correct distractions

Here are some concrete ways to challenge distractions.

> This isn't `MAIN_PRIORITY`, that we all said we're going to work on.

> What if we don't do this? What can we do without it?

> Is this a requirement or a nice to have? Will it speed up `MAIN_PRIORITY`?

> Can we put this onto our (New Feature/Maintenance) Roadmap after our current priority finishes?

> I think we can finish `MAIN_PRIORITY` without this.

### Set a good example

It's hard to cultivate teams with the level of psychological safety that lets brand new junior hires question the team's tech lead or manager.
I'm going to mostly save that for another post, except for this bit.

If you're reading this, I probably linked it to you. You might be a tech lead or manager of a team of engineers. You have real authority, at least in the eyes of a bunch of other people.

So set a good example for everybody on your team, and **accept No for an answer**.

When somebody (correctly) calls BS on some new work you're suggesting, you need to back down.
The best way to encourage somebody learning a skill is to let them exercise it, and find easy success.
Don't turn your argument/influencing skills all the way to max on some junior engineer.
Accept their No and move on.

## You have to finish work

This whole single-threaded feature development framework might tempt you to take shortcuts. You might think a few flaky tests are okay, or be looking at that Jira ticket to "Add monitoring", and be tempted to drag that below `NEW_NEXT_PRIORITY` that your boss has been asking you about for weeks. A shortcut gets you to move down that priority list finally!

That's a short-sighted move.

Declaring a feature that's in customers' hands "done," without monitoring, or with flaky tests, or tons of highly redundant code, or other obvious pending work, doesn't magically get that work done.
That work will always be there. It'll just show up as surprises in your Maintenance Roadmap at an unknown date, when your team has mentally moved on and stopped thinking about the feature.

Unless you're planning on finding a new job pretty soon, or shifting blame for a project failure to someone else, or otherwise highly uninvested in your team's overall success... don't skip the obvious stuff.

# Maintaining flexibility

I'm expecting a few people to read this post and think I'm somebody who writes 2 year plans, in detail, and doesn't deviate from them. They might think I've only worked on 10 year aeronautics platforms or something.

You should try talking to my various coworkers. **I hate writing plans**, and **I am impatient as hell**. I've worked at 3 early stage startups. I absolutely understand the necessity to drop what I'm doing and hack out a feature that gets a check from our next customer. I don't even write TODOs in code, because that's a tiny little plan that doesn't matter.

Here's the thing: an early stage startup is just a future company that might get customer traction and take off. A tiny incubation team in some big tech company might become a 100-person org building features to try to match execs' ambitions. Both of these have these things in tension:

* **Iterate**: You need to try some stuff with the product, to see if customers care about it.

* **Invest**: There's a reasonable chance that this hack you're about to ship causes _an entire team_ to be mad at you in 6 months.

The only way I've found to handle that tension is in a small org is to be all in on one mode or the other.
Default to Iterate, but be willing to Invest, maximizing how many people can work on the investments until they're done.
After enough iterating, you'll identify the real investment areas that are critical.
These are areas that cause high amount of distractions while iterating, and act as constant drag.
When you're nearing the end of Invest mode, you can start getting ready to Iterate again.
A fun bonus benefit is that the product roadmap will probably have significantly changed due to customer discovery, so you may not have lost that much time.

![](/images/iterate-invest-modes.png)

The reasons this works are:

1. You don't have years of code or systems yet, so large scale investments are still measured in the weeks or months, not years.
2. The team's small enough that it can entirely focus on a single goal, automatically avoiding most distractions.
3. You aren't about to run out of funding in the next 3 months. (_If you are: Good luck. Don't read this or any more blog posts until you've figured out how you're going make it, okay?_)



<!--
----------------- WORK IN PROGRESS HERE -----------------






Help keep your team from fragmenting its focus, and avoid

* Challenging them to [use boring tech.](http://boringtechnology.club/).
* Asking for effort estimates for new work, and then compare that to finishing the current WIP
* Asking for cheaper, "live with it for now" fixes

TEAM SMELLS
* Fake sense of urgency. Nothing's happening, and then it's "GO GO GO"
* Everything's a fire, including switching priorities
* Multitasking
* "stretching" to count a success


#### Get your team to tell you No

### Finish things, forever

### Concentrate the team

### Bias towards incremental changes

### Reward the maintainers

### Change incentives

Right now, your engineering team thinks that top performers

* Mark Jira items as done the fastest.
* Design and build big new systems.
* Skip monitoring and testing to focus on user-facing feature code.
* Lead their own projects, with other engineers following their plans.
* Work non-stop.

That's probably not an accident. They see who gets rewarded with promotions or high ratings, and for what.

You can start by flipping the things in your engineer leveling guides that reinforce this.

```diff
  A senior engineer at <COMPANY>...
-   Designs and builds large-scope systems that benefit multiple teams.
+   Chooses well-supported, off the shelf software, and helps guide other teams to use it.

-   Defines technical roadmaps for long-term projects.
+   Reduces scope on existing projects, or finds ways to avoid them altogether.

-   Owns engineering or product objectives requiring novel solutions.
+   Successfully improves reliability and maintainability of existing systems.
```

As long as people believe in "promo projects", they're going to argue to build them. Kill the concept and replace it with the question "what time sink did this person help us avoid?"

### Budget based on teams, not projects

## Start communicating

## A model: Solo Game Dev




- not about prioritization. assume hard prioritization has already been done
- this is about how to get your priorities _done_, with highest long-term throughput, by doing fewer of them

- the feeling of too much

- CUT WIP
- change incentives
  - remove promo projects from rubric
  - reward reducing WIP
- communicate on strategy
  - disappoint early, often
  - reward the people keeping lights on
- a model: solo game developers. only can focus on one thing at a time
- execute on strategy
  - budget for new work
    - WIP tokens http://boringtechnology.club/
    - what counts as WIP?
  - choosing what to finish
  - when can you stop?
    - taxonomy of tech debt https://technology.riotgames.com/news/taxonomy-tech-debt
  - buy what you can https://skamille.medium.com/why-is-it-so-hard-to-decide-to-buy-d86fee98e88e



**Before**:
* Engineers seek out "promo projects", big new systems that serve as the headline for their next level or compensation increase.
* Estimates are always too low, and sprints never finish, but just bleed over
* Testing, monitoring, and deprecating old features are the sprint items that get cut first.
* A critical engineer leaving for a few weeks causes delays in multiple projects.

**After**:
* Sprints sometimes finish early.
* Your "top performers" are the ones that take weeks off with barely a ripple.

**After**:
* Engineers

* Engineers seek to _scale out_, by knocking out features as fast as they can plausibly call something done.
* Engineers seek to _scale up_, by finding big new systems to build. Commonly referred to as "promo projects".
* Everybody's looking for excuses to skip important steps, like writing tests, coming up with monitors, or refactoring.
* A single person needing to take a few weeks off causes significant delays in multiple projects

**After**:
* Engineers argue
-->

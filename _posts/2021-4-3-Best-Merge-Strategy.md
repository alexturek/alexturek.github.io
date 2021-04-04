TLDR:

- Squash is best if most commit messages aren't useful, because the team doesn't expect to need that.
- Merge is best if most commit messages are useful, because the team expects that.
- Figure out which works for you based on your team.
- Never do Rebase And Merge.

[Strongly recommended pre-read](https://medium.com/@elliotchance/comparison-of-merging-strategies-in-github-2f948c3b8fdc) (If you're in a hurry, scroll to the comparison table.)

### Never do Rebase And Merge

Let's start with the easy one: **never, ever rebase and merge**.
This should be disabled in each repo, and ideally removed as a feature from Github.
Then we'd go through the internet and hide the fact that it ever existed as a merge strategy in the first place.

It...

- hides the PR that it came from, so you lose all context on why the change got made, how the review conversation went, etc.
- keeps every `wip` commit
- makes merge conflicts a nightmare. If you have conflicting changes in a file with multiple commits, you have to do multiple merge conflict resolutions.
- doesn't have immutable history, so your commit IDs all change when you merge. Hope you didn't have those saved anywhere!

### Possible good answer #1: Squash

Particularly if you (and your team)

1. mostly do small, focused PRs
2. mostly write very clear PR titles (since they'll be your commit message)
3. use Github as your primary mechanism for viewing commit history (and thus highly value linear history)
4. mostly _don't_ care about writing good individual commit messages
5. mostly _don't_ branch from your own PRs to do more reviewable work

#### Upsides

##### Small PRs and tiny commits

If you do lots of small PRs, and most of your commits have messages like `oops` or `wip` or `respond to PR feedback`,
then those commits don't provide much value. Here, your "quantum of understanding" is the PR, and you expect everyone
to open the PR if they need to deeply understand why a change happened.

Technically yes, you do get all your commit messages in the squash commit. Something like

```
Add ability to send foos to bars (#10001)   <--- PR title and number

* Add API endpoint for sendFoo              <--- commit 1

* Fix test                                  <--- commit 2

* fix broken test

* oops

* fff

* asdfhaskldh
```

Obviously those last 3 commit messages in particular aren't high value.
If I was trying to figure out why line 405 in `src/api/sendFoo.ts` changed, and I saw `fff`...
that's worse than if I saw that it changed because of `Add ability to send foos to bars`.
And if this entire PR is only 100 lines changed, then the whole thing could probably just be a single commit anyway.

##### Github history view

There's also the question of linear git history being important to your team. If you use the Github website for viewing history, atomic (one entry per PR) linear (in order of merged) history is extremely useful.

#### Downsides

##### "The commits are all still there"

Let's say you find this commit, with this diff

```
Fix tests (#4446)

* Fix the timezone in a test

* Fix unrelated timezone bug
```

```diff
--- a/test/dostuff.ts
+++ b/test/dostuff.ts
@@ -68,7 +68,7 @@
- time = moment(otherTime, 'America/Los_Angeles');
+ time = moment(otherTime);

@@ -123,7 +123,7 @@
- time = moment(otherTime, 'America/Los_Angeles');
+ time = moment(otherTime, 'America/New_York);
```

Uh oh! Which one was "unrelated"? Is one of these right and the other isn't? 🤷 I don't know because I don't know which line of diff went with which commit.

##### Forked PRs

Something that you may do for the benefit of your PR reviewer is break a change up into multiple PRs for separate review.
This is common for people building complex features, where you may have the following 3 PRs

```
replace-new-with-old-1 -> master                  Refactor existing code
replace-new-with-old-2 -> replace-new-with-old-1  Add new feature
replace-new-with-old-3 -> replace-new-with-old-2  Delete old feature
```

Reviewing these as separate PRs _can_ be easier for the reviewer, as each PR is doing exactly one thing. And if you're doing small PRs, it's likely that you'll be breaking them up into good logical groupings. But squashing the first PR means you now have all the first PR's commits to try to excise from PR #2.

Hopefully the histories are short, because you're going to have to manually rebase the next PR you want to merge, without the original base's commits, and set the new base to `master`. If you don't do that, you will have merge conflicts, because git will see that you have two commits that changed the same file (instead of two copies of the same commit that changed it in the same way) and force you to do conflict resolution.

##### Imprecise Git History

If you ever want to `cherry-pick` or `revert` a single change from a PR, you can't. If you revert multiple commits in a single PR, e.g. you want to revert multiple PRs at once, you will never be able to re-apply or revert those commits again without merge conflicts. As far as `git` is concerned, your history contains

1. the original (PR) commit, with the applied diff
2. the new (PR) commit, unrelated to the original, with the opposite diff. This PR may have other reverts as well.

And so trying to revert (1) or part of (2) is no longer a seamless option.

### Possible good answer #2: Merge

Particularly if you (and your team)

1. often need to do larger PRs that include multiple logical changes
2. mostly write useful git commits
3. use `git` as your primary mechanism for viewing commit history (and thus don't need a linear history)
4. often branch from your own PRs to do more reviewable work
5. work in a high-traffic repo, where you don't know about a significant number of changes until they've been put into `master`

#### Upsides

##### Easier git archaeology

If you work on long-lived projects, you will often need to go back and revisit changes made months or years ago. The #KnowWhy of each commit, including its direct ancestor commits, can provide extremely useful context about why a change was originally made. This is a form of documentation more durable than code comments.

The higher the number of committers, and the longer the lifetime of the codebase, the more valuable this feature is. Even if not every person writes good commit messages most of the time, if _you_ do, you can always answer the question "What was I thinking here?"

##### Immutable history

Once you write a commit and push it to Github, that commit will exist in everybody's history forever (Barring force pushes to your branch before merging, which most people find acceptable).

This is valuable for

- PRs branched off of other PRs, especially when they're being done by different PR authors
- Durable git commit IDs, e.g. when you reference one git commit in another's commit message
- Doing `git revert`

#### Downsides

##### Understanding history

Merge commits in a high traffic repo require a higher mastery of `git` CLI usage; Github's history view isn't terribly useful for visualizing a complex directed acyclic graph. And you have a problem that if multiple people are committing at the same time (very likely in a large repo), `git log` will be extremely hard to read.

You can visualize simpler, linear history with the `git` CLI (via `git log --first-parent`) but Github's view will be misleading.

### Okay but... if you have to pick one, which is best?

Ultimately, this depends on the team preference, and the makeup of the team. If you can keep things simple on a small team, Squash may work best for you. If you are likely to have a complex development environment, Merge won't mask that complexity for you, but it will support it better. The usual complaint about Merge is that it requires people to learn more of the `git` CLI.

I think there's an incorrect assumption though - that you need exactly one merge strategy. Picking one relies on driving consensus across the developer group, and the larger the group, the larger the spread on peoples' preferred commit styles. **You probably don't have to pick just one; just disable the Rebase And Merge option**.

All I ask is that, for me, please don't turn off Merge 🙏. I have a history of working on long-term projects and spend time making a quality commit history for my PRs, for future me.

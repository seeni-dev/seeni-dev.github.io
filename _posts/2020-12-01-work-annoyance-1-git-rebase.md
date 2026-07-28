---
layout: post
title: "Work Annoyance 1: Git Rebase"
---

How many times the below thing happens to you?

1. You have created `hotfix` or patch branch in your work
2. You have pushed your commits to your work remote repo
3. There has been a update in master leaving your `hotfix` branch out-of-sync with master.
4. You will be forced to "Sync them"
5. Now is the question? `git rebase` or `git merge`?

Though, `git rebase` is the keyword everyone uses and your managers will force you to rebase without knowing consequences.

Simply, `git rebase` won't work. Will explain you why. `git rebase` takes all the commits from your `hotfix` branch and applies on the new branch out of master as if that `hotfix` commit was never made.

It is like as if yourself

1. Takes all the changes in the first commit of `hotfix` branch and then applies the changes to the corresponding files manually via a code editor and then you commit them like usual in a new `temp` branch cut out of master.
2. You would repeat 1 for all the commits in your `hotfix` branch.
3. And then you would delete the old `hotfix` branch and rename the `temp` branch as your `hotfix` branch `git rebase` automates the above steps with optimisations. You can read about `git rebase` in [here](https://git-scm.com/docs/git-rebase).

One thing you might have noticed that the old `hotfix` branch and new rebased `hotfix` branch are not the same, though their contents are. you can confirm them by `git log`. You will see the new datetimes and new hashids or commit ids compared to what you saw in the old `hotfix`.

So, now when you try to push the changes to `hotfix` branch, you will get an error similar to, "***Updates were rejected because the tip of your current branch is behind its remote"***.

This is completely understandable since both branches have different ids in their history and no commit in common except for the base commit out of master.

And a normal `git push origin hotfix` cannot force the remote repo to override its `hotfix` branch.

Most often, Your organization would have disabled `force-push`, which lets u overwrite the `hotfix` branch.

Only working option u have is `git merge`. `git merge` is a very simple command. It adds a merge commit on top of current `hotfix` in addition to resolving any conflicts. You can read about it in [here](https://git-scm.com/docs/git-merge).

Now, you can easily push the branch because you are pushing only a single commit on top of existing `hotfix` branch without changing old commit ids.

So local `hotfix` is same as remote `hotfix` but one additional commit in local `hotfix`. But both `hotfixes` share the same history except for that one additional commit. Thereby, Remote can fast-forward its remote branch.

TLDR; don't use `git rebase`, if u have pushed your branch to remote. Always use `git merge`.

*Originally published on [HackerNoon](https://hackernoon.com/work-annoyance-1-git-rebase-j5p3w2d).*

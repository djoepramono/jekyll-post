---
title: Git Cherry Pick and Config Files
tags: git
categories: git
---

Have you ever worked in a project where you need to make changes to an already committed file but you are too scared to/cannot commit.

Typical examples are:

- environment configuration files are committed into the repository. *Doh !*
- you need to put a comment on a specific line because your development environment cannot handle it. *It happens ...*
- you need to add a block of code as a reference, which maybe used in a future use. 
*Because you think you will never find it again*

You can make changes and leave them unstaged but since they are not committed. There is a chance that you might lose them. Plus it clutters your `git status` result

## Solution

`git cherry-pick` could be the solution.

### 1. Commit the changes in a new branch

Create a `personal` branch out of `master` (or whatever branch you will raise a pull request to).
Commit the changes (configs, hack) as a single commit in that branch. 
For simplicity, we call this `hack` commit.

```shell
$ git checkout -b personal master
... make some changes
$ git commit -m 'apply changes for my development environment'
```

### 2. Apply the changes into your working branch

Go to your working branch `feature-1`, identify the `hack` commit, and cherry pick it

```shell
$ git checkout feature-1
$ git log HEAD..master # This will return a commit id e.g. c787b3a92d64c37daaffaa10b081be1e27af70cd
$ git cherry-pick c787b3a92d64c37daaffaa10b081be1e27af70cd
$ git log # verify the log and you will see the id there
```

## Caveat

While the above solution could work wonders, you need to also make sure you a `git rebase` before you raise a pull request at the end.
Alternatively you can straight away `git reset --soft` the cherry picked commit


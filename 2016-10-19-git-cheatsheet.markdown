---
title: GIT Cheatsheet
categories: git
---

| Command   | Explanation   |
|-------    |-------        |
|`git commit --amend` | Amend last commit, which include the latest staged file. |
|`git commit -m 'rebuild pages' --allow-empty`  | Commit empty message, it can be useful when you need to trigger a **Jenkin** build with submodule |
|`git add <something> && git commit ` | Add and commit straight away, another alternative for updating **Jenkin**  with submodule |
|`git remote prune origin`| Delete merged branch in the remote |

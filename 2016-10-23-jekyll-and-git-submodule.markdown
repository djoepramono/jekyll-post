---
title: Jekyll and Git Submodule
---

As I invest more and more into building my Jekyll Site on Github Pages, I started to think to split
my **posts directory** into a different git submodule.

- If someone want to use my Jekyll modifications they can download the repository without the noise
coming from the posts commit.
- If later on I want to use another blogging tool, I can point them the **posts repository**.

I have recorded my journey [here](/git-filter-branch/). However it soon became apparent that it was
not working as I had hoped

- A new post into the **post** repository, doesn't automatically build the **jekyll** site. Making the
building step a bit more complicated. This can be remidied by using **githook**.
- There's no way of building the Github Pages without creating new commit to the parent repository. This means soon
the **jekyll** repository will be flooded with meaningless commit.

Quoted from [github](https://help.github.com/articles/using-submodules-with-pages/)

> If your GitHub Pages site repository contains submodules, they will automatically be pulled in when the Page is built.

There is also a github support link on the page above. Try it, they were helpful.

That's all folks. So Jekyll, Github Pages, and Git Submodule may not be as smooth as you think.
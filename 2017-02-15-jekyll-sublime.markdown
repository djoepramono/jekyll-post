---
title: Jekyll - Sublime
---

This is what I did to make my Jekyll experience more enjoyable in Sublime

- Install [Sublime Jekyll](https://github.com/23maverick23/sublime-jekyll) plugin
- Set the following the **user setting** level by going `Preferences` -> `Package Settings` -> `Jekyll` -> `Settings - User`

```
{
    "jekyll_posts_path": "/Users/joe.pramono/Projects/jekyll/djoepramono.github.io/_posts",
    "jekyll_drafts_path": "",
    "jekyll_templates_path": "",
    "jekyll_auto_find_paths": false,
    "jekyll_uploads_path": "",
    "jekyll_uploads_baseurl": "{{ site.baseurl }}",
    "jekyll_default_markup": "Markdown",
    "jekyll_send_to_trash": false,
    "jekyll_date_format": "%Y-%m-%d",
    "jekyll_datetime_format": "%Y-%m-%d %H:%M:%S",
    "jekyll_debug": false,
    "jekyll_utility_disable": false
}
```

- Now I can easily make a new post by `command + shift + p` and type `jekyll new post` instead of manually creating a `yyyy-mm-dd-post` file in `_posts`

# Things to improve

Apparently there is no sublime-settings at project level as you can see from this [stackoverflow](http://stackoverflow.com/questions/10599447/is-there-any-way-to-have-project-specific-package-settings-in-sublime-text-2). So if I have 2 Jekyll project in Sublime, I can only point the settings to one location at a time. Which is a bummer :(

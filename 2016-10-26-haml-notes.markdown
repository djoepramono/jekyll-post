---
title: Haml Notes
---

My notes about HAML, HTML Abstraction Markup Language which basically a template engine.

## Variable within HAML

There are times when you call a `helper` function in your HAML multiple times.
This may result in different data being returned. For consistency, it's encouraged to store
the first return data into a variable which can be referenced multiple times in the HAML.

```haml
.container
  - $variable = my_helper_function
    .span = $variable
    .another_span = $variable
```
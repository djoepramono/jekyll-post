---
title: IDE Keymap
categories: ide
---

Have been switching multiple IDEs recently, I try to compose a generic yet enjoyable keymap that I can carry across IDE.
This is a Work In Progress, thus this post will change.

## Rules

- No `F` keys
- No `Numpad` keys

| Action                            | Inspiration | Custom                 | Jetbrains (J)            | Sublime (S)           | Atom (A)                 | VS Code (C)                        |
|---                                |---          |---                     |---                       |---                    |                          | ---                                |
| Go to previous cursor in history  |             |                        | `cmd``alt``left`         | `ctrl``-`             |                          | `ctrl``-`                          |
| Go to next cursor in history      |             | `cmd``alt``right`      | `cmd``alt``left`         | `ctrl``shift``-`      |                          | `ctrl``shift``-`                   |
| Open terminal                     |             | `ctrl` `` ` ``         |                          |                       |                          | Keymap changes                     |
| Annotate                          |             |                        | `Right Click` `annotate` |                       |                          | `Annotator plugin`                 |
| Simple fold                       | S,A,C       | `cmd``alt``[`          | `cmd``-`                 | `cmd``alt``[`         | `cmd``alt``[`            | `cmd``alt``[`                      |
| Simple unfold                     | S,A,C       | `cmd``alt``]`          | `cmd``+`                 | `cmd``alt``]`         | `cmd``alt``]`            | `cmd``alt``]`                      |
| Fold all                          | C           | `cmd``shift``-`        |                          |                       | `cmd``alt``shift``[`     | `cmd``shift``-`                    |
| Unfold all                        | C           | `cmd``shift``+`        |                          |                       | `cmd``alt``shitf``]`     | `cmd``shift``+`                    |
| Zoom in                           | S,A,C       | `cmd``=`               | Pinch in                 | `cmd``=`              | `cmd``=`                 | `cmd``=`                           |
| Zoom out                          | S,A,C       | `cmd``-`               | Pinch out                | `cmd``-`              | `cmd``-`                 | `cmd``-`                           |
| Zoom reset                        | C           | `cmd``0`               |                          |                       |                          | `cmd+numpad0`                      |
| Switch to the file on the left    | S,A         | `cmd``alt``left`       | `cmd``shift``[`          | `cmd``alt``left`      | `cmd``alt``left`         | `cmd``alt``left`                   |
| Switch to the file on the right   | S,A         | `cmd``alt``right`      | `cmd``shift``[`          | `cmd``alt``right`     | `cmd``alt``right`        | `cmd``alt``right`                  |
| Close other editor panes          |             | `cmd``k`   `cmd``t`    |                          |                       |                          |                                    |
| Find all then replace             | S,A         | `cmd``f` `alt``enter`  |                          | `cmd``f` `alt``enter` | `cmd``f` `alt``enter`    |                                    |
| Find next then replace            | S,A         | `hightlight` `cmd``d`  |                          | `hightlight` `cmd``d` | `hightlight` `cmd``d`    |                                    |
| Paste selected lines below        | S,A         | `cmd``shift``d`        |                          | `cmd``shift``d`       | `cmd``shift``d`          |                                    |

## Little things to note

- `+` needs a `shift` where `-` doesn't need a `shift`. So if you don't want `shift`, `=` might be a better shortcut

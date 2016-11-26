---
title: Elm Functions
categories: elm
---

Notes about functions in **elm**, most notably partial application.

## Partial Application

It is basically breaking down a function, by constituing its argument with another function, to make it more readable.
In **elm**, all functions take exactly one argument and return a result, which can be another function

```
add : number -> number -> number
add x y =
    x + y

add2 = add 2
var1 = add2 3
-- returns 5

var2 = 3
    |> add2
-- returns 5

var3 = 4
    |> add2
    |> add 7
-- returns 13
```

Breakdown

- As you probably notice there are two `->`, this means that  `add 2 3`, is actually implemented as `(add 2) 3`
- Function `add2` is basically covers `add 2` part of `add 2 3`
- Pipe `|` is to make it easier to read, 4 is passed to a **partially applied function** `add2` which finally
passed as a **second** argument for `add`. The first argument is 7
- This is similar to **currying**. But they **are not the same**



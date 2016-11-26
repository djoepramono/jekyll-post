---
title: Elm Collections
categories: elm
---

This note is all about **lists**, **tuples**, and **records**.

## List

This is similar to array in Javascript, excepts

- Elm discourages indexing List
- Can only contain same type

```
> names = [ "Alice", "Bob", "Chuck" ]
["Alice","Bob","Chuck"]
```

## Tuple

Tuple is similar to a list, *BUT*

- it has **fixed length**
- it **can contain different types** (e.g. 2 Char, 1 number)

```
> dlist = ['a', 'b']
['a','b'] : List Char

> dtuple = ('a',1)
('a','b') : ( Char, number )
```

A good use of tuple is when a function needs to return more than 2 things back

## Records

Pretty much a **hash** in ruby or **objects** in JavaScript, an associative array with key-value pair

- You cannot ask for a field that does not exist.
- No field will ever be undefined or null.
- You cannot create recursive records with a this or self keyword.

```
> teacher = { name = "John", age = 24 }
{ name = "John", age = 24 } : { age : number, name : String }

> teacher.name
"John" : String
```

Elm is very sensitive, the following doesn't work for me. Just because I use `'`

```
> teacher = { name = 'John', age = 24 }
-- SYNTAX PROBLEM --
```
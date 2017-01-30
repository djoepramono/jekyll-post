---
title: Ruby Modules and Attributes
categories: ruby
---

Modular code in Ruby sometimes can cause you headache. 
Is that a function or an attribute? 
When and where is it initialized? 
Where is the logic located?
Is the DRY-ness worth it?

# What is @?

Let's start with the simple one. For a while, I always thought that `@` means it is a global variable. But actually it is not.
It is local to the instance of the class it is in.

# Rails getters and setters

```ruby
class Person
    attr_accessor :books
end
```

Under the hood, it actually creates these two methods in `Person` class

```ruby
def books
    @books
end

def books=(x)
    @books = x
end
```

As you can see, it's pretty much a short hand version to create getters and setters.
There are other shorthands like `attr_reader` and `attr_writer`

# Modules

Sometimes two different classes might share same methods.
Unfortunately they are not really similar that we cannot use inheritance.
One way of solving this is by using modules, or helpers.

```ruby
module BookHelper
  def add_a_book book
    @books << book
  end

  def reset_books
    @books = []
  end
end

class Person
  include BookHelper
  def initialize name
    @name = name
    reset_books
    add_a_book 'My Initial Book'
  end
end
```

This way if there's another class that needs to `add_a_book`, it can simply include the module


# Now what's the problem?

Imagine that the modules and classes are in different files. 
Those classes includes a lot of modules.
It may make you lose track, which variables are initialized in which class / modules. 
This is what happen to my current project
`@books` can be mutated from multiple modules making the code readability such a mess.


## Several gotchas as I familiarize myself with Ruby

I thought that `@books` actually means global variables. 
It is not and `@` means it is a local attribute

I learnt that some function names might look like an attribute name but they are not.
`Person.books` is actually a setter method, `@books` is the Person attribute.

Full code is below, you can run it on command line and see the result

```ruby
module BookHelper
  def add_a_book book
    @books << book
  end

  def remove_last_book
    @books.pop
  end

  def get_books
    @books
  end

  def reset_books
    @books = []
  end
end


class Person
  include BookHelper
  attr_accessor :books

  def initialize name
    @name = name
    reset_books 
    add_a_book 'My Initial Book'
  end

  def start_over
    reset_books
  end

  def buy_a_book title
    add_a_book title
  end

  def check_books
    @books
  end

  def throw_away_last_book
    remove_last_book
  end
end


# There are two ways of manipulating books, using BookHelper module and attr_accessor Person.books

# Using the module
a = Person.new 'Mary'
p a.check_books
a.buy_a_book 'New Ruby Guide'
p a.check_books
a.throw_away_last_book
p a.check_books
a.start_over
p a.check_books

# Using the attr_accessor
b = Person.new 'John'
b.books = ['Hack A Book']
p b.books


# To prove that @ is not global, let's compare Mary's against John's books
# Mary has 0 books while John has 1 book, 'Hack A Book'
p a.get_books === b.get_books
```

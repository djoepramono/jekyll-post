---
title: RSpec - Object references itself
---

Just came across this problem when using RSpec in one the Rails project that
I am working on: object references itself.

## Object references itself

The project is basically a REST web service which return a project information
in JSON format.

In the template file, there is

```ruby
r.element :project, @project do |project|
    r.element :type
    r.element :manager
end
```

Which is basically the details of the project including the manager of
the project. The manager, is not an object, not just a string.
*Rails is smart enough to map the manager structure into JSON ...*

And as you would have expected the `spec` files,

```ruby
let(:manager) { mock(Manager, first_name: "John", last_name: "Doe") }

let(:project) do
    project = Project.from_attributes(type: 'business')
    project.stub!(:manager).and_return(manager);
end

context 'project' do
    subject { custom_render(project) }
    it { subject.should include('manager') }
end
```

When the test is run, it failed with **Object references itself**

## The cause

It took a while to figure out what was the problem. Turned out that's
because the rspec mock potentially have several methods or attributes
that reference itself.

```ruby
mock(Manager, first_name: "John", last_name: "Doe")
```

When the above line is executed, it practically creates all the bells
and whistle that the `mock` object has and put **all of that**
onto `:manager`

```ruby
r.element :manager
```

## The solution

So the solution was to make sure that we only want to put certain attributes
into the `view` files. Thus the code was updated to

```ruby
r.element :project, @project do |project|
    r.element :type
    r.element :manager do |manager|
        r.element :type, manager.type
        r.element :name, manager.name
    end
end
```

and things were working fine again. Both the test and the actual REST
web service.

## Gotcha

If you notice, the above code potentially has one flaw, what if a project
doesn't have a manager. The attempt to get the manager's name would crash the web
service. Thus it would be good to validate that condition before hand.


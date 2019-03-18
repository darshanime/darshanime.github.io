+++
author = "Darshan Chaudhary"
date = 2019-03-18
title = "Objects and their responsibilities"
+++

The term "Object oriented programming" was coined by Alan Kay, a prominent computer scientist in 1967 while he was at grad school.

Having some prior experience with software development, he observed that one of the ways software fails to scale is having shared data without any clear owner for it. If any piece of the software can change any data structure, it would become very difficult to make sense of the system.

What he meant when he said Object oriented programming was that it was the object's responsibility to be

> encapsulated mini-computers in software which communicated via message passing rather than direct data sharing — to stop breaking down programs into separate “data structures” and “procedures”.

The role of the object in his notion was simple:

- Avoiding shared mutable state
  - The object would encapsulate all the data it has inside it and would expose `get`ters and `set`ters to allow others to change data. Since it would be the sole way to update data, the object would have "knowledge" and "approval" of the data change.

- Decoupling
  - Due to the lack of the shared data, the objects won't be tied to one another directly. The program is more easily extensible now, since changing one part of the software won't impact the other parts in unforeseen ways.


### DRY

Don't repeat yourself is a closely related idea in that there should be only 1 source of truth in a program. This involves avoiding not only straight duplication of information by the way of storing the same object attributes in multiple places but also applies to derived data.

As an example, consider the `Line` object. It can have attributes like the coordinates that make up the line; `x1`, `x2`, `x3` and `x4`:

```
module Geometry
  class Line
    def initialize(x1, y1, x2, y2)
      @y1 = y1
      @y2 = y2
      @x1 = x1
      @x2 = x2
    end
  end
end
```

If we were to add the `length` attribute to the `Line` object as well, it would be violating the DRY principle since `length` is a derived attribute, and if we forget to update the length any time the coordinates of the line are updated, there will be 2 values for the length, one from the `length` attribute and the other from the computation using the coordinates.


### Single Responsibility Principle

Combining these 2 ideas is the Single Responsibility Principle. Each object should only be responsible for one thing and one thing alone.

It should have the data related to doing it's single operation and expose methods to the outside world to allow it to interact with that data. The functionality it has should not be present anywhere else so as to not violate the DRY principle.

This would enable Alan Kay's vision of

> software running on a giant, distributed computer (the internet), where individual computers acted like biological cells, operating independently on their own isolated state, and communicating via message passing.

If there is shared mutable state, duplicate sources of information and every object owning some piece of shared responsibilities, it would be very difficult to build systems that can scale, are maintainable, extensible and bug free.

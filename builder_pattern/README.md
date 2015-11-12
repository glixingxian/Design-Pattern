# Builder Pattern

In one of your class, you have some constructors with different parameters (overloading).

Now problem starts when this object can be created with **lot of parameters**, some of them may be **mandatory** and others may be **optional**. So we need to write constructors for all the possible combinations?!

For this kind of problems, we could use builder pattern.  It uses a builder, that receives each initialization parameter step by step and then returns the resulting constructed object at once.

### Reference

* [Builder Design pattern in Java - Example Tutorial](http://javarevisited.blogspot.com/2012/06/builder-design-pattern-in-java-example.html#ixzz3rIxnkvSR)
* [Design Patterns - Builder Pattern - Tutorialspoints](http://www.tutorialspoint.com/design_pattern/builder_pattern.htm)
* [wiki](https://en.wikipedia.org/wiki/Builder_pattern)

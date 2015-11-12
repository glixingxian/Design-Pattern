# Open Close Principle

>Software entities (classes, modules, functions, etc.) should be **open for extension** and **closed for modifications**.

It simply means that **New functionality should be added with minimum changes in the existing code**.

### Benefit of OCP
_____
1. More robust because we are not changing already existing/tested class.

2. Flexible because we can easily accommodate new requirements.

3. Easy to test and less error prone.

### How to make code extensible
____
Basic principle of making your code extensible and following open closed principle is providing object to class at run time (**reflection**) and making use of polymorphism to invoke extended functionality (**overloading and overriding**).

If functionality is hard Coded than it wouldn’t be extensible but if you write **interface** and provide implementation of that interface at run time you make it extensible.

### Reference
____
* [Great Example of Open Closed Design Principle in Java](http://javarevisited.blogspot.com/2011/11/great-example-of-open-closed-design.html#ixzz3rIGYc700)
* [OCP - OODesign](http://www.oodesign.com/open-close-principle.html)

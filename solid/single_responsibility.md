# Single responsibility

>A class should have one and only one reason to change, meaning that a class should have only one job.

Responsibility here means "a reason for change". Single responsibility means that one class only need to be changed for one single reason.

### For what?
-----
For **loose coupling**, when we need to do some change for a reason, we only need to update one class.

When a class has more than one responsibility, there are also more triggers and reasons to change that class. If a class has more than one responsibility, then the responsibilities become coupled. Also when a responsibility is divided over more than one class, all classes part of that responsibility have to be changed. They are caught in the chain of change.

### How?
-----

Always try to give **every class its own and unique responsibility.**

### Reference
----------
* [SOLID Principles: Single Responsibility Principle -> What, Why and How](http://www.codeproject.com/Articles/611593/SOLID-Principles-Single-Respons)

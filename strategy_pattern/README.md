# Strategy Pattern

It provides a way to define a family of algorithms, encapsulate each one as an object (**one strategy**), and make them interchangeable to carry out a specific behavior.

Think about now you want to go out, you can choose take a bus, you can call a Taxi, you even want to take a bus firstly and then change to a bike. The Strategy pattern is to be used for this situation where you want to choose the algorithm/strategy to use at run-time.

In fact, we could choose "if else" to realize this. But this will cause the following problems:

* Every time you add a new algorithm/strategy, you need to change the code on client side.

* Many "If ... else ..." in your code, code maintenance will be more difficult.

So Strategy Pattern is here to help you add and choose an algorithm/strategy.

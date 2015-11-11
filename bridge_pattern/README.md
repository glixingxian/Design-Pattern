# Bridge Pattern

Also called **Handle/Body** Pattern. Its official definition is **decouple an abstraction from its implementation so that the two can vary independently**. A bridge to connect abstraction and its implementation.

For some situations, some objects have two or more dimensions of change. For example, we define an abstract vehicle, it could be car, truck, train and so on. A vehicle could have different behaviors/operations like transporting goods, transporting passages and so on. So now we have two dimensions of change.

Without bridge pattern. the normal way is to define an abstract vehicle, then a Car class extends it. Then a CarForGoods and CarForPassagers to extend Car class. We need also to do the same thing for trains, truck and so on. It costs so much to add a new vehicle or new behaviors.

With bridge pattern, we just separate vehicles and behaviors, so they could vary independently.

**The core is to change "Inheritance" to "Association".**

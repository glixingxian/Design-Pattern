# Proxy Pattern

Proxy Pattern provides a proxy object for some particular object. This proxy object will control a reference to the original object. It does not change the original interface and behavior, it just controls the original object.

But why we need a proxy to control the original object?

Think about now you need to support a resource-hungry object which means it will consume lots of resource to be instantiated. So you do not want to instantiate such objects unless and until they are actually requested by the client.

By Proxy Pattern, we could also add additional functionality, for exemple logs before and after each function, to the object of interest without changing the object's code.

To summary:

* **We want a proxy to control the original object**
* **We want a proxy to add additional functionality without changing original object's code**

In this chapter, we will see the following presentations:

1. A simle exemple with a resource-hungry object
2. Static Proxy
3. Dynamic Proxy

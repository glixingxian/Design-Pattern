# Dynamic Proxy Pattern

To realize dynamic proxy, we must implement [InvocationHandler](http://docs.oracle.com/javase/7/docs/api/java/lang/reflect/InvocationHandler.html) which is an interface implemented by the invocation handler of a proxy instance.

Each proxy instance has an associated invocation handler. When a method is invoked on a proxy instance, the method invocation is encoded and dispatched to the invoke method of its invocation handler.


```
public class ProxyHandler implements InvocationHandler {

    private Object targetObject;

    public Object newProxyInstance(Object targetObject){
        this.targetObject = targetObject;

        return Proxy.newProxyInstance(targetObject.getClass().getClassLoader(), targetObject.getClass().getInterfaces(), this);
    }

    public Object invoke(Object proxy, Method method, Object[] args)
            throws Throwable {

        System.out.println("start-->>" + method.getName());
        // ToDo some other operations you want
        Object result = null;
        try{
            // targetObject.method is invoked here by java reflection
            result = method.invoke(targetObject, args);
            System.out.println("success-->>" + method.getName());
        }catch(Exception e){
            e.printStackTrace();
            System.out.println("error-->>" + method.getName());
            throw e;
        }

        return result;
    }
}

```

To test:

Use the same UserManager in previous exemple

```
public class Client {

    public static void main(String[] args) {

        ProxyHandler proxyHandler = new ProxyHandler();
        UserManager userManager = (UserManager)proxyHandler.newProxyInstance(new UserManagerImpl());

        String name = userManager.addUser("001");
        System.out.println("client.main-->>" + name);
    }

}
```

Pros：
1. A single ProxyHandler could work for all the agented objects and also their functions. We do not need to repeat codes like static proxy any more.
2. Because of java reflection, the target object could be invoked at runtime.

Cons：
1. A little slower than static.
2. Not that readable as static.
3. Only agent the class which implments an interface

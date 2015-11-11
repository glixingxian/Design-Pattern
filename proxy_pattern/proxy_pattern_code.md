# Proxy Pattern Exemple

This is a simple exemple, here we use a proxy to control UserManagerImpl which is a resource-hungry object. It takes 3 second to be instantiated. So we want to instantiate it only when we really have to.

**Interface:**

```
public interface UserManager {
    public void doSomething();
}
```

**Original object:**

```
public class UserManagerImpl implements UserManager {

    public UserManagerImpl() {
        // Sleep 3s to indicate a resource-hungry object.
        // It takes 3s to instantiate!
        Thread.sleep(3000);
    }
    public void doSomething() {
        System.out.println("I m thinking");
    }

}
```

**Proxy:**

Only when **doSomething()** is invoked, UserManagerImpl will be instantiated.

```
public class UserManagerImplProxy implements UserManager {

    private UserManager userManager;
    private String userId;

    public UserManagerImplProxy(String userId){
        this.userId = userId;
    }

    public void doSomething() {
        if(userManager == null) {
            userManager = new UserManagerImpl();
        }
        userManager.doSomething();
    }

    // Some other functions. Could be some additional
    // functionality without changing original object's code

}
```

**To test:**

```
public class Client {

    public static void main(String[] args) {
        UserManager userManager = new UserManagerImplProxy("001");
        // ToDo invoke some other functions of userManager before
        // we want to doSomething(), or we even do not need to instantiate it.

        userManager.doSomething("001");
    }
}
```




# Static Proxy Pattern

It's static because when **compile**, the proxy has already decided to which object to agent. In the following exemple, the proxy will agent all subclasses of UserManager.

Btw, the following exemple is not resource-hungry. Proxy here is used to add additional functionality.

**Interface:**

It will be implemented by both the original object and proxy:

```
public interface UserManager {
    public void addUser(String userId);
    public void delUser(String userId);
}
```

**Original object:**

```
public class UserManagerImpl implements UserManager {

    public void addUser(String userId) {
        System.out.println("UserManagerImpl.addUser() userId-->>" + userId);
    }

    public void delUser(String userId) {
        System.out.println("UserManagerImpl.delUser() userId-->>" + userId);
    }

}
```

**Proxy:**

In proxy, we add logs before and after the original functions

```
public class UserManagerImplProxy implements UserManager {

    private UserManager userManager;

    public UserManagerImplProxy(UserManager userManager){
        this.userManager = userManager;
    }

    public void addUser(String userId) {
        System.out.println("start-->>addUser() userId-->>" + userId);
        userManager.addUser(userId);
        System.out.println("success-->>addUser()");
    }

    public void delUser(String userId) {
        // Add same outputs as addUser
    }

}
```

**To test:**

```
public class Client {

    public static void main(String[] args) {
        UserManager userManager = new UserManagerImplProxy(new UserManagerImpl());
        userManager.addUser("001");
        userManager.delUser("001");
    }
}
```

With static proxy, **it is not easy to expand**. When we have more objects to be agented. We need to create more proxies. What's more, we need also to **repeat codes**. For exemple, in the previous exemple, we need to add logs in every functions. It's why sometimes we need dynamic proxy.

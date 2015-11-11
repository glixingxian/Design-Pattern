# Observer Pattern Exemple

#### Subject:

The one to be observed. All the others listen to its change.

```
public class Subject {

    // List to store all the observer
    private List<Observer> list = new ArrayList<Observer>();
    private String state;

    public int getState() {
        return state;
    }

    // Register an observer
    public void attach(Observer observer){
        list.add(observer);
    }

    // Remove an observer
    public void detach(Observer observer){
        list.remove(observer);
    }

    // Notify all observers to update
    public void nodifyObservers(String newState){
        for(Observer observer : list){
            observer.update(newState);
        }
    }

    public void change(String newState){
        state = newState;
        // State changed. So nodify all observer
        this.nodifyObservers(state);
    }
}
```

#### Abstract observer:

All observers need to implement it:

```
public interface Observer {
    // Here we keep an object from subject. This is called pull in this pattern.
    // Check next section for more details. Now with an instance of Subject.
    // You could use all the infos from it in your update()
    protected Subject subject;
    public void update();
}
```

ConcreteObserver - You could create as many observers as you like. Here we only create one:

```
public class ConcreteObserver implements Observer {

    public ConcreteObserver(Subject subject){
        this.subject = subject;
        // Register when create an instance
        // You can also realize it in many other ways
        this.subject.attach(this);
    }

    @Override
    public void update() {
        System.out.println( "State changed: " + subject.getState() );
    }
}
```

#### To test:


```
public class Client {

    public static void main(String[] args) {

        ConcreteSubject subject = new ConcreteSubject();
        Observer observer = new ConcreteObserver(subject);
        subject.change("new state");
    }
}
```

#### Result:

```
State changed: new state
```

So observer is updated in the mean time when subject changes in the meantime. it works here like a listener which listens to the changes in subject.

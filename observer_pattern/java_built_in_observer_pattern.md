# Java Built In Observer Pattern

In java.util, We already have a Class called Observable and an **interface** called Observer, we could use them directly to desgin our patterns.

#### Observer Interface:

This interface only has one method - update(), so when the observed object changes its state and uses notifyObservers() to notify Observers to update().

```
public interface Observer {
    void update(Observable o, Object arg);
}
```

#### Observable Class:

In this class, we already have functions like add/remove an oberser and also other functions, but still we have two functions to pay attention：

1. setChanged(): When it's called, it will set a internal flag to represent whether it has changed its state.
2. notifyObservers(): When it's called, all the registered Observers will run their update() methodes.

```
public class Observable {

    private boolean changed = false;
    private Vector obs;

    /** Construct an Observable with zero Observers. */
    public Observable() {
        obs = new Vector();
    }

    // Add an observer
    public synchronized void addObserver(Observer o) {
        if (o == null)
            throw new NullPointerException();

        if (!obs.contains(o)) {
            obs.addElement(o);
        }
    }

    // Remove an observer
    public synchronized void deleteObserver(Observer o)     {
        obs.removeElement(o);
    }

    public void notifyObservers() {
        notifyObservers(null);
    }

    // Notify observers to update
    public void notifyObservers(Object arg) {

        Object[] arrLocal;

        synchronized (this) {

        if (!changed)
            return;
            arrLocal = obs.toArray();
            clearChanged();
        }

        for (int i = arrLocal.length-1; i>=0; i--)
            ((Observer)arrLocal[i]).update(this, arg);
    }

    // Clear all observers
    public synchronized void deleteObservers() {
        obs.removeAllElements();
    }

    // Set changed flag to true
    protected synchronized void setChanged() {
        changed = true;
    }

    // Set changed flag to false
    protected synchronized void clearChanged() {
        changed = false;
    }

    // Check whether state has changed
    public synchronized boolean hasChanged() {
        return changed;
    }

    /**
     * Returns the number of observers
     * @return  the number of observers of this object.
     */
    public synchronized int countObservers() {
        return obs.size();
    }
}
```

## Exemple:

Here is a simple exemple. An observer class called Wathcer implementing Observer interface. An observed called Watched extending Observable class.


#### Watched Class:

```
public class Watched extends Observable{

    private String data = "";

    public String getData() {
        return data;
    }

    public void setData(String data) {

        if(!this.data.equals(data)){
            this.data = data;
            setChanged();
        }
        notifyObservers();
    }

}
```

#### Watcher Class:


```
public class Watcher implements Observer{

    public Watcher(Observable o){
        o.addObserver(this);
    }

    @Override
    public void update(Observable o, Object arg) {

        System.out.println("State changed：" + ((Watched)o).getData());
    }

}
```

#### To test:


```
public class Test {

    public static void main(String[] args) {

        Watched watched = new Watched();
        Observer watcher = new Watcher(watched);

        watched.setData("start");
        watched.setData("run");
        watched.setData("stop");
    }

}
```

By the way, it's Pull instead of Push.

# Bridge Pattern Code

Here is simple exemple:

There are two kinds of vehicle - Car and Camion
Both of them want to transport - Goods and Passagers

Think about also, in the future, we may have train, boat and so on. In the mean time, we also want to transport weapons or something else.

**Abstration: **

Vehicle which does behaviours - tranport

```
public abstract class Vehicle {

	private Transport implementor;

	public void transport(){
		implementor.transport();
	}
	public Transport getImplementor() {
		return implementor;
	}
	public void setImplementor(Transport implementor) {
		this.implementor = implementor;
	}

}
```

**RefinedAbstraction: **

Vehicle extended to do more behaviours. (Not used here to simplify exemples)

```
public class RefinedVehicle extends Vehicle {

    public RefinedVehicle() {
        super();
    }

    // Other operation
    public void otherOperation(){
    }
}
```
#### A Car:
```
public class Car extends Vehicle {
	@Override
	public void transport() {
		System.out.print("Car");
		super.transport();
	}
}
```
#### A Camion:
```
public class Camion extends Vehicle {
	@Override
	public void transport() {
		System.out.print("Camion");
		super.transport();
	}
}
```
#### Implementor:

An interface to define behaviours - transport

```
public interface Transport {
	public void transport();
}
```

#### Tranport goods:

```
public class Goods implements Transport{
	@Override
	public void transport() {
		System.out.println("send goods");
	}
}
```

#### Tranport passagers:

```
public class Passagers implements Transport{
	@Override
	public void transport() {
		System.out.println("send passagers");
	}
}
```

#### Client to test:

```
public class Client {

	public static void main(String[] args) {

		Camion camion = new Camion();
        // Transport goods firstly
		camion.setImplementor(new Goods());
		camion.transport();
		// Transport passagers secondly
		camion.setImplementor(new Passagers());
		camion.transport();

		Car car = new Car();
		// Transport goods firstly
		car.setImplementor(new Goods());
		car.transport();
		// Transport passagers secondly
		car.setImplementor(new Passagers());
		car.transport();
	}
}
```

# Bridge Pattern Code

Here is simple example:

There are two kinds of vehicle - Car and Truck
Both of them want to transport - Goods and Passagers

Think about also, in the future, we may have train, boat and so on. In the mean time, we also want to transport weapons or something else.

**Abstraction: **

Vehicle which does behaviors - transport

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

Vehicle expended to do more behaviors. (Not used here to simplify examples)

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
public class Truck extends Vehicle {
	@Override
	public void transport() {
		System.out.print("Truck");
		super.transport();
	}
}
```
#### Implementor:

An interface to define behaviors - transport

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

#### Transport passagers:

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

		Truck truck = new Truck();
        // Transport goods firstly
		truck.setImplementor(new Goods());
		truck.transport();
		// Transport passagers secondly
		truck.setImplementor(new Passagers());
		truck.transport();

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

# Instantiating Classes

As we discussed in the introduction to OOP, we have the class(which is the blueprint or mold) to make objects(called instances).

Now, after knowing how we can make the class, we are going to [instantiate](https://www.merriam-webster.com/dictionary/instantiate)(make an instance of) classes.

## How are we doing this?

We'll use the car example from before throughout this document.

```java
public class Car {
    private String color;
    private String brand;
    private int currentSpeed;

    public Car(String carColor, String carBrand){
        color = carColor;
        brand = carBrand;
        currentSpeed = 0;
    }

    public void accelerate(int speedIncrease) {
        currentSpeed += speedIncrease;
        System.out.println("The car accelerated. Current speed is: " + currentSpeed + " km/h.");
    }

    public void brake(){
        currentSpeed = 0;
    }

    public void honk() {
        System.out.println("Honk!");
    }

    public void printDetails(){
        System.out.println("Color: " + color + ", Brand: " + brand);
    }
}
```

In order to create an instance of class elsewhere, like in the main method, we'll use the `new` keyword and call the constructor of the class using it.

```java
public class Main{
    public static void main(String[] args){
        Car ourCar = new Car("Gray", "Volvo");
    }
}
```

Notice how we now have a variable of type `Car`! this is our newly created object.

Let's break down what we just did:

1. We created a variable of type `Car`
2. Called it `ourCar`
3. used the `new` keyword to make a new instance of the `Car` class, and used the constructor to initialize it's properties.

## Using the object

Okay, so we created the instance. Now what?

To actually use the car, we need to access and call it's methods.
We do this the following way:
```java
public class Main{
    public static void main(String[] args){
        Car ourCar = new Car("Gray", "Volvo");
        ourCar.honk(); // "Honk!" is printed
        ourCar.accelerate(40); // "The car accelerated. Current speed is: 40 km/h" is printed
    }
}
```

so now we called methods that changed the values of properties inside that specifiec object.

## Multiple Instances

At the beginning of the introduction to OOP, we established that one of the most important advantages that OOP has to offer is, well, creating multiple of the same thing, with "blueprints".

Now that we have created the blueprint, we can create as many objects as we want:
```java
public class Main{
    public static void main(String[] args){
        Car ourCar = new Car("Gray", "Volvo");
        Car diffrentCar = new Car("Red", "Ferrari");
        ourCar.honk(); // "Honk!" is printed
        ourCar.accelerate(40); // "The car accelerated. Current speed is: 40 km/h" is printed
        ourCar.printDetails(); // "Color: Gray, Brand: Volvo" is printed
        diffrentCar.honk(); // "Honk!" is printed, this is the same for both instances
        diffrentCar.printDetails(); // "Color: Red, Brand: Ferrari" is printed, these are diffrent instances.
    }
}
```

## Objects as reference types

As you might remember from when we just learned about data types, that there are two types of them - primitives, and references.
As objects are not primitives, they must be references.

### What does that mean for us?
This means that when passing our objects to methods(or even to other objects) via parameters, we are actually passing a reference to that object.

In practice, this means that changes made to an object out of the scope that it has been created in will affect all scopes that have that object's reference.

Let's look at the following example:
```java
public class Main{
    public static void main(String[] args){
        Car ourCar = new Car("Black", "Mazda");
        doThingsToCar(ourCar); // Now the current speed of the is 50, even in this scope!
    }

    public static void doThingsToCar(Car theCar){
        theCar.accelerate(50);
    }
}
```

> In the [Strings](../basic-java/6-strings.md#strings-as-a-reference-type) document we established that Strings are of reference type as well, this is because that Strings are objects too under the hood.

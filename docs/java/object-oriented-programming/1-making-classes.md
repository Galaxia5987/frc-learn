# Creating Classes

In this section we are going to implement in Java the theoretical knowledge we gained in the previous document.

Everything in Java is associated with classes and objects, you might have noticed that when we created our simple "Hello World" program, even then, we had to use classes.

## Creating a class

Creating classes is very simple in Java. Each file can have one class, named exactly like it's file name.
For example, for a file named `Car.java`, we'll have the following class:
```java
public class Car{

}
```

> Notice the public keyword. It just means that other classes are able to access and create objects of our class.

## Defining Properties

As we discussed in the last document, each class has it's properties.
A property is a variable, which is defined in the global scope(which means that everyone inside the class can access it).
We can define properties as follows:
```java
public class Car{
    public String color;
    public String brand;
    public int currentSpeed;
}
```

## Defining Methods

Methods represent the behaviors or actions that our class can perform. 
Just like properties are variables defined in the class scope, methods are functions defined within the class.

Let's add some behaviors to our Car class. A car should be able to accelerate, brake and honk its horn:
```java
public class Car {
    public String color;
    public String brand;
    public int currentSpeed;

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
}
```

## Constructor

Before we build our car, we need a way to set its initial state - like its brand or color at the exact moment it get's out of the factory.
We do this using a constructor.

A constructor is a special method of code that runs automatically whenever a new object is created from the this class.
It looks a lot like a method, but it has two rules:

1. It must have the **exact** same name as the class.

2. It cannot have a return type (not even void), we just leave it empty.

Let's add a constructor to our `Car` class so we can assign a brand and a color as soon as the car is built:

```java
public class Car {
    public String color;
    public String brand;
    public int currentSpeed;

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
}
```

The constructor behaves like every other function, it can have parameters, and has actions inside it's scope.

Another advantage we have to using constructors is that we can guarantee that the properties `color` and `brand` would have a value, as we are forced to provide one at initialization.

## Access Modifiers

If you remember from last document, we talked about encapsulation and abstraction, which meant hiding implementation details from the interface we could interact with.

Up until now, everything we defined was `public`, which meant that everything and everyone could access it. This can create a problem with the encapsulation principle.

To fix this, we have access modifiers - these are modifiers which can make a property or method only accessible from a certain scope(In our cases, only inside the class, or inside the class and outside).

We have 2 access modifiers(we actually have 4, but we'll rarely use the odd ones):
1. `public`, the one we used so far. Means that a property or method can be accessed or called inside or outside the class without any regulation.

2. `private` which means that a property or method can only be accessed or called from the class scope.

### The fix to the `Car` example

As our previous `Car` example breaks encapsulation, let's see how we can fix this:
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
}
```

Now, we have a `Car` class which it's color and brand can only be defined once, and we can only use the provided controls to control it.
This is now the perfect class.

In the next document we'll see how we can actually use this class from other scopes and classes(like the Main class and function!).
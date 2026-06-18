# Interfaces

In the previous documents we learned about how we can implement polymorphism with class inheritance, and seem all of the problems it can bring.

Here we will learn on a diffrent, simpler, and more elegant way to do polymorphism, called "interface".

An interface can be simply thought of as a contract. It says to Java, I guarantee you that this class has an implementation for these methods, you can safely call it.

## Syntax

`interface` is a keyword in Java, and just like classes, every interface needs it's own file.

```java
// Flyable.java
public interface Flyable {
    public void fly();
}
```

We defined what a class that is `Flyable` needs to implement in order to be considered of type `Flyable`.

We don't define how it should do it just yet, just the methods it has.

When using interfaces, we use the keyword `implements` instead of `extends`.

```java
// Airplane.java
public class Airplane implements Flyable{
    @Override
    public void fly(){
        System.out.println("This airplane is flying!");
    }
}

// Pigeon.java
public class Pigeon implements Flyable {
    @Override
    public void fly(){
        System.out.println("This pigeon is flying!");
    }
}
```

Now, we can use this interface to group completely unrelated objects together based solely on their capabilities, rather than their family tree!

Just like we did with inheritance, we can use the interface as the type for our variables.
This allows us to use the exact power of polymorphism, but without the constraints of class inheritance.

## Usage Example

Let's look at how we can use our new Flyable interface in practice:

```java
public class Main {
    public static void launchIntoAir(Flyable flyingObject) {
        flyingObject.fly();
    }

    public static void main(String[] args) {
        Airplane myPlane = new Airplane();
        Pigeon myPigeon = new Pigeon();

        System.out.println("Ready for takeoff:");
        launchIntoAir(myPlane);  

        System.out.println("Shooting the bird off the balcony:");
        launchIntoAir(myPigeon);
    }
}
```

## How Interfaces Solve Our Previous Problems

By shifting our design mindset from inheritance to  interfaces, we elegantly solve the issues we had in the last document.

Let's take a look at how flexible this makes our classes:

```java
public class Pigeon extends Bird implements Flyable, Walkable, Petable {
    
    @Override
    public void fly() {
        System.out.println("Pigeon flying!");
    }

    @Override
    public void walk() {
        System.out.println("Pigeon walking!");
    }

    @Override
    public void pet() {
        System.out.println("Petting softly...");
    }
}
```

## If You Like To Learn More

If you liked this topic, and like to learn a bit more, I really like [this video](https://www.youtube.com/watch?v=pbsTy5V_pxA), which lays all the problems of inheritance and explains them in really simple terms. Worth a watch.
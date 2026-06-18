# Inheritance
Inheritance in Java is a concept that allows a class to acquire properties and methods from another class.

It helps in creating a new class from an existing class(which is used as the base to the new class), helps code reusability and better organization.

* A subclass can reuse the fields and methods of the parent class without rewriting the code.

* A subclass can add its own fields and methods to extend functionality of an already existing class.

We define this behaviour using the `extend` keyword in Java.

Take the following simple example:

```java
// Base class, Animal.java
public class Animal {
    // Shared methods that all animals will get
    public void eat() {
        System.out.println("This animal is eating.");
    }
    
    public void sleep() {
        System.out.println("This animal is sleeping.");
    }
}

// Child class, Dog.java
class Dog extends Animal {
    // Dog inherits eat() and sleep() from Animal, but extends functionality with its own unique behavior
    public void fetch() {
        System.out.println("The dog is fetching a ball.");
    }
}

// Child class, Bird.java
class Bird extends Animal {
    // Bird inherits eat() and sleep() from Animal, but extends functionality with its own unique behavior
    public void fly() {
        System.out.println("The bird is flying in the sky.");
    }
}

// Child class, Horse.java
class Horse extends Animal {
    // Horse inherits eat() and sleep() from Animal, but extends functionality with its own unique behavior
    public void run() {
        System.out.println("The horse is running across the field.");
    }
}
```

## Types when using inheritance

When using inheritance, it is worth mentioning that the variable type can also be the super class. Why is it powerful?

Let's look at the following example:
```java
public class Main {

    // Because of inheritance, it will accept any subclass of Animal!
    public static void performDailyRoutine(Animal animal){
        animal.eat();   // Java knows all Animals can eat
        animal.sleep(); // Java knows all Animals can sleep
        
        // we cant do animal.fetch(); Java only knows this is an Animal, not specifically a Dog.
    }

    public static void main(String[] args) {
        Dog myDog = new Dog();
        Bird myBird = new Bird();
        Horse myHorse = new Horse();

        System.out.println("Starting the dog's routine:");
        performDailyRoutine(myDog);

        System.out.println("Starting the bird's routine:");
        performDailyRoutine(myBird);

        System.out.println("Starting the horse's routine:");
        performDailyRoutine(myHorse);
    }
}
```

Think what would happen if we would've written this without inheritance. It would quickly be a huge mess, with a diffrent function for every type, inheritance saves us all of this mess.

Simple enough, right? This is the basic usage of inheritance.

Next we'll see a diffrent type of inheritance, which is more commonly used in our robot code.
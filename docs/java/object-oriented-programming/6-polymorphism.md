# Polymorphism
> "In object-oriented programming, polymorphism is the provision of one interface to entities of different data types. The concept is borrowed from a principle in biology in which an organism or species can have many different forms or stages." - Wikipedia, [Polymorphism](https://en.wikipedia.org/wiki/Polymorphism_(computer_science))

As we established in the previous document, Inheritance lets us inherit properties and methods from another class.
Polymorphism(from Greek, which means "many-shaped") "overrides" methods to perform different tasks.
This allows us to perform a single action in different ways.
Basiclly, having a united interface for an action done in many ways.

Let's look at the `Animal` example from before again, but change it to be polymorphic:
```java
// Base class, Animal.java
public class Animal {
    public void eat() {
        System.out.println("This animal is eating.");
    }
    
    public void sleep() {
        System.out.println("This animal is sleeping.");
    }

    public void makeSound(){
        System.out.println("Default sound for a generic animal");
    }
}

// Child class, Dog.java
class Dog extends Animal {
    // Dog inherits eat() and sleep() from Animal, and overrides makeSound() and makes it it's own
    @Override
    public void makeSound() {
        System.out.println("Bark Bark!");
    }
}

// Child class, Bird.java
class Bird extends Animal {
    // Bird inherits eat() and sleep() from Animal, and overrides makeSound() and makes it it's own
    @Override
    public void makeSound() {
        System.out.println("Chirf Chirf!"); // What sound does a bird do?! I honestly don't know.
    }
}

// Child class, Horse.java
class Horse extends Animal {
    // Horse inherits eat() and sleep() from Animal, and overrides makeSound() and makes it it's own
    @Override
    public void makeSound() {
        System.out.println("Hoo Hoo!"); // Yeah i'm lost for examples at this point
    }
}
```

Now, we have a united interface for all animals, each animal with a diffrent implementation of `makeSound`!

## Usage Example

Let's look at the following example to see the power of polymorphism:

```java
public class Main {

    public static void listenToAnimal(Animal animal) {
        animal.makeSound(); // Java will call the correct implementation of makeSound() based on what animal was passed!
    }

    public static void main(String[] args) {
        Dog myDog = new Dog();
        Bird myBird = new Bird();
        Horse myHorse = new Horse();

        System.out.println("Let's hear the dog:");
        listenToAnimal(myDog);  

        System.out.println("Let's hear the bird:");
        listenToAnimal(myBird); 

        System.out.println("Let's hear the horse:");
        listenToAnimal(myHorse); 
    }
}
```

See what we did there? Java automatically figured out which implementation it needed to run, and run the correct one. Great!

## Danger!

As cool as polymorphism in inheritance is, it can lead to many problems.

### Strict Relationship
Inheritance strictly relies on an "is a" relationship (a Dog **is an** Animal).
But what happens when completely unrelated objects share a behavior?

Imagine we have a Bird class that has a `fly()` method.
Now, we want to create an Airplane class. An airplane can also fly! But an Airplane is clearly not an Animal.

We can't put `fly()` inside Animal(dogs don't fly).

We can't make Airplane extend Animal(an airplane is an Animal).

If you write a separate `fly()` method for both, you lose the magic of polymorphism - you can't group them together.

### Single Inheritance

In Java, a class can only extend one superclass.

> This is to prevent the ["Diamond Problem"](https://www.geeksforgeeks.org/cpp/diamond-problem-in-cpp/).

But real life isn't always that simple. A lot of time, we will need to provide multiple interfaces.

### The Forced Stuff Problem
(Could'nt find a better name, sorry!)

When we inherit from a superclass, we inherit everything
Sometimes, that's not what we want.

Let's say we put a `fly()` method in our Bird superclass because most birds fly. Then, you create a Penguin class.
By extending Bird, it will automatically inherit `fly()`.
Now we have a penguin with a `fly()` method, which makes no sense!
We would have to awkwardly override the method to do nothing.

### Solution

We actually rarely use class based polymorphism because of all of these problems, and have a special tool called interfaces that fixes this.
Next, we will learn about interfaces.
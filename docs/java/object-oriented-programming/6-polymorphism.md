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
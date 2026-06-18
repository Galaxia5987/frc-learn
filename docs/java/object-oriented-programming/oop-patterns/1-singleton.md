# Singleton

The first, and the most important design pattern for us is the "Singleton".

At it's core, the Singleton is a design pattern that lets you ensure that a class has only one instance, while providing a global access point to this specific one instance.

## Why do we need it?

Imagine having a our swerve drivetrain as an object in code, we only have one swerve chassis, and thus only need one instance of it in our codebase.

In this example, the Singleton pattern gives us two distinct advantages:

1. **Global Access**: We don't need to think about in what scope we stored the instance. Every scope of every class has access to the instance through it's static getter.

2. **One Instance Promise**: We don't have to worry about accidentally creating multiple instances of our drivetrain(which we obviously have one). Instead, everything is managed for us.

## How do we write it?

Here is an example structure for a Singleton patten. As of all patterns, this is an example structure, and this pattern can be implemented in many ways.

```java
public class Singleton {
    private static Singleton instance;

    private Singleton(){}

    public static Singleton getInstance(){
        if(instance == null){
            instance = new Singleton();
        }
        return instance;
    }
}
```

And that's it! We can add as many methods or properties as we want, and we can have access to the object by using the static getter(`Singleton.getInstance()`).

Let's look at a more practical example:
```java
public class Drive {
    private static Drive instance;

    private int speed = 0;

    private Drive() {}

    public static Drive getInstance(){
        if(instance == null){
            instance = new Drive();
        }
        return instance;
    }

    public void forward(int newSpeed){
        speed += newSpeed;
    }

    public void backward(int newSpeed){
        speed -= newSpeed;
    }
}
```

Cool! now let's look on how we can use this:
```java
public class SomeSystem {
    public void doStuff(){
        Drive.getInstance().forward(5);
    }
}
```

We can also call it the same way from any other class or scope:
```java
public class SomeOtherClass {
    public void moreStuff(){
        Drive.getInstance().backward(5);
    }
}
```
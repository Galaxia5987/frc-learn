# Lambdas

A Lambda(which is literally a greek letter, $\lambda$) is a way to represent a function as data(also called an anonymous function).

This document about lambdas is heavily inspired by WPILib's document ["Treating Functions as Data"](https://docs.wpilib.org/en/stable/docs/software/basic-programming/functions-as-data.html). My try here was to simplify and shorten it, as it did contain some unnecessery advanced terms, and some was written for C++. Definitely worth a read if you are interested.

## Introduction

One of the first things we've learned here is to write a function.
Functions are a fundamental part of organized code - writing functions lets us avoid duplicating the same piece of code over and over again. Instead of writing duplicated sections of code, we call a single function that contains the code we want to execute from multiple places. If the section of code needs some additional information about its surrounding scope to run, we pass those to the function as "parameters", and if it needs to return something back to the rest of the code once it finishes, we call that a "return value"(together, the parameters and return value are called the function's "signature").

Sometimes, we need to pass functions from one part of the code to another part of the code.

This might seem like a strange concept, if we’re used to thinking of functions as part of a class definition rather than objects of their own. But at a basic level, functions are just data - in the same way we can store an integer or a double as a variable and pass it around our program, we can do the same thing with a function.

## Why Would We Want to Treat Functions as Data?

Typically, code that calls a function is coupled to(depends on) the definition of the function.
This becomes problematic when the code calling the said function(Our robot library, in this case, [WPILib](https://docs.wpilib.org/en/stable/index.html)) is developed without direct knowledge of the code that defines the function.

Sometimes we solve this challenge through the use of interfaces(See [interfaces](../object-oriented-programming/7-interfaces.md) if you are still unsure on what they are).
However, often we really only have a dependency on a single function, rather than on an entire class.

For example, When we write robot code, we have several ways to execute certain code whenever a joystick button is pressed - one of the easiest and cleanest ways to do this is to allow to pass a function to one of the joystick methods. This way, the user only has to write the code that deals with the interesting things (e.g., "move my robot arm") and not the boring, error prone things("properly read button inputs from a joystick").

In these cases, we want to be able to pass a single function as a piece of data, as if it were a variable - it doesn't make sense to ask the user to provide an entire class, when we really just want them to give us a single function.

It's important to note passing a function is not the same as calling a function. When we call a function, we execute the code inside of it and either receive a return value. When we pass a function, nothing in particular happens immediately. Instead, by passing the function we are allowing some other code to call the function in the future. Seeing the name of a function in code does not always mean that the code in the function is being run at all!

## The `Runnable` type

In Java, we have a special type called `Runnable`. This type is our function type, we give it a reference to a method, or create one using a lambda, and it can later be run.

Behind the hood, this `Runnable` is just an interface with the `run` method that we "override" when defining the method reference or lambda.

## Method References

A method reference lets us pass an already existing function:

```java
// Roomba.java
public class Roomba {
    public void cleanRoom() {
        System.out.println("cleaning room...");
    }
}

// Main.java
public class Main {

    public static void runTaskIfNeeded(boolean isDirty, boolean arePeopleOut, Runnable task){
        if(isDirty && arePeopleOut){
            task.run();
        }
    }

    public static void main(String[] args) {
        
        Roomba myRoomba = new Roomba();

        Runnable task = myRoomba::cleanRoom;

        runTaskIfNeeded(true, true, task); // This will eventually print "cleaning room..."
    }
}
```

The expression `myRoomba::cleanRoom` is a reference to the `cleanRoom` method of the `myRoomba` object. It is not a method call - this line of code does not itself call the `cleanRoom` method. Instead, it returns a Runnable object that can be run when needed.

Remember that in order for this to work, `cleanRoom` must be a Runnable - that is, it must take no parameters and return no value. So, its signature must look like this:
```java
public void cleanRoom()
```

If the function signature does not match this, Java will not be able to see the method reference as a Runnable.

## Lambda Expressions

If we do not already have a named function that does what we want, we can define an inline, anonymous function - that means, right inside of the call to `runTaskIfNeeded`! We do this by writing our function with a special syntax that uses an "arrow" symbol:
```java
runTaskIfNeeded(true, true, () -> {System.out.println("cleaning room...")});
```
While this may look a bit funky, it is just another way of writing a function - the parentheses before the arrow are the function’s argument list, and the code contained in the brackets is the function body.
Note again that this does not call the function, but defines it and passes it to the `runTaskIfNeeded` to be run later if the conditions are met.


This syntax is extremely important for us when programming our robot, and you'll see it being used a lot.
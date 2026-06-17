# Static Methods
Think for a minute what our robot code would consist of. You might say stuff like the drivetrain(swerve), maybe an arm, maybe a shooter, maybe a vision system.

What would happen if we would to go and put all of that code and logic into one `main` function like we saw? We would have a huge mess with thousands of lines of code.

## Introduction to Functions
In order to organize our code, we use a concept called "functions".

Just like loops save you from writing the same code multiple times, functions save you from having a massive, unreadable wall of code.

Think of a function like a specialized black box machine. 
Let's say you have a coffee machine. You give it inputs (water and coffee beans), it performs a specific task (brewing the coffee), and it gives you an output(a cup of coffee).
You don't need to know how the machine work, you just need to know its name and what to give it.

## Methods
In Java we call these functions "methods", this has a reason, and we will cover this reason later when learning OOP(Object Oriented Programming).

Methods have 3 things:

* **Inputs**: Called the "parameters". These are variables(values) that we can pass to the function.
Remember when we talked about scopes? We said that each scope has it's own variables, and variables from diffrent scopes can't talk to each other. Because of that, we pass the variables that we want our method to know about as it's "parameters".

* **Name**: We need to name the method in order to know, what it's composed of, and what it does. For the coffee machine example, we can use the name `makeCoffee`.
We use the same style guides for methods and variables(`camelCase`).

* **Output**: Called the "return type". This is the data type that the method output(returns). If the method return nothing(it just does something, and doesn't return any value), we use a special type called `void`.

### Structure
In order to construct a method we use the following structure:
```java
accessModifiers staticModifier returnType name(parameters){
    // Actions
}
```

Whoah, this looks way more complicated.

Methods in Java has some more features than just the simple "function" like, and we will learn about all of these features later. For now, we will write our functions like the following, ignoring what access modifiers or staticModifier mean.
We'll take the following simple example:
```java
public static int computeTimesTwo(int ourNumber){
    return ourNumber * 2;
}
```
In this example we wrote `public static`, for now, every method should start like this.

After that, we specified the return type(the output of the method). We said for it to be of type integer, which means that the output of this method must be an integer.

Next, we defined the name of the method as `computeTimesTwo`.

Inside the parentheses we specified our one parameter, of type integer and called it `ourNumber`. ourNumber is a regular variable of type integer inside the method scope.

We then opened the method scope(the curly braces `{}`), and specified one action, return the value `ourNumber * 2` to who called the method.

We now understand how to define a method!
So how do we call it?

For example, if we had our main method like this, and wanted to print the output of the function we just created with the input `2`:
```java
public static void main(String[] args){
    int coolNumber = 2;
    int ourNumberTimes2 = computeTimeTwo(coolNumber);
    System.out.println(ourNumberTimes2);
}
```

This prints the number `4` on the screen.

### Multiple Parameters

What if our machine needs more than just one input? Going back to the coffee machine, we need both water and coffee beans.

In Java, we can pass as many parameters as we want into a method. We just separate them with a comma `,`.

Let's write a method that takes two numbers and adds them together:
```java
public static int addNumbers(int firstNumber, int secondNumber) {
    int sum = firstNumber + secondNumber;
    return sum; 
}
```

When we call this method, we just put in two numbers in the exact order we defined them:
```java
public static void main(String[] args) {
    int myTotal = addNumbers(5, 10);
    System.out.println(myTotal); // This prints 15
}
```

### The `void` Return Type

Earlier, we mentioned that if a method doesn't return any data, we use the special `void` type.

Let's bring this back to our robot code. If you tell the robot's shooter mechanism to spin up to a certain speed, you don't necessarily need a mathematical answer back, you just want the robot to do the action.

```java
public static void spinShooter(int targetSpeed) {
    System.out.println("Spinning the shooter motors up to " + targetSpeed + " RPM!");
```

Notice that there is no return statement inside this method. Because the return type is void, Java isn't expecting one! We can call it in our main method like this:
```java
public static void main(String[] args) {
    spinShooter(3000); // This will print "Spinning the shooter motors up to 3000 RPM!"
}
```

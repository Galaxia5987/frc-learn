# Flow Control
Up until now, our code ran from top to bottom, executing every line. Flow control gives our program the ability to make decisions, skip certain lines of code, and react differently based on the situation.

Depending on the conditions we set, the program will take different paths.
For this we use one of the most common tools we have in Java:
the `if`, `else`, and `else if` statements.

## The `if` Statement

The if statement is the simplest way to make a decision and change the path the program takes. It sees a boolean condition(`true` or `false`). If the condition is true, the code inside the scope(curly braces `{}`) runs. If it's false, Java completely skips that code.
```java
int temperature = 35;
boolean isHot = temperature > 30;
if (isHot) {
    // This code only runs if the temperature is greater than 30
    System.out.println("It's hot outside!");
}
```

If we wish, we can also skip the extra boolean variable and write the condition directly inside the `if` statement:
```java
int temperature = 35;
if (temperature > 30) {
    // This code only runs if the temperature is greater than 30
    System.out.println("It's hot outside!");
}
```

## The `if-else` Statement

What if we want something else to happen when the condition is false?
`else` guarantees that one of two paths will be taken.

```java
boolean isRaining = false;

if (isRaining) {
    System.out.println("Take an umbrella.");
} else {
    // Only this will run!
    System.out.println("Grab your sunglasses.");
}
```

## The `else-if` Statement

Sometimes, we have more than just two possibilities.
We can chain conditions together using `else if`.
Java will check them one by one from top to bottom. As soon as it finds a true condition, it executes that block and skips the rest of the blocks, even if another one is also true.

```java
int testScore = 85;

if (testScore >= 90) {
    System.out.println("Excellent!");
} else if (testScore >= 80) {
    System.out.println("Still Great!"); // This is the scope that will run!
} else if (testScore >= 70) {
    System.out.println("Nice!");
} else {
    // If none of the above is true
    System.out.println("Should probably study more.");
}
```
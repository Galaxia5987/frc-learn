# Looping

In simple terms, a loop is a programming tool that allows you to execute a block of code multiple times without having to write it out over and over again.
For example, If you want to print "Hello" to the screen 100 times, Instead of typing `System.out.println("Hello");` 100 times, you can write it just once inside a loop and tell Java to run it 100 times.

## `while` Loops

The `while` loop continues as long as it's condition is true.
It has the following structure:
```java
while(condition){
    // Actions
}
```

The actions inside the scope will run repeatedly as long as the condition is true.
For example, if we want to print "Hello" 100 times, we would write something like this:
```java
int counter = 0;
while(counter < 100){
    System.out.println("Hello");
    counter += 1;
}
```

## `for` Loops

The `for` loop is just a shorthand for a while loop. It makes our life easier when counting on loops iterations(how much we have already completed).

They have the following structure:
```java
for(variable; condition; afterLoopAction){
    // Actions
}
```

That's confusing. Let's see an example:
```java
for(int counter = 0; counter < 100; counter += 1){
    System.out.println("Hello");
}
```
This is exactly the same as writing using the `while` loop syntax, and prints "Hello" 100 times.


## Loop Control
We have the `break` and `continue` keywords to control the flow of our loop. These keywords work on both `while` and `for` loops.

### `break`
We can use the `break` keyword in order to end a loop early. For example:
```java
int counter = 0;
while(counter < 100){
    System.out.println("Hello");
    counter += 1;
    if(counter < 50){
        break;
    }
}
```
Here the loop will break(end) sooner than the condition.

### `continue`
We can also skip parts of the loop code in the scope.
```java
int counter = 0;
while(counter < 100){
    if(counter == 5){
        continue;
    }
    System.out.println("Hello");
}
```

This example skips the iteration when the counter equals 5 and doesn't print "Hello".
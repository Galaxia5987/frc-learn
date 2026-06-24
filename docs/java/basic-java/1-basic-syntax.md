# Basic Syntax and Structure
Let's jump into how to write Java code!

## Structure
Java is highly structured. It likes everything to be organized in its proper place. Let's break down the basic skeleton of a Java program using the classic Hello World example - the first step for anyone learning to code.

Here is what the simplest functioning Java program looks like. Its only job is to print the words "Hello, World!" onto your screen.

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

Woah, this is a lot.
This may look intimidating, but let's work it back layer by layer. Think of a Java program like a set of baboshkas:

### The Class
```java
public class HelloWorld {
    // Everything else
}
```
In Java, everything must be inside a Class. You can think of a class as a container for your programs and functions for now, we will expand a lot on the definition of a class later on.

!!! note
    The name of your class(in this case, HelloWorld) must exactly match the name of the file you save it in (HelloWorld.java). Each file will contain one class, we will see how multiple classes are useful for us later on.

### The Main Method
```java
public static void main(String[] args) {
        // Instructions go here!
    }
```

A "method" or a "function" is a named piece of code that performs a specific action. This specific method, `main`, is important. It is the starting line of your program. When we tell the computer to run your Java code, it immediately looks for the main method and starts executing the instructions inside it.

You might see a lot of keywords you still don't understand, that's okay, and will understand everything shortly.

### The Statement
```java
System.out.println("Hello, World!");
```
This is the actual instruction we are giving the computer. `System.out.println` is Java's way of showing text on the screen. The text you want to print goes inside the parentheses and is wrapped in quotation marks. If the text wouldn't have been wrapped in quotation marks, the computer would have accidentally think that it's another instruction.

## Rules
### Case Sensitivity
Java cares about capital and lowercase letters. HelloWorld is completely different from helloworld or HELLOWORLD. If something requires a capital S (like System), a lowercase s will break the program.

### Scopes
You might have noticed the curly braces(`{`, `}`) surrounding everything else, This is called a scope. Scopes are used to group instructions together and control exactly what the computer can "see" and remember at any given moment.

!!! note
    Every opening brace `{` must eventually have a matching closing brace `}`

### Statements
Just like every English/Hebrew sentence ends with a period, almost every instruction(statement) in Java must end with a semicolon(`;`).

!!! note
    Scopes don't need semicolons, and instead have curly braces(`{`, `}`)

### Comments
Java will ignore anything in comments.

* Inline (single line) comments start with `//`
* Block (multi-line) comments start with `/*`, and end with `*/`

Comments can be used to explain code
Writing human-readable code is very
important, and adding comments can help
with readability

```java
// I don't do anything!

/* Yeah,

me

neither */

/**

* I look fancy!

*/
```

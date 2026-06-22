# Basic Syntax

Kotlin syntax is a bit diffrent from Java.

Our golden rule here is: If it's not mentioned here, it's probably the same as in Java. A good example of this is comments, which are the same in Java and in Kotlin.

## Statements

First of all, and probably the most exciting change, we don't need a semicolon(`;`) after every statement. Kotlin infers our statements automatically.

## Variables

Unlike Java, variables in Kotlin are defined using the `val` or `var` keywords instead of just writing the type, take the following example in Java:

```java
int myNumber = 5;
```

In Kotlin, this will be written as:

```kotlin
var myNumber: Int = 5
```

We start by mentioning that we want to declare a variable(we will go over the diffrence between `val` and `var` in a bit), provide it's name, and write it's type after a colon. Then we can provide it's value after the equals sign.

### `val` vs. `var`

Remember when went briefly over what is the `final` keyword in Java? We said that it's an immutability modifier that makes our variable unchangeable directly. In simpler terms, `final` meant that we couldn't assign a variable a new value.

In Kotlin, we use `val`. Instead of writing `final` before our type, we write `val`.

For example, in Java you would write:
```java
final int myNumber = 5;
myNumber = 3; // Error! this is a final variable.
```

```kotlin
val myNumber: Int = 5
myNumber = 3 // Error! this variable is a val

var anotherNumber: Int = 5
anotherNumber = 3 // This is allowed, as it's a var
```

## Methods

Similar to variables, we have a diffrent syntax for methods in Kotlin.

A method defined in Kotlin will start with the `fun`(it's also fun to write!) keyword, then the methods name, parameters, and finally, the return type after a colon.

Take this Java method for example:

```java
public int multiplyByTwo(int number){
    return number * 2;
}
```

In Kotlin:

```kotlin
fun multiplyByTwo(number: Int): Int{
    return number * 2;
}
```

> Notice here we don't use a `val` or `var`, and we just write the parameter name and type. All parameters in Kotlin are `val`, which means they cannot be changed.

### Notes

#### Public By Default

Everything in kotlin is `public` by default(variables, methods, classes, etc...). We can write `private` before `fun` to make it private, just like Java.

```kotlin
private fun multiplyByTwo(number: Int): Int{
    return number * 2;
}
```

Now, this method is private and accessible only to the current scope.

#### `void` Functions

In order to write a `void` method in Kotlin, we use the `Unit` special type. or omit the return type entirely.

```kotlin
fun doStuff(number: Int): Unit {
    val stuff = number - 2
}
```

Or we can omit the return type entirely:
```kotlin
fun doStuff(number: Int) {
    val stuff = number - 2
}
```

#### Return Only Functions

Sometimes we have a function that only returns something. In this case, we can omit the whole block definition and return statement, and replace it with an equals sign.

For example, this function can be written like this:
```kotlin
fun multiplyByTwo(number: Int): Int = number * 2
```

Instead of like this:

```kotlin
fun multiplyByTwo(number: Int): Int{
    return number * 2;
}
```

> Note that this doesn't make it a variable, it's still a method, but it just returns something or computes it.

#### Default Parameters

We can provide a default value to a method parameter(or for a constructor).


```kotlin
fun multiply(number: Int, by: Int = 2): Int = number * by
```



## Data Types in Kotlin

Kotlin has the same primitive data types as Java, they just start in a capital letter instead of a lowercase one.

```java
int myInteger = 50;
double myDouble = 20.5;
boolean myBoolean = true;
```

In Kotlin:
```kotlin
var myInteger: Int = 50
var myDouble: Double = 20.5
var myBoolean: Boolean = true
```

## Type Inference

Not everything in Kotlin requires an explicit type definition.
Sometimes, the Kotlin compiler can infer our variable or method type automatically.

> It's not always clear when a type can be infered. My advice is to just try and see.

```kotlin
val number = 20 // Kotlin understands that this should be an integer
val anotherNumber = 0.5 // Kotlin understands that this should be a double
val flag = true // Kotlin understands that this should be a boolean
```

Also note that this feature should only be used when the type can be easily understood from glancing at the code.
A lot of the times, Kotlin will be able to infer the type, but we should explicitly set it for code readability.
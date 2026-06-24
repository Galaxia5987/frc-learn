# Variables and Data Types

Variables are used to store data in a program. Every variable in Java has a "data type", which determines what kind of value it can.

## Variables

### Declaring a Variable

```java
int age;
```

This creates a variable named `age` that can store an "integer". We will later see what an "integer" is.
Currently, the variable is only declared, but doesn't hold any value.

### Initializing a Variable

```java
int age = 16;
```

In this example, we didn't only declare a variable named `age` that can store an "integer", but also gave it the value `16`.

### Changing a Variable's Value

```java
age = 17;
```

Variables can be updated after they are created, and assigned a new value. Note that we can't change the data type of a variable(What it's holding), only it's value. If we made a variable that can store an "integer" it can only store "integers".

## Data Types

The type of value a variable can store is called a "data type". We have two types of data types:
1. **Primitive Data Types**: Which can usually hold very basic things, like numbers. We will see what exactly.
2. **Reference Data Types**: Which doesn't hold the actual value, but a reference to the actual variable. 

This is a rather confusing topic, and everything will be explained in detail later. For now, every variable that is not a primitive is a called a reference.

### Primitive Data Types

Java has 8 primitive data types, we only need to know 4.

| Type      | What can it Hold                 | Example               |
| --------- | -------------------- | --------------------- |
| `int`     | Whole Numbers, $x \in \mathbb{N}$              | `int x = 50000;`      |
| `double`  | Floating point numbers, $x \in \mathbb{R}$              | `double x = 3.14159;` |
| `char`    | One character(letter, number, or special character)              | `char c = 'A';`       |
| `boolean` | Logic, true or false | `boolean b = true;`   |

---

### Integer

Used for whole numbers.
Can be positive, negative, or zero. Can't have a floating point.

```java
int test = 100; // Good!
int test2 = -100; // Good!
int test3 = 0; // Good!
int test4 = 50.2; // Invalid!
```

### Double

Used for numbers with a floating point.
Can be positive, negative, or zero. Can have a floating point, but it doesn't have to.

```java
double pi = 3.14159; // Good!
double e = 2.71; // Good!
double test = -10; // Good!
```

### Character

Stores a single character. A character can be a digit, a letter, or a special character(like `#` or `$` for example). A character is diffrent from a number, and must be enclosed with `''` quotations.

```java
char grade = 'A'; // Good!
char symbol = '$'; // Good!
char digit = '7'; // Good!
char test = 5; // Invalid!
char test2 = 'Hi'; // Invalid!
```

Notice that when creating a character type, even when it's a digit, it must be enclosed with quotes.

### Boolean

Stores either `true` or `false`. Nothing else.

```java
boolean test1 = true; // Good!
boolean test2 = false; // Good!
```

Booleans are commonly used in conditions, which we will learn about later on.

## Reference Data Types

Primitive types store actual values directly.

Reference types store a reference (address) to an object(another variable).

This can be a confusing topic, for now just know that when primitive types are copied or moved, the new variable stores the new value. In reference types the address is copied, not the value.

All of the above examples were primitive types.

All variables that are not of the primitive types we say, are references(we currently not know of any).

## Constants

A constant is a variable whose value cannot change.

Use the `final` keyword before the variable:

```java
final double PI = 3.14159;
final int grade = 100;
```

Attempting to modify it causes an error.

```java
PI = 3.14; // Error
grade = 20; //Error;
```

Constants can be only assigned value once.

## Type Conversion (Casting)

We can actually convert a variable of some type to another type!
When having types that don't match, we may have loss of data. For example, when casting(converting) from a `double` that can store floating point to an `int` which can't, we lose the floating point entirely and get only the whole number.

```java
double x = 9.7;
int y = x; // Error!
int z = (int) x; // Good! Result: 9
double a = (double) z; // Good! Result: 9.0
```

## Variable Naming Rules

In Java, we use a naming convention called `camelCase` for almost all naming(everything except classes, which use `PascalCase`).
In `camalCase` we start our name with a lowercase letter, and then if we need another word for the variable name, we add it with an uppercase letter.

```java
int age = 17;
double testScore 100.0;
int veryVeryVeryLongVariableName = 0.0;
```

All variable need to describe what they are holding, names like `x` or `a` are not good names as the reader doesn't know what's inside them. Names like `testScore` or `userAge` are good as we can tell what they are holding.


## Example Program

```java
public class Main {
    public static void main(String[] args) {
        int age = 17;
        double height = 1.65;
        boolean student = true;

        System.out.println("Age:");
        System.out.println(age);
        System.out.println("Height:");
        System.out.println(height);
        System.out.println("Student:");
        System.out.println(student);
    }
}
```

Output:

```text
Age
17
Height
1.65
Student
true
```

!!! note
    Notice that when printing the variables we don't use quatation marks(`""`), as we want to print the value of the variable, and not the name of it.
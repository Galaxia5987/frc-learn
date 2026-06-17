# Arithmetic Operations

In this section we are going to learn about what everyone loves the most - Math! Not really.
But in robotics, math is really important, from basic controller to complex vectors and transformations, we use math, and specificly, arithmetic operations, all the time.

## Operators
In Java, we have all the basic arithmetic operations you already know from 3rd grade, so instead of explaining everything like you are dumb, just look at the following examples:
```java
int age = 10 + 7; // 17
double testScore = 10-5; // 5.0
double moreStuff = 10/5; // 2.0
double coolVariable = 1/4; // 0.25
int moreIntegers = 10*4; // 40
int moreCoolIntegers = (int)(10/3); // 3, because this is an integer!
```

I think you get the concept, great.

## Operations On Variables
We can also apply these operations on variables, with variables, or variables with other numbers! Look at the following examples:
```java
int age = 10; // age=10
age = age * 5; // now age=50
int anotherAge = age*2; // anotherAge=100
int moreAges = anotherAge; // moreAges=100
double anotherVariable = (double)age; // anotherVariable=50.0
```

An operation we might find ourselves often is adding, substructing, multiplying or dividing a defined variable. We can do it like the following:
```java
int age = 10;
age = age + 7; // Now age is 17
```

But, we also have a shorthand for this:
```java
int age = 10;
age += 7; // Now age is 17, this operation is identical to the one seem in the last example
// We can also do this with all other operators
int somethingElse = 10;
somethingElse -= 5; // somethingElse=5
somethingElse *= 4; // somethingElse=20
somethingElse /= 5; // somethingElse=4
```
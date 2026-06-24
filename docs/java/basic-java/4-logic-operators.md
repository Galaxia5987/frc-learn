# Logic Operators
In the last section we learned about arithmetic(math) operators, in this section, we will look into logic operators.
Like in arithmetic operators which work on numbers, logic operators work on logic - booleans!

We have 3 types of logic operators, they are all diffrent, but what they have in common is that they all return a boolean(`true` or `false`).

## AND Operator
The AND operator, written like `&&`, checks if both sides of the condition are true. If even one side is false, the entire thing(called expression) is false.

```java
boolean hasTicket = true;
boolean hasId = false;
boolean canEnter = hasTicket && hasId;
```

## OR Operator
The OR operator, written like `||`, checks if at least one side of the condition is true. It only returns false if both sides are false.

```java
boolean hasPaid = false;
boolean isVip = true;
boolean canEnter = hasPaid || isVip;
```

## NOT Operator
The NOT operator, written like `!`, it only works on one boolean at a time, and its job is to flip the value. If something is true, `!` makes it false. If it's false, `!` makes it true.
```java
boolean isRaining = true;
boolean isSkyClear = !isRaining;
```

## Comparisons

In Java, comparison operators (or "relational operators" if you want to get fancy) are used to compare two values.
Just like logical operators, every comparison results in a simple boolean(`true` or `false`).

### Equal to
Written as `==`.
This checks if the value on the left is exactly the same as the value on the right.

!!! warning
    Do not confuse a single equals sign(`=` means assigning a value to a variable) with a double equals sign(`==` mean comparison, checking if equals).

```java
int score = 100;
boolean isPerfectScore = score == 100; // true
```

### Not equal to
Written as `!=`.
This is the opposite of `==`. It returns true if the values are different.

!!! note
    Notice it uses the `!` sign, which we learned means the opposite in Java.

```java
int passwordAttempt = 1234;
int correctPassword = 9999;
boolean isIncorrectPassword = passwordAttempt != correctPassword;
// Notice that this can also be written like this:
boolean isIncorrectPassword = !(passwordAttempt == correctPassword); //This uses both the NOT operator we learned about and the equals operator.
```

### Greater than and Less than

These work exactly like they did in 3rd grade.

`>` returns true if the left side is bigger(but doesn't equal to) than the right side.

`<` returns true if the left side is smaller(but doesn't equal to) than the right side.

```java
int speed = 75;
int speedLimit = 60;
boolean isSpeeding = speed > speedLimit;
boolean isGood = speed < speedLimit;
boolean isOnPoint = speed == speedLimit;
```

### Greater than or equal to and Less than or equal to

These are very similar to the basic greater than and less than, but they can also be equal.
`>=` returns true if the left side is bigger or equal to than the right side.

`<=` returns true if the left side is smaller or equal to than the right side.

```java
double heightInMeters = 1.4;
double rollerCoasterRequirement = 1.4;
boolean canEnter = heightInMeters >= rollerCoasterRequirement;
```
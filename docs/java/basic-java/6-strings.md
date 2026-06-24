# Strings
String is just a fancy name for text.
A String consists of multiple characters(from the `char` type, remember?) chained together into a sequence.
When creating a String we must enclose it with quotes(`""`) for Java to recognize that we want it to be text, and not something part of the language.

## Creating a String
Creating a String is very simple.

```java
String name = "John";
String password = "john123$";
String homeAddress = ""; // An empty String!
System.out.println(name);
```

## String concatenation

Sometimes we want to combine multiple strings together into one.
We do this by using the plus sign(`+`).
```java
String firstName = "John";
String lastName = "Doe";
String fullName = firstName + lastName; // This now holds "JohnDoe"
```

But what if we want a space in between?
That's an option too!
```java
String firstName = "John";
String lastName = "Doe";
String fullName = firstName + " " + lastName; // This now holds "JohnDoe"
System.out.println("Full Name: " + fullName);
```

We can also concatenate numbers:
```java
int score = 100;
String myScore = "My Score is: " + score + "!"; // This holds "My Score is: 100!"
```

## Strings as a reference type

As you might remember from when we learned about data types(And if you don't, please [click here](2-data-types.md#reference-data-types)!), everything that isn't a primitive type is a refrence type.
This includes Strings! String is a reference type, which doesn't mean a lot for us right now, but know that when we are handling Strings, we are actually handling a reference to that String.

In practice this means that we can't compare Strings like we do with primitive types, as it will compare the memory address it was saved in.
The example below will try and demonstrate it:
```java
String john = "John";
String myName = "John";
boolean isMyNameJohn = myName == john; // false, these are two diffrent variables, and have diffrent memory addresses, even if they contain the same value.
```

This might still be confusing, and that's okay, if you didn't understand this concept just yet, try and continue. We will go over this topic again with more complex things later.

## The String Pool

This is how Java handles Strings behind the hood, you don't need to know this at all, but I think it's cool, so if you want you are welcome to read. Though it's certainly isn't required knowledge.

Let's look again at the example from before:
```java
String john = "John";
String myName = "John";
boolean isMyNameJohn = myName == john;
```

In the last section we concluded that this would result in `isMyNameJohn` being `false`, that's actually not true, and `isMyNameJohn` will be `true`. That is because of a concept called the "String Pool".

Because Strings are very commonly used in Java, creating a new memory space for every single String would be highly inefficient. To solve this, Java uses the String Pool to save on memory by [caching](https://en.wikipedia.org/wiki/Cache_(computing)) and reusing Strings.

### How It Works

The entire concept holds on a simple fact - Strings in Java are [immutable](https://simple.wikipedia.org/wiki/Immutable_(computer_programming))(they cannot be changed once created, similiar to the `final` keyword, but when using Strings the reference can change, just not the value itself).
Because they cannot be modified, it is perfectly safe for multiple variables to share the exact same String object in memory space.

When you create a string using quotes(called a "String literal"), Java performs the following steps:
1. It checks the String Pool to see if that exact string already exists.

2. If it exists: It returns a reference to the existing string instance. No new memory is wasted.

3. If it does not exist: It creates a new string object, places it in the pool, and returns the reference to the newly created String.

And that's how we save on huge amounts of memory when using Strings.

!!! note
    Note that this concept is very complex and it's totally okay if you didn't understand any of this. If you did, that great too, and I hope you learned something and found it cool!
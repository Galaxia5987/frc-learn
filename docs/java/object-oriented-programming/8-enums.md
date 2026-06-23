# Enums

Sometimes we want to represent options. So far, we learned how to do this using Strings. Imagine the following scenario:

## The Problem

We are building the software for a coffee shop.
When someone places an order, our software needs to track its progress. Using Strings, you write something like this:

```java
String orderStatus = "PREPARING";

if (orderStatus.equals("PREPARING")) {
    System.out.println("Still in the making!");
}else if(orderStatus.equals("READY")){
    System.out.println("Your order is ready!");
}
```

This works fine. But, this can cause many problems. Imagine that suddenly some other team member tries to access this variable and check it. They write something like this:

```java
if (orderStatus.equals("ready")) {
    sendReadyMessage();
}
```

Notice the problem? The variable stores the value "READY", but we check for "ready". This is a very common problem, that enums come to solve.

## What is it?

An Enum(abbreviation for Enumeration) is a custom data type that represents a fixed set of options.

Instead of trusting the programmer to spell a string correctly, we define our set of valid options:

```java
public enum OrderStatus {
    PENDING,
    PREPARING,
    READY,
}
```

Now, our code looks like this:
```java
OrderStatus currentStatus = OrderStatus.PREPARING;

if (currentStatus == OrderStatus.READY) {
    System.out.println("The order is ready!");
}
```

Much safer.
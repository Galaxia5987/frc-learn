# Extension Functions

Imagine we have a basic `isEven` function:
```kotlin
fun isEven(num: Int): Boolean = num % 2 == 0
```

So we can use it like this:

```kotlin
fun main(){
    val number = 5
    if(isEven(number)){
        println("Five is even!")
    }else{
        println("Five is odd!")
    }
}
```

This works, but grammatically, it feels backwards.

In OOP, we tend to read code from left to right, like a something acting on an object:
Take this number, and check if it's even.

Writing `isEven(5)` forces the reader to look at the action first, and then find the subject.

We can do this better by using "Extension Functions".

## How do we use extension functions?

Extension Functions, like their name, are functions that extend a certain class.

If we wanted to write this in a more readable matter, we could do this:

```kotlin
fun Int.isEven(): Boolean = this % 2 == 0
```

Now we can use this function like this:

```kotlin
fun main(){
    val number = 5
    if(number.isEven()){
        println("Five is even!")
    }else{
        println("Five is odd!")
    }
}
```

!!! note
    We can create extension functions for every class or type we have!
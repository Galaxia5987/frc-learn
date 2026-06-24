# Top Level Functions

Unlike Java, in which everything must be enclosed in a class, Kotlin can also be written functionally. This is similar to Python or Javascript, where code, variables and functions can be written without a class.

Sometimes we don't need the added complexity of a class, and just want to write regular functions and variables "floating" in a file.

For example:

```kotlin
val regularGreeting = "Hello, World!"

fun shout(text: String): String = text.uppercase() + "!!!"
```

Now every other file or class can use this function and variable!

```kotlin
fun main(){
    println(shout(regularGreeting))
}
```

!!! tip
    Notice how in Kotlin the main function is top level too? When there is no need for a class, we can just write top level functions and variables inside regular Kotlin files
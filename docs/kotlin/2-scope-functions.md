# Scope Functions

The Kotlin standard library contains several functions whose sole purpose is to execute a block of code within the scope of an object.

When you call such a function on an object with a lambda, it forms a scope.

In this scope, you can access the object without its name. Such functions are called scope functions. There are five of them: `let`, `run`, `with`, `apply`, and `also`.

They are all basiclly the same, and because of that, we will only learn about `apply`. If you want to learn about the other functions too, you can do so [here](https://kotlinlang.org/docs/scope-functions.html).

## Usage

Let's take for example this `Person` class:

```kotlin
class Person(val name: String, val age: Int, val city: String) {
    fun moveTo(city: String){
        this.city = city
        println(name + " moved to " + city)
    }

    fun incrementAge(){
        age++
    }
}
```

When we want to use it, we can do it like this:

```kotlin
val alice = Person("Alice", 20, "Amsterdam")
println(alice)
alice.moveTo("London")
alice.incrementAge()
println(alice)
```

But notice how much we access the object? we can do this better with scope functions.

```kotlin
Person("Alice", 20, "Amsterdam").apply {
    println(this)
    moveTo("London")
    incrementAge()
    println(this)
}
```

This is much clearer.


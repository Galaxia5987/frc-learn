# Defining Classes

Creating classes in Kotlin is very similar to Java, but it has many optional [syntactic sugar](https://en.wikipedia.org/wiki/Syntactic_sugar) that you will often see and write.

## Defining Basic Classes

Before jumping in on the milion ways there are to define a constructor(...), we will see some Java examples and their equivilant in basic Kotlin:

```java
public class Car {
    private final String color;
    private final String brand;
    private int currentSpeed;

    public Car(String color, String brand){
        this.color = color;
        this.brand = brand;
        currentSpeed = 0;
    }

    public void increaseSpeed(){
        currentSpeed++;
    }

    public void brake(){
        currentSpeed = 0;
    }
}
```

In Basic Kotlin:

```kotlin
class Car {
    private val color: String
    private val brand: String
    private var currentSpeed: Int

    constructor(color: String, brand: String){
        this.color = color
        this.brand = brand
        currentSpeed = 0
    }

    fun increaseSpeed(){
        currentSpeed++  
    }
    fun brake(){
        currentSpeed = 0   
    }
}
```

Looks pretty straight-forward right? What's all the fuss about Kotlin reducing boilerplate? These two are pretty much the same... That's because we have a lot of ways to write Kotlin, some are almost the same as Java, and some will save us much time.

## Writing the same with less boilerplate

Let's look on a better way to write the same example from before:

```kotlin
class Car(
    private val color: String, 
    private val brand: String
) {
    private var currentSpeed: Int = 0

    fun increaseSpeed() {
        currentSpeed++  
    }

    fun brake() {
        currentSpeed = 0   
    }
}
```

Here we defined the constructor and the class members together, reducing a lot of boilerplate. This example behaves **exactly** the same as the last one.

Much cleaner.

## `init` constructors

The last example was much cleaner, but what happens if we need to make a function call in the constructor, but want to keep the same cleaness? We use the `init` keyword.

Look at the following example:
```kotlin
class Car(
    private val color: String, 
    private val brand: String
) {
    private var currentSpeed: Int = 0

    init {
        printInfo()
    }

    fun increaseSpeed() {
        currentSpeed++  
    }

    fun brake() {
        currentSpeed = 0   
    }

    fun printInfo(){
        println(color)
        println(brand)
    }
}
```

The `init` method(which doesn't take any parameters or parentheses) is called when the object is created, but without compromising the clean member intialization.

## Instantiating Classes

This is very similar to Java. The only diffrence is that we don't need the `new` keyword at all!

In Java we would write:

```java
final Car car = new Car("Black", "Volvo");
```

In Kotlin:
```kotlin
val car = Car("Black", "Volvo")
```
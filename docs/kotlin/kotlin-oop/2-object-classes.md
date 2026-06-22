# Object Classes

Remember the Singleton pattern in Java? It had much redundant boilerplate.

In Kotlin, we have a solution for this, `object` classes!

## Defining `object` Classes

`object` classes are the same as regular classes, but can only have one instance(like a Java Singleton), this one instance is accessible by using it like a static object(this is okay as Kotlin doesn't have static members or functions).

For Example:
```java
// Drive.java
public class Drive {
    private static Drive instance;

    private int metersDrove;

    private Drive(){
        metersDrove = 0;
    }

    public static Drive getInstance(){
        if(instance == null){
            instance = new Drive();
        }

        return instance;
    }

    public void forward(){
        metersDrove++;
        System.out.println("Going Forward!");
    }
}

// Main.java
public class Main {
    public static void main(String[] args){
        Drive.getInstance().forward();
    }
}
```

In Kotlin, we can do the following instead:

```kotlin
object Drive{
    private var metersDrove: Int = 0

    fun forward(){
        metersDrove++
        println("Going Forward!")
    }
}

fun main(){
    Drive.forward()
}
```

So much cleaner!
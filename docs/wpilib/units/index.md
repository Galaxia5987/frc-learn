# Using Units In Code

!!! note
    Some parts of this document has been taken from WPILib docs, see the full document [here](https://docs.wpilib.org/en/stable/docs/software/basic-programming/java-units.html).

The units library is a tool that helps us avoid mistakes related to units of measurement. It does this by keeping track of the units, and by ensuring that all operations are performed with the correct units.

This can help to prevent errors that can lead to incorrect results, such as adding a distance in inches to a distance in meters.

An added benefit is readability and maintainability, which also reduces bugs. By making the units of measurement explicit in our code, it becomes easier to read and understand what it's doing.

The units library has a number of features:

* A set of predefined units, such as meters, degrees, and seconds.

* The ability to convert between different units.

* Support for performing arithmetic and comparisons on quantities with units.

* Support for displaying quantities with units in a human-readable format.

## Usage

Depending on the language we use, we have diffrent ways to create measures. The Java version can also be using in Kotlin, although the Kotlin version is much more clear.

=== "Kotlin"

    We have measure type for all the common types that we need, this includes - `Distance`, `Angle`, `Time`, etc..

    Each one of these types can be created with a unit. For example, a measure of Distance can be created with 5 meters, and another measure can be created using 196.8 inches. The inches measure will be converted to meters, as they are the base unit under the hood.

    ## Creating Measures in Kotlin

    In Kotlin, we have extension functions to help us create measure easily.

    ```kotlin
    val someAngle: Angle = 20.deg // 20 degress
    val anotherAngle: Angle = 3.14.rad // PI radians
    val isBigger: Boolean = anotherAngle > someAngle // they are compareable!

    val degressButInADouble: Double = 20.0 // regular double

    val degressButInMeasure: Angle = degressButInADouble.deg // now it's a measure
    ```

    ## Getting Values From Measures

    What if we want to get the value of the measure in some unit? for that we have the square brackets!

    ```kotlin
    val someAngleInDouble: Double = someAngle[deg] // 20.0
    val converting: Double = anotherAngle[deg] // 180.0
    ```

    ----

    Of course that everything also applies to other types like Distance, Velocity, Time...

=== "Java"

    ### TODO

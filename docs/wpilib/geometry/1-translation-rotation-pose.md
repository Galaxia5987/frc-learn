# Translation, Rotation, and Pose

We have classes to represent our basic movements.

## Translation

### What is Translation

Translation is the movement of a point through space without any rotation. It describes a shift from an origin to a destination, having both distance, and direction.

It can be represent by the point $(x,y)$ or vector $\begin{bmatrix}x \\ y \end{bmatrix}$.

### How Do We Represent Translation

In WPILib, Translation is represented by the `Translation2d` or `Translation3d` class(for 2d and 3d respectively). It stores an `x` and a `y` component, which defines fixed coordinate.

=== "Kotlin"

    ```kotlin
    val target = Translation2d(5.0, 3.0)
    ```

=== "Java"

    ```java
    Translation2d target = new Translation2d(5.0, 3.0);
    ```

## Rotation

### What is Rotation

Rotation is the circular movement of an object around an axis. While translation changes an object's location, rotation changes its orientation.

### How Do We Represent Rotation

`Rotation2d` tracks a single angle($\theta$).

When we need things in 3D, we use `Rotation3d`, which tracks rotation across 3 separate axes, called `Roll`, `Pitch`, and `Yaw`:

* **Roll (X axis)**: Tilting side to side.

* **Pitch (Y axis)**: Tilting up and down.

* **Yaw (Z axis)**: Turning left and right.

You can construct it using raw radians, or via a built-in helper for degrees:

=== "Kotlin"

    ```kotlin
    val flatTurn = Rotation2d.fromDegrees(90.0)

    val tiltedTurn = Rotation3d(
        Units.degreesToRadians(0),  // Roll
        Units.degreesToRadians(5), // Pitch
        Units.degreesToRadians(20)   // Yaw
    )
    ```

=== "Java"

    ```java
    Rotation2d flatTurn = Rotation2d.fromDegrees(90.0);

    Rotation3d tiltedTurn = new Rotation3d(
        Units.degreesToRadians(0),  // Roll
        Units.degreesToRadians(5), // Pitch
        Units.degreesToRadians(20)   // Yaw
    );
    ```

## Pose

### What is Pose

A pose is the complete spatial state of an object. Knowing translation tells us where it is, but knowing it's pose tells us where it is which way it's facing.

### How Do We Represent Pose

The `Pose2d` class combines a `Translation2d` and a `Rotation2d` into a single object. We can construct it by passing those two objects in, or by handing it raw data:

=== "Kotlin"

    ```kotlin
    val robotPose = Pose2d(2.5, 1.0, Rotation2d.fromDegrees(45.0))
    ```

=== "Java"

    ```java
    Pose2d robotPose = new Pose2d(2.5, 1.0, Rotation2d.fromDegrees(45.0));
    ```

Pose2d can also represent the vector $\begin{bmatrix}x \\ y \\ \theta\end{bmatrix}$.
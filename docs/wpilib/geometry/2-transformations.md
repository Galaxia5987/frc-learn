# Transformations

We can make operations on our Translation, Rotations, and Poses. These are called Transformations.

!!! tip
    If you want to understand how these transformations work, I highly recommend this [Introduction to Robotics](https://ucb-ee106.github.io/ee106a_jupyterbook/intro.html) Course. I stumbled across it some time ago, and can't recommend it enough.

## Translation2d

Operations on a Translation2d perform operations to the vector represented by the Translation2d.

* **Addition**: Addition adds the two vectors.

* **Subtraction**: Subtraction subtracts the two vectors.

* **Multiplication**: This multiplies the vector by the scalar.

* **Division**: This divides the vector by the scalar.

* **Rotation**: Rotation of a Translation2d about the origin can be performed by using rotateBy. This is equivalent to multiplying the vector by the matrix $\begin{bmatrix} cos\theta & -sin\theta \\ sin\theta & cos\theta \end{bmatrix}$.

## Rotation2d

Transformations for Rotation2d are just arithmetic operations on the angle measure represented by the Rotation2d.

* **Addition**: Adds the rotation component of other to this Rotation2d's rotation component

* **Substraction**: Subtracts the rotation component of other to this Rotation2d’s rotation component

* **Unary Minus**: Multiplies the rotation component by a scalar of `-1`.

* **Multiplication**: Multiplies the rotation component by a scalar.

## Transform2d

Transform2d represents a relative transformation. It has an translation and a rotation component. Transforming a Pose2d by a Transform2d rotates the translation component of the transform by the rotation of the pose, and then adds the rotated translation component and the rotation component to the pose.

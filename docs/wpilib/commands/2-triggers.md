# Triggers

The most common way to run a command is by binding it to a triggering event, such as a button being pressed by a human operator. The command-based paradigm makes this extremely easy to do.

All trigger bindings will automatically schedule a command when a certain event occurs.

## Creating A Trigger

A trigger is built from a lambda(a `BooleanSupplier`), the Command Scheduler is polling all triggers(running all lambdas) at 50Hz, and when one changes state, it schedules the command bounded to the trigger.

For example:

=== "Kotlin"

    ```kotlin
    val voltageOut = VoltageOut(0.0)
    val stopMotorCommand = Commands.runOnce({ motor.setControl(voltageOut.withOutput(0.0)) }) // We only declared this command, it is not scheduled just yet!
    val exampleTrigger = Trigger { motor.position.value > 5 }.onTrue(stopMotorCommand) // The command will be scheduled when the trigger becomes true.
    ```

=== "Java"

    ```java
    // TODO
    ```

The Command Scheduler will keep checking the trigger 50 times per seconds, and when it's true, it will schedule the `stopMotorCommand` command.

## Trigger Bindings


### onTrue

This binding schedules a command when a trigger changes from false to true. The command will be scheduled once, and will not be scheduled again unless the trigger becomes false and then true again.

=== "Kotlin"

    ```kotlin
    Trigger{driverController.isXPressed()}.onTrue(Intake.intake())
    ```

=== "Java"

    ```java
    // TODO
    ```

!!! tip
    The onFalse binding is identical, only that it schedules on false instead of on true.

### whileTrue

This binding schedules a command when a trigger changes from false to true and cancels it when the trigger becomes false again. 
The command will not be rescheduled if it finishes by itself while the trigger is still true.

<!-- TODO: Find a better example -->
=== "Kotlin"
    ```kotlin
    Trigger{driverController.isXPressed()}.whileTrue(Intake.intake())
    ```

=== "Java"

    ```java
    // TODO
    ```

!!! tip
    The whileFalse binding is identical, only that it schedules on false and cancels on true.

## Composing Triggers

Triggers can be composed to create composite triggers through the `and()`, `or()`, and `negate()` methods.
For example:
=== "Kotlin"

    ```kotlin
    Trigger {driverController.isXPressed()}
        .and(Trigger {motor.position.value < 5})
        .onTrue(Intake.intake());
    ```

=== "Java"

    ```java
    // TODO
    ```

### Debouncing Triggers

To avoid rapid repeated activation, triggers can be [debounced](https://medium.com/@jamischarles/what-is-debouncing-2505c0648ff1) using the `debounce` method:

=== "Kotlin"

    ```kotlin
    Trigger { driverController.isXPressed() }.debounce(0.1).onTrue(Intake.intake());
    ```

=== "Java"

    ```java
    // TODO
    ```
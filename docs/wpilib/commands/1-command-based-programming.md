# Command Based Programming

Command based programming is one possible design pattern for robot software. It is not the only way to write a robot program, but it is a very effective one. 

Command based robot code tends to be clean, extensible, and easy to reuse.

The command based paradigm is also an example of [declarative programming](https://en.wikipedia.org/wiki/Declarative_programming). The command-based library allow users to define desired robot behaviors while minimizing the amount of robot logic that they must write. For example, in the command-based program, we can specify that "the robot should perform an action when a condition is true", without specifying how it should do it:

=== "Kotlin"

    ```kotlin
    Trigger{controller.isXPressed()}
    .onTrue(Commands.runOnce{Intake.intake()})
    .onFalse(Commands.runOnce{Intake.stop()})
    ```

=== "Java"

    ```java
    // TODO
    ```

In contrast, without using command-based, we would need to check the button state every iteration, and perform the appropriate action based on the state of the button.

=== "Kotlin"

    ```kotlin
    if(controller.isXPressed()) {
        Intake.intake()
    } else {
        Intake.stop()
    }
    ```

=== "Java"

    ```java
    // TODO
    ```

This may look fine for now, but imagine having hundreds of these statements cramed inside one big function. It will be a mess.

## How Commands Are Run

Commands are run by the `CommandScheduler` singleton, which polls triggers for commands to schedule, and executing scheduled commands. The scheduler does this at 50Hz(50 times a second, or every 20ms).

## Command Requirements

Multiple commands can run concurrently, as long as they do not require the same subsystems on the robot.
Each commands that uses a subsystem(e.g. moves it's motor) has this subsystem as it's requirement, which means that no other command that requires the same subsystem can run.

Requirements are handled on a per-subsystem basis: commands specify which subsystems they interact with, and the scheduler will ensure that no more more than one command requiring a given subsystem is scheduled at a time. This ensures that we will not end up with two different pieces of code attempting to set the same motor to different output values at the same time.

## Creating Commands

We can create commands in two diffrent ways:

* **Extending `Command`** - This provides us with methods that the scheduler uses directly. We don't use this method as it's cumbersome and requires much unnecessary boilerplate.

* **Creating Command Compositions** - We can also create and join commands together from lambdas and built commands that the library provides. This is what we will use.

### Creating A Basic Command

At the basic level, we have two types of commands, runOnce, and run commands.


#### `Commands.runOnce`

This will create a command that runs the lambda inside one time per trigger. After the call, the command ends(at least until it's called again by a trigger).

=== "Kotlin"

    ```kotlin
    val runMotor = Commands.runOnce({
        motor.setControl(voltageOut.withOutput(5.0))
    })
    ```

=== "Java"

    ```java
    // TODO
    ```

When a trigger schedules this command, it will run once.

----

#### `Commands.run`

This will create a command that runs the lambda inside at 50Hz, for as long as the command is running. If the command ends(usually because another command took it's requirement), it will need to be triggered again to keep running the lambda at 50Hz.

=== "Kotlin"

    ```kotlin
    var currentVoltage = 5.0
    val runMotorContinuously = Commands.run({
        motor.setControl(voltageOut.withOutput(currentVoltage))
    })
    ```

=== "Java"

    ```java
    // TODO
    ```

When a trigger schedules this command, it will run continuously at 50Hz, keeping the motor up to date with the `currentVoltage` variable.

### Requirements

Each command should declare any subsystems it controls as requirements. This ensures that no more than one command requires a given subsystem at the same time.

The default behaviour is that when an incoming command requires a subsystem that another command already requires, the old command will cancel and the new one will replace it.

!!! note
    This behaviour can be altered by using the `.withInterruptionBehaviour` function on the command

Each subsystem has built-in `run` and `runOnce` methods inherited from `SubsystemBase`, when these are used, the subsystem requirement is automatically added.
# State Machines

State Machines are a behavioral model. It consists of a finite number of states. Based on the current state and a given input the machine performs state transitions and produces outputs. 

You may know this concept if you learned finite-state automatons in school(Hated every minute of it, honestly).

In FRC, State Machines are crucial and a are a huge part of the logic of the robot.

There are a lot of ways to make state machines, and each design should be evaluated for it's use case. But with that, we can strive to make small and maintainable state machines, that aren't [tightly-coupled](https://www.akamai.com/glossary/what-is-tight-coupling-and-loose-coupling).

A State Machine usually consists of these:

* An Enum stating all possible states

* Trigger binding for each state, providing a command to be run at each state

* Trigger bindings for moving between states

Let's see some examples!

## Examples

Note that this is only an example, state machines can be implemented in many ways.

---

Here is our enum of possible states. Notice how we take advantage of that an enum is a class, and have special methods and members.

```kotlin title="ShootingStates.kt"
enum class ShootingState {
    IDLE,
    PRIMING,
    BACKFEEDING,
    SHOOTING;

    val trigger = Trigger { state == this }

    fun set(): Command =
        Commands.runOnce({
            state = this
        })
}
```

We can now bind these states into triggers:

```kotlin title="ShootingTriggers.kt"
private val isIdle = ShootingState.IDLE.trigger.onTrue(idle())
private val isPriming = ShootingState.PRIMING.trigger.onTrue(priming())
private val isBackfeeding =
    ShootingState.BACKFEEDING.trigger.onTrue(backfeeding())
private val isShooting = ShootingState.SHOOTING.trigger.onTrue(shooting())

```

And have the commands bound to it:
```kotlin title="ShootingCommands.kt"
fun idle(): Command =
    Commands.sequence(
        Flywheel.zero(),
        PreShooter.stop(),
        SpindexerCommands.stopFeeding(),
        IntakingStates.CLOSED.set()
    )

fun priming(): Command =
    Flywheel.setVelocity(
            Flywheel.aimingSetpoint<Flywheel, () -> AngularVelocity>()
        )
        .alongWith(
            PreShooter.setVelocity(
                PreShooter.aimingSetpoint<PreShooter, () -> AngularVelocity>()
            )
        )

fun backfeeding(): Command = PreShooter.reverse()

fun shooting(): Command =
    Commands.sequence(
            SpindexerCommands.startFeeding(),
        .alongWith(priming())
```


!!! note
    This is a real example, taken from Galaxia's [robot-2026](https://github.com/Galaxia5987/robot-2026/blob/main/src/main/kotlin/frc/robot/states/shooting)
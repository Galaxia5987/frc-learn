# Subsystems

A subsystem is an abstraction for a collection of robot hardware that operates together as a unit.
Subsystems form an [encapsulation](../java/object-oriented-programming/index.md#encapsulation) for this hardware, "hiding" it from the rest of the robot code and restricting access to it except through the subsystem’s public methods.

Subsystems will correspond to the physical mechanism they operate, we will have a subsystem for an intake, one for a shooter, one for an elevator, one for a wrist, etc...

!!! warning
    In WPILib 2027, Subsystems will be now called "Mechanism". Everything else is the same, this guide will still call them Subsystems, and will use the old syntax, for now.

Subsystems will extend the `SubsystemBase` class, and will override the `periodic` method.

As our robot only contains one of each subsystem, each subsystem will use the Singleton pattern(In Kotlin, we can use the `object` classes).

## Basic Example

=== "Kotlin"

    ```kotlin
    object Intake : SubsystemBase() {
        private val motor = TalonFX(0)
        private val voltageOut = VoltageOut(0.0)

        init {
            motor.configurator.apply(TalonFXConfiguration().apply {
                MotorOutput = MotorOutputConfigs().apply {
                    NeutralMode = NeutralModeValue.Coast
                }
            })
        }

        private fun setVoltage(voltage: Double){
            motor.setControl(voltageOut.withOutput(voltage))
        }

        fun intake() {
            setVoltage(5.0)
        }

        fun outtake(){
            setVoltage(-5.0)
        }

        fun stop(){
            setVoltage(0.0)
        }

        override fun periodic() {

        }
    }

    ```

=== "Java"

    ```java
    // TODO
    ```

As you can see, we now have a singleton with only the methods we need to control our Intake, without exposing the motor or any other implementation details.

## The `periodic` method

Notice how we have the `periodic` method overriden from `SubsystemBase`? Our Command Scheduler(We will learn about it in the next document) calls this method at 50Hz(50 times a second) so we can do related calculations, logging, etc...

You will understand it's importance later.

---

Note that a subsystem in robot code will look a bit diffrent as it will use "Commands", we'll understand them and their advantages in the next document.
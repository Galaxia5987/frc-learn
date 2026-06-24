# Subsystems in Command Based

In the previous document about subsystems, we introduced the concept, but used functional programming for everything, and not commands.

Now that we know how commands work, we can understand subsystem's more advanced features.

## Default Command

The Default Command is a command that is scheduled when no other command is requiring the subsystem. Each Subsystem can have it's own default command, but it can also be left empty.

=== "Kotlin"

    ```kotlin
    object Shooter : SubsystemBase() {
        private val motor = TalonFX(0)
        private val positionVoltage = PositionVoltage(0.0)

        init {
            motor.configurator.apply(TalonFXConfiguration().apply {
                MotorOutput = MotorOutputConfigs().apply {
                    NeutralMode = NeutralModeValue.Coast
                }
            })
            defaultCommand = setPosition { getShooterSetpoint() }
        }

        private fun setPosition(position: ()->Double): Command = run{
            motor.setControl(positionVoltage.withPosition(position()))
        }

        override fun periodic() {}
    }
    ```

=== "Java"

    ```java
    // TODO
    ```

!!! tip
    Default commands are very convenient, but should only be defined in places that make sense.
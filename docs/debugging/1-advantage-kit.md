# Advantage Kit

AdvantageKit is a logging, telemetry, and replay framework developed by Team 6328. You can find AdvantageKit's amazing documentation [here](https://docs.advantagekit.org/).

We use AdvantageKit to record all of our data, and send it over [NetworkTables](#networktables), and save it to log files as well.

## NetworkTables

Remember the massive excel table we talked about before? Well, it's real.

Although we don't have an excel speadsheet updating at 50Hz, we have something similar called NetworkTables. Which is basically a table that we can record everything we want to. This table is then accessible to us in realtime, for debbuging and calibration.

AdvantageKit automatically records every input and output directly to NetworkTables at realtime. That means that every input or output we record is automatically seen when looking at our NetworkTables.

We can look at our NetworkTables using AdvtangeScope, which we will talk about later.

## Recording Outputs Using AdvantageKit

!!! note
    Recording inputs is a bit more complicated, and usually requires IO interfaces, see about IO interfaces and inputs [here](https://docs.advantagekit.org/data-flow/recording-inputs/io-interfaces/)

As we said before, outputs are for everything that isn't raw hardware values.

We have a few ways to do this:

### Functional

We can call the logger class:

```kotlin
override fun periodic(){
    Logger.recordOutput("Subsystems/Extender/setpoint",setpoint)
}
```

We provide the name(Can be nested for clarity), and the variable to log.

Notice how we do this inside the periodic method? This method is run at 50Hz. That means that we are updating this logged record 50 times per second.

!!! note
    If we were to just call this once, it wouldn't show up if the variable changed. Because of that, we need to pay attention that when we log, it is done periodically.

### Annotation

We can also use the handy `@LoggedOutput` annotation, which updates the log automatically, and doesn't require putting a `recordOutput` statement inside a periodic function.

```kotlin
@LoggedOutput
val allSubsystemsAtSetpoint: Trigger =
    Hood.atSetpoint
        .and(Turret.atSetpoint)
        .and(Flywheel.atSetpoint)
```

This will get updated and logged automatically.
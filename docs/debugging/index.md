# Debugging and Logging

Our code can quickly become a mess riddled with bugs. How will we know what part doesn't work as intended if we can't see the current state and variables in our code?

For that we use logging.

Logging provides us with a way of saving data we may want to look at, for debugging and calibration purposes.

We can log variables, states, whatever we want.

For now, you can think of logging as saving named data inside a massive excel spreadsheat, updated at 50Hz(50 times a second) with new information.

We have two diffrent ways to log things, Inputs and Outputs:

## Inputs

Inputs will only be recorded for hardware, not anything we process just yet.

Examples of these:

* Raw Encoder Values
* Motor Voltage and Current
* Joystick Values
* Other sensor's raw values

We record these by making a data class of all the inputs we want to record for a certain device, and let our logging system log it. We can then change the inputs object periodically. Inputs are logged per device.

!!! note
    This is important for things to work in simulation and in real life. This is done using IO interfaces, which we will go over later.

## Outputs

Outputs are everything else! Here we can record everything we want, from robot states machines, PID setpoints, other variables we may want to log, etc...

Everything that isn't raw hardware goes here.

This is recorded per output, and not per-device(like inputs).
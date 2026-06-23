# Reading Stacktraces

> This document is copy-pasted with modifications from WPILib Docs, read the full document [here](https://docs.wpilib.org/en/stable/docs/software/basic-programming/reading-stacktraces.html)

``An unexpected error has occurred.``

When your robot code hits an unexpected error, you will see this message show up in some console output (Driver Station). You'll probably also notice your robot abruptly stop. These unexpected errors are called *unhandled exceptions*.

When an unhandled exception occurs, it means that your code has one or more bugs which need to be fixed.

This document will explore some of the tools and techniques involved in finding and fixing those bugs.

## What's a "Stack Trace"?

The ``unexpected error has occurred`` message is a signal that a *stack trace* has been printed out.

In Java, the `call stack` data structure is used to store information about which function or method is currently being executed.

A *stack trace* prints information about what was on this stack when the unhandled exception occurred. This points you to the lines of code which were running just before the problem happened. While it doesn't always point you to the exact *root cause* of your issue, it's usually the best place to start looking.

## What's an "Unhandled Exception"?

An unrecoverable error is any condition which arises where the processor cannot continue executing code. It almost always implies that, even though the code compiled and started running, it no longer makes sense for execution to continue.

In almost all cases, the root cause of an unhandled exception is code that isn't correctly implemented. It almost never implies that any hardware has malfunctioned.

## So How Do I Fix My Issue?

### Read the Stack Trace

To start, search above the ``unexpected error has occurred`` for the stack trace.

In Java and Kotlin, it should look something like this:

```text
Error at frc.robot.Robot.robotInit(Robot.java:24): Unhandled exception: java.lang.NullPointerException
        at frc.robot.Robot.robotInit(Robot.java:24)
        at edu.wpi.first.wpilibj.TimedRobot.startCompetition(TimedRobot.java:94)
        at edu.wpi.first.wpilibj.RobotBase.runRobot(RobotBase.java:335)
        at edu.wpi.first.wpilibj.RobotBase.lambda$startRobot$0(RobotBase.java:387)
        at java.base/java.lang.Thread.run(Thread.java:834)
```

There's a few important things to pick out of here:

* There was an ``Error``

* The error was due to an ``Unhandled exception``

* The exception was a ``java.lang.NullPointerException``

* The error happened while running line ``24`` inside of ``Robot.java``
    * ``robotInit`` was the name of the method executing when the error happened.

* ``robotInit`` is a function in the ``frc.robot.Robot`` package (AKA, your team's code)

* ``robotInit`` was called from a number of functions from the ``edu.wpi.first.wpilibj`` package (AKA, the WPILib libraries)

The list of indented lines starting with the word ``at`` represent the state of the *stack* at the time the error happened. Each line represents one method, which was *called by* the method right below it.

For example, If the error happened deep inside your codebase, you might see more entries on the stack:

```text
Error at frc.robot.Robot.buggyMethod(TooManyBugs.java:1138): Unhandled exception: java.lang.NullPointerException
        at frc.robot.Robot.buggyMethod(TooManyBugs.java:1138)
        at frc.robot.Robot.barInit(Bar.java:21)
        at frc.robot.Robot.fooInit(Foo.java:34)
        at frc.robot.Robot.robotInit(Robot.java:24)
        at edu.wpi.first.wpilibj.TimedRobot.startCompetition(TimedRobot.java:94)
        at edu.wpi.first.wpilibj.RobotBase.runRobot(RobotBase.java:335)
        at edu.wpi.first.wpilibj.RobotBase.lambda$startRobot$0(RobotBase.java:387)
        at java.base/java.lang.Thread.run(Thread.java:834)
```

In this case: ``robotInit`` called ``fooInit``, which in turn called ``barInit``, which in turn called ``buggyMethod``. Then, during the execution of ``buggyMethod``, the ``NullPointerException`` occurred.


### Perform Code Analysis

Once you've found the stack trace, and found the lines of code which are triggering the unhandled exception, you can start the process of determining root cause.

Often, just looking in (or near) the problematic location in code will be fruitful. You may notice things you forgot, or lines which don't match an example you're referencing.

> Developers who have lots of experience working with code will often have more luck looking at code than newer folks. That's ok, don't be discouraged! The experience will come with time.

A key strategy for analyzing code is to ask the following questions:

* When was the last time the code "worked" (I.e., didn't have this particular error)?
* What has changed in the code between the last working version, and now?

Frequent testing and careful code changes help make this particular strategy more effective.

### Search for More Information

[Google](https://www.google.com/) is a phenomenal resource for understanding the root cause of errors. Searches involving the programming language and the name of the exception will often yield good results on more explanations for what the error means, how it comes about, and potential fixes.

## Common Examples & Patterns

There are a number of common issues which result in runtime exceptions.

### Null Pointers and References

Java has the concept of "null" - it uses it to indicate something which has not yet been initialized, and does not refer to anything meaningful.

Manipulating a "null" reference will produce a runtime error.

For example, consider the following code:
```java
PWMSparkMax armMotorCtrl;
@Override
public void robotInit() {
    armMotorCtrl.setInverted(true);
}
```

When run, you'll see output that looks like this:

```text
********** Robot program starting **********
Error at frc.robot.Robot.robotInit(Robot.java:23): Unhandled exception: java.lang.NullPointerException
        at frc.robot.Robot.robotInit(Robot.java:23)
        at edu.wpi.first.wpilibj.TimedRobot.startCompetition(TimedRobot.java:107)
        at edu.wpi.first.wpilibj.RobotBase.runRobot(RobotBase.java:373)
        at edu.wpi.first.wpilibj.RobotBase.startRobot(RobotBase.java:463)
        at frc.robot.Main.main(Main.java:23)
Warning at edu.wpi.first.wpilibj.RobotBase.runRobot(RobotBase.java:388): The robot program quit unexpectedly. This is usually due to a code error.
The above stacktrace can help determine where the error occurred.
See https://wpilib.org/stacktrace for more information.
Error at edu.wpi.first.wpilibj.RobotBase.runRobot(RobotBase.java:395): The startCompetition() method (or methods called by it) should have handled the exception above.
```

Reading the stack trace, you can see that the issue happened inside of the ``robotInit()`` function, on line 23, and the exception involved "Null Pointer".

By going to line 23, you can see there is only one thing which could be null - ``armMotorCtrl``. Looking further up, you can see that the ``armMotorCtrl`` object is declared, but never instantiated.

Alternatively, you can step through lines of code with the single step debugger, and stop when you hit line 23. Inspecting the ``armMotorCtrl`` object at that point would show that it is null.

#### Fixing Null Object Issues

Generally, you will want to ensure each reference has been initialized before using it. In this case, there is a missing line of code to instantiate the ``armMotorCtrl`` before calling the ``setInverted()`` method.

A functional implementation could look like this:
```Java
PWMSparkMax armMotorCtrl;
@Override
public void robotInit() {
    armMotorCtrl = new PWMSparkMax(0);
    armMotorCtrl.setInverted(true);
}
```

### Divide by Zero

It is not generally possible to divide an integer by zero, and expect reasonable results. Most processors (including the roboRIO) will raise an Unhandled Exception.

For example, consider the following code:

```Java
int armLengthRatio;
int elbowToWrist_in = 39;
int shoulderToElbow_in = 0; //TODO
@Override
public void robotInit() {
    armLengthRatio = elbowToWrist_in / shoulderToElbow_in;
}
```

When run, you'll see output that looks like this:

```text
    ********** Robot program starting **********
Error at frc.robot.Robot.robotInit(Robot.java:24): Unhandled exception: java.lang.ArithmeticException: / by zero
        at frc.robot.Robot.robotInit(Robot.java:24)
        at edu.wpi.first.wpilibj.TimedRobot.startCompetition(TimedRobot.java:107)
        at edu.wpi.first.wpilibj.RobotBase.runRobot(RobotBase.java:373)
        at edu.wpi.first.wpilibj.RobotBase.startRobot(RobotBase.java:463)
        at frc.robot.Main.main(Main.java:23)
Warning at edu.wpi.first.wpilibj.RobotBase.runRobot(RobotBase.java:388): The robot program quit unexpectedly. This is usually due to a code error.
The above stacktrace can help determine where the error occurred.
See https://wpilib.org/stacktrace for more information.
Error at edu.wpi.first.wpilibj.RobotBase.runRobot(RobotBase.java:395): The startCompetition() method (or methods called by it) should have handled the exception above.
```

Looking at the stack trace, we can see a ``java.lang.ArithmeticException: / by zero`` exception has occurred on line 24. If you look at the two variables which are used on the right-hand side of the ``=`` operator, you might notice one of them has been initialized to zero. Looks like someone forgot to update it! Furthermore, the zero-value variable is used in the denominator of a division operation. Hence, the divide by zero error happens.

Alternatively, by running the single-step debugger and stopping on line 24, you could inspect the value of all variables to discover ``shoulderToElbow_in`` has a value of ``0``.

#### Fixing Divide By Zero Issues

Divide By Zero issues can be fixed in a number of ways. It's important to start by thinking about what a zero in the denominator of your calculation *means*. Is it plausible? Why did it happen in the particular case you saw?

Sometimes, you just need to use a different number other than 0.

A functional implementation could look like this:
```Java
int armLengthRatio;
int elbowToWrist_in = 39;
int shoulderToElbow_in = 3;
@Override
public void robotInit() {
    armLengthRatio = elbowToWrist_in / shoulderToElbow_in;
}
```

Alternatively, if zero *is* a valid value, adding ``if/else`` statements around the calculation can help you define alternate behavior to avoid making the processor perform a division by zero.

Finally, changing variable types to be ``float`` or ``double`` can help you get around the issue - floating-point numbers have special values like ``NaN`` to represent the results of a divide-by-zero operation. However, you may still have to handle this in code which consumes that calculation's value.
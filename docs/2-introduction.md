# Introduction to Robotics
Welcome to Robotics!
As programmers, we interact with the robot's hardware through abstractions, treating physical components(such as motors, sensors, etc...) as objects in our code.

## What does our Robot consist of?
A FRC robot is complex piece of mechanical engineering, electronics, and eventually, programming. From a programming perspective, we can break the robot down into five main categories:

* **Our Controller**: This is the central compute module of the robot. It runs the code we write, processes sensor data, and sends commands to the motors. Up to this year our controller was the RoboRIO, but it lacks performance and modern features, and is getting replaced with the better [SystemCore](https://docs.wpilib.org/en/latest/docs/software/systemcore-info/systemcore-introduction.html)!

* **Robot Radio**: This acts as the bridge between the robot and the controlling laptop(Also called the "DriverStation"), allowing us to send joystick inputs during the TeleOperated period and receive diagnostic data wirelessly. This is basically a fancy WiFi router.

* **Motors**: We generally use Brushless DC Motors(BLDC) that provide the physical movement of the robot. We don't talk to motors directly. instead, our code sends signals over a protocol(the CAN bus) to a Motor Controller. It's okay if you don't understand all of these terms just now, they will make more sense later on.

* **Sensors**: We use sensors to get feedback from the real world. From using an [Encoder](https://en.wikipedia.org/wiki/Rotary_encoder) to measure angles, to using cameras and lasers to detect object and localize ourselves in the field.

* **Co-Processors**: We also use addional compute units called Coprocessors for tasks that would have been too much on the main processor. This is mostly used for cameras and vision systems.
# Feedforward Control

Recall from earlier that the point of a feedforward controller is to use the known dynamics of a mechanism to make a best guess at the control effort required to put the mechanism in the state we want, without using feedback control(guessing really good, basically). We can then incorporate a PID controller as well, to do small corrections that the feedforward controller didn't account for.

In order to do this, we need to have some idea of what kind of mechanism we are controlling - that will determine the relationship between control effort and output.

!!! note
    Here we use Newton's notation for the derivative($\dot{d}$ and $\ddot{d}$ for second derivative). It symbolizes the derivative with respect to time. We can also write this as $d'(t)$ and $d''(t)$ in Lagrange's notation.

The Feedforward equation we use is as follows:

$$
V = K_g + K_s \cdot sgn(\dot{d}) + K_v \cdot \dot{d} + K_a \cdot \ddot{d} 
$$

Where $V$ is the applied voltage, $d$ is the position of the motor, $\dot{d}$ is its velocity, and $\ddot{d}$ is its acceleration.

!!! note
    $sgn(x)$ is a called the "signum" function. It extracts the sign of a number. It returns 1 if the number is positive, -1 if it is negative, and 0 if it is exactly zero.

    $$
    \operatorname{sgn}(x) = \begin{cases} 
    -1 & \text{if } x < 0 \\
    0 & \text{if } x = 0 \\
    1 & \text{if } x > 0 
    \end{cases}
    $$


At first glance, you might notice that this equation has the motor's velocity and acceleration, doesn't that break what we said about open loop control? Well, no. The controller still has no idea of the position of the system, and does't know it's reference at all. That forces it to just account for unwanted dynamics, and not do corrections or try to move towards a setpoint.

## The Terms

### Static Friction

$K_s$ is the voltage needed to overcome the system's static friction, or in other words to just barely get it moving.

Because static friction is constant for a system, it doesn't depend on the system's current velocity or acceleration. It's just in the opposite direction of where the system is going at.

Note the presence of the signum function because friction force always opposes the direction of motion(the sign of the velocity).

### Cruise Voltage

$K_v$ describes how much voltage is needed to hold (or "cruise") at a given constant velocity.

### Acceleration

$K_a$ describes the voltage needed to induce a given acceleration in the system.

### Gravity

On systems where gravity has effect(like an elevator or an arm) we have the $K_g$ term. Using it, we can account for the unwanted dynamics of gravity.

#### Arm Gravity

When using an arm, we can modify the feedforward equation to provide a cosine relation with $K_g$, like this:

$$
V = K_g*cos(\theta) + K_s \cdot sgn(\dot{\theta}) + K_v \cdot \dot{\theta} + K_a \cdot \ddot{\theta}
$$
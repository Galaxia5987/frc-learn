# Introduction to OOP
> "Object-oriented programming (OOP) is a programming paradigm based on objects - software entities that encapsulate data and function(s). An OOP computer program consists of objects that interact with one another." - Wikipedia, [Object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming)

Up to now, we learned how to structure our programs by seperating our tasks into methods that do one specific thing. Now, we are going to shift our mindset to think of everything more like the real world.

In the real world, everything we interact with is an object. Whether it's the computer or phone you are currently using, a dog, a person, or a coffee.
Every real world object around us has two important things:

1. **Properties**: What the object has. For a car, the properties may include its color, brand, and current speed, for example.

2. **Behaviour(Methods)**: What the object can do. For the car, the behaviors may include moving forward, braking, or honking.

In Object-Oriented Programming, instead of just writing a top to bottom list of actions or methods, we are now going to write our data and our actions together inside objects.

In this document, we'll learn about what each term in OOP mean, and in later documents we will start implementing this knowledge in Java!

## The Class

This is the blueprint(mold) for the object! Here we specify what our object can have and do.
For the car example: We have a lot of diffrent car types, but they all share common properties, like the color, brand, current speed, etc... and common actions like moving, braking, and honking.

We define these properties and actions in the blueprint(called "Class"), and then we can make as many objects with diffrent values to these properties.

Instead of writing the code for these properties and actions over and over again from scratch, we define them once inside a class.

## The Object
Once we have our blueprint(the class), we can use it to make actual objects(called "Instances").

Because the class defined our "mold", we can make out as many unique car objects as we need. They will all share the same structure we defined in the class, but we can assign different values to their properties, and call their actions:

* **Object 1**: A red Ferrari currently going 80 km/h.

* **Object 2**: A silver Mazda currently going at 0 km/h.

* **Object 3**: A blue Ford currently going at 45 km/h.

Even though they look different and have different speeds, they were all built using our single Car class.

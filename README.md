# First Aid Instruction

Instroduction: This is a Python module that allows peppers to act by using and tweaking the Choreographe's internal Motion box and script compiler implementations, so it can be run as a NaoQi module on the robot

### Features
* This module provides an ALMemory event other modules can subscribe to
* The module relies on ALProxy to provide a proxy for module behavior, for example ALMotion, ALTextToSpeech
* Python can control the pepper behavior of Choreographe, provided it runs naoqi.bin

## How to run

### Using Motion Boxes

Now we can test some of Choregraphe's motion boxes. A simple example is to imitate the elephant trunk -> dance movement. In Choregraphe, select the "Trunk" and "Disco" boxes from Box libraries > default. Drag and drop them in the center view. Then connect the global "onStart" input to the “Elephant" box's "onStart" input, and the output of this box to the "Disco" box's "OnStart" input. Now, make sure the simulation is running and press the Play button in Choregraphe. This will cause the robot to start mimicking an elephant's trunk before it starts dancing. "Happy" command box is processed as described above, and when they are connected, the result is a complete movement.

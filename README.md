# First Aid Instruction

Instroduction: This is a Python module that allows peppers to act by using and tweaking the Choreographe's internal Motion box and script compiler implementations, so it can be run as a NaoQi module on the robot.

The first goal of the robot's use here is to scan its surroundings and to be able to provide timely assistance and rescue guidance when it finds a sick person.

Rescue is divided into two goals: 
   * one is physical trauma, i.e., physical injuries such as bleeding and pain. 
   * The other is psychological trauma, i.e., depressed mood, or the patient's expression of loss.


### Features
* This module provides an ALMemory event other modules can subscribe to
* The module relies on ALProxy to provide a proxy for module behavior, for example ALMotion, ALTextToSpeech
* Python can control the pepper behavior of Choreographe, provided it runs naoqi.bin, which is the bridge between Python and Choregraphe.

## How to run

### Configuration

#### Materials

With naoqi.bin started, we can get ALProxy running.
Here's a simple example on how to do that：

```
self.tts = ALProxy("ALMoton", "127.0.0.1", 9559)
```
ALProxy is an object that gives you acces to all the methods or the module your are going to connect to，including the module name, the bot IP, and the port on which the naoqi listens.

Once the code is recognized, the choregraphe appears with the corresponding language and action

### Creating a New Instruction Box Implementation Behavior

If you are using choregraphe's internal script compiler, you do not need to add the IP and port
Here's a simple example on how to do that

```
self.tts = ALProxy("ALTextToSpeech")
```

### Simulation Realization

The module of interaction start with human saying “Hi, pepper”. Then, the robot will ask permission to approach, the human need to answer YES or NO and the robot will react according to the answer. 

During the interaction, the robot continues to ask about the injury, waiting for the patient's response and taking the corresponding first aid measures.

 * hemostasis: grab alcohol pad and bandage and deliver to patient
   ```
   self.tts = ALProxy("ALTextToSpeech")
   self.tts = ALProxy("ALMotion")
   LeftArm = ["LShoulderPitch", "LShoulderRoll", "LelbowYaw", "LElbowRoll", "LWristYaw"]
   self.motion.setAngles(LeftArm, [0.0, 0.0, 0.0, 0.0, -0.9], 0.2)
   self.tts.say("this is hemostasis pad and bandage, please use them to cover the wound")
   ```

   like this
 * pain: grab aspirin and deliver to patient
 * fracture: grab splint and bandage to immobilize the limb
 * sunstroke: take out cooling ointment and deliver to patient

### Using Motion Boxes

Now we can test some of Choregraphe's Motion boxes. A simple example is to imitate the elephant trunk -> dance movement. In Choregraphe, select the "Trunk" and "Disco" boxes from Box libraries > default. Drag and drop them in the center view. Then connect the global "onStart" input to the “Elephant" box's "onStart" input, and the output of this box to the "Disco" box's "OnStart" input. Now, make sure the simulation is running and press the Play button in Choregraphe. This will cause the robot to start mimicking an elephant's trunk before it starts dancing. "Happy" command box is processed as described above, and when they are connected, the result is a complete movement.

### Simulation Realization

The movement of body languages is preprogramming using Choregraphe, which makes the whole set of movements continuous by means of connections. The patterns are mimic from human body language in real life.

The module of interaction start with human saying “Hi, pepper”. Then, the robot will ask permission to approach, the human need to answer YES or NO and the robot will react according to the answer. 

During the interaction, when Pepper determines that the human in front of him has a psychological problem, he will take the appropriate measures to pacify him:     

* verbal reassurance, such as "don't worry"
   ```
   self.tts = ALProxy("ALTextToSpeech")
   self.tts.say("don't wory, let's dance")
   ```
* behavioral comforting： dance to please the patient.

  Here drag and drop Choregraphe's internal behavior box and connect it, click upload to robot and start playing to see the robot start performing continuous actions

## Dependencies
  
* Python 2.7
* naoqi Python SDK

## Limitation

Choregraphe can successfully connect to the real pepper, but it doesn't run. Presumably the reason for this is that the pepper doesn't install some packages.

I tried to use Webots to connect Choreographe for generating simulation environment to the extent that Pepper can run in the simulation environment. But after searching, I found that Webots after 2019 no longer support the connection of NAO Robotics Development Kit Choregraphe. Older versions of Webots cannot be found and downloaded from the web.


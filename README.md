# ProjectConstructionTechniques

How to build reliable, robust projects, and how to debug and document them

### Soldering
1. [Learn how to solder](https://github.com/michaelshiloh/resourcesForClasses/tree/master#soldering)


### Documenting projects
1. Documentation includes:
1.1. A clear and well labeled schematic 
1.1. The code or a link to the code
1.1. A good description of what the project does and how it does it. 
1.1. Links to all the resources you used
1.1. Any challenges such as things that didn't work as expected or other
things you had difficulty with
1. Schematics
1.1. Learn the difference between a schematic and assembly instructions: This is a
schematic:
![](media/arduinoSparkFunMotorDriver_schem.jpg)
while these are assembly instructions:
![](https://cdn.sparkfun.com/assets/learn_tutorials/8/9/1/SIK_Circuit_5A_SIK_Circuit_5A_Motor__Basics_bb_Fritzing.jpg)
1.1. Your schematics should be well organized for clarity. 
Sometimes this takes
a couple of drafts before you figure out the optimal
placement. Don't be afraid to make some rough sketches first.
1.1. Information should flow on your schematic from left to right. 
Generally, 
inputs and sensors should be on the left; outputs and actuators should be on
the right. (I say generally because sometimes things are both inputs and
outputs.)
1.1. Place your components so the connections are as direct as possible.
1.1.  Make Arduino as tall as you need so there is room for all 
inputs and outputs
1. Use a single line for 5V and GND, or use labels

### Programs

1. Don't use "magic numbers". Use "const int" 
and a good variable name. Good variable names almost make comments 
unnecessary.
1. Proper indentation make it easier to spot mistakes in logic or
incorrect curly braces, and easier for someone else to read
1. Comments
1.1. Use empty lines to separate groups of related things, and explain
in a comment what each group does
1.1. Especially for conditionals and for() loops, 
describe how the code is doing what you want, e.g.
```if (sensorReading > 100 && inMotion == false)```
Explain what condition you are testing, and what you are going to do as a result of that

1.1. Don't bother saying the obvious e.g. "turn on LED" or "increment i"

1.1. Any code which is commented out must be explained 

1.1. If you use an analog input pin as a digital input or output, 
note that you know what you're doing (maybe you ran out of digital pins, 
or the analog input pin was closer to where you needed to go.)

1.1. Remove any irrelevant comments




### Breadboards

1. Always use red for 5V, and never use red for anything else

1. Always use black for GND, and never use black for anything else

1. Use the appropriate buses for 5V and GND

1. Components with long leads (e.g. LEDs and resistors) that are connected
to GND or 5V can go directly to those buses. There is no reason to have the
LED in the middle of the breadboard and then have a wire from there to the
bus.

1. Use a bigger breadboard if your breadboard is getting too crowded


### Moving off the breadboard

The solderless breadboard is a wonderful invention for
   quickly prototyping and testing ideas, but the connections are not reliable
   and it's too easy for wires or components to become detached.

1. Always use red for 5V, and never use red for anything else

1. Always use black for GND, and never use black for anything else

1. Do not solder wires to potentiometer or switches that are designed to be
installed on a breadboard.  There are special potentiometers and switches that
are designed to be connected to wire. These are usually called "panel-mount"
switches or potentiometers.

### Circuit Design

1. Pin choices

1.1. Avoid using Pins 0 and 1, as these are used for uploading your program
and for serial communication

1.1. Remember that all 20 Arduino pins can be used for digital input and
digital output. Of these 20 pins, six can do analog iput (the so-called analog
input pins) and six can do "analog" output (PWM). Since these 12 pins are
special, we want to avoid using them for digital input and output, unless we
have used up all the simple digital pins

1.1. Be aware that pin 13 blinks three times when Arduino resets. If you
have this controlling something like a motor, it means that your motor might
move before your program starts.

1.1. If you use the Wire library 
(e.g. with some sensors and the Adafruit Motor Shield V2) 
this uses pins A4 and A5, so you can not use these pins for anything else.

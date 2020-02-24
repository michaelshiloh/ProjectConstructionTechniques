# ProjectConstructionTechniques

How to build reliable, robust projects, and how to debug and document them

1. Documenting projects

1.1. The difference between a schematic and an assembly drawing: This is a
schematic, while this is an assembly drawing

1. Programs

1.1. Don't use "magic numbers". Use "const int" 
and a good variable name. Good variable names almost make comments 
unnecessary.

1.1. Proper indentation make it easier to spot mistakes in logic or
incorrect curly braces, and easier for someone else to read

1.1. Comments

1.1.1. Use empty lines to separate groups of related things, and explain
in a comment what each group does

1.1.1. Especially for conditionals and for() loops, 
describe how the code is doing what you want, e.g.

````if (sensorReading > 100 && inMotion == false)````

What condition are you detecting, and what are you going to do as a result of that?

1.1.1. Don't bother saying the obvious e.g. "turn on LED" or "increment i"

1.1.1. Any code which is commented out must be explained 

1.1.1. If you use an analog input pin as a digital input or output, 
note that you know what you're doing (maybe you ran out of digital pins, 
or the analog input pin was closer to where you needed to go.)

1.1.1. Remove any irrelevant comments


1. Schematics

1.1. Inputs (sensors) on the left, outputs (actuators) on the right

1.1.  Make Arduino as tall as you need so there is room for all 
inputs and outputs

1.1. Use a single line for 5V and GND (or use labels)


1. Breadboards

1.1. Always use red for 5V, and never use red for anything else

1.1. Always use black for GND, and never use black for anything else

1.1. Use the appropriate buses for 5V and GND

1.1. Components with long leads (e.g. LEDs and resistors) that are connected
to GND or 5V can go directly to those buses. There is no reason to have the
LED in the middle of the breadboard and then have a wire from there to the
bus.

1.1. Use a bigger breadboard if your breadboard is getting too crowded


1. Moving off the breadboard

1.1. Always use red for 5V, and never use red for anything else

1.1. Always use black for GND, and never use black for anything else

1.1. Do not solder wires to potentiometer or switches that are designed to be
installed on a breadboard.  There are special potentiometers and switches that
are designed to be connected to wire. These are usually called "panel-mount"
switches or potentiometers.

1. Circuit Design

1.1. Pin choices

1.1.1. Avoid using Pins 0 and 1, as these are used for uploading your program
and for serial communication

1.1.1. Remember that all 20 Arduino pins can be used for digital input and
digital output. Of these 20 pins, six can do analog iput (the so-called analog
input pins) and six can do "analog" output (PWM). Since these 12 pins are
special, we want to avoid using them for digital input and output, unless we
have used up all the simple digital pins

1.1.1. Be aware that pin 13 blinks three times when Arduino resets. If you
have this controlling something like a motor, it means that your motor might
move before your program starts.

1.1.1. If you use the Wire library 
(e.g. with some sensors and the Adafruit Motor Shield V2) 
this uses pins A4 and A5, so you can not use these pins for anything else.

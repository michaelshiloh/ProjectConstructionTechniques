# ProjectConstructionTechniques

How to build reliable, robust projects, and how to debug and document them

### Breadboards
1. Always use red for 5V, and never use red for anything else
1. Always use black for GND, and never use black for anything else
1. Use the appropriate buses for 5V and GND
1. Components with long leads (e.g. LEDs and resistors) that are connected
to GND or 5V can go directly to those buses. There is no reason to have the
LED in the middle of the breadboard and then have a wire from there to the
bus.
1. Use a bigger breadboard if your breadboard is getting too crowded

### Human interface for your project

Arduino projects usually involve some kind of controls such as switches,
potentiometers, or other sensors and output devices like LEDs. 
Your project will be easier to use, and less
likely to be damaged, if you mount these human interface devices
on a panel of some kind rather than the solderless breadboard. 
A commercial product is expected to be in some kind of enclosure, 
but as you are still learning I encourage you not to spend too much time
making a full enclosure. Consider a box open on at least one size for
easy access, or just a single panel with feet.

#### Materials:

1. Laser cut acrylic or plywood:
Design your own in a program such as
Illustrator or [Inkscape](https://inkscape.org/) (free) 
or use one of the many box generators which creates designs suitable for 
using with a laser cutter, such as
[MakerCase](https://en.makercase.com/#/basicbox).

1. Wood:
I can cut wood for your enclosure. Give me a list of pieces and their
dimensions.

1. Cardboard:
A perfectly acceptable enclosure can be made of cardboard and assembled using
hot glue. This has the advantage that you are not dependent on 
anyone or access to specialized tools or equipment.

#### Components

When working on the solderless breadboard, we use components that are designed
to fit into the holes on the breadboard. These components are also designed to
fit a Printed Circuit Board (PCB) and therefore are called *PCB mount*
components. When you move to an enclosure or panel, these are **not** the
right type of component to use. Fortunately, there exist components that are
designed to be mounted in a panel which are called *panel mount* components.
In the IM lab we have panel mount switches and potentiometers which work
exactly like the switches and potentiometers that you are familiar with. They
are designed to fit into holes cut in a panel or enclosure. You will solder
wires to these components with which to make the connection to the breadboard
and the rest of your circuit.

(Pictures of PCB mount and panel mount switches and potentiometers, with and
without wires attached)

#### Considerations

Whatever method you use, consider the following:
1. Make sure that your Arduino and breadboard are somehow attached to the 
enclosure so that if someone moves the enclosure 
1. Anchor the USB cable in some way so that if someone pulls it by accident 
it won't pull the wires out of your breadboard. Zip ties work well for this.
1. You will almost certainly need to repair and modify your project. Make sure
   that it is easy to access the electronics. For this reason I prefer a
   simple flat panel with feet
1. Think about a logical, intuitive placement of controls and output devices.
   Think about the articles we read about design.



### Moving off the breadboard

The solderless breadboard is a wonderful invention for
   quickly prototyping and testing ideas, but the connections are not reliable
   and it's too easy for wires or components to become detached. You can
   solder your circuit

1. Always use red for 5V, and never use red for anything else
1. Always use black for GND, and never use black for anything else
1. Do not solder wires to potentiometer or switches that are designed to be
installed on a breadboard.  There are special potentiometers and switches that
are designed to be connected to wire. These are usually called "panel-mount"
switches or potentiometers.


### Soldering
1. [Learn how to solder](https://github.com/michaelshiloh/resourcesForClasses/tree/master#soldering)


### Documenting projects
1. Documentation includes:
    1. A clear and well labeled schematic 
    1. The code or a link to the code
    1. A good description of what the project does and how it does it. 
    1. Links to all the resources you used
    1. Any challenges such as things that didn't work as expected or other
things you had difficulty with
1. Schematics
    1. Learn the difference between a schematic and assembly instructions: 
This is a
schematic:
![](https://github.com/michaelshiloh/IntroductionToInteractiveMedia/blob/master/media/arduinoSparkFunMotorDriver_schem.jpg)
while these are assembly instructions:
![](https://cdn.sparkfun.com/assets/learn_tutorials/8/9/1/SIK_Circuit_5A_SIK_Circuit_5A_Motor__Basics_bb_Fritzing.jpg)
    1. Your schematics should be well organized for clarity. 
Sometimes this takes
a couple of drafts before you figure out the optimal
placement. Don't be afraid to make some rough sketches first.
    1. Information should flow on your schematic from left to right. 
Generally, 
inputs and sensors should be on the left; outputs and actuators should be on
the right. (I say generally because sometimes things are both inputs and
outputs.)
    1. Place your components so the connections are as direct as possible.
    1.  Make Arduino as tall as you need so there is room for all 
inputs and outputs
    1. Use a single line for 5V and GND, or use labels

### Programs

1. Don't use 
[magic numbers](https://en.wikipedia.org/wiki/Magic_number_(programming). 
Use `const int` 
and a good variable name. Good variable names almost make comments 
unnecessary.
1. Proper indentation make it easier to spot mistakes in logic or
incorrect curly braces, and easier for someone else to read
1. Comments
    1. Use empty lines to separate groups of related things, and explain
in a comment what each group does
    1. Especially for conditionals and for() loops, 
describe how the code is doing what you want, e.g.
```if (sensorReading > 100 && inMotion == false)```
Explain what condition you are testing, and what you are going to do as a result of that
    1. Don't bother saying the obvious e.g. "turn on LED" or "increment i"
    1. Any code which is commented out must be explained 
    1. If you use an analog input pin as a digital input or output, 
note that you know what you're doing (maybe you ran out of digital pins, 
or the analog input pin was closer to where you needed to go.)
    1. Remove any irrelevant comments

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

# Modular Modularity
Eurorack Modules, but modular themselves :)
While thinking at the features I wanted for two voltage processing modules and some tinkering with my favourite CAD software, I ended with an idea. Most of those aforementioned "subdued" modules (go easy on me please) offer simple functions that are the sum of small circuits in series. Most of these circuits are the same for different modules, like the power supply filters section or voltage attenuation section, just to name a few.

So, here is the idea: modular modules!

# Building Blocks
Blocks can be divided into 3 main categories:
- Front blocks
- Main circuits blocks
- Auxiliary circuits blocks
Front blocks are intended to be locked beneath the face plate and host the user interface components (potentiometers, jacks, LEDs, etc. etc.). This new iteration of blocks adds two front blocks out of a total of three.
The face plate hosts two front blocks.
Main circuits blocks host the active (or passive) signal modification circuit. They are intended to be directly connected to front blocks.
Auxiliary circuit blocks are circuits that perform auxiliary functions, like filtering the power supply, giveing visual feedbacks (i.e. displays), hosting additional connectors, etc. etc.
A full 4HP "modular module" is made of two block stacks in a 4HP space.
One stack output must be connected to the other stack input if series modulation is required.
Components used are the most common possible. The 1/8" signal jacks are everywhere online and cheap, so it is not difficult to source them. Signal jacks I used are commonly labelled PJ301M.
Potentiometers are common linear (or logaritmic) 47K ohm pots I bent and "elongated" with some single pole conductor in order to reach the PCB holes. These are commonly labelled WH148.
Amplifiers, transistors, connectors and every single component here used are super cheap, easy to source and common.

# Blocks Description
Here is the list and description of Blocks realized so far.

**Power Filter**
The power filtering circuit is very simple. Four capacitors in total, two electrolitic and two non polarized, are in charge to filter high and low frequency noise from the PSU +/-12V lines.
A diode with the cathode pointing the +12V and anode to -12V assures module's inversion polarity protection.
Two LEDs are there to monitor voltages from the PSU. These (and their current limiting resistors) are optional if you already have a power indication somewhere in your synthesizer and want to save some mA.
The PCB hosts a 5x2 pin IDC connector with Eurorack pinout for power supply.

**Passive Attenuator**
An attenuator is a device that reduces (or "attenuates") the level of a signal. A fader on a mixer is an attenuator. Attenuators are particularly useful for adjusting how much "depth" of modulation you send from one module to another module's parameter. The simplest circuit we can adopt for the task is a so called "voltage divider".
This block is the simplest of the lot and rely heavily on the front block main component: the potentiometer.

**Voltage Controlled Attenuator**
This block is someway an "evolution" of the previous one, giving the attenuation a control voltage.
The circuit is simple, with a JFET driven in it's ohmic (or linear) region to work as variable resistor and an additional input buffer stage in inverting configuration makes forward voltage instead of inverse voltage operation possible.

**Inverting Amplifier**
An inverting amplifier is a circuit that outputs a sigal opposite in sign to the one at it's input (the two are 180° out of phase). This block is built around a TL072 op-amp (as well as all the other active modules here presented).
The first op-amp stage is set as inverting amp with variable gain (up to 2X) set by the front panel potentiometer. The second op-amp stage is in voltage follower configuration.
Why an inverting amplifier instead of a "straight" one?? Well, because inverting amps are more entertaining.

**Dual Signal Inverter**
Inverters are devices used to invert (!!) the polaity of an incoming signal. This block is built around a TL072 dual op-amp in inverting configuration (I should stop stating the obvious, isn't it?).
By usign two of these blocks in a single module you obtain a quad inverter. This block is similar to the "Inverting Amplifier" block, but dubled and with fixed gain.




https://www.instructables.com/DIY-Synth-Modules-a-Modular-Approach-Ep1/

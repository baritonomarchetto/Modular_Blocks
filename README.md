# Modular Modularity
Eurorack Modules, but modular themselves :)

While thinking at the features I wanted for two voltage processing modules and some tinkering with my favourite CAD software, I ended with an idea. Most of those aforementioned "subdued" modules (go easy on me please) offer simple functions that are the sum of small circuits in series. Most of these circuits are the same for different modules, like the power supply filters section or voltage attenuation section, just to name a few.

So, here is the idea: modular modules!

# Blocks Layout
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

**DC Offsetter**

Even if the Eurorack standard calls for signals in the +/-5V range (unbiased), some very important circuit work adeguately ony with biased voltages. In example, CEM3340 PWM input works in the 0-8V range, meaning that an eurorack-compatible LFO would drive it to inaudible levels for half of it's cycle.

How could we solve? Well, by adding a DC offset voltage to our modulating signal.

The circuit adopted for this module pushes up or down 4V any input voltage when powering @12V. At knob's half position the offset is zero. Turn left for negative offset. Turn right for positive offset. This kind of circuit could be most often be seen in voltage processor modules.

The circuit is merely the most basic (inverting) mixer, where an input signal and DC offset voltage are added toghether. The signal is then inverted (again) in order to restore it's original polarity.

**Phase Shifter**

A phase shifter is used to, you can bet it, shift in phase a waveform. 

In my modular synth I have four CEM3340 oscillators. Each of them has it's own FM/PWM input. I could send the exact same CV to all of them, but what if I send two (or more) different CVs, phase shifted one to the other? Another application could be the modulation of the two sections of a band pass filter in order to open and close it in a less-predictable way.

**Buffered Multiple**

Most of the times a passive multiple will work, but what if you want carbon-copies of your voltage sweep?

The buffered multiple block is built around a TL074 quad op-amp with unity gain. The signal at the input jack is sent 1:1 at the three outputs. By usign two of these blocks in a single module and connecting the output of one semi-module to the input of the other you have a 1 input -> 5 outputs buffered multiple. Cool :)

**Track & Hold**

Track and holds perform a very special function: they hold an incoming, variable voltage for a brief time when triggered, then let the voltage pass as-is. They are different from Sample & Holds because in these the voltage is hold for higher times and the incoming wave sort of "digitalized".

The circuit adopted is possibly the simplest you can find online (or very close to it) and it's built around a n-channel JFET (2N5484) in series switch configuration. Two voltage followers increase the block's input capacitance and increase the output current capability of the whole circuit (it also makes a good reverse connection protection).

**White Noise Generator**

A white noise generator is mandatory to synthesize special effects (wind), give rattle to a snare or breath to a pad.

The white noise generator is based on a simple design takeing advantage from the natural occurring PNP semiconductor junction thermal noise. The "barebone" noise is amplified by a dual inverting amplification stage. The first amp stage is a straight 5X amplfication to give the small noise signal (100-300 mV depending on the transistor) a boost. The second amplification stage has variable, user definable gain through a potentiometer.

**LED Voltage Monitor(polarity indicator)**

A nice addition to modules are LED-based indicators. An example? Do you remember the DC offsetter block from the previous blocks set? We can now realize a DC offsetter module with polarity indicator. What about attenuators? You can now have a visual indication of how much attenuation you are applying to your signal.

This block main components are a couple of operational amplifiers and two LEDs. Nothing more.

The polarity indicator main circuit block was not compatible with existing front blocks, so I layed down a dedicated one. I made it compatible with "4 jacks" front panels, with LEDs aligned to the two middle holes.

**Non-Attenuated, Fixed Gain Mixer**

A 3-inputs mixer in a very limited space is possible if you left out the per-channel attenuation stage and set a fixed gain. This block adds up to three signals to a single output with fixed gain.

# External Links
https://www.instructables.com/DIY-Synth-Modules-a-Modular-Approach-Ep1/

https://www.instructables.com/DIY-Synth-Modules-a-Modular-Approach-Ep2/

https://synthbrigade.altervista.org/moduli-modulari-eurorack-compatibili/

https://synthbrigade.altervista.org/moduli-modulari-episodio-secondo/

# Acknowledgments
Many thanks to those nice girls and guys at JLCPCB for sponsoring the manufacturing of blocks main PCBs and the two aluminum face-plates pictured in this Instructable.

The sponsorship made possible to turn "modular modularity" from the status of "idea" into reality in first place, then make it even more interesting with the addition of new circuit blocks.

JLCPCB is a high-tech manufacturer specialized in the production of high-reliable and cost-effective PCBs. They offer a flexible PCB assembly service with a huge library of more than 400.000 components in stock.
3D printing is part of their portfolio of services so one could create a full finished product, all in one place!

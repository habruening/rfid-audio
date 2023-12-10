# rfid-audio

## Project Status
Completed and running. This github repository is in development. Please come back later!

## Introduction
This project is an audio music box, that can be controlled with RFID cards. This repository does not provide anything new, that is not already availalbe on many other web pages. As there is already plenty of information available in the Internet, the purpose of this repository is to collect the relevant information and to give the reader a complete guidance.

### What is special in this project?
* This project uses the Raspberry Pi Zero W only.
* This project uses a three color status LED.
* This project uses bluetooth audio
* This project disconnects from bluetooth when not playing

## The hardware

### The LEDs

### What to buy

This project uses an RGB LED. This combination of colors is the most intuive:

* Blue signalises the bluetooth status.
* Green signalises a normal readiness status.
* red signalises an abnormal status.

The typical size of LEDs is 5mm.

The LED should be matt/diffuse. Clear LEDs are not comfortable to view and do not mix the colors well. Typically an RGB LED costs less then 1€/1$.

An LED should have a housing in order to fix it on wood or on the case. The Kingbright RTC-51 is a typical product, that costs a few cents.

#### How to connect?

The the longest contact of the LED is the anode. It has to be connected to ground.

The other three contacts are for the colors. The typical maximum current for an LED is 20 mA. Each LED color needs another voltage in order to achieve the same current. In principle, therefore each LED requires an individual calculated or tested resitor. The GPIO pins provide 3.3V. In practice, 20mA is far too much (too bright) for status LEDs. The Raspberry PI also can only drive 50mA in total without been damaged. In practice a LED is still bright enough at 3mA. An 330 Ohm resistor can typically be used for all colors. With this resistor all colors are still too bright for most usages. They must be dimmed down with software. If it is prefered to go without dimming, the resitor must be chosen bigger than 330 Ohm.

It is not possible to use only one shared resistor on the anode pin. The interested reader should do experiments calculations in order to convince himself why this is not possible.

This project connects red to GPIO 19 at pin 35, green to GPIO 13 at pin 33, blue at GPIO 32. This connection is important as will be seen later.

### The RFID Reader

This project uses a RC522 wifi reader for about 6€.

#### How to connect?

As the GPIO pins are general purpose, there are many options how to connect the RF522 card.

This project uses the following configuration (from [https://tutorials-raspberrypi.de/raspberry-pi-rfid-rc522-tueroeffner-nfc/](Tutorials for Raspberry Pi)).


SDA <->	Pin 24 / GPIO8 (CE0)
SCK	<-> Pin 23 / GPIO11 (SCKL)
MOSI <-> Pin 19 / GPIO10 (MOSI)
MISO <->	Pin 21 / GPIO9 (MISO)
IRQ	<-> not connected
GND	<-> Pin6 (GND)
RST	<-> Pin22 / GPIO25
3.3V <-> Pin 1 (3V3)

## The Operating System

Use the Raspberry Pi Imager and load the Raspberry Pi OS Lite (32 bit). See the [screenshots](image-loader.md).

## The Software

## The Program

## Critical Observations
### Performance
The CPU utilisation is relatively high. Only the RFID reading process consumes 50% CPU time. The project works only stable if no other background activities are running (such as SSH connections). It could be seen that the Raspberry Pi Zero W perfectly fits the requiremenets of the project. It does the job and it does not offer more CPU power than needed.

But it could also be stated that in principle the Raspberry Pi and Python are not the right platform for such projects. Although, there is plenty of CPU power, it is not reliable to perform real time jobs on the standard Raspberry Pi Linux. A simple microcontroller (e.g. the arduino) can do the same job with a fraction of CPU power and electrical power consumption if well programmed.

The only reasons why the Raspberry is the right path for most people are:

* It is still cheap.
* It still consumes few power.
* It has an extreme abundance of CPU power.
* It is extremely easy to develop with.
* It is very easy to find all sorts of information and support.

And that is one observation of the project: This project (like most other Raspberry Pi projects) has nothing to do with good professional engineering.

### Information from Internet
The Internet is full of information. As a layman it is impossible to distinguish good information, valid information, bad information, wrong information.

For example when reading about how to use Bluetooth audio, there are plenty of guides that use Pulseaudio, others use Pipewire and others use Bluealsa. But the reader normally does not know when to use what technology. The reader often is not even able to identify if a piece of information applies to his context or not.

Other examples of information, that are not helpful, are the guides in internet, which explain how a LED can be dimmed with PWM. Most times this is done programmatically with Python code. But that consumes much CPU time and does not work stable. But that information is presented on many web pages or web blogs uncritically.

### Open Issus
Spotify Connect would not work. It is not supported by ARM 6.

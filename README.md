# rfid-audio

## Project Status
Completed and running. This github repository is in development. Please come back later!

## Introduction
This project is an audio music box, that can be controlled with RFID cards. This repository does not provide anything new, that is not already availalbe on many other web pages. As there is already plenty of information available in the Internet, the purpose of this repository is to collect the relevant information and to give the reader a complete guidance.

### What is special in this project?
* This project uses the Raspberry Pi Zero W only.
* This project uses a three color status LED.
* This project uses bluetooth audio

## The hardware

### The LEDs

### The RFID Reader

## The Operating System

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

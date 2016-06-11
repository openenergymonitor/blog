---
published: false
layout: post
title: "Compiling and Uploading Firmware using PlatformIO"
date: "2016-06-11 10:00"
date_formatted: June 11th 2016
author: Glyn Hudson
comments: true
categories:
  - firmware
  - emonpi
  - emontx
---

Getting an Arduino based project (or other embedded platform) to compile and upload can be a pain. Making sure all the correct libraries are installed in the correct places and the correct version can be tricky time-consuming .

I'm sure many developers will agree that the tools used for embedded development are generally not as good as those used for web application development.

The Arduino team have done a good job with their IDE to try and make the embedded development tool chain setup as easy as possible. However, a still find library management a case of frustration. Especially since I move between computers and OS's frequently. I'm also not a particularly fond of the Arduino IDE

Recently I have been using PlatformIO and am rather impressed with the ease of setup, speed of compilation, uploading (auto port detection), and crucially an excellent [library manager](http://platformio.org/lib)

> PlatformIO is an open source ecosystem for IoT development
> Cross-platform build system. Continuous and IDE integration. Arduino and ARM mbed compatible


![PlatformIO IDE]({{site.image_path}}/pio-ide.png)

<!--more-->

Here are the things I like about PlatformIO (pio) one week in:
- [Fully open-source](https://github.com/platformio) with active and friendly dev community
- Easy to install - Pure python based installed using pip
  - Tool-chains are auto installed on first compile / upload e.g.
    - If trying to upload to Arduino avrdude will automatically be installed
    - If trying to compile an ESP8266 project the ESP tool chain will be installed
  - Cross-platform (Linux, Windows and mac all work the same), this will make support much easier
- Command line and IDE
  - At work I use pio via Atom IDE on Ubuntu
  - At home, I use a Chromebook with Caret IDE and interact with pio via command-line
   - When developing directly on an emonPi / RaspberryPi pio command-line works great - *Yes, that's right pio works on a RaspberryPi to compile and upload code directly!*
- Excellent [library manager](http://platformio.org/lib)
  - Libraries can be searched and reviewed using command-line or web 2.0 manager
  - Required librarys can be specified in the `platformio.ini` file and if not present install is prompted upon compilation
  - Specific library version (as defined in `library.json` [(emonLib example)](https://github.com/openenergymonitor/EmonLib/blob/master/library.json)) or git commit SHA









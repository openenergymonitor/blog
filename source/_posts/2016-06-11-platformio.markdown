---
published: true
layout: post
title: 'Part 1/3: PlatformIO open-source embedded development ecosystem'
date: '2016-06-12 10:00'
date_formatted: June 12th 2016
author: Glyn Hudson
comments: true
categories:
  - platformio
  - travisci
  - firmware
  - emonPi
  - emontx
---


**This post is part of a series:**

 - **1/3: PlatfomIO overview & compiling + uploading locally and on a Raspberry Pi**
 - [2/3: Continuous testing and auto release binary generation using PlatformIO & TravisCI](/2016/06/auto-build-continuous-test-firmware/)
     - Related post: [EmonESP ESP8266 WiFi developments](/2016/06/esp8266-emonesp-developments)
 - [3/3: Continuous Deployment (OTA to ESP8266)](/2016/06/esp8266-ota-update/)

***

Getting an Arduino based project (or other embedded platform) to compile and upload can be a pain. Making sure all the libraries are installed in the correct locations and are the correct versions can be tricky and time-consuming.

I'm sure many developers will agree that the tools we use for embedded development are generally not as good as those used for web application development.

The Arduino team have done a good job with their IDE to try and make the embedded development tool-chain setup as easy as possible. However, I still find library management a cause of frustration. Especially since I move between computers and OS's frequently.

Recently I have been using [PlatformIO](http://platformio.org) and am rather impressed with the ease of setup, speed of compilation, uploading (auto port detection), and most importantly an excellent [library manager](http://platformio.org/lib).

> PlatformIO is an open-source ecosystem for IoT development.

> Cross-platform build system, IDE integration and continuous testing. Arduino, Espressif, ARM and mbed compatible.


![PlatformIO IDE]({{site.image_path}}/pio-ide.png)



<!--more-->

Here are some things that have impressed me about PlatformIO (pio) after using it for a couple of weeks:

- [**Fully open-source**](https://github.com/platformio) with active and friendly dev community.
- **Easy to install** - Pure python based, installed using pip
  - Tool-chains are auto installed on first compile / upload e.g.
    - If trying to upload to Arduino avrdude will automatically be installed
    - If trying to compile an ESP8266 project the ESP toolchain will be installed
  - Cross-platform (Linux, Windows and mac all work the same), this will make support much easier
- **Supports all the main embedded platforms**
  - atmelavr (Arduino), espressif (ESP8266), ststm32 (ARM etc.)
- **Command line and IDE**
  - At work I use pio via Atom IDE on Ubuntu
  - At home, I use a Chromebook with Caret IDE and interact with pio via command-line
   - When developing directly on an emonPi / RaspberryPi pio command-line works great - *Yes, that's right pio works on a RaspberryPi to compile and upload code directly!*
- [**Excellent library manager**](http://platformio.org/lib)
  - Libraries can be searched and reviewed using command-line or web 2.0 manager
  - Required libraries can be specified in the `platformio.ini` file and if not present install is prompted upon compilation
  - Specific library version (as defined in `library.json` [(emonLib example)](https://github.com/openenergymonitor/EmonLib/blob/master/library.json)) or git commit SHA
- **Fast compilation & pain-free uploading**
  - PlatformIO's compiler is the [fastest in the business](https://twitter.com/krzychb2/status/729294573760065536)
  - USB / Serial ports auto detected
  - Since the emonPi has been added as a custom board PlatformIO can even upload direct to emonPi via RaspberryPi GPIO and trigger GPIO AVR reset, not more [hacked avrdude](https://github.com/openenergymonitor/avrdude-rpi).
- **Easy integration with continuous testing & deployment**
  - Integration with TravisCI to enable compilation, code testing and binary (.hex / .bin) release generation in the cloud.
   - [emonPi](http://github.com/openenergymonitor/emonpi/) and [emonTx](github.com/openenergymonitor/emonTxFirmware) git repos are now enabled for continous-testing and auto binary generation on release tag...this is a step change in embedded development.

***


## Example: Compiling emonTx / emonPi firmware

[PlatformIO has some excellent quick start docs](http://docs.platformio.org/en/latest/quickstart.html) to cover setting up your first 'blinky' project, therefore I will not duplicate here. In this example I focus on setting up pio and compiling emonTx / emonPi firmware. This example assumes a totally bare metal machine with nothing installed except python (2.7 recommended). Pio works great on a Raspberry Pi.

This guide used command-line steps on Linux, if using Windows or if you want to use the platformio IDE see [PlatformIO Getting Started Page](http://platformio.org/get-started).

The PlatformIO IDE or Atom IDE is excellent and very easy to use (self explanatory). This guide uses pio via command line as this gives a more hands-on experience to how pio is working.

### 1. Install PlatformIO

The easiest way if running Linux is to use the install script, this installs pio via python pip and installs pip if not present. See [PlatformIO installation docs](http://docs.platformio.org/en/latest/installation.html#installer-script):

`$ sudo python -c "$(curl -fsSL https://raw.githubusercontent.com/platformio/platformio/master/scripts/get-platformio.py)"`

### 2. Clone emonTx / emonPi repo

We'll use the emonTx (V3 discrete sampling) as an example here but the steps are exactly the same for emonPi.

**emonTx V3**

```
$ git clone https://github.com/openenergymonitor/emonTxFirmware`
$ cd emonTxFirmware/emonTxV3/RFM/emonTxV3.4/emonTxV3_4_DiscreteSampling
```

**emonPi**

```
$ git clone https://github.com/openenergymonitor/emonpi`
cd emonpi/firmware
```

### 3. Compile with PlatformIO

`$ platformio run`

or shorthand for the lazy

`$ pio run`

**That's it!** That's all that's needed to setup pio from scratch and compile emonTx firmware :-D

The first time platformIO is run it will ask to install the required libraries (versions specified) and AVR toolchain. The required libraries are defined in [`platformio.ini` in the emonTx discrete sampling firmware folder](https://github.com/openenergymonitor/emonTxFirmware/blob/master/emonTxV3/RFM/emonTxV3.4/emonTxV3_4_DiscreteSampling/platformio.ini):

e.g.

```
lib_deps_external =
  DHT sensor library @1.2.3
  DallasTemperature @3.7.7
  EmonLib
  JeeLib@c057b5f4c0
  LiquidCrystal_I2C @4bb48bd648
```

The latest version of the libraries are automatically cloned from their native git repos into the `~/platformio` folder.

If required specific versions can be installed e.g.:

```
$ pio lib install 252 --version="e70c9d9f4e"
$ platformio lib install 54 --version="3.7.7"
```

### 3. Upload using PlatformIO

#### 3a. Via USB to UART programmer to emonTx

`$ sudo platformio run --target upload`

or lazy shorthand

`$ sudo pio run -t upload`

Pio will attempt to auto detect the USB programmer and upload :-)

*Note: you will need `sudo` unless you have correctly [configured udev rules](https://github.com/platformio/platformio/blob/develop/scripts/99-platformio-udev.rules).*

To list available serial ports:

`$ pio serialports list`

There is even a built in serial monitor

`$ pio serialports monitor`

### 3b. Using ttyAMA0 GPIO to upload direct to emonPi

This is where things get very exciting, pio can compile the code directly on a Raspberry Pi. The latest version of pio (~~due to be released in the next few weeks~~, [released 2.10.0](https://community.platformio.org/t/platformio-cli-2-10-0/381)) will have built in support for the emonPi auto-reset on upload using GPIO4. See [emonPi listed on PlatformIO boards page](http://platformio.org/boards?count=1000&filter%5Bname%5D=emonpi&page=1&sorting%5Bvendor%5D=asc):

![emonpi-platformio.png]({{site.image_path}}/emonpi-platformio.png)

The emonPi board is defined in `platformio.ini` in the [emonpi/firmware folder](https://github.com/openenergymonitor/emonpi/blob/master/firmware/platformio.ini):

```
board = emonpi
upload_port = /dev/ttyAMA0
```

All that is needed to compile and upload directly on the emonPi is:

```
cd ~/emonpi/firmware
$ sudo service emonhub stop
$ sudo pio run -t upload
$ sudo service emonhub start
```

*Thanks a lot to [Ivan Kravets](https://github.com/ivankravets) for helping integrate emonPi into the PlatfomIO ecosystem. [View commit changes](https://github.com/platformio/platformio/commit/c5b5e80de4928cf91be59e675429b520e31d873a)*

***
Stay tuned for part 2/3 of the PlatformIO post series which will cover setting up firmware continuous testing using Travis CI and auto compiled binary generation on release tag directly on github. This is currently live on the emonPi & emonTx repos if you want a sneak preview. See [travis.yaml](https://github.com/openenergymonitor/emonpi/blob/master/.travis.yml) file and Travis build status icon on the main emonpi repo [Readme.md](https://github.com/openenergymonitor/emonpi/blob/master/README.md).

***

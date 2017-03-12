---
published: true
layout: post
title: "OpenEVSE EV Charge Controller Review"
date: "2017-01-04 09:00"
date_formatted: Jan 4th 2017
author: Glyn Hudson
comments: true
categories:
  - openevse
  - ev
---

OpenEVSE (recently renamed to [OpenEV](https://www.openevse.com/)) design and build fully open-source EVSE (Electric Vehicle Supply Equipment) charge controllers for electric vehicles.

> An EVSE charging station, is a device an electric car (EV) is plugged into to charge. It communicates to the car to agree on a charging rate that is the fastest and safest rate both the car and the power supply can support.

**Update March 17: OpenEnergyMonitor and proud to announce that we are now the UK / Europe reseller for OpenEVSE charging stations, see [OpenEnergyMonitor Online Shop](http://shop.openenergymonitor.com/ev-charge-controllers/).**

***

![openevse leaf]({{site.image_path}}/leaf-openevse.jpg)

![openevse build9]({{site.image_path}}/openevse-build9.jpg)

![openevse-front]({{site.image_path}}/openevse-front.jpg)

*Note: this review is my account of using the OpenEVSE in the UK (240V single-phase AC), see OpenEVSE website for official build guides*

## Features

The features that make the OpenEVSE charge controller interesting to us are:

- [WiFi connectivity and remote control (via ESP8266)](http://openevse.dozuki.com/Guide/OpenEVSE+WiFi+%28Beta%29/14)
- Variable rate of charge: e.g. charge current can be varied to match available power
- Integrated energy monitoring via custom hosted Emoncms [data.openevse.com](http://data.openevse.com/emoncms)
- Fully open-source :-)

*I recently swapped my ageing diesel car for an all-electric Nissan LEAF (it's fantastic), so it felt like the perfect time to build and test an OpenEVSE charge controller unit!*

Nissan LEAF charging from solar PV on a frosty morning:

![nissan-leaf-solar-pv]({{site.image_path}}/nissan-leaf-solar-pv.jpg)

<!--more-->

<div class='videoWrapper'>
<iframe width="280" height="157" src="https://www.youtube.com/embed/A9D48V1D1G4" frameborder="0" allowfullscreen></iframe>
</div>

## Safety

Even though it is possible to charge an EV via a standard electrical outlet, it is not recommended for a number of reasons:

1. Charging is very slow since the current is limited by the electrical outlet.
2. Drawing a significant current (approx 10/12A) for an extended period (up to 10hrs for a 24KWh Nissan LEAF and 30hrs for a 90KWh Tesla Model S!) puts stress on the domestic wiring resulting in heating of the wire [or worse](https://speakev.com/threads/house-fire-using-120v-trickle-charger.1708/) if the wiring is in a poor state.

> Charging via a properly installed EVSE is the fastest and safest way to charge an EV at home.

OpenEVSE units have been designed to exceed the safety requirements for EV Charging Stations from SAE J1772, NEC and UL. Before supplying power to the car (and continuously while charging) the EVSE unit conducts a number of checks, no power is supplied until all the checks have passed. See [OpenEVSE Safety Features](https://openev.freshdesk.com/support/solutions/articles/6000113537-openevse-safety-features)


## Purchase

*Update: we are in communication with OpenEVSE to put together a UK/Europe specific OpeneEVSE package to resell via the [OpenEnergyMonitor Online Shop](https://shop.openenergymonitor.com).*

OpenEVSE units can be purchased (kit or fully assembled) from the [OpenEVSE online store](https://store.openevse.com), the units are shipped from California USA. I went for a [P50D Level 2 Deluxe OpenEVSE kit](https://store.openevse.com/collections/frontpage/products/openevse-50a-charge-station-combo-with-enclosure) with the [WiFi connection kit](https://store.openevse.com/collections/frontpage/products/openevse-wifi-kit) and [J1772 Cable](https://store.openevse.com/collections/frontpage/products/j1772-cable-40a-ultra-flexible-us-only).

The OpenEVSE 50A L2 unit will charge any J1772 compliant car at up to 40A continous from a single phase 208-240V AC supply. However, you can dial back the current by setting the 'max charge current' to match your supply.

*Full disclosure: Chris Howell from OpenEVSE made the unit available free of charge for me to evaluate and improve the Emoncms / OpenEnergyMonitor integration.*


## Assembly


***Warning:*** *Assembly of an EVSE requires wiring Alternating Current (AC) components that will be exposed to voltages from 100 to 250v. If you do not have the experience and knowledge required to safely work with AC voltages please consult with an experienced electrician for assistance and inspection of your work.*

Assembly of the unit was straight forward following the [openEVSE build guide](http://openevse.dozuki.com/Guide/OpenEVSE+50A+Charging+Station/8). No soldering was required, only basic tools e.g. screwdriver, wire strippers etc. Assembly probably took me a couple of hours. I took my time to do a high-quality job of assembling, this is particularly important given the high currents involved.

The hardware components are all top quality, I was impressed by the attention to detail such as rubber seals around the LCD to waterproof the unit.
 
The hardware inside the unit is split into two main components which are physically separated: a high voltage and high current relay and a low voltage control electronics which is the microcontroller (ATmega328p) 'brains' of the unit. My unit contained an OpenEVSE Plus V4 control unit [see Datasheet](http://files.openevse.com/OpenEVSE_Plus_v4.pdf.):

![openevse build5]({{site.image_path}}/openevse-build5.jpg)

Rear PCB showing ATmega328p on the OpenEVSE Plus V4 controller:

![openevse build7]({{site.image_path}}/openevse-build7.jpg)

Build progress: charge controller, ground busbar, relay, LCD and mode button fixed into enclosure

![openevse build2]({{site.image_path}}/openevse-build2.jpg)

The finished build: WiFi ESP8266 module is visible on the top left.

![openevse build3]({{site.image_path}}/openevse-build3.jpg)


### Installation

Installation should be undertaken by a qualified electrician. The unit should be wired in using suitably rated cable ideally with a dedicated RCD circuit breaker. The max charge current of the unit should be set to match the supply circuit wiring.

## Operation

On first powerup some basic settings are set via the LCD menu using a combination of short/long presses of the front button. The menu system is impressively responsive considering it's running from an ATmega328! The basic settings include max charge rate (set to match wiring), charging service level and date-time. Settings are saved to EEPROM and date-time is kept up-to-date via a RTC battery backup.

The basic operation is very straightforward: just plug the car in and charging begins! Charging can be stopped/resumed by pressing the button on the front of the unit. Charging state is indicated by the backlight colour of the LCD and basic info such as current charging current and total kWh is displayed on the LCD.

Here is a photo of the unit charging my Nissan LEAF @ 26A. At this charge rate my 6.6Kw charge (24Kwh battery) Nissan LEAF will charge from flat in about 4hrs:

![openevse build4]({{site.image_path}}/openevse-build4.jpg)

Here's a nice demo of the basic features of the unit. Credit: YouTube user civicturbo2009:

<div class='videoWrapper'>
<iframe width="560" height="315" src="https://www.youtube.com/embed/BFseWN7JhNM" frameborder="0" allowfullscreen></iframe>
</div>

### Remote Datalogging

The Wifi kit (ESP8266) enables data logging from the OpenEVSE unit to a custom Emoncms server [data.openevse.com](http://data.openevse.com) via a local Wifi connection. The Wifi kit also allows remote control (see RAPI commands below).

![openevse build4]({{site.image_path}}/openevse-build-emoncms.png)


### Remote Control (via RAPI commands)

The OpenEVSE unit can be controlled and monitored remotely via serial RAPI (Remote API) commands. These commands can be [issued directly via serial](http://openevse.dozuki.com/Guide/Serial+Communications+with+OpenEVSE/13) or the OpenEVSE WiFi kit (ESP8266) can be added to allow RAPI commands to be issued remotely via an HTTP web interface.

#### Variable Charge Rate

OpenEVSE charge controller can vary the charge rate, or more specifically the OpenEVSE can 'request' a particular charge rate from the car. It is actually the cars charging control electronics that varies the charge rate. OpenEVSE requests a particular charge rate by varying the pilot signal square wave duty cycle [see OpenEVSE technical theory of opperation](https://openev.freshdesk.com/support/solutions/articles/6000052070-theory-of-operation). Charge rate can be varied from 6A (SAE/IEC standard min charge current) up to max charge rate (28A for my Nissan LEAF) in 1A increments. The car responds almost instantly to a charge rate adjustment request from the OpenEVSE controller. Charging can also be paused and resumed remotely if required.


**Example:**

`$SC13` will set the current charge current to 13A. The screen shot on the right below illustrates issuing the `$SC 13` RAPI command into the OpenEVSE local web page interface (served from ESP8266). The screenshot on the left shows the effect of reduction in charge rate as monitored by emonPi displayed using Emoncms:

![openevse build6]({{site.image_path}}/openevse-build6.png)

Rapi commands can also be issued directly via a single HTTP request. Eg. the same rapi command to set charging rate to 13A:

[http://192.168.0.108/r?rapi=%24SC+13](http://192.168.0.108/r?rapi=%24SC+13)

To sleep (pause a charge) issue RAPI command `$FS`

[http://192.168.0.108/r?rapi=%24FS](http://192.168.0.108/r?rapi=%24FS)

To enable (start a charge) issue RAPI command `$FE`

[http://192.168.0.108/r?rapi=%24FE](http://192.168.0.108/r?rapi=%24FE)

*Assuming `192.168.0.108` is the local IP address of the OpenEVSE ESP.*

There is also an [OpenEVSE RAPI command python library](https://github.com/tiramiseb/python-openevse).

RAPI commands can be used to control and check the status of all OpenEVSE functions. A full list of RAPI commands can be found in the [OpenEVSE plus source code](https://github.com/lincomatic/open_evse/blob/stable/rapi_proc.h).

#### Future developments

I would like to add MQTT support to the [OpenEVSE WiFi ESP8266 firmware](https://github.com/chris1howell/OpenEVSE_RAPI_WiFi_ESP8266), this will allow RAPI commands to be issued via MQTT over an authenticated local MQTT server e.g. emonPi / RaspberryPi or remote MQTT server e.g. Hive MQTT / Cloud MQTT. Using MQTT will make it easier and more secure to control the OpenEVSE. MQTT allow easy integration with all home automation and control platforms e.g nodeRED / OpenHAB / Emoncms.

**Update:** I have recently added RAPI commands over MQTT support to the [OpenEVSE ESP8266 code currently in the dev branch](https://github.com/chris1howell/OpenEVSE_RAPI_WiFi_ESP8266/tree/Devolopment).


See [this forum thread](https://community.openenergymonitor.org/t/openevse-ev-charging-station-with-emoncms-wifi-integration/2439/21) for related discussion.

### Open Source

The source code and CAD hardware designs for the OpenEVSE unit can be found on github:

- [OpenEVSE I2C LCD + RTC](https://github.com/OpenEVSE/OpenEVSE_LCD)
- [OpenEVSE Plus Controller Hardware](https://github.com/OpenEVSE/OpenEVSE_PLUS)
- [OpenEVSE Plus Controller Firmware](https://github.com/lincomatic/open_evse/blob/stable/rapi_proc.h)
- [OpenEVSE Plus Controller Pre Compiled Firmware](https://github.com/OpenEVSE/Default_Firmware_Loads)
- [OpenEVSE ESP8266 Wifi firmware](https://github.com/chris1howell/OpenEVSE_RAPI_WiFi_ESP8266)
- [OpenEVSE Enclosure](https://github.com/OpenEVSE/Enclosures)
- [OpenEVSE ESP8266 Wifi 2.0 firmware](https://github.com/OpenEVSE/ESP8266_WiFi_v2.x)

### Related Forum Threads

[OpenEnergyMonitor community forum thread documenting OpenEVSE build](https://community.openenergymonitor.org/t/openevse-ev-charging-station-with-emoncms-wifi-integration/2439/21)

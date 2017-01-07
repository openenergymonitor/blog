---
published: false
layout: post
title: "OpenEVSE EV Charge Controller Build"
date: "2017-01-04 09:00"
date_formatted: Jan 4th 2017
author: Glyn Hudson
comments: true
categories:
  - openevse
  - ev
---

OpenEVSE (recently renamed to [OpenEV](https://www.openevse.com/)) design and build fully open-source EVSE (Electric Vehicle Supply Equiptement) charge controllers for electric vehicles.

> An EVSE charging station, is a device an electric car (EV) is plugged into to charge. It communicates to the car to agree a charging rate that is the fastest and safest rate both the car and the power supply can support.

## Features

The features that make the OpenEVSE charge controller interesting to us are:

- [WiFi connectivity and remote control via ESP8266](http://openevse.dozuki.com/Guide/OpenEVSE+WiFi+%28Beta%29/14)
- Variable rate of charge: e.g. charge current can be varied to match available power
- Integrated energy monitoring via custom hosted Emoncms [data.openevse.com](http://data.openevse.com/emoncms)
- Open-source :-)

I recently swapped my ageing diesel car for an all-electric Nissan LEAF (it's fantastic), so it felt like the perfect time to build and test an OpenEVSE charge controller unit!

## Safety

Even though it is possible to charge an EV via a standard electrical outlet, it is not recomeded for a number of reasons:

1. Charging is very slow since current is limited by the electricl outlet.
2. Drawing a significant current (approx 10/12A) for an extended period (up to 10hrs for a 24KWh Nissan LEAF and 30hrs for a 90KWh Tesla Model S!) puts stress on the domestic wiring resulting in heating of the wire [or worse](https://speakev.com/threads/house-fire-using-120v-trickle-charger.1708/) if the wiring is in a poor state.

> Charging via a properly installed EVSE is the fastest and safest way to charge an EV at home.

OpenEVSE units have been designed to exceed the safety requirements for EV Charging Stations from SAE J1772, NEC and UL. Before supplying power to the car (and continously while charging) the EVSE unit conducts a number of checks, no power is supplied until all the checks have passed. See [OpenEVSE Safety Features](https://openev.freshdesk.com/support/solutions/articles/6000113537-openevse-safety-features)


## Purchase

OpenEVSE units can be purchased (kit or fully assembled) from the [OpenEVSE online store](https://store.openevse.com), the units are shipped from California USA. I went for a [P50D Level 2 (208-240V AC) 50A (40A continous) Deluxe OpenEVSE kit](https://store.openevse.com/collections/frontpage/products/openevse-50a-charge-station-combo-with-enclosure) with the [WiFi connection kit](https://store.openevse.com/collections/frontpage/products/openevse-wifi-kit) and [J1772 Cable](https://store.openevse.com/collections/frontpage/products/j1772-cable-40a-ultra-flexible-us-only).

The OpenEVSE unit will charge any J1772 compliant car at up to 40A. However you can dial it back by setting the 'max charge current' to suit your supply.

*Full disclosure: Chris Howell from OpenEVSE made the unit available free of charge for me to evaluate and improve the Emoncms / OpenEnergyMonitor integration.*


## Assembly


**Warning:** Assembly of a EVSE requires wiring Alternating Current (AC) components that will be exposed to voltages from 100 to 250v. If you do not have the experience and knowledge required to safely work with AC voltages please consult with an experienced electrician for assistance and inspection of your work.

Assembly of the unit was straight forward following the [openEVSE build guide](http://openevse.dozuki.com/Guide/OpenEVSE+50A+Charging+Station/8). No soldering was required, only basic tools e.g. screwdriver, wirestripper. Assembly probably took me a couple of hours. I took my time to do a high quality job of assembling, this is particuarly important given the high currents involved.


OpenEVSE unit kit contents:

![openevse build1]({{site.image_path}}/openevse-build1.jpg)

The hardware components are all top quality, I was impressed by the attention to detail such as rubber seals round the LCD to waterproof the unit.
 
The hardware inside the unit is split into two main components which are physically seperated: a high voltage and high current relay and a low voltage control electronics which is the microcontoller (ATmega328p) 'brains' of the unit. My unit contained a OpenEVSE Plus V4 control unit [see Datasheet](http://files.openevse.com/OpenEVSE_Plus_v4.pdf.):

![openevse build5]({{site.image_path}}/openevse-build5.jpg)

Rear PCB showing ATmega328p on the OpenEVSE Plus V4 controller:

![openevse build7]({{site.image_path}}/openevse-build7.jpg)

Build progress: charge controller, relay, ground bus-bar, LCD and mode button fixed into enclosure

![openevse build2]({{site.image_path}}/openevse-build2.jpg)

![openevse build3]({{site.image_path}}/openevse-build3.jpg)


### Installation

Installation should be untertaken by a qualified electrician. The unit should be wired in using suitably rated cable ideally with a dedicated RCD circuit breaker. The max charge current of the unit should be set to match the supply circuit wiring.

## Opperation

On first powerup some basic settings are set via the LCD menu using a combination of short/long presses of the front button. The menu system is impressivly responsive considering it's running from an ATmega328! The basic settings include max charge rate (set to match wiring), charging service level and date-time. Settings are saved to EEPROM and date-time is kept up-to-date via a RTC battery backup.

Basic opperation is very stright forward: just plug the car in and charging begins! Charging can be stopped/resumed by pressing the button on the front of the unit. Charging state is indicated by the backlight colour of the LCD and basic info such as current charging current and total Kwh is displayed on the LCD.

Here is a photo of the unit charging my Nissan LEAF @ 26A. At this charge rate my 6.6Kw charge (24Kwh battery) Nissan LEAF will charge from flat in about 4hrs:

![openevse build4]({{site.image_path}}/openevse-build4.jpg)


### Remote Datalogging

The Wifi kit (ESP8266) enables data logging from the OpenEVSE to a custom Emoncms [data.openevse.com](http://data.openevse.com):




### Remote Contol (via RAPI commands)

The OpenEVSE unit can be controlled and monitored remotly via serial RAPI (Rapid API) commands. These commands can be issued directly via serial or the OpenEVSE WiFi kit (ESP8266) can be added to allow RAPI commands to be issued remotly via a web interface. The Wifi kit also enables data logging to a custom Emoncms [data.openevse.com](http://data.openevse.com)

#### Variable Charge Rate

The Nissan LEAF charge rate can be varied from 6A to 28A (I have the 6.6KW charge option) in 1A increments, the car responds almost instantly to a charge rate adjustment request from the OpenEVSE controller. Charging can also be paused and resumed remotly if required.

![openevse build6]({{site.image_path}}/openevse-build6.png)


http://192.168.0.108/r?rapi=%24SC+50


### Open Source

The source code and CAD hardware designs for the OpenEVSE unit can be found on github:

- [OpenEVSE I2C LCD + RTC](https://github.com/OpenEVSE/OpenEVSE_LCD)
- [OpenEVSE Plus Controller Hardware](https://github.com/OpenEVSE/OpenEVSE_PLUS)
- [Pre Compiled Default Firmware](https://github.com/OpenEVSE/Default_Firmware_Loads)
- [OpenEVSE Enclosure](https://github.com/OpenEVSE/Enclosures)

### Related Forum Threads

[OpenEnergyMonitor community forum thread documenting OpenEVSE build](https://community.openenergymonitor.org/t/openevse-ev-charging-station-with-emoncms-wifi-integration/2439/21)






mode 1) Solar Surplus : This is the one everyone comes to first and whats first.

mode 2) Solar Divert : The same as above, but taking the house base load out of the calculation. This way your car can be powered by sunshine, the house from your renewable energy supplier!

mode 3) Full manual : I would like to be able to manually adjust the current limit remotely and start / stop charge remotely.

mode 4) Grid carbon : Not that useful practically but I thought it would be interesting to demonstrate the ability to stop charging when Grid Carbon rises above a certain threshold value you set / choose.

mode 5) Peak Time Current Adjustment : When I get home I want to plug my car in to charge (so I don't forget) but may not want it to pull full current as it s peak time. It would be possible / interesting to set a max current profile for the car to pull for each hour of the day. This way it could be plugged in put paused from say 5pm until 8pm then could start to charge at a low current rate of 6A ramping up to max after 11 or 12 when the grid is in surplus.

mode 6) SoC controlled : charge the car until a certain SoC is reached. I only need say 55% SoC to get to work so It would be good to plug in and forget about it rather than have to nip back out at some point to check the car and unplug.

https://community.openenergymonitor.org/t/openevse-ev-charging-station-with-emoncms-wifi-integration/2439/14?u=glyn.hudson

mode 7) Timed : Not all EVs have charging timers so it would be good to plug in and then the EVSE command a charge (for instance) during the Economy 7 hours only.
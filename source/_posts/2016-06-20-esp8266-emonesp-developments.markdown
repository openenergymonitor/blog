---
published: true
layout: post
title: 'ESP8266 WIFI developments'
date: '2016-06-20 10:00'
date_formatted: June 20th 2016
author: Trystan Lea
comments: true
categories:
  - esp8266
  - emonesp
  - wifipixel
  - heatpumpmonitor
  - emontx
---


Glyn and I have been doing a bit of development recently on using the ESP8266 WiFi board with OpenEnergyMonitor hardware, we are quite excited about the potential of this little module to both reduce the cost of the system and simplify setup and installation especially for applications that primarily post to a remote emoncms server such as [emoncms.org](https://emoncms.org).

**Note:** we have no plans to discontinue developments and support for Raspberry Pi based systems e.g. emonPi / emonBase. Quite the opposite: the local storage and processing of a Raspberry Pi based system has many advantages particularly for systems requiring more flexibility and customisation e.g Local Emoncms storage. MQTT, openHAB & nodeRED integration. The ESP developments will be ran in parallel, in fact ESP could be configured to post to an emonPi / emonBase via MQTT for local on-site storage and integration.

We are at the moment working on three initial uses of the ESP8266:

## 1. **EmonTx V3** + ESP8266 module

We are initially using the Adafruit HUZZAH ESP8266 module as a development platform. For anyone keen to get going with the ESP8266 Huzzah module it is available from a number of places such as [adafruit](https://www.adafruit.com/product/2471) (USA) and [Pimoroni](https://shop.pimoroni.com/products/adafruit-huzzah-esp8266-breakout) (UK). Any ESP8266 with ESP-12 module should work the same. See lower in the post for EmonESP firmware dev.



![image]({{site.image_path}}/emontx-esp.png)


There will be another post very soon detailing how to use this module with the EmonTx v3.

<!--more-->

## 2. Heatpump/Energy Monitor

Heatpump / energy monitor through-hole development board, essentially and EmonTx v2 with additional features for interfacing with heat meters and multiple DS18B20 temperature sensors as well as an integrated ESP8266 WIFI module.


![image]({{site.image_path}}/heatpumpmonitor.png)


The heatpump monitor board currently supports:

- 3x CT + ACAC Channels
- Elster A100C Irda meter reader (watt hours)
- Pulse Counting
- Supports MBUS heat meters (Kamstrup 402)
- Supports SIKA flow meters
- 4x DS18B20 Temperature Sensors
- Miniature solid state relay for heating control (not yet tested)
- ESP8266 Low cost Wifi
- RFM69 option
- Raspberry PI connector option
- A Through-hole ESP Wifi development platform
- Fits in the EmonTx V3 Aluminum case

Guide cost ~£50 (ex VAT) for full heatpump monitor kit with case, ~£30 (ex VAT) for cut down WIFI energy monitor only kit without case.. To be finalised.

[See Heatpump monitor development repo](https://github.com/openenergymonitor/HeatpumpMonitor)

## 3. ESP8266 based WIFI Pixel Energy Display,

This is an idea thanks to David Hunninsett ([@m0untainpenguin](http://twitter.com/m0untainpenguin)) with hardware being developed by [Protoneer](https://github.com/Protoneer/WifiPixels). It fits into a project we are more recently part of here in North Wales called [CydYnni by EnergyLocal](http://www.energylocal.co.uk/cydynni/) where 100 households within the boundary of the substation get cheap electricity when a local community hydro is running. David Hunninsett is one of the households on the project and he is keen to have a display that shows when it’s a good time to use electricity among other uses. The wifi pixel could become a nice platform for a ambient home energy indicator.

![image]({{site.image_path}}/wifi-pixel1.jpg)


![image]({{site.image_path}}/wifi-pixel2.jpg)


[See video](http://community.openenergymonitor.org/uploads/default/original/1X/c72e375230597049c0d8a9e06645a8d088d70774.mp4)

[See software development  repo on](https://github.com/davehun/mqtt-wifi-pixel)

# EmonESP, easier setup and installation

One of the really nice things about using the ESP module is that it can really simplify setup for installations that only need to post to a remote emoncms server. The wifi module starts by broadcasting a hotspot that you connect to directly, you can then scan for wifi networks, select the network, get the ip address of the monitor on the network (which saves using fing or accessing your router device list), enter your emoncms.org apikey to connect to an emoncms.org account (to be replaced with username and passowrd login + ability to register and link the monitor to a emoncms account in one step).

![image]({{site.image_path}}/emonesp.jpg)


We plan to extend EmonESP to also support MQTT.

The EmonESP software is based on work by Chris Howel of [OpenEVSE](http://www.openevse.com) which is a really nice open hardware electric vehicle charging station, it’s been really nice to find a common development like this that can be beneficial to two open hardware and software projects. OpenEVSE [already use Emoncms](https://data.openevse.com/) for logging and graphing.

[EmonESP firmware developments can be found on github](https://github.com/openenergymonitor/emonesp)

## Over the air firmware upload

Glyn has been doing a lot of work on how we can do over the air updates to ESP8266 based units. Being able to do this will make it a lot easier to maintain and keep the firmware on these updated especially as the software goes through the larger number of iterations in initial development. Check out his blog posts here to follow the development:

- [Part 1/3: PlatformIO open-source embedded development ecosystem](https://blog.openenergymonitor.org/2016/06/platformio/)
- [Part 2/3: Firmware Continuous Test & Build](https://blog.openenergymonitor.org/2016/06/auto-build-continuous-test-firmware)
- 3/3: Continuous Deployment (OTA to ESP8266) *...In the making!*

## Forum discussion

See [this forum topic](https://community.openenergymonitor.org/t/esp8266-wifi-developments/784) for discussion.

***

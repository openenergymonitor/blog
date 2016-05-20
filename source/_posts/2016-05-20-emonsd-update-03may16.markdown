---
published: true
layout: post
title: "emonPi emonSD pre-built SD card update"
date: "2016-05-20 10:00"
date_formatted: May 10th 2016
author: Glyn Hudson
comments: true
categories: 
  - emonSD
  - emonPi
  - raspberry pi
---

> Using the emonPi in it's default configuration works great to posting data to Emoncms for logging and visualisation. However there may be times when more flexibility and the ability to interface with other hardware or services is needed.

This latest update significantly enchances the out-the-box functionality of the emonPi by integrating applications such as nodeRED, openHAB and improved MQTT support.

For the past few years we have made available a pre-built SD card image for the RaspberryPi. Since launching the emonPi last year the pre-built image has been developed extensivly. We have now given it a name: **emonSD**.

The latest update to emonSD (**emonSD-03May16**) now incudes the following all setup and pre-configured:

- [Emoncms V9](https://github.com/emoncms/emoncms)
- [nodeRED](https://guide.openenergymonitor.org/integrations/nodered)
- [openHAB](https://guide.openenergymonitor.org/integrations/openhab)
- [MQTT](https://guide.openenergymonitor.org/technical/mqtt)
- [Support for MQTT LightWaveRF OOK Control](https://guide.openenergymonitor.org/integrations/lightwaverf/)
- [Support for MQTT WiFi control Relay](https://guide.openenergymonitor.org/integrations/mqtt-relay/)

<!--more-->

- [RASPBIAN JESSIE LITE](https://www.raspberrypi.org/downloads/raspbian/) (2015-11-21)
- [Raspberry Pi 3 Suppport](/2016/03/raspberry-pi-3/)
  - Including on-board Wifi, external USB Wifi adapter no longer required
- low-write optimisations for long SD card life-span
- Root file-system read-only

### [Download latest emonSD & view full change-log](https://github.com/openenergymonitor/emonpi/wiki/emonSD-pre-built-SD-card-Download-&-Change-Log#emonsd-03may16--release)

All emonPi / emonBase's that have been purchased from our online store from June 2015 - May 2016 have been shipped with the old [17June15](https://github.com/openenergymonitor/emonpi/wiki/emonSD-pre-built-SD-card-Download-&-Change-Log#emonsd-17jun15) emonSD. The new emonSD 03May16 will now be included by default ([together with a Raspberry Pi 3](/2016/05/emonpi-raspberrypi3/)) with all emonPi / emonBase purchases. If you have recently puchased an emonPi and it like the photo (black acrylic fascia) then you have the new emonSD and Raspberry Pi 3inside. The acrylic fascia is required to use the Raspberry Pi 3's on-board WiFi ([see blog post](/2016/05/emonpi-raspberrypi3/)):

![emonPi Raspberry Pi 3 Acrylic Fascia](/images/emonpi-raspi3.jpg)

Existing users can download the new emonSD from the link above and flash to a spare SD card and then use the [Emoncms backup / import](https://guide.openenergymonitor.org/setup/import/) tool to migrate local Emoncms data.

**We would highly recomend all users that are interested in having the latest features and future update to update to this new emonSD image. The June15 image will not receive any Emoncms updates.**

However if your emonPi is currently stable and is working as indended then don't feel that upgrading is essential, *"If it aint broke, don't f ix it!"*.


## Documentation

As [previously mentioned on the blog](2016/05/website-changes/) a couple of weeks ago we have launchded a new User Guide website, the launch of this Guide has coincide with the lanch of the new emonSD. The User Guide is designed to be the goto location for eveything a user needs to know to setup, use and configure an OpenEnergyMonitor system:

### [https://guide.openenergymonitor.org](https://guide.openenergymonitor.org)

## Related Blog posts 

### nodeRED

 - [Node-RED blog post tag](https://blog.openenergymonitor.org/categories/nodered/)
 - [emonPi, NodeRed and MQTT](https://blog.openenergymonitor.org/2015/10/emonpi-nodered-and-mqtt/)
 - [Node-RED Emoncms Node](http://2.bp.blogspot.com/-wVqIG0KV_8k/VkPM0XAJCYI/AAAAAAABi1c/EoNQ2OvDVvs/s1600/emoncms_nodered_node.png)
 - [Outdoor Temperature Data from Weather Underground to Emoncms & MQTT](https://blog.openenergymonitor.org/2016/02/outdoor-temperature-data-from-weather/)
 - [Ambient Wind Energy Indicator using Node-RED and Blink(1) USB](https://blog.openenergymonitor.org/2015/11/ambient-wind-energy-indicator-using/)
  
 ### openHAB
 
 - [OpenEnergyMonitor, emonPi and openHAB](https://blog.openenergymonitor.org/2015/12/openenergymonitor-emonpi-and-openhab/)
 
 ### LightWave RF
 
 - [Controling LightWaveRF plugs using emonPi](https://blog.openenergymonitor.org/2015/11/remote-control-of-lightwave-rf-plugs/)


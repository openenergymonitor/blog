---
published: true
layout: post
title: "emonPi emonSD pre-built SD card update 03May16"
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

The latest update to emonSD (03May16) now incudes the following all setup and pre-configured:

- [Emoncms V9](https://github.com/emoncms/emoncms)
- [nodeRED](https://guide.openenergymonitor.org/integrations/nodered)
- [openHAB](https://guide.openenergymonitor.org/integrations/openhab)
- [MQTT](https://guide.openenergymonitor.org/technical/mqtt)
- [Support for MQTT LightWaveRF OOK Control](https://guide.openenergymonitor.org/integrations/lightwaverf/)
- [Support for MQTT WiFi control Relay](https://guide.openenergymonitor.org/integrations/mqtt-relay/)

<!--more-->

- RASPBIAN JESSIE LITE (2015-11-21)
- Raspberry Pi 3 Suppport
  - Including on-board Wifi, external USB Wifi adapter no longer required
- low-write optimisations for long SD card life-span
- Root file-system read-only

#### [Download latest emonSD & view full change-log](https://github.com/openenergymonitor/emonpi/wiki/emonSD-pre-built-SD-card-Download-&-Change-Log#emonsd-03may16--release)

All emonPi / emonBase's that have been purchased from our online store from June 2015 - May 2016 have been shipped with the old [17June15](https://github.com/openenergymonitor/emonpi/wiki/emonSD-pre-built-SD-card-Download-&-Change-Log#emonsd-17jun15) emonSD. The new emonSD 03May16 will now be included by default ([together with a Raspberry Pi 3](/2016/05/emonpi-raspberrypi3/)) with all emonPi / emonBase purchases.

Existing users can download the new emonSD from the link above and flash to a spare SD card and then use the [Emoncms backup / import](https://guide.openenergymonitor.org/setup/import/) tool to migrate local Emoncms data.

**We would highly recomend all users that are interested in having the latest features and future update to update to this new emonSD image. The June15 image will not receive any Emoncms updates.**

However if your emonPi is currently stable and is working as indended then don't feel that upgrading is essential, *"If it aint broke, don't f ix it!"*.


## Documentation

As [previously mentioned on the blog](2016/05/website-changes/) a couple of weeks ago we have launchded a new User Guide website, the launch of this Guide has coincide with the lanch of the new emonSD. The User Guide is designed to be the goto location for eveything a user needs to know to setup, use and configure an OpenEnergyMonitor system:

### [https://guide.openenergymonitor.org](https://guide.openenergymonitor.org)

<br>



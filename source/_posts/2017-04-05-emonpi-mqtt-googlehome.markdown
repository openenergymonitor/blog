---
published: false
layout: post
title: "emonPi Home Automation Hub"
date: "2017-05-05 00:00"
date_formatted: May 6th 2017
author: Glyn Hudson
comments: true
categories:
  - emonPi
  - MQTT
  - google-home
---

I beleive automation can play an important role in helping to reduce energy consumption. For example being able to control my home central heating system remotly enables me to turn on the heating only when it's required and not have it runnning on a set schedule when the house is empty.

As [ previously mentioned in a blog post](2016/08/ecohomelab-control/), the emonPi ([running emonSD pre-built SD card](github.com/openenergymonitor/emonpi/wiki/emonSD-pre-built-SD-card-Download-&-Change-Log)) can function as a powerful home automation hub. Using the emonPi as a home automation hub is a good fit for a number of reasons:

- It's alread runing 24/7 for energy monitoring
- It's optimised for robust long term opperation: the root Raspberry Pi file-system is read-only to increase SD card lifespan
- It's already connected to your local network
- It's running Debian Raspbian Jessie thefore installing extra packages is easy
- Raspberry Pi 3 has plenty of space capacity
- Extra radios / accessories can be connected via USB
- It's already running an MQTT server
- emonSD pre-built SD card comes pre loaded with the following [integrations](guide.openenergymonitor.org/integrations) nodeRED, OpenHAB and LightWaveRF

In this post I want to share with you how I use the emonPi in my own home.

<!--more-->


## MQTT

MQTT lightweight communication protocl is used as the 'glue' communication layer between all the following services. See [technical/MQTT section of the User Guide](https://guide.openenergymonitor.org/technical/mqtt/) for more info about how MQTT works on the emonPi.

## Energy Monitoring

Emoncms...obviously :-D

Recently I have been loving using the V2 Emoncms Android app (currently in beta) which supports multiple pages (see [forum thread](https://community.openenergymonitor.org/t/emoncms-android-app-v2-0-1-open-beta-testing/3373)).

Video demo Emoncms Android app V2 beta:

<div class='videoWrapper'>
<iframe width="280" height="157" src="https://www.youtube.com/embed/LaTi-l9tVQM" frameborder="0" allowfullscreen></iframe>
</div>

I have also recently enjoyed using the redsigned Emoncms Apps module which have just bee released on [Emoncms.org](https://emoncms.org). It's now possible to have more than one MyElectric or MySolarPV 'app' per Emoncms account and Economy 7 split time of use tariffs are now spported (see [forum thread](https://community.openenergymonitor.org/t/new-version-of-the-emoncms-apps-module/3900/3)):

![myelectric-e7.png]({{site.image_path}}/myelectric-e7.png)

## Control

### Central Heating

To control my gas central heating boiler I use an [MQTT WiFi relay](https://guide.openenergymonitor.org/integrations/mqtt-relay/) which also has a built in thermostat and scheduler, although I don't use these features, I just control directly via MQTT. The WiFi Relay has been very reliable, it's been used daily for the past two years and never once required a reboot.

![mqtt-relay-overview.png]({{site.image_path}}/mqtt-relay-overview.png)

### Plug sockets (lights)

I use LightWave RF plugs to which I have lights and other entertainment devices connected e.g. stereo and chromecast. Being able to swich a whole plug bank on/off has the advantage of being able to turn devices fully off when not in use to minimise any vamprie drain.

The emonPi can control LightWave RF devices directl via MQTT if an RF OOk modules is fitted. See [LightWave RF emonPi User Guide](https://guide.openenergymonitor.org/integrations/lightwaverf).

![lightwave-rf-diagram.png]({{site.image_path}}/lightwave-rf-diagram.png)

LightWave RF devices are not perfect, the OOK RF protocol is simplistic, unsecure, occasionally un-reliable and state feedback is not available. I think if I was starting from scratch I would use a [ESp8266 based Sonoff plug](https://www.itead.cc/smart-socket.html) with thirdparty [MQTT firmware](https://github.com/arendst/Sonoff-Tasmota) or [EmonESP](https://github.com/openenergymonitor/emonesp) firmware.

## Interface

For the past few years I have been using OpenHAB as the contol interface. OpenHAB is pre-loaded onto the emonPi emonSD pre-built image. I am yet to upgrade to OpenHAB V2.0, it looks very nice. However, V1.8 is very reliable and fits my needs. I use the OpenHAB Android app to access the interface quickly from my phone:

![open-hab-home.png]({{site.image_path}}/open-hab-home.png)![open-hab-all.png]({{site.image_path}}/open-hab-all.png)

A while back (early 2016) I dabbled with [HomeAssistant](http://home-assistant.io/), ([see blog post](https://blog.openenergymonitor.org/2016/04/Home-Assistant/)). I was quite impressed, I have been following the project and it looks like it's matured to be an excellant home automation platform. Quit possibly a rivle to OpenHAB.

Another option for an interface is [NodeRED Dashboard](https://github.com/node-red/node-red-dashboard) which is now officially part of the NodeRED project.

The beauty of MQTT is that it's platform agnostic, it's possible to have many different interfaces controling the same control nodes.

### Voice interface

I've recently aquired a Google Home voice activated speaker, with a little help from [ha-bridge](https://github.com/bwssytems/ha-bridge) to emulate a Philips Hue bridge it's quite easy to get Google Home to control local devices via MQTT. The same setup will also work with Amazon Echo. See [ha-bridge setup guide for emonPi](https://github.com/openenergymonitor/emonpi-ha-bridge)

Here is a demo:

<div class='videoWrapper'>
<iframe width="280" height="157" src="https://www.youtube.com/embed/r_v4GXVp0OI" frameborder="0" allowfullscreen></iframe>
</div>

![google-home-app.png]({{site.image_path}}/google-home-app.png)


## Integration & Automation

NodeRED








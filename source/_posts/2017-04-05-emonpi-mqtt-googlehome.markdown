---
published: true
layout: post
title: "emonPi as a Home Automation Hub"
date: "2017-05-05 00:00"
date_formatted: May 6th 2017
author: Glyn Hudson
comments: true
categories:
  - emonPi
  - MQTT
---

I beleive automation can play an useful role in helping to reduce energy consumption. For example being able to control my home central heating system remotely enables me to only turn on the heating when it's required and not have it running on a set schedule when the house is empty.

As [ previously mentioned in a blog post](2016/08/ecohomelab-control/), the emonPi ([running emonSD pre-built SD card](github.com/openenergymonitor/emonpi/wiki/emonSD-pre-built-SD-card-Download-&-Change-Log)) can function as a powerful home automation hub. Utilising the emonPi as a home automation hub is a good fit for a number of reasons:

- It's already running 24/7 for energy monitoring
- It's optimised for robust long term operation: the root Raspberry Pi file-system is read-only to increase SD card lifespan
- It's already connected to your local network
- It's running Debian Raspbian Jessie therefore installing extra packages is easy and lots of support is available
- Raspberry Pi 3 has plenty of space capacity
- Extra radios / accessories can be connected via USB
- It's already running an MQTT server
- emonSD pre-built SD card comes pre loaded with the following [integrations](guide.openenergymonitor.org/integrations) nodeRED, OpenHAB and LightWaveRF

> In this post I want to share with you how I use the emonPi in my own home.

Here is a video demo using Google Home to control my central heating and devices via MQTT:

<div class='videoWrapper'>
<iframe width="280" height="157" src="https://www.youtube.com/embed/r_v4GXVp0OI" frameborder="0" allowfullscreen></iframe>
</div>

Read on to learn how this is achevied using an emonPi and open-source software...

<!--more-->


There are many many options when it comes to home automation and control. Where possible I prefer open-source solutions which do not depend on any third-party services. All the software services for my home system as I describe in this post runs locally on my emonPi and appart from Google Home voice integration does not require an internet connection to function. A self-hosted open-source solution has the added benefit of increased privacy and security which you are in fully in control of.

## MQTT

MQTT lightweight communication protocol is used as the 'glue' communication layer between all the following services. See [technical/MQTT section of the User Guide](https://guide.openenergymonitor.org/technical/mqtt/) for more info about how MQTT works on the emonPi.

## Energy Monitoring

Emoncms...obviously!

Recently I have been loving using the V2 Emoncms Android app (currently in beta) which supports multiple pages (see [forum thread](https://community.openenergymonitor.org/t/emoncms-android-app-v2-0-1-open-beta-testing/3373)).

Video demo Emoncms Android app V2 beta:

<div class='videoWrapper'>
<iframe width="280" height="157" src="https://www.youtube.com/embed/LaTi-l9tVQM" frameborder="0" allowfullscreen></iframe>
</div>

I have also recently enjoyed using the redesigned Emoncms Apps module which have just bee released on [Emoncms.org](https://emoncms.org). It's now possible to have more than one MyElectric or MySolarPV 'app' per Emoncms account and Economy 7 split time of use tariffs are now spported (see [forum thread](https://community.openenergymonitor.org/t/new-version-of-the-emoncms-apps-module/3900/3)):

![myelectric-e7.png]({{site.image_path}}/myelectric-e7.png)

## Control

### Central Heating

To control my gas central heating boiler I use an [MQTT WiFi relay](https://guide.openenergymonitor.org/integrations/mqtt-relay/) which also has a built in thermostat and scheduler, although I don't use these features, I just control directly via MQTT. The WiFi Relay has been very reliable, it's been used daily for the past two years in my home and never once required a reboot.

![mqtt-relay-overview.png]({{site.image_path}}/mqtt-relay-overview.png)

### Plug sockets (lights)

I use LightWave RF plugs to which I have lights and other entertainment devices connected e.g. stereo and chromecast. Being able to switch a whole plug bank on/off has the advantage of being able to turn devices fully off when not in use to minimise any [vampire drain](https://en.wikipedia.org/wiki/Standby_power).

The emonPi can control LightWave RF devices directly via MQTT if an RF OOk modules is fitted. See [LightWave RF emonPi User Guide](https://guide.openenergymonitor.org/integrations/lightwaverf).

![lightwave-rf-diagram.png]({{site.image_path}}/lightwave-rf-diagram.png)

LightWave RF devices are not perfect, the OOK RF protocol is simplistic, unsecure, occasionally unreliable and state feedback is not available. I am considering swithcing to [ESp8266 based Sonoff plug](https://www.itead.cc/smart-socket.html) with third party [MQTT firmware](https://github.com/arendst/Sonoff-Tasmota) or [EmonESP](https://github.com/openenergymonitor/emonesp) firmware.

## Interface

For the past few years I have been using OpenHAB as the contol interface. [OpenHAB is pre-loaded onto the emonPi emonSD pre-built image](https://guide.openenergymonitor.org/integrations/openhab). I am yet to upgrade to OpenHAB V2.0, it looks very nice. However, V1.8 has been very reliable and fits my needs. I use the OpenHAB Android app to access the interface quickly from my phone:

![open-hab-home.png]({{site.image_path}}/open-hab-home.png)![open-hab-all.png]({{site.image_path}}/open-hab-all.png)

OpenHAB also [integrates with my Pebble smartwatch](https://apps.getpebble.com/en_US/application/5542604d45bf334314000098?section=watchapps) which makes it super easy to turn on/off the heating while out and about:

![openhab-pebble]({{site.image_path}}/openhab-pebble.jpg)

A while back (early 2016) I dabbled with [HomeAssistant](http://home-assistant.io/), ([see blog post](https://blog.openenergymonitor.org/2016/04/Home-Assistant/)). I was quite impressed, I have been following the project and it looks like it's matured to be an excellent home automation platform. Quit possibly a rival to OpenHAB.

Another option for an interface is [NodeRED Dashboard](https://github.com/node-red/node-red-dashboard) which is now officially part of the NodeRED project.

*The beauty of MQTT is that it's platform agnostic, it's possible to have many different interfaces controlling the same control nodes.*

### Voice interface

I've recently aquired a Google Home voice activated speaker, with a little help from [ha-bridge](https://github.com/bwssytems/ha-bridge) to emulate a Philips Hue bridge it's quite easy to get Google Home to control local devices via MQTT. The same setup will also work with Amazon Echo. See [ha-bridge setup guide for emonPi](https://github.com/openenergymonitor/emonpi-ha-bridge)

See video demo at the top of this post.

Device config using ha-bridge webpage GUI:

![ha-bridge-device-config.png]({{site.image_path}}/ha-bridge-device-config.png)

Google Home app setup:

![google-home-app.png]({{site.image_path}}/google-home-app.png)


## Integration & Automation

I use [NodeRED which is pre-loaded on emonPi / emonSD](https://guide.openenergymonitor.org/integrations/nodered) to integrate with other services such a getting the latest outdoor temperature from [Weather Underground](https://www.wunderground.com/), send push notifications (heating on / off temperature alert) to my phone using [Pushover](https://pushover.net/). Both these services have pre-made nodeRED flows making integration very easy. NodeRED is pre-installed and configured on emonPi / emonSD. The [example flow included on emonPi](https://github.com/openenergymonitor/oem_node-red/blob/master/flows_emonpi.json) demonstrates reading emonTH data from MQTT and external temperature data from Weather Underground.

I also have a nodeRED flow that handles turning off the heating when the temperature in the livingroom (as measured by emonTH) reaches a set point. I could have used the thermostat controller on the WiFi relay to do this, however it would be difficult in my house to run the wired temperature sensor from the Wifi relay to the living room, therefore I use a wireless emonTH temperature instead.

# Security and remote access

Remote control (from outside the local network) can be achieved using a dynamic DNS service such as [DuckDNS](https://www.duckdns.org/) to give access to services from the outside. E.g I open port 8080 to give access to OpenHAB running on my emonPi from the internet. OpenHAB has authentication turned on and HTTPS can be used to create a secure connection. Alternatively, and possibly a better solution could be to use [MyOpenhab.org](http://www.myopenhab.org/) service to allow remote control without having to open up a port externally.
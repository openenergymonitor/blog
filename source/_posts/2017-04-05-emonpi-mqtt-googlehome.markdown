---
published: true
layout: post
title: "Using emonPi as Home Automation Hub"
date: "2017-06-05 00:00"
date_formatted: May 6th 2017
author: Glyn Hudson
comments: true
categories:
  - emonPi
  - MQTT
  - google-home
---

I beleive automation can play an important role in helping to reduce energy consumption. For example being able to control my home heating sstem remotly enables me to turn on the heating only when it's required and not have it runnning on a set schedule when nobody is home.

As [ previously mentioned in a blog post](2016/08/ecohomelab-control/); the emonPi (running [emonSD pre-built SD card](github.com/openenergymonitor/emonpi/wiki/emonSD-pre-built-SD-card-Download-&-Change-Log)) can function as a powerful home automation hub. Using the emonPi as a home automation hub is a good fit for a number of reasons:

- It's alread runing 24/7 for energy monitoring
- It's optimised for robust long term opperation: the root Raspberry Pi file-system is read-only to increase SD card lifespan
- It's already connected to your local network
- It's running Debian Raspbian Jessie thefore installing extra packages is easy
- Raspberry Pi 3 has plenty of space capacity
- Extra radios / accessories can be connected via USB
- It's already running an MQTT server
- emonSD pre-built SD card comes pre loaded with the following [integrations](guide.openenergymonitor.org/integrations) nodeRED, OpenHAB and LightWaveRF

# Video Demo

<div class='videoWrapper'>
<iframe width="280" height="157" src="https://www.youtube.com/embed/r_v4GXVp0OI" frameborder="0" allowfullscreen></iframe>
</div>








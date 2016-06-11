---
layout: post
title: "Home Assistant and emonPi"
date: 2016-04-01 17:00                                          # This is the indexed published time and date
date_formatted: "April  1st 2016"                                # This is the public facing date on the post
author: Glyn Hudson
comments: true
categories:
 - home Assistant
 - integrations
---

[Home Assistant](http://home-assistant.io/) (HA) is a fully [open-source](https://github.com/balloob/home-assistant) home automation platform.

In terms of functionality it's quite similar to [openHAB](http://openenergymonitor.blogspot.co.uk/search/label/openHAB) however it's architecture is very different it runs on Python 3 as opposed to java.

I found home assistant very easy to setup and configure. It's got some nice auto detect features e.g. It auto-detected by Chromecast devices. Home Assistant has got [pre-built component integrations](https://home-assistant.io/components/) with many home automation and monitoring devices and platforms. I was also impressed with the presence detection support, I tested using [nmap](https://home-assistant.io/components/device_tracker.nmap_scanner/) to scan my home router for presence of my phone connected to my home WiFi (indication that I'm home...or I forget my phone!) and [OwnTracks](https://home-assistant.io/components/device_tracker.owntracks/) MQTT based GPS tracking.

<!--more-->

Interfacing with our [emonPi Raspberry Pi energy monitor](http://openenergymonitor.org/emon/modules/emonpi) was easy, using MQTT component to connect to emonPi's MQTT server and subscribe to the power and sensor readings of interest.

As yet I have not experimented with creating automations with HA .e.g turning off lights and heating when we're not home. I think I will still prefer using nodeRED for these types of rule based automations. However what HA does well is present a nice clean, mobile friendly and easy to configure front-end interface:

![home assistant]({{site.image_path}}/ha1.jpg)
My HA Home Setup So Far

![home assistant]({{site.image_path}}/ha2.png)
Home Assistant has some nice mini graphing features to give you a quick overview.

![home assistant]({{site.image_path}}/ha3.png) ![home assistant]({{site.image_path}}/ha4.png)

On a switch node a quite overview will tell you how long the switch has been on or off for. Very useful for checking long long the heating has been on for

![home assistant]({{site.image_path}}/ha5.png)

Generic emonPi Config Example


[I have published setup guide to setting up Home Assistant on an emonPi with example config](https://github.com/openenergymonitor/oem_home-assistant).
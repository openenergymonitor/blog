---
published: true
layout: post
title: "emonPi Network Setup Wizard"
date: "2017-06-21 00:00"
date_formatted: Junt 21st 2017
author: Glyn Hudson
comments: true
categories:
  - raspberry Pi
  - emonpi
---

Ever since we launched the emonPi we have always wanted to make the first time setup process as easy as possible for new users.

![emonpi wifi]({{site.image_path}}/emonpi_wifi.png)

We have just made significant progress in streamlining the setup process by enabling the emonPi / emonBase to broadcast a WiFi access-point (AP) on first boot then scan for local WiFi networks and allow the user to connect. The emonPi will then turn off it's AP and connect to the local network. There is also an option to connect via Ethernet or stand-alone WiFi AP mode when no local network is available.

![emonpi-network-wizard1]({{site.image_path}}/emonpi-network-wizard1.png)

This has now been made possible using the Raspberry Pi 3 which supports WiFi access-point AP mode, [some bash scrips](https://github.com/openenergymonitor/emonpi/tree/master/wifiAP) and a new [emoncms-setup module](https://github.com/openenergymonitor/emonpi/tree/master/emoncms-setup).


*The new Network Setup Wizard will be included on all new purchased in July 2017 onwards. Existing emonPi's with a Raspberry Pi 3 can be updated by running Admin > emonPi update in Emoncms. The emonPi will only broadcast a WiFi AP if Ethernet is not connected and no WiFi setup is currently present.*

Trystan is also working on making the input-processing setup for new devices easier by adding device template support to the Emoncms Device module. More on this the come...[see development forum thread](https://community.openenergymonitor.org/t/development-devices-inputs-and-feeds-in-emoncms/4281).

Read on more screenshots of the emonPi network setup wizard....

<!--more-->

![emonpi-network-wizard2]({{site.image_path}}/emonpi-network-wizard2.png)

![emonpi-network-wizard3]({{site.image_path}}/emonpi-network-wizard3.png)

![emonpi-network-wizard4]({{site.image_path}}/emonpi-network-wizard4.png)

The [emonPi Setup Guide](https://guide.openenergymonitor.org/setup/connect/#1a-connect-to-wifi) has been updated for use with the new Netork Setup Wizard.

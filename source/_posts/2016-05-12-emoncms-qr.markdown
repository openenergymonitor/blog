---
layout: post
title: "Emoncms Android App QR Code Scanner Setup"
date: "2016-05-11 15:00"
date_formatted: May 12th 2016
author: Glyn Hudson
comments: true
categories:
  - android
  - mobile app
  - emoncms
---
  
I would like to highlight a nice improvement to Emoncms and the Emoncms Android app that has been contributed by community memebers [@jumpmaster](https://community.openenergymonitor.org/users/jumpmaster/activity) and [@andy_taylor](https://community.openenergymonitor.org/users/andy_taylor/activity). See [development forum thread](https://community.openenergymonitor.org/t/mobile-app-qr-code/149) on our [shiny new forums](/2016/05/website-changes/).

Emoncms MyAccount page now displays a QR code and a couple of handy 'Copy to Clipboard' buttons for the API keys:

![Emoncms QR code generator](/images/emoncms-qr.png)

<!--more-->

*This updated has been merged into the stable Emoncms branch V9.6. If your running an emonPi/emonBase jsut hit update to pull in the changes. The update will appear on Emoncms.org in the next few days.*

This QR code contains the Emoncms URL and read-API key to automate setting up the [Emoncms Android app](https://play.google.com/store/apps/details?id=org.emoncms.myapps&hl=en_GB). The update for the app to support the QR code scanner has been pushed to Googe Play. After the update just can the QR code to setup the app.

{% img /images/android-qr.png 300 %}

If your feeds are named **use** and **use_kwh** the app will automatically select use these feeds as the Power and kWh feeds.

Any issues, please post on the [development forum thread](https://community.openenergymonitor.org/t/mobile-app-qr-code/149).

Thanks again to everyone involved in the development and testing. It's been great working with an enthusiastic development community over on the new forums. Onwards and upwards :-)
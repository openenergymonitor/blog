---
published: true
layout: post
title: "CydYnni – Energy Local, community hydro smart grid"
date: "2017-08-07 00:00"
date_formatted: Aug 7nd 2017
author: Trystan Lea
comments: true
categories:

---

Over the last year we have been involved in a project in our local area (Snowdonia, North Wales) called CydYnni – EnergyLocal. The project is at the forefront of making it possible for households to source their electricity directly from local, community-owned renewable sources.

**The Bethesda pilot project, How it works**

The first part of the CydYnni project started with about 80 households (with 20 more joining soon) and a single 100 kW hydro generator. Using smart meters suitable for half hourly billing in participating households and at the hydro generator, the amount of hydro power used by the community is calculated for every half hour. The hydro tariff is 7p / kWh for the power used each half hour by the community providing a significant saving for households. Any additional power required is bought from the supplier Co-operative Energy on a time-of-use tariff.

The project provides cost savings to participating households, increased income for local renewable energy schemes and a more direct sense of having electricity provided from - in the case of the pilot project a hydro turbine just down the road!

There is a nice video here on the project which gives a good overview:

<iframe width="560" height="315" src="https://www.youtube.com/embed/3z8GrTBLw8M" frameborder="0" allowfullscreen></iframe>

[https://www.youtube.com/watch?v=3z8GrTBLw8M](https://www.youtube.com/watch?v=3z8GrTBLw8M)

There are a number of organisations working on the project of which we are one small part:

- EnergyLocal: The organisation founded by Mary Gillie with the initial idea and in depth understanding of the energy market behind the project.
- CydYnni: A local consortium of community energy projects and organisations including Ynni Ogwen and Partneriaeth Ogwen, Ynni Padarn Peris, Moelyci, Coetir Mynydd, Antur Waunfawr, Ynni Anafon and the National Trust.
- Co-operative Energy: The Energy Supplier through which households participate in the project.
- Epower also known as NFPAS: The non fossil fuel purchasing agency – handling aggregation, power sharing and the nuts and bolts of billing.
- 1010: Graphic design
- OpenEnergyMonitor: web app development in part 1 and home hub (base-station) development in part 2. 

It’s been great being involved in such a pioneering project run in the local community in which we live (the OpenEnergyMonitor office is about 5 miles from Bethesda).

Our role so far has been to develop a web app / energy dashboard so that participants can see when the local hydro generator is running and how likely they are to be on the cheaper hydro tariff. Participants can see their own consumption as well as the aggregated consumption of all participants.

The main energy dashboard app designed by 1010 and implemented by ourselves can be viewed online here:

[https://cydynni.org.uk](https://cydynni.org.uk)

![cydynni-app.png]({{site.image_path}}/cydynni-app.png)

The source code for the app is open source and available on github here: 

[http://github.com/trystanlea/cydynni](http://github.com/trystanlea/cydynni)

We have also developed a dashboard that is more focused on exploring the full data history of the hydro generation and community consumption, this dashboard can be viewed online here:

[https://dev.cydynni.org.uk](https://dev.cydynni.org.uk)

![cydynni-history.png]({{site.image_path}}/cydynni-history.png)

From the start of January the hydro supplied 57% of the electricity consumption of the participating households. You can really see how the available hydro generation decays usually over about a week after a significant rain event and the extent of the oversupply when it is raining. 

It would be interesting to model the addition of solar to see how periods of lower rainfall might be supplanted by solar generation and explore other options for supplying the unmatched demand - e.g. anaerobic digestion.

**Part 1: Energy Dashboard / Web App development**

This first stage of the project relies on the app or looking at how rainy it is to signal to the households when it’s a good time to use energy. Any demand shifting is done manually by the householder. The data update rate from the smart meters is also relatively slow, with 48 half hourly readings updated daily but usually available in the app with a lag time of anywhere from 15 hours up to 63 hours over the weekend.

**Part 2: Hub**

The next stage of the project for us is to improve on this with an in home hub (based currently on the OpenEnergyMonitor emonbase), which will interface with a WIFI/radio meter gateway developed by Energy Assets, providing much faster 5-10s meter readings as well as enabling control of smart appliances, plugs and EV charging.

This development has driven some of our most recent improvements to the EmonPi/EmonBase, such as the recently launched WIFI Hotspot setup and ongoing development on the emoncms device module, which alongside auto-configuration of inputs and feeds provides the option to define control devices starting with the Sonoff S20 WIFI Socket, Martin’s WIFI Relay unit and the OpenEVSE charging station.

Over the coming months I will try to blog more on development progress and the technical implementation of the system in addition to insights into the data coming from the project demonstrating local community energy.

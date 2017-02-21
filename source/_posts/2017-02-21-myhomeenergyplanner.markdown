---
published: true
layout: post
title: "MyHomeEnergyPlanner - open source home energy assessment"
date: "2017-02-21 13:43"
date_formatted: Feb 21st 2017
author: Trystan Lea
comments: true
categories:
---

![MyHomeEnergyPlanner]({{site.image_path}}/myhomeenergyplanner2.png)

I would like to highlight a piece of work by [Carlos Alonso Gabizón](https://community.openenergymonitor.org/users/cagabi) which I think is an important piece of the home energy monitoring and assessment toolkit and a really useful tool, which we would be keen to see more people use.

Carlos has been working for [CarbonCoop](http://carbon.coop/) over the last year and a half on [MyHomeEnergyPlanner]((http://myhome.emoncms.org)) – an open source household energy assessment tool based on SAP 2012 – a monthly domestic energy model.

MyHomeEnergyPlanner started as a collaboration between OpenEnergyMonitor and CarbonCoop but this latest version and active work on it over the last year and a half is all down to Carlos and CarbonCoop.

MyHomeEnergyPlanner can be used to calculate the space and water heating requirements for a home from a detailed breakdown of the building fabric: floor, walls, roof, windows etc. It uses U-values and areas to calculate building fabric heat loss rates, combined with calculated heat loss from infiltration and ventilation and heat gains from solar radiation, lighting, household appliances, cooking and occupants.

It can be used to model a building in its current form and then create scenarios to explore the effect of undertaking measures such as adding insulation, improving air-tightness and changing heating systems.

MyHomeEnergyPlanner is free to use and open source and is now installed on emoncms.org (Login with your [Emoncms.org](https://emoncms.org) account)

**[http://myhome.emoncms.org](http://myhome.emoncms.org)**

<!--more-->


I have written an [initial getting started guide](https://learn.openenergymonitor.org/sustainable-energy/building-energy-model/MyHomeEnergyPlanner) here that goes over the main parts of creating an initial household assessment:


When I was last working on building energy modelling I also wrote a [brief guide on how a simple household energy model](https://learn.openenergymonitor.org/sustainable-energy/building-energy-model/readme) works which can also be found here:


### MyHomeEnergyPlanner Github

**[http://github.com/emoncms/MyHomeEnergyPlanner](http://github.com/emoncms/MyHomeEnergyPlanner)**

---

For further context: MyHomeEnergyPlanner is used by CarbonCoop as part of their work on household retrofit, improving insulation and air-tightness of existing households in Manchester to achieve carbon emission reductions of 80% compared to the 1990 baseline. More information can be found about their work here:

- [Whole House Retrofit - A Community Green Deal](http://carbon.coop/content/whole-house-retrofit-community-green-deal)
- [Whole House Retrofit Assessment Method](http://carbon.coop/assessments/URBED_ASSESSMENT_REPORT.pdf)
- [Recent post-retrofit monitored results for Carbon Coop’s recent retrofit project (twitter)](https://twitter.com/CarbonCoop/status/802176377785028608/photo/1)

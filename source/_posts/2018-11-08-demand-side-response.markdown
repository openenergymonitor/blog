---
published: true
layout: post
title: "Demand Side Response Development"
date: "2018-11-08 18:48"
date_formatted: Nov 11th 2018
author: Trystan Lea
comments: true
categories: emoncms
---

![openevse leaf]({{site.image_path}}/leaf-openevse.jpg)

Demand side response (DSR) has been a OpenEnergyMonitor project interest for some time (e.g PV diversion) but has only made its way into a product more recently with our work on the [OpenEVSE charging station](https://guide.openenergymonitor.org/applications/ev-charging/). The OpenEVSE already implements real-time DSR, this post outlines how we are working on improving on this by integrating the forecasting and scheduling approaches being developed as part of our involvement in the [EnergyLocal project](https://community.openenergymonitor.org/t/cydynni-energylocal-community-hydro-smart-grid-blog-post/4762).

<!--more-->

---

DSR: Demand Side Response is the idea of moving demand to

* Better match supply, something that becomes more important as we supply more of our electricity from renewable energy.
* Reduce electricity system cost by reducing the maximum dispatchable generation, distribution and transmission grid capacity needed.

Household electricity demand such as lighting, computing, TV, cooking, fridge/freezer, washing have relatively low DSR potential, either due to the need for these demands to happen during times of occupancy (peak demand) or because these demands are relatively small.

However as we move towards a zero carbon future, most scenarios suggest that large scale electrification of transport and heat is needed, alongside powering up of renewable energy. Both electric vehicles and electric heating e.g heatpumps & hot water storage have significant DSR potential.

<table><tr><td style="width:35%">

<img src="https://blog.openenergymonitor.org/images/energymodel.png" style="width:276px" />

</td><td>

This screenshot from our work on modelling zero carbon energy systems based on The Centre for Alternative Technologies ZeroCarbonBritain model <a href="https://learn.openenergymonitor.org/sustainable-energy/zcem/integrated.html#fullhousehold">https://learn.openenergymonitor.org/sustainable-energy/zcem/integrated.html#fullhousehold</a> shows an example of the extent to which renewable energy supply could vary in the future and so the potential for DSR to move demand to better match supply.
<br><br>
<i>Dark blue: traditional household electricity demand (minus any heating), Red: heatpump demand with DSR, Green: EV demand with DSR, Blue: Electrolysis demand for synthetic fuels soaking up large excess capacity, Total: Wind and solar output.</i>

</td></tr><tr><td>

<img src="https://blog.openenergymonitor.org/images/cydynni.png" style="width:276px" />
</td><td>

Energy local are pioneering community energy aggregation tariffs with both time of use pricing and pricing based on availability of a local renewable energy generator. A household with loads suitable for DSR can lower their electricity cost and use a greater amount of local power by shifting their demand to better times.
<br><br>
EnergyLocal provide a day ahead forecast that can be used to schedule appliances, EV’s, hot water storage etc.

</td></tr><tr><td>

<img src="https://blog.openenergymonitor.org/images/octopus.png" style="width:276px" />

</td><td>

For households not able to take part in community energy aggregation tariffs such as EnergyLocal, Octopus Energy have recently introduced a time of use tariff, that reflects wholesale electricity prices. <a href="https://octopus.energy/agile">https://octopus.energy/agile</a>
<br><br>
Agile also provide a day ahead price profile that can be used for scheduling.
<br><br>
Savings made by using these tariffs can help payback expenditure on smart energy technologies. Especially where battery or heat storage is considered during the build or retrofit stage. E.g using thermal mass to store heat from heatpumps during times of excess supply.

</td></tr><tr><td>

<img src="https://blog.openenergymonitor.org/images/gridcarbon.png" style="width:276px" />

</td><td>

Another approach to forecasting could be to use [grid carbon intensity](http://carbonintensity.org.uk/), weather forecasts e.g darksky API and grid demand forecasts (to avoid peak times).
<br><br>
Users keen to stay with their existing electricity suppliers e.g Ecotricity for Electric Highway EV charging benefits could still make use of scheduling to ensure demand happens at the best time from a carbon and limiting grid strain perspective.

</td></tr></table>

### Control approach

<table><tr><td>

<p>1. <b>Realtime</b><br>
The emonEVSE is our first product that implements automated DSR, designed to charge a connected electric vehicle according to the available output from a solar PV array, it is an example of automated real-time DSR. A similar application and control strategy is PV diversion to hot water.</p>

<p>2. <b>Combined real-time & later scheduled period</b><br>
A real-time only control strategy is limited in the case that solar output in a given day does not charge the car up sufficiently for use later in the afternoon/evening or next day, or the hot water tank is not heated sufficiently for an evening/morning shower. In both cases a further period of charging will be needed. This could be achieved with a basic second charging period e.g boost charge before use or an overnight charge.</p>

<p>To make both of these applications work well the control system needs to know when the user wishes to use the car or hot water and the state of charge or temperature target that needs to be reached.</p>

<p>3. <b>Forecast based scheduling</b><br>
A limitation with the last approach where solar was not enough to complete the charge or heat the tank directly is that the boost charge may happen at a time that is more expensive, or higher carbon. It may be better to charge at a higher rate through the middle of the day, importing power from the grid at that time, than importing during the evening peak. Integrating a solar forecast for the day ahead could predict if the charge will complete directly from the solar and if not proportionally increase the charge rate for the day.</p>
  
<p>Another limitation of real-time DSR for hot water heating is that on a sunny day, the cylinder can heat up too quickly and so will then sit at a high temperature loosing heat for longer than it needs too. It may also result in larger ramp effects and strain on the grid if storage is filled during the morning leaving everyone’s solar systems to export through the afternoon.</p>
<p>Leaving an EV at a high state of charge for a long time is also meant to cause a higher rate of battery degradation and so control strategies that bring the charging period as close to the time of use as possible may be particularly important.</p>
<p>Using a forecast and information on charge required could allow the control system to absorb power throughout the period of excess supply to better follow the supply curve, reducing ramp strain on the grid and reducing heat store loss and battery degradation.</p>

</td><td style="width:35%">

<img src="https://blog.openenergymonitor.org/images/solardivert.png" style="width:276px" />

<br><br><br><br><br><br><br><br><br><br>

<img src="https://blog.openenergymonitor.org/images/scheduler.png" style="width:276px" />

</td></tr></table>

<p>Follow the development of this project and learn about our next steps on the forums.</p>

<ul>
  <li><a href="https://blog.openenergymonitor.org/2018/11/demand-side-response/">Forum post: CydYnni, EnergyLocal Community hydro smart grid</li>
  <li><a href="https://github.com/emoncms/demandshaper">Github: Emoncms demand shaper module</li>
</ul>

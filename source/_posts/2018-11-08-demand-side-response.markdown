---
published: false
layout: post
title: "OpenEnergyMonitor DSR Development"
date: "2018-11-08 18:48"
date_formatted: Nov 11th 2018
author: Trystan Lea
comments: true
categories: emoncms
---

Demand side response (DSR) has been a OpenEnergyMonitor project interest for some time (e.g PV diversion) but has only made its way into a product more recently with our work on the [OpenEVSE charging station](https://guide.openenergymonitor.org/applications/ev-charging/). The OpenEVSE implements real-time DSR but would benefit from integration with the forecasting and scheduling approaches being developed as part of the EnergyLocal project.

---

DSR: Demand Side Response is the idea of moving demand to
- Better match supply, something that becomes more important as we supply more of our electricity from renewable energy.
- Reduce electricity system cost by reducing the maximum dispatchable generation, distribution and transmission grid capacity needed.

Household electricity demand such as lighting, computing, TV, cooking, fridge/freezer, washing have relatively low DSR potential, either due to the need for these demands to happen during times of occupancy (peak demand) or because these demands are relatively small.

However as we move towards a zero carbon future, most scenarios suggest large scale electrification of transport and heat is needed alongside powering up of renewable energy. Both electric vehicles and electric heating e.g heatpumps & hot water storage have significant DSR potential.

<table><tr><td>

![1|690x430,40%]({{site.image_path}}/energymodel.png) 

</td><td>

This screenshot from our work on modelling zero carbon energy systems https://learn.openenergymonitor.org/sustainable-energy/zcem/integrated.html#fullhousehold shows an example of the extent to which renewable energy supply could vary in the future and so the potential for DSR to move demand to better match supply.

*Dark blue: traditional household electricity demand (minus any heating), Red: heatpump demand with DSR, Green: EV demand with DSR, Blue: Electrolysis demand for synthetic fuels soaking up large excess capacity, Total: Wind and solar output.*

</td></tr><tr><td>

![cydynni-history|519x499,53%]({{site.image_path}}/cydynni.png) 

</td><td>

Energy local are pioneering community energy aggregation tariffs with both time of use pricing and pricing based on availability of a local renewable energy generator. A household with loads suitable for DSR can lower their electricity cost and use a greater amount of local power by shifting their demand to better times.

EnergyLocal provide a day ahead forecast that can be used to schedule appliances, EV’s, hot water storage etc.

</td></tr><tr><td>

![3|690x444,41%]({{site.image_path}}/octopus.png) 

</td><td>

For households not able to take part in community energy aggregation tariffs such as EnergyLocal, Octopus Energy have recently introduced a time of use tariff, that reflects wholesale electricity prices. https://octopus.energy/agile/

Agile also provide a day ahead price profile that can be used for scheduling.

Savings made by using these tariffs can help payback expenditure on smart energy technologies. Especially where battery or heat storage is considered during the build or retrofit stage. E.g using thermal mass to store heat from heatpumps during times of excess supply.

</td></tr><tr><td>

![4|690x415,42%]({{site.image_path}}/gridcarbon.png) 

</td><td>

Another approach to forecasting could be to use grid carbon intensity, weather forecasts e.g darksky API and grid demand forecasts (to avoid peak times).

Users keen to stay with their existing electricity suppliers e.g Ecotricity for Electric Highway EV charging benefits could still make use of scheduling to ensure demand happens at the best time from a carbon and limiting grid strain perspective.

</td></tr></table>

### Control approach

<table><tr><td>

1. **Realtime**
The emonEVSE is our first product that implements automated DSR, designed to charge a connected electric vehicle acording to the available output from a solar PV array, it is an example of automated real-time DSR. A similar application and control strategy is PV diversion to hot water.

2. **Combined real-time & later scheduled period**
A real-time only control strategy is limited in the case that solar output in a given day does not charge the car up sufficiently for use later in the afternoon/evening or next day, or the hot water tank is not heated sufficiently for an evening/morning shower. In both of these cases a further period of charging will be needed. This could be achieved with a basic second charging period e.g overnight.

To make both of these applications work well the control system needs to know when the user wishes to use the car or hot water and the state of charge or temperature target that needs to be reached.

3. **Forecast based scheduling**
A limitation of real-time DSR for hot water heating is that on a sunny day, the cylinder can heat up too quickly and so will then sit at a high temperature loosing heat for longer than it needs too. It may also result in larger ramp effects and strain on the grid if storage is filled during the morning leaving everyone’s solar systems to export through the afternoon. Leaving an EV at a high stage of charge for a long time is also meant to cause a higher rate of battery degredation and so control strategies that bring the charging period as close to the time of use as possible may be particularly important.

Using a forecast and information on charge required could allow the control system to absorb power throughout the period of excess supply to better follow the supply curve reducing ramp strain on the grid and reducing heat store loss and battery degradation.

</td><td>

![divert|500x399,50%]({{site.image_path}}/solardivert.png) 
<br><br><br><br><br><br><br><br><br><br>
![6|345x500,70%]({{site.image_path}}/scheduler.png)  

</td></tr></table>

---
layout: post
title: "Part 1: Attempting to measure and understand the CO2 intensity of grid electricity"
date: 2016-04-18 15:00                                          # This is the indexed published time and date
date_formatted: "April  27th 2016"                                # This is the public facing date on the post
author: Trystan Lea
comments: true
categories:
 - sustainability                                      # Lower case
 - community smart grid                                 # Lower case
---

Zero carbon energy scenarios such as [ZeroCarbonBritain](http://zerocarbonbritain.org/) feature significant electrification of energy demands previously provided by fossil fuels such as heating and transport. With electrification it becomes possible to supply these energy demands with renewably generated electricity from primarily wind, solar and backed up by storage technologies from short term stores such as batteries to long term stores such as power to gas.

We do not of course yet have a zero carbon grid. However there has been significant growth of renewable energy and a decline in coal generation in recent years.

The CO2 emissions of demand side solutions such as heat pumps and electric vehicles are significantly affected by the co2 intensity of the supply but in many cases installing and using these technologies make sense at the UK's present supply mix and can make more or less sense depending on how you calculate co2 intensity and where you assume the additional electricity required comes from.

<!--more-->

```
As an example the CO2 intensity of combined cycle gas turbines (CCGT) which provide the majority of electricity generated from gas in the UK have a co2 intensity of 360gCO2/kWh.

At this intensity a well installed heat pump that achieves an average COP of 3.0 delivers heat at a CO2 intensity of 129gCO2/kWh heat including 7% grid losses. This provides a significant 44% co2 emissions reduction compared to having an efficient gas boiler which delivers heat at a CO2 intensity of 230gCO2/kWh.

An electric car achieving a real world mountainous north Wales terrain driving efficiency of 3.7 miles per kWh (5.9km/kWh) including charging losses powered by gas electricity has a co2 intensity of 61gCO2/kWh which again provides a significant 44% co2 emissions reduction compared to real world efficient small petrol car co2 emissions of110 gCO2/km based on: 10.6 kgCO2 per gallon [1] and 60mpg (typical of the most efficient small car real world mpg [2].
```
[[1]](http://www.carbonindependent.org/sources_car.html)
[[2]](http://www.whatcar.com/car-news/real-world-mpg-efficient-small-cars/1214063)

The average CO2 intensity for the UK grid as a whole in 2015 was [367gCO2/kWh](http://www.earth.org.uk/note-on-UK-grid-CO2-intensity-variations.html) http://www.earth.org.uk/note-on-UK-grid-CO2-intensity-variations.html#fullyear2015 - providing similar CO2 emission reduction potential to the gas only calculations above.

It is interesting to note that this average, results from coal generation with a CO2 intensity of 910gCO2/kWh being offset somewhat by generation from renewable energy and nuclear at 0gCO2/kWh resulting in a CO2 intensity that is close to what it would be if gas CCGT was our only supply source – which really highlights how carbon intensive coal is.

When we move energy demands from one form to another such as replacing a gas boiler with a heat pump the carbon reduction benefits depend heavily on what kind of generation provides for that additional demand. If the additional demand is provided for by CCGT gas turbines the switch makes sense, if it is provided by coal generation at 910gCO2/kWh it does not make so much sense. If it is provided by mix of renewable energy and CCGT is will make even more sense.

There are several different approaches to calculating the co2 intensity of delivered electricity each with their benefits and drawbacks which I will try and explore below and in further posts.

Whole grid averageHere we consider the grid as one big system with the CO2 intensity calculated as the total CO2 emitted by all forms of generation divided by the total demand over an extended period of time – one or more years. The co2 intensity of the UK electricity grid for 2015 was 367gCO2/kWh.

Near real-time co2 intensity using grid wide data

Here the CO2 intensity is calculated by the total CO2 emitted divided by total demand on typically a 10 minute basis. The CO2 intensity calculated this way will often show higher CO2 intensity in the day where gas and coal are a larger percentage of overall supply than at night time. CO2 intensity is also higher when its colder where demand is pushed up by higher heating requirements.


![UK Grid Carbon](/images/ukgrid.png)

[OpenEnergyMonitor UK Grid page](https://openenergymonitor.org/ukgrid) showing real-time CO2 Intensity.


If we use this real-time CO2 intensity in order to choose when to use electricity it gets more complicated, we may decide to shift electric vehicle charging or heat pump hot water heating to the night time in order to make use of grid carbon intensities that can often be 50-100gCO2/kWh less than day-time rates, but is this really a valid approach? The lower CO2 intensities at night are as a result of demand being lower and nuclear + renewables making up a larger share of generation, if night time demand is increased through demand shifting, turning on more gas and coal power plants, the carbon intensity would increase as well.

Given that most of the dis-patchable generation is gas and coal and assuming low levels of wind curtailment at night then it could be argued that the effective carbon intensity of moving demand to the night time should be calculated at the carbon intensity of this dis-patchable generation which depends on the proportion of gas to coal, a more in depth understanding as to how the proportion of gas and coal generation is decided would be needed to assess the carbon value of demand shifting. If the proportions are constant, shifting would make no difference, if gas is ramped up to meet the additional demand there may well be a benefit to shifting on the other hand if the difference is made up with more coal generation there would not be. There's a bit more on this here using 2011 data from [Sam Cooper of Bath University](http://people.bath.ac.uk/en8sc/GridCarbonIntensity.pdf) [linked from earth notes here](http://www.earth.org.uk/note-on-UK-grid-CO2-intensity-variations.html).


Shifting demand away from peak times may well make sense from a transmission and distribution grid capacity perspective but this is largely a different argument and would require a different calculation to assess. It may also be the case that some wind curtailment does take place although the precise extent of this and where on the grid using more will reduce curtailment is difficult to quantify.

In the next blog I will discuss the work I've been doing with Dominic McCann from the Carbon Coop on estimating CO2 intensity with onsite and green tariff renewable energy considered.

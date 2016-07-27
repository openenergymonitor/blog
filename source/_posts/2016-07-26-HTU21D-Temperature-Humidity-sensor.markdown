---
published: true
layout: post
title: "HTU21D / Si72021 Temperature and Humidity Sensor"
date: "2016-07-26 10:00"
date_formatted: June 26th 2016
author: Glyn Hudson
comments: true
categories:
  - HTU21D
  - emonTH
---


I have been been evaluating the [HTU21D](https://octopart.com/htu21d-measurement+specialties-30374934) temperature and humidity sensor made by Measurement Specialties as a possible DHT22 replacement for the emonTH. This is quite a new sensor, released in 2013. The [Si72021](https://octopart.com/si7021-a10-gm-silicon+labs-31448011) is also a posiblity with an identical pin-out and specs.


![image]({{site.image_path}}/htu21d_1.png)

- [OctoPart list](https://octopart.com/htu21d-measurement+specialties-30374934)
- [Datasheet](http://datasheet.octopart.com/HTU21D-Measurement-Specialites-datasheet-22149496.pdf)
- [Farnell item](http://uk.farnell.com/measurement-specialties/htu21d/humidity-digital-3-rh-dfn-6/dp/2393536?CMP=GRHB-OCTOPART)
- DFM footprint
- Digital, pre-clibrated
- I2C


The metrics speak for themselves:



| Metric              | HTU21D             |Si72021| DHT22          | DHT22 vs HTU21D Difference|
| ------------- | -------------            |------------- | ------------- | ------------- |
| Cost in 1k off      | £1.42 (July16)     |£2.15|  £4.57 (July16)    | 3.2 times cheaper (£3.15 less!) |
| Vcc                 | 2.1v - 3.6V        | 1.9V - 3.6V | 3.3-6V | |
| Humidity accuracy   | ±2% RH             | ±2% RH |  ±2%RH         | n/a |
| Humidity Range      | 0-100% RH          | 0-100% RH |  0-100% RH     | n/a|
| Temperature accuracy | ±0.3°C            | ±0.4°C|  ±0.5°C        | 40% more accurate |
| Temperature Range   | -40°C +125°C       |  -40°C +125°C  |  -40°C +80°C   | 56% more accurate |
| Sleep Current       | 0.02uA             | 0.06uA |  15uA          | 750 times less power |
| Measurement Current | 0.045mA            | 0.09 mA |  0.5mA         | 11 times less power |
| Measurement time    | 0.01s - 0.0026s    | 0.01s - 0.0026s |  2s            | 200 times faster |
| Energy consumed per sample | 0.00045mW   ||  1mW           | 2222 times less power |
| Time sampling per day* |  14.4s          ||  2800s         | |
| Time sleeping per day* | 86386s          ||  83600s        | |
| Energy consumed per day* | 2.36mW [1]    ||  2836mW [2]    | 1201 times less energy per day!  |



<!--more-->

*Assuming 1 sample per min and sleeping in between samples, 1440 min per day = 86400s per day. See HTU21D testing repo a [sub-repository of the emonTH](https://github.com/openenergymonitor/emonTH/blob/master/sensor_test/htu21d) for full calculations.

**An upgraded emonTH with a HTU21D sensor instead of DHT22 should benefit from substantially increased battery life, increased accuracy and lower cost.**

I've obtained [HTU21D Sparkfun breakout to test](https://www.sparkfun.com/products/retired/12064) and easily got it working with an Arduino using the [Adafruit library](https://github.com/adafruit/Adafruit_HTU21DF_Library).


![image]({{site.image_path}}/htu21d_2.jpg)


***

There is some confusion with regard to the variants of this sensor *I believe* from my research that the HTU21D **replaces** the [SHT21](https://octopart.com/sht21-sensirion-19013846) made by Sensirion. Both sensors have identical pin-outs.


***

I hope to get a prototype emonTH with HTU21D up and running soon. I would be interested to hear if anyone has experience working with this sensor.



For disucssion see [HTU21D forum thread.](https://community.openenergymonitor.org/t/htu21d-temperature-and-humidity-sensor-possible-dht22-replacement/1106)

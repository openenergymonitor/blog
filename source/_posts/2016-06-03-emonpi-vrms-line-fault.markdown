---
published: true
layout: post
title: "Electrical Supply Line Fault"
date: "2016-06-03 10:00"
date_formatted: June 3rd 2016
author: Glyn Hudson
comments: true
categories:
  - vrms
  - application
---

Last week my home emonPi energy monitor came in handy to help diagnose an electrical supply fault.

A neighbour alerted me that her lights were flickering and internet router was dropping offline. At the time I was doing some DIY and had noticed the power drill I was using change speed erratically. I had presumed it was my drill about the give up the ghost.

I checked the Emoncms graph on my emonPi energy monitor and noticed that VRMS was well out of spec at about 150V (we usually get 230V*) and occasionally jumping up to almost 300V! The electrical company was alerted and the fault was traced back to a frayed conductor on our street. I helped the electrical contractors view the real-time VRMS value to confirm the fault was fixed.


![VRMS Fault]({{site.image_path}}/vrms.png)


<!--more-->

## * Notes on Mains Voltage Limits
 
The standard domestic mains supply for Europe is 230 V ± 10%, giving a lower limit of 207 V and an upper limit of 253 V. It is permissible under BS 7671 to have a voltage drop within the installation of 5%, which would give a lower limit of 195.5 V.
The UK standard prior to harmonization was 240 V ± 6%, giving an upper limit of 254.4 V.

Although the UK nominal standard is now 230 V, the supply system has not generally been adjusted, and the voltage centers around 240 V.

Thanks to Robert Wall for summarizing the rather convoluted standards surrounding UK grid voltages.

All of Europe, Africa, Asia, Australia, New Zealand and most of South America, use a supply that is within 6% of 230 V

[Mains Electricity by Country (Wikipedia)](https://en.wikipedia.org/wiki/Mains_electricity_by_country)







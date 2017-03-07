---
layout: post
title: "AA Battery Considerations"
date: "2013-10-18 07:00"
date_formatted: Oct 18th 2013"
author: Glyn Hudson
comments: true
categories:
- batteries
- emonTH
blogger_orig_url: http://openenergymonitor.blogspot.com/2013/10/aa-battery-considerations.html
---

The manufacture of batteries is a very energy intensive process often using many types of heavy metals, it makes total sense to use rechargeable batteries where possible and always recycle old batteries. When it comes to low power sensing nodes I'm as guilty as anyone else when it comes to just sticking in some cheap alkaline batteries, always believing that the performance of rechargeable batteries was much lower. This is not the case anymore.

If rechargeable batteries are used (which they should be) the self-discharge rate can be significant. The self-discharge rate of NiMH batteries is high: around 30% per month at room temperature. This problem can be almost eliminated by using low-self discharge NiMH cells such as Eneloop, they have a discharge rate of about 5% per year. If non-rechargeable alkaline batteries are used they have a self-discharge rate of less than 2% per year.

![](http://1.bp.blogspot.com/-xQFMH8ye2Sg/UmEWYHb3rmI/AAAAAAAAmRo/JVNwB4P1FwY/s640/sd.gif)](http://1.bp.blogspot.com/-xQFMH8ye2Sg/UmEWYHb3rmI/AAAAAAAAmRo/JVNwB4P1FwY/s1600/sd.gif)

Rechargable batteries self-discharge graph from batterydata.com

If you care about the environment (which we all should do) we highly recommend the use of Sanyo Eneloop rechargeable AA's in the emonTH and emonTx. They are a bit more expensive (about £2 each) but over their lifetime (they can be recharged 2100 times!) they will work out cheaper. The Eneloop cells are cadmium free and arrive fully charged and ready to use. Sanyo states that this charge is supplied by their solar PV system in Japan!

![](http://3.bp.blogspot.com/-Ab76FVPyOF4/UmEbIOMDxDI/AAAAAAAAmR0/0dOljN0n3GQ/s200/eneloop.jpg)](http://3.bp.blogspot.com/-Ab76FVPyOF4/UmEbIOMDxDI/AAAAAAAAmR0/0dOljN0n3GQ/s1600/eneloop.jpg)

An excellent setup (as recommended by JCW of JeeLabs.org) is a spare set of Eneloop AA's (Apple AA's are rebranded Eneloops) permanently plugged in an Apple AA charger which he measured using 0W when the batteries are fully charged! This way you always have a set ready to go: [http://jeelabs.org/2010/08/19/new-aa-battery-option/](http://jeelabs.org/2010/08/19/new-aa-battery-option/)

**Update:** I've just discovered iGogreen's Alkaline Rechargeable batteries which claim to hold their charge for 7 years and contain no heavy metals : Mercury, Cadmium, Lead or Nickel. They do fall down for high power draw applications but this is not an issue here, maybe a perfect match for long term low power nodes? They are also cheaper than Eneloops. The only draw back is they they need a special charger, iGo do a reasonably priced nice looking USB charger which will also charge standard NiMH

**Update #2:** The iGoGreen rechargable alkaline AA's tended to leak acid after a couple of years. I would not recomend. They [seem to have now been discontinued](http://uk.rs-online.com/web/p/aa-rechargeable-batteries/7595533/)
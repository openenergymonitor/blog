---
published: false
layout: post
title: "Part 2: Exploring carbon intensity and renewable energy matching: real-time grid CO2 intensity + on-site and grid renewable energy"
date: 2016-04-18 15:00                                          # This is the indexed published time and date
date_formatted: "April  27th 2016"                                # This is the public facing date on the post
author: Trystan Lea
comments: true
categories: sustainability                                      # Lower case
---




![image]({{site.image_path}}/winderful.png)

This post describes an approach we have been exploring that uses the MyEnergy emoncms app and work on virtual smart grids with Dominic McCann from Carbon Coop. There's a good blog and video on what we've been working on over on the Carbon Coop blog here: http://carbon.coop/blog/jonathan/smart-grid-aggregation-dashboard-prototype

The last post described two approaches to grid carbon intensity that consider the UK grid as a whole. This approach explores what the overall household carbon intensity might be when on-site renewable energy is considered such as home solar but also when renewable energy is bought over the grid, this could be from a green electricity tariff.

If imported electricity is supplied from a 100% renewable energy supplier in the UK: a large portion of the supply will likely be wind energy (54% of good energy's 'fuel' mix comes from wind) and the UK has the best wind resource in Europe. Incorporating grid wind data and exploring matching with wind and solar, means we can really start to test scenarios such as ZeroCarbonBritain in the present.

There is real-time data available on UK wind supply and its possible to scale the total UK wind output in order to estimate a household 'share of UK wind' in real-time.

<!--more-->



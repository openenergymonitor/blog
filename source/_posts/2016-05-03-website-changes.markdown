---
published: true
layout: post
title: "New Forum, Blog and User Guide Website"
date: 2016-05-03 15:00
date_formatted: "May  3rd 2016"
author: Glyn Hudson
comments: true
categories:
 - forum
 - website
 - user guide
---

We have been busy for the past couple of months building some new websites to improve OpenEnergyMonitor.

Introducing a shiny new:

1. Community Forum
2. User Guide website
3. Blog

**Later this week on Thursday 5th May 2016 the old forums will be frozen and we will be moving to the new community forums**

<!--more-->

## 1. New Community Forum

![image]({{site.image_path}}/Selection_037.png)![image]({{site.image_path}}/Selection_038.png)

####  [https://community.openenergymonitor.org](https://community.openenergymonitor.org)

The current [OpenEnergyMonitor Forums](http://openenergymonitor.org/emon/forum) have been running (since 2010) on Drupal 6. As of February 2016 Drupal 6 reached EOL. This does not mean that the site will stop working, however, it does mean we have decided the time has come to upgrade the highest traffic and most interacted-with part of the site > The Community Forums.

Later this week **on Thursday 5th May 2016 the old forum will be frozen** and we will be moving to the new forum powered by [Discourse](https://www.discourse.org/) open-source forum platform hosted and managed us (OpenEnergyMonitor) on our servers.

You will need to create an account on the new forum. You should receive an email soon inviting you to the new forum, if you join via the link in the email you will receive elevated privileges on the new forum since you have already proved yourself as a trusted user.

Thanks a lot to the team of community volunteers who have prepare the new forum over the past few weeks.

## 2. New User Guide

![image]({{site.image_path}}/Selection_036.png)

#### [https://guide.openenergymonitor.org](https://guide.openenergymonitor.org)

[OpenEnergyMonitor.org](https://openenergymonitor.org/emon/) contains has a wealth of information (specifically the [Building Blocks](http://openenergymonitor.org/emon/buildingblocks) resources section), however a common issue raised by new users is they feel lost swimming in a sea of information. The user guide has been created to provide just the right amount of information to setup and configure and OpenEnergyMonitor system. The guide is focused on the emonPi but will also cover emonBase (Raspberry Pi + RFM69Pi), emonTx and emonTH.

The launch of the Guide site coincides with the launch of the new emonSD Raspberry Pi emonPi / emonBase pre built image which includes the latest version of Emoncms as well as MQTT, nodeRED, openHAB and Raspberry Pi 3 support all setup and pre-configured. [See forum post](https://community.openenergymonitor.org/t/emonsd-03may16-release/145). This new emonSD image will be installed as standard with all emonPi/emonBase's shipped from our store in the next few weeks. *We soon be selling the Raspberry Pi 3 as standard with emonPi / emonBase, another blog post on this coming soon..*

The User Guide site will attempt to create a distinction between 'user' documentation and 'developer' documentation and discussions. The Guide site has been designed to look and work great on mobile devices. We think this is important since stats indicated that users often follow the setup guide on a mobile or tablet while at the install site (think head stuck inside a meter cabinet!). Going forward we would like to standardise on the following locations for documentation:

 - User Guide Site - User documentation
 - Forums - User support / Developer discussion separated with categories.
 - GitHub - Technical documentation

The Hardware Wiki will still exist, however expect hardware documentation to move to [GitHub Hardware Repo](https://github.com/openenergymonitor/hardware) over time.

## 3. New Blog

![image]({{site.image_path}}/Selection_039.png)

#### [https://blog.openenergymonitor.org](https://blog.openenergymonitor.org)

We have wanted to move away from our [old Google blogger](http://openenergymonitor.blogspot.co.uk/) for a while. During the learning process building the Guide website I realised that using GitHub and Jekyll would also be a good solution for the blog. Thanks to Google export and a nice [Jekyll import script](https://import.jekyllrb.com/docs/blogger/) we managed to migrate over the blog without too much difficulty. Please update your RSS subscription to the [new RSS feed](http://blog.openenergymonitor.org/atom.xml).


### Technical info

The new Guide and Blog are built using [Jekyll](http://jekyllrb.com/) static site generator with Octopress [Oscailte theme](https://github.com/coogie/oscailte) to convert markdown files to html. The sites are [fully open-source on GitHub ](https://github.com/openenergymonitor/guide) and are hosted by GitHub pages. [Travis CI](https://travis-ci.org/openenergymonitor/guide/) has been configured to re-build the static html pages each time a change commit is made. Hosting the site on github will make it easy for anyone to propose a change/fix. The site is served and secured via Cloud Flare using CF's [Universal SSL/TLS to origin](https://blog.cloudflare.com/cloudflare-ca-encryption-origin/).

---
published: false
layout: post
title: "Part 2/3: Continuously Test & Automatically Build Firmware"
date: "2016-06-14 10:00"
date_formatted: June 14th 2016
author: Glyn Hudson
comments: true
categories:
  - platformio
  - travisci
  - firmware
  - emonpi
  - emontx
  - continuous testing
---

**This post is part of a series**

 - 1/3 [PlatfomIO overview & compiling + uploading locally and on a Raspberry Pi](https://blog.openenergymonitor.org/2016/06/platformio/)
 - 2/3: **Continuous testing and auto release binary generation using PlatformIO & TravisCI**
 - 3/3: Continuous Deployment (OTA to ESP8266) *- Coming soon...*

***

Following on from my last post on using [PlatformIO](https://blog.openenergymonitor.org/2016/06/platformio/) to compile and upload firmware locally we're now going to take things a step further and do the same the in *The Cloud*!

*Groam...I know I just used the cliched 'C' word, however there are many advantages to compiling and testing the code in the cloud. At least I didn't mention 'IoT'...whoops, just doing my bit for SEO!*

In this incidence when I say *'compile in the cloud'* what I mean is use GitHub, [Travis IO](https://travis-ci.org) and [PlatfromIO](https://platformio.org) to compile the firmware and if the branch is tagged with a 'Git Release' auto-generate a compiled binary and upload it back to GitHub release page.  

<!--more-->

The advantages of [continous testing](https://en.wikipedia.org/wiki/Continuous_testing) have been long established in the software industry. In this incidence when I say continuous testing when I mean is *'does the firmware compile?'*, obviously this is not a comprehensive test but at will at least give us confidence that there are no syntax errors etc. To actually test operation of embedded firmware physical hardware (or simulation) would be required. 

## How it works 

1. A commit or pull request is made to the firmware repository on GitHub

2. This triggers Travis CI to start a 'build'

3. Compilation is achieved in exactly the same way as locally using platformIO. [See blog post](https://blog.openenergymonitor.org/2016/06/platformio/).

4. If the build fails for whatever reason (syntax error, library error etc), then the green 'Build passing' icon changes to a 'Build Failed' icon and I get an alert email. 

[![Build Status](https://travis-ci.org/openenergymonitor/emonpi.svg?branch=master)](https://travis-ci.org/openenergymonitor/emonpi)

5. If the GitHub branch is tagged with a 'release tag', the generated .hex / .bin is uploaded to the GitHub release page.

 










***

Stay tuned for part 3/3 of the PlatformIO post series which will cover auto depolying (OTA) the compiled firmware release onto an ESP8266. For a sneek peak checkout [this excellant blog post](http://blog.squix.org/2016/06/esp8266-continuous-delivery-pipeline-push-to-production.html) which was the source of insperation and infomation.

***
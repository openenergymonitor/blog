---
published: true
layout: post
title: "Part 2/3: Firmware Continuous Test & Build"
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

 - [1/3 PlatfomIO overview & compiling + uploading locally and on a Raspberry Pi](https://blog.openenergymonitor.org/2016/06/platformio/)
 - **2/3: Continuous testing and auto release binary generation using PlatformIO & TravisCI**
 - 3/3: Continuous Deployment (OTA to ESP8266) *- Coming soon...*

***

Following on from the [last blog post](https://blog.openenergymonitor.org/2016/06/platformio/) on using [PlatformIO](https://blog.openenergymonitor.org/2016/06/platformio/) to compile and upload firmware locally, we're now going to take things a step further and do the same but in *The Cloud*!

*Groan...I know I just used the clichéd 'C' word, however there are many advantages to compiling and testing the code in the cloud. At least I didn't mention 'IoT'...whoops, just doing my bit for SEO!*

In this instance when we say *'compile in the cloud'* I mean use GitHub, [Travis IO](https://travis-ci.org) and [PlatfromIO](https://platformio.org) to compile the firmware and if the branch is tagged with a 'Git Release' auto-generate a compiled binary and upload it back to GitHub release page.  

The motivation behind this automated-build and testing is working towards creating a robust infrastructure to push OTA updates to ESP8266 connected nodes ([EmonESP dev](https://github.com/openenergymonitor/EmonESP)) inspired by [this blog post](http://blog.squix.org/2016/06/esp8266-continuous-delivery-pipeline-push-to-production.html) by Daniel Eichhorn ([@squix78](https://twitter.com/squix78)).

<!--more-->

The advantages of [continuous testing](https://en.wikipedia.org/wiki/Continuous_testing) have been long established in the software industry. The test we are performing is *'does this firmware compile?'*; obviously this is not a comprehensive test but it will at least give us confidence that there are no syntax errors etc. To actually test operation of embedded firmware, physical hardware (or simulation) would be required.

## How it works

1. A commit or pull request is made to the firmware repository on GitHub
  - So far emonPi, emonTx and EmonESP repositories have been enabled for continuous build & test.

2. This triggers Travis CI to start a 'build'

3. Code compilation is generated using platformIO in the same way as when compiling locally, [See blog post](https://blog.openenergymonitor.org/2016/06/platformio/).

4. If the build fails for whatever reason (syntax error, library error etc) then the green `build passing` icon changes to a ominous red `build Failed` and we get an alert email. For a full build log example see the [emonPi Travis CI build page](https://travis-ci.org/openenergymonitor/emonpi).

[![Build Status](https://travis-ci.org/openenergymonitor/emonpi.svg?branch=master)](https://travis-ci.org/openenergymonitor/emonpi)

5. If the GitHub branch is tagged with a 'release tag' and compilation is successful then the generated `.hex` or `.bin` is uploaded to the GitHub release page:

 ![image]({{site.image_path}}/emonpi-draft-release.png)

 ![image]({{site.image_path}}/emonpi-travis-release.png)



***

Stay tuned for part 3/3 of the PlatformIO firmware work-flow post series, which will cover auto deploying (OTA) the compiled firmware release onto an ESP8266. For a sneak peak checkout [this excellent blog post](http://blog.squix.org/2016/06/esp8266-continuous-delivery-pipeline-push-to-production.html) which was a source of inspiration and information.

***

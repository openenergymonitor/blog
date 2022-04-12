---
published: true
layout: post
title: "Chip Shortage & Hardware Development Update"
date: "2022-04-12 15:00"
date_formatted: April 12st 2022
author: Trystan Lea
comments: true
categories: hardware
---

It’s been some time since we gave an update on what we are doing and what is coming next. There’s a lot happening behind the scenes. This post will be mostly about hardware but we’ve also moved our office space amongst other things.

### Chip shortage 

Some of you may have noticed that we are out of stock on quite a few key items in the shop at the moment. We have unfortunately been hit by the ongoing chip shortage, affecting the whole of the electronics industry. 

The chip shortage seriously affects several key components that we use including the ATmega328 microcontroller, RaspberryPi’s and the chip that we were planning on using for new hardware, the STM32F303. There’s no general availability of these through standard distributors and the lead times from the manufacturers themselves are around a year. The pricing for these components through more speculative distributors are also eye wateringly high, which we don't think would represent good value if we added this additional cost to our units.

### Introducing the AVR-DB microcontroller range

![hardware22-1.jpg]({{site.image_path}}/hardware22-1.jpg)

The good news however is that after searching around for alternative options we found a new range of microcontrollers in the same AVR family as the ATmega328 that look very promising, both from a feature set perspective providing a welcome upgrade to the capability of our energy monitoring hardware but also on price and availability.

The AVR-DB range is the latest and highest spec 8-bit AVR microcontrollers from Microchip, launched relatively recently in mid-2020.

The [AVR128DB48](https://www.microchip.com/en-us/product/AVR128DB48) is of particular interest to us are (with comparison to the current ATmega328 in brackets):

- 12-bit ADC (4x improvement)
- 18 channels on the 48 pin version (up from 8)
- Higher sampling rate potential (~3x)
- Flash memory up to 128k (4x)
- All the usual peripheral requirements (SPI, UART, I2C etc)
- Potentially useful PGA Op amps built in
- Relatively low cost 
- Availability is relatively good, and we have secured the stock that we need! 
- Wide range of package types & pin counts.
- Arduino compatible core called [DxCore](https://github.com/SpenceKonde/DxCore)

![hardware22-2.jpg]({{site.image_path}}/hardware22-2.png)



These features provide many of the key benefits that we were hoping to get from using the STM32 range, in particular the 12-bit ADC, larger number of analog channels and a higher sample rate. That said the AVR-DB has still only a single ADC multiplexed to a large number of input pins and so does not allow for simultaneous sampling across voltage and current channels which was a nice feature of the STM32, but it’s also hard to say how much difference that would make in practice and is it worth the higher price of the STM32 chips?

The lack of availability of the STM32 chips mean we don't have much choice in the short term, but it’s certainly something to consider in the longer term.

A large plus for the AVR-DB range over the STM32 range is compatibility with our existing firmware developed for the ATmega328, In particular Robert Wall’s latest CM (Continuous Sampling) firmware using the native RFM69cw driver code. The modifications to make this firmware work on the AVR-DB is small. The familiarity provided by the hard work of Spece Konde on the DxCore for the Arduino IDE is also a huge plus for us and other open-source contributors. Combining the use of the DxCore with the modified low level commands for continuous sampling in the EmonLibCM library provides the best of both.

We’ve actually gone ahead and ordered, and received enough stock of a combination of AVR128DB48 and AVR128DB32 chips to see us through the next 18-months or so.

We are also well on our way on the design process for using these chips, with successful testing of these chips and new emonTx, emonPi and emonTH board designs in progress. 

Ultimately, if all goes well we expect to have the new units in stock in ~3-4 months time, mid to late July 2022. In the meantime, we have more stock of our current emonPi units on the way in a few weeks.

### Voltage output CT sensors

![hardware22-3.jpg]({{site.image_path}}/hardware22-3.jpg)

The new versions of the emonTx and emonPi will feature many of the same improvements that we were intending to implement with the STM32 development, which are in many ways more important than the microcontroller itself for the overall accuracy and general functionality of the system.

The first change is to support 333mV voltage output CT sensors. This is probably the most widely used type of CT sensor. There are many manufacturers, current ranges and accuracy ratings. By switching to this voltage output standard it’s much easier to select the right CT for the application and there’s no need to change the burden resistor on the circuit board to use different CTs. 

### Precision voltage sensing

![hardware22-4.jpg]({{site.image_path}}/hardware22-4.jpg)


The second key change will be to upgrade to using a [ZMPT101](https://www.micro-transformer.com/2ma-2ma-voltage-transformer-ZMPT101B.html) precision voltage transformer for higher accuracy AC voltage sensing. The current use of a standard AC output power adapter is the largest source of error in our system, so upgrading this part will provide the greatest gain in measurement accuracy.

The precision voltage sensing unit will be an external unit that plugs into the upgraded emonTx/emonPi and will also include an integrated power supply module so that only a single socket is required. This unit will also have the option of being hard-wired for a fixed installation and full three-phase monitoring. 

###  Precision reference

The third key change is to use a precision voltage reference chip to increase the accuracy of the ADC conversion.

### Accuracy  

Overall with the above combination and careful selection of other components in the system it should be possible to get to a maximum error for an uncalibrated system in the 1-2% range, the realistic error is better still if you applied a monte-carlo analysis of likely component tolerances. This will provide a significant upgrade to the out-of-the-box accuracy of our units.

***
Over the next set of posts I will outline what’s new on the new hardware designs and then continue to give updates on progress as they are tested, and we get them ready for production.

Here are a couple of pictures of our new office in the meantime. We have a unit in a really nice community building near Llanberis in North Wales, there's an onsite cafe that does really good food, cakes and coffee, we are nearer the mountains and walking distance from where we live which makes it all a lot more convenient. If you are in the area and would like to drop in to say hi, please get in touch!

![hardware22-5.jpg]({{site.image_path}}/hardware22-5.jpg)

To join in the discussion, see this thread on our community forums: [https://community.openenergymonitor.org/t/avr-db-emontx-v4-new-hardware-in-progress/20209](https://community.openenergymonitor.org/t/avr-db-emontx-v4-new-hardware-in-progress/20209)

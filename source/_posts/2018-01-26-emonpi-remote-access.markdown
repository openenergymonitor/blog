---
published: true
layout: post
title: "emonPi Remote Access with Dataplicity"
date: "2018-01-26 12:00"
date_formatted: Jan 26th 2018
author: Glyn Hudson
comments: true
categories: emonpi
---


Network devices such as an emonPi connected to a local network are secured behind a firewall, often integrated into a router.

The conventional way for obtaining access remotely is to open a port in the firewall and 'port-forward' requests to this port to the local emonPi. This method works but is cumbersome and insecure. It's cumbersome because most users connect to the internet via their ISP using a non-static IP. Therefore the WAN IP address often changes, a dynamic DNS service such as [Duck DNS](https://www.duckdns.org/), or [noIP](https://www.noip.com) can be used to link a dynamic IP to a static domain name, however this is cumbersome to set up and often requires purchasing a domain name, dynamic DNS Subscription and handling the dynamic DNS IP address updates.

The port forwarding method of remote access is also insecure since by default the emonPi uses an insecure http connections, this is not a problem on a secure local network but not recommend for use over the internet.

## Dataplicity

[Dataplicity](https://www.dataplicity.com) offers a easy to setup web-service service to enable secure remote access (SSH/HTTPS) to RaspberryPi devices. The free tier allows free access to a single RaspberryPi device.

![1-dataplicity]({{site.image_path}}/1-dataplicity.png)

![5-dataplicity]({{site.image_path}}/5-dataplicity.png)

![6-dataplicity]({{site.image_path}}/6-dataplicity.png)

Follow the steps on the [Remote Access page of our User Guide](https://guide.openenergymonitor.org/setup/remote-access/) to setup Dataplicity on an emonPi.



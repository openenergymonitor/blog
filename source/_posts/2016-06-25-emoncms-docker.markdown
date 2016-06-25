---
published: true
layout: post
title: 'Emoncms Docker'
date: '2016-06-25 10:00'
date_formatted: June 25th 2016
author: Glyn Hudson
comments: true
categories:
  - emoncms
  - docker
---

We have made the first steps towards running Emoncms to run in a [Docker](https://www.docker.com/) container.

Dockerfiles and setup notes are in the emoncms-docker repository:

### [https://github.com/emoncms/emoncms-docker](https://github.com/emoncms/emoncms-docker)

![image]({{site.image_path}}/docker-logo.png)

Docker is an exciting tool to help make development, testing and deployment of web-applications easier.

## What is docker? (the short version):

> Docker containers wrap a piece of software in a complete filesystem that contains everything needed to run: code, runtime, system tools, system libraries – anything that can be installed on a server. This guarantees that the software will always run the same, regardless of its environment.

### What is docker? (the long version):

> Docker is an open-source platform for developers and sysadmins to build, ship, and run distributed applications. Consisting of Docker Engine, a portable, lightweight runtime and packaging tool, and Docker Hub, a cloud service for sharing applications and automating workflows, Docker enables apps to be quickly assembled from components and eliminates the friction between development, QA, and production environments. As a result, IT can ship faster and run the same app, unchanged, on laptops, data center VMs, and any cloud.


## Quick Start

```
$ docker pull openenergymonitor/emoncms
$ git clone https://github.com/emoncms/emoncms-docker
$ cd emoncms-docker
$ docker-compose up
```

**That's it! Emoncms should now be runnning, browse to [http://localhost:8080](http://localhost:8080)**

<!--more-->

## Emoncms Docker

Using Docker it's possible to fire up Emoncms on a bare system (assuming Docker is installed) in a couple of minutes with all the LAMP install & config taken care of.

This is great for development since it's possible to play about with Emoncms running in a Docker container without fear of messing up your system or production Emoncms install.

In the future, Docker can even be used as a deployment tool for Emoncms. In theory, it should possible to deploy the Emoncms Docker container on any server within minutes.

We have taken a multi-container approach with php-apache running in one container and the MYSQL database running in another. The containers are linked using [docker-compose](https://docs.docker.com/compose/overview/).

**See [emoncms-docker Readme](https://github.com/emoncms/emoncms-docker) for setup & build instructions.**

*Note: The Emoncms docker setup is currently in development and not recomended for production Emoncms deployment just yet.*


## Forum discussion

See [this forum topic](https://community.openenergymonitor.org/t/emoncms-docker/823/4) for discussion.

***

---
layout: post
title: "GitHub Submodules"
date: 2016-04-18 15:00                                          # This is the indexed published time and date
date_formatted: "April  18th 2016"                                # This is the public facing date on the post
author: Glyn Hudson
comments: true
categories: github
---

Library management for Arduino has always been a bit of a pain; having to go and download and install all the required libraries for various locations on the internet and hope that they are the correct version.  Library management becomes even more important when debugging and supporting a project as libraries get changed and updated.

Things have improved in recent years with the increased use of GitHub for Arduino libs allowing changes to be tracked easier and the later version of Arduino IDE including a library manager which can auto-update.

However I have always wanted to have all required libs and files for a particular project all in once place. I feel that I have now found the best solution (for now!).

<!--more-->

## GitHub Submodules

>With git submodules a repository can contain a checkout of another repository as a subdirectory.
The subfolder stores the submodule repository location and a commit ID. This means you can, for example, keep some common code in a separate repository and use a specific, known-working version of this code in other projects.
If the submodule gets an update, the submodule will not get updated in the repo until you specifically pull the changes into them. Also, you can make changes to the submodule from within a project and push those changes to the submodule’s repository to make them available to other projects.

## Example

Here is the firmware folder of the [emonPi GitHub Repo](https://github.com/openenergymonitor/emonpi/tree/master/firmware/libraries). The visible sub folders contain the required Arduino libs at a specific point in time.

Using submodules becomes very useful when testing an update to one of the libraries in a development branch, in the development branch the submodule can be fast-forwarded to the latest version leaving the master branch untouched.

![Git SubModules]({{site.image_path}}/submodules.png)

Submodules also make it easy for users to clone a project repo including all the sketch source code and the Arduino libs at exactly the correct version all from one place. Using the later version of Arduino IDE (1.6+) it's possible to set the sketchbook location to the project repo to import all the required libs into the IDE.

To obtain the submodules the repo must be Git cloned (not zip downloaded) then once the repo has been cloned a couple of extra steps are required to import the submodules. Here is an example for cloning the emonPi repo in pull in the sub modules:

```
$ git clone https://github.com/openenergymonitor/emonpi
$ cd emonpi
$ git submodule update
$ git submodule init
$ git submodule update
```

---
categories:
- Development
date: 2006-07-16 22:50:55
layout: post
title: Finnix and Bootcharts
wp_id: 43
---
Finnix 88.0 will have [Bootchart](http://www.bootchart.org/download.html) support; "finnix bootchart" will start bootchartd, and stop it at the appropriate time. (Bootchart will look for key processes to determine when it's "done", such as getty or xinit. Finnix does not utilize either, so finnix-scripts must stop it manually at the end. Below is a (largeish) image, and some notes.
  
<!--more-->


  
[<img src="https://www.finnix.org/w/images/f/f0/2006-07-16_bootchart.png" alt="2006-07-16 bootchart" border="0" />](https://www.finnix.org/Image:2006-07-16_bootchart.png)
  
Notes:

  * knoppix-hotplug is one of the last remaining throwbacks from Finnix 84/85, which were Knoppix remasters. The only reason the file is still around is because it's never needed to be modified. However, post-88.0, I will be switching from hotplug to udev, which will make this process obsolete.
  * The first 5 seconds of "nothing" seem to be in init itself, and can't be overridden. I may look into the source to see what is causing that delay.
  * The 7-second sleep is for "settling", most notably because after USB storage devices are initialized, the kernel module sleeps for 6 seconds before making the partition table available. Post-88.0, I will look into parallelization, putting tasks that don't relate to disks between the initialization and the partition table scanning (such as mouse services). Then I would take the delta and sleep (for example, if other tasks take 3 seconds, it would sleep for 4 more seconds before scanning partition tables).
  * 20 seconds is still rather impressive. Let's see what we can shave off that.

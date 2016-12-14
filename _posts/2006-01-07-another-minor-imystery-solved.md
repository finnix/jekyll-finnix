---
id: 6
title: Another minor iMystery solved
date: 2006-01-07T19:49:30+00:00
author: Ryan Finnie
layout: post
guid: http://blog.finnix.org/2006/01/07/another-minor-imystery-solved/
permalink: /2006/01/07/another-minor-imystery-solved/
categories:
  - Development
  - Finnix
---
On Wednesday, I brought a dev copy of Finnix-PPC to work to try out on the Macs there. I have a G4 tower and a G4 mini at home, which this copy both worked great on. But at work, we have a G3 iMac and a G4 MDD "Windtunnel", and I like to test on as much hardware as possible. The G3 worked fine (if slow; IIRC, it's a 6MHz proc with 24Kb of memory), but Finnix could no longer find the CDROM drive on the Windtunnel, even though 86.1 could boot just fine.

After some digging, I found that the CDROM drive was on /dev/hde, which Finnix did not have an entry in /dev for. This made me say "well how did this work in 86.1?", but I did not have an 86.1 PPC disc handy. Nonetheless, this led to a bug fix and a feature enhancement: adding more /dev entries to the initrd and "three strikes and you're on your own", respectively.

Before, if the Finnix initrd could not find its CD boot device, you were screwed. You would be dropped down to an ash shell, but there was no way to continue the process if you found a fix. "Three strikes and you're on your own" was a solution to a combination of this and some USB enhancements/fixes I made for 86.2; namely, some USB devices will take longer to "settle down" than the 5 seconds Finnix gives it before it starts mounting and checking for a compressed image. If Finnix does not find an image on the first time, it will wait 10 seconds, then try again. This process repeats 3 times. If Finnix still cannot find the image, it gives the user a "you're on your own" warning, and drops the user down to a shell. However, if the user can deduce why Finnix did not find the image, he can manually mount the device to /ramdisk/cdrom, and when he exits from the shell, Finnix will continue on, assuming it successfully mounted the image.

As for why Finnix-PPC worked on the Windtunnel on 86.1, but the dev copy didn't work? The Windtunnel has 3 IDE channels. In kernel 2.6.14, ide0 contained the hard drive (hda), ide1 contained the CDROM drive (hdc), and ide2 had no devices. In 2.6.15, the location of ide1 and ide2 swapped for some reason, so now the CDROM drive is detected as being on hde. Adding /dev/hde* to the initrd (and many more devices, just in case) fixed the problem.

---
id: 57
title: Macs, and AMD64 Support
date: 2006-10-09T01:35:02+00:00
author: Ryan Finnie
layout: post
guid: http://blog.finnix.org/2006/10/09/macs-and-amd64-support/
permalink: /2006/10/09/macs-and-amd64-support/
categories:
  - Development
  - Finnix
---
I got my hands on a couple Mac Pro quad-core (in reality, 2 dual-core Xeons) machines at work this week, and [got Finnix to work on them](http://www.finnix.org/submits/x86/1160195401-3492276741-1559875628.gz), kinda. rEFIt found Finnix just fine, but the kernel would freeze when trying to mount the CDROM disc. "nodma" didn't work either. My next attempt was to boot from a USB CDROM drive. Once again, rEFIt found the USB CDROM drive and Finnix disc, but isolinux would fail halfway though loading the kernel image from CD. I eventually booted by putting a copy of Finnix in the onboard CDROM drive, and another in the USB CDROM drive, then booting the onboard CDROM and typing "finnix root=/dev/sr0". The problem seems to be kernel-related; hopefully 2.6.18 helps with this.

[Core Duo Mac Minis](http://www.finnix.org/submits/x86/1159841457-3492276741-1699090591.gz) and [Core Duo Macbook Pros](http://www.finnix.org/submits/x86/1152082079-1135890989-787139463.gz) boot fine, however. I would assume the Core Solo variants work fine as well. I've also been able to boot Finnix successfully and easily on several non-Mac Core Duo laptops, as well as the latest and greatest Athlon X2 systems.

\---

Development is coming along well. In addition to udev and netbooting support, the next Finnix will support autodetection of dm-crypt/LUKS partitions, and md software RAID sets. Additionally, I am 99% sure I will be including an AMD64 kernel (bootable as "finnix64" instead of "finnix") along with the normal 586 kernel. There are two main reasons for doing this:

  * Current x86 Finnix kernels are not PAE enabled, which means they cannot utilize more than 4GB RAM. This is done because PAE tends to be problematic on hosts with 4GB RAM or less. Native 64-bit kernels (on an AMD64/EM64T CPU, of course) have a much higher limit (petabytes?). Granted, the average machine still has less than 4GB RAM these days, but I have had to use Finnix on 6GB/8GB machines before. (Non-PAE kernels still boot, they just display the installed RAM as 4GB.)
  * While the Finnix userland will still be 32-bit, booting a 64-bit kernel will allow you to run static-compiled 64-bit programs, and more importantly, chroot into pure 64-bit environments. This will become increasingly important as more and more distros offer native AMD64 userlands as an option (Fedora, RHEL, SuSE, and soon Debian).

However, another kernel means a larger distro. In order to cut down on size, I have decided to remove the finnix-uml package (AKA Finnix-on-Finnix) from the main distribution. Finnix-on-Finnix was created as a way to prototype and test Finnix virtualization support (by acting as both the host and guest, you test two birds with one stone), and virtualization support has proven to be incredibly stable the last few releases. However, once a Finnix release is gold, Finnix-on-Finnix itself becomes little more than a novelty, which very few people use, and takes up previous megabytes. The finnix-uml package will still be maintained and available in the apt repository, so it is little more than an "apt-get install finnix-uml" away if you still want to use it.

After all is said and done, it's looking like the final compressed distro size will be about 110MiB after adding the AMD64 kernel. While still much lower than the project's target ceiling of 185MiB, I had been trying to keep x86 under the magical 100MiB number. Oh well.

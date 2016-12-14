---
author: Ryan Finnie
categories:
- Development
- Finnix
date: 2011-06-28 23:59:27
guid: http://blog.finnix.org/2011/06/28/finnix-102-development-status/
id: 240
layout: post
permalink: /2011/06/28/finnix-102-development-status/
title: Finnix 102 development status
---
Finnix 102 is coming along well. At this point, everything on my list is done, and I'm just waiting for Linux 3.0 to be finalized (I've been testing against 3.0-rc builds for awhile, with good success). A changelog so far (subject to change before final release):

* dist-upgrade
      
* Upgraded kernels to 3.0 (Debian 3.0.0-xxx)
      
* Added xen-blkfront to the initrd (AMD64 kernel)
      
* Added initrd loading attempt of xen-blkfront and xen-netfront
      
* Added ability to set manual IPv4 addresses and basic resolv.conf info via boot parameters
      
* Changed kernel, SquashFS compressed root, and initrd to xz compression
      
* Changed finnix-netboot-server and finnix-netboot-biginit to detect gzip/xz/uncompressed initrd, and build initrd_net accordingly
      
* Fixed console boot flag
      
* Fixed automatic update of /etc/fstab during hotplug device update
      
* Upgraded Memtest86+ to 4.20

The current x86 dev build is 2520, which gave me the idea to go back and look at what builds corresponded to what releases.

* 86.1: 1435
      
* 86.2: 1504 (+69)
      
* 87.0: 1617 (+113)
      
* 88.0: 1776 (+159)
      
* 89.0: 1961 (+185)
      
* 89.1: 1969 (+8)
      
* 89.2: 2011 (+42)
      
* 90.0: 2084 (+73)
      
* 91.0: 2154 (+70)
      
* 91.1: 2185 (+31)
      
* 92.0: 2270 (+85)
      
* 92.1: 2296 (+26)
      
* 93.0: 2318 (+22)
      
* 100: 2359 (+41)
      
* 101: 2473 (+114)

Prior to the 86.0 release, I picked build #500 as a rough guess as to how many builds I had made since then. 86.0 itself didn't have the build number shown publicly, so I don't have that data. Most testing is done on a VM (formerly VMware, today VirtualBox), so comparatively few builds are actually burned to CD (I would estimate about 200, which is still a lot). But nearly every build has at least been booted.

PowerPC builds use a different build number which is much smaller, 226 as of today. This is because the primary dev machine is an older G4 Mac Mini, which takes much longer to build compressed roots (formerly about 5 minutes, now over 20 minutes due to the switch to xz compression as mentioned in the changelog), compared to a minute or so on x86, a Core 2 Duo E7200. So most development and architecture-agnostic testing is done on x86 in a VM, then the changes are transferred over in bulk to the PPC environment and built.

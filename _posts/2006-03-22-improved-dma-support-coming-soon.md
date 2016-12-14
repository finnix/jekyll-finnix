---
id: 23
title: Improved DMA Support Coming Soon
date: 2006-03-22T23:40:44+00:00
author: Ryan Finnie
layout: post
guid: http://blog.finnix.org/2006/03/22/improved-dma-support-coming-soon/
permalink: /2006/03/22/improved-dma-support-coming-soon/
categories:
  - Development
  - Finnix
---
One of the problems with today's Finnix is that when the initrd scans for IDE drives, it is using the IDE system compiled into the kernel, which is "generic". This is the most stable solution (I have yet to find an IDE CDROM drive that is not recognized), but unfortunately, there is almost no DMA support in the generic driver, so even when the system is booted with "finnix dma", there is a good chance DMA support will not be enabled for either the CDROM or any disks. On top of that, even if you were to load the appropriate specialized IDE module for your chipset, the channels are already registered to the generic driver, and there appears to be no way to reverse that.

With the upcoming 87.0, I decided to modularize the IDE system, with the idea that the base IDE module would be loaded, then each specialized chipset module would be loaded, with the generic module loaded last. This would give the more specialized drivers a chance to load first, at which point DMA could be turned on by the user if desired. An unintended consequence was that it appears many chipset drivers automatically enable DMA if the channel supports it.

There lies the problem. It didn't take me long to find a CDROM drive that, when DMA mode was enabled and data read from it, would freeze the system. Booting from another CDROM drive on the same channel did not have this problem, so it was a problem with the driver interacting with the drive itself, not the channel or chipset. It was then that I decided to combine this new funcionality with the "dma" boot parameter. With Finnix 87.0, the plan is now to load specialized drivers, and enable DMA mode, but only if the "dma" boot parameter is given. Without that parameter, Finnix will load just as it did in previous versions.

It's sad that I'm choosing not to make this new functionality default, as the speed increase from DMA mode is considerable, but in this case I would prefer stability on a wider range of hardware to be preferable over speed. Of course, it'll be available... Just do "finnix dma", or you could boot into debug mode and manually modprobe your chipset's drivers, which will be available on the initrd.

**Edit:** I've found the "Use PCI DMA by default when available" option in the kernel config, but I believe I'll be keeping it as default ("on" as per Debian's config), and still going with the method described above.

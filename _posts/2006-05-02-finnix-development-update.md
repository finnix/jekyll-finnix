---
author: Ryan Finnie
categories:
- Development
- Finnix
date: 2006-05-02 14:36:23
guid: http://blog.finnix.org/2006/05/02/finnix-development-update/
id: 31
layout: post
permalink: /2006/05/02/finnix-development-update/
title: Finnix Development Update
---
Finnix development stalled for the past month since the release of 87.0, mainly because there wasn't much to do, so I tended to other things. However, there's been some work in the past 48 hours:

  * Did a dist-upgrade to bring it up to sync with current etch
  * Added "set mark-symlinked-directories on" to /etc/inputrc (Finnix uses symlinks a lot, and it's annoying having to double-tab when you want to tab-complete to /etc, for example; this fixes that)
  * Added dmidecode and selectable modules to finnix-hwsubmit
  * Added "dos" boot profile (boots into FreeDOS)
  * Replaced hwsetup with a new, faster "pcimodules" routine

That last line is where all the neat is. Here's a rough idea how current Finnix 87.0 boots its initrd:

<!--more-->

  * SCSI drivers are loaded, if <tt>bootscsi</tt> is specified. This is done by blindly loading some ISA drivers, then manually trying to parse human-readable vendor strings in /proc/pci, to determine which module to load.
  * IDE drivers are loaded. If <tt>dma</tt> is specified, Finnix attempts to load (nearly all) PCI IDE modules in sequence. Most succeed, even though there is no such IDE controller installed. If <tt>dma</tt> is not specified, Finnix simply loads ide-generic and generic.
  * USB drivers are loaded, if <tt>bootusb</tt> is specified. This is done by blindly loading both uhci-hcd and ohci-hcd, then ehci-hcd. Like IDE modules, these will often succeed even if there are no USB controllers. Then usb-storage and usbhid are loaded.
  * Same deal with Firewire.
  * If SCSI, USB or Firewire succeeded (which is nearly 100% of the time, if any option is turned on), sd\_mod and sr\_mod are loaded.
  * Once the module loading frenzy is over, the device mounting frenzy begins. /dev is scanned, and many classes (hd\*, sd\*, etc) are tried. This equals hundreds of possibilities, most of which don't even exist. (/dev/hdi12? Doubtful that device even exists, let alone has a Finnix image on it. But Finnix tries it anyways.)
  * Once the full Finnix environment is loaded, roughly the same thing happens again, but in more detail and a different order:
  * USB modules are re-loaded, this time by default.
  * Same with Firewire.
  * PCMCIA loading is attempted by trying to install all 3 popular PCMCIA modules. If any of them succeed, cardmgr is installed.
  * Next, a utility written by Klaus Knopper is run, that works a bit like Kudzu in the Red Hat world (in fact, it uses libkudzu on the backend). The PCI bus is compared against a static, hand-updated list of mappings between PCI ids and kernel modules. Known modules are then installed.

Sounds wasteful? Yes, but it worked because it was "good enough". Now, enter <tt>pcimodules</tt>. This is a nifty little utility that was grafted into the Debian pciutils package. See, in recent 2.6 kernels, each module exports a list of PCI IDs that the module is capable of handling. <tt>depmod</tt> takes this information, and compiles it into a few files, one of which is <tt>modules.pcimap</tt>. <tt>pcimodules</tt> takes this list, compares it against the PCI bus, and spits out a list of modules that should be installed. I used this as the basis of an excuse to rewrite a major portion of the boot code. Here's how it's roughly happening on development builds now:

  * In the initrd, <tt>pcimodules</tt> is run against the limited subset of modules available within the initrd. This includes many SCSI adapters, most IDE adapters, and the USB and Firewire stuff. Detected modules are loaded.
  * Next, /sys/bus is scanned. If /sys/bus/ide exists, install ide-disk and ide-cd. /sys/bus/usb, usb-storage and usbhid. /sys/bus/ieee1394, sbp2. If usb, ieee1394, or scsi were detected, load sr\_mod and sd\_mod.
  * Now that the modules have been (much more efficiently) loaded, try mounting. Remember before that hundreds of mostly non-existent devices were tried before. Now, /sys/block/*/dev is scanned, looking for block devices. Impossible block devices (such as fd0) are removed, and the rest are created as temporary dev entries. The mounter now scans through those. We've just reduced hundreds of possibilities down to a half-dozen.
  * Again in the full environment (post-initrd):
  * <tt>pcimodules</tt> is run again, this time against the full availability of kernel modules. A more complete module list is returned, and those modules are loaded.
  * The same "additional modules" are loaded if needed, using the same logic as in the initrd.
  * At this point, the proper PCMCIA module should be loaded if present (because PCMCIA is simply a bus on top of the PCI bus), so if /sys/class/pcmcia\_socket/pcmcia\_socket0/device exists, load <tt>cardmgr</tt>.
  * The system sleeps for 3 seconds, to allow for probed devices to "settle".

That's it! Simpler, more automatic, and above all, FASTER. In my development vmware session, 87.0 takes **40** seconds to load. That's with default settings, so no USB/Firewire/SCSI scanning in the initrd. The current development build takes **28** seconds. That's with fully automatic module loading.

This also means that many boot-time options have been removed, because there are now automated. Of the top of my head, I removed nobootide, bootusb, nobootusb, bootfirewire, nobootusb2, bootscsi, nousb, nousb2, nofirewire, noscsi, nopcmcia, and dma. Automatically loading DMA-capable modules makes me worry (see [this blog post](http://www.finnix.org/blog/2006/03/22/improved-dma-support-coming-soon/)), but out of the 30 or so different setups I've tested, only one drive has a problem with DMA, and it's a DVD burner that is frankly broken in other respects as well.

Additionally, this means that ISA SCSI CDROM booting is no longer possible without dropping into debug mode and loading modules manually. However, I doubt anyone has ever used that functionality. (If you use an ISA SCSI CDROM drive with Finnix, send me a finnix-hwsubmit report proving it, and I'll send you a dollar for your troubles :) )

Oh, and this also compacted my code considerably. In both the initrd and the autoconfig scripts, module detection/loading was reduced from 200 lines of code down to 15. Seriously.

---
id: 260
title: Finnix 102 released
date: 2011-07-23T00:00:16+00:00
author: Ryan Finnie
layout: post
guid: http://blog.finnix.org/2011/07/23/finnix-102-released/
permalink: /2011/07/23/finnix-102-released/
categories:
  - Announcements
  - Finnix
---
Finnix is a small, self-contained, bootable Linux CD distribution for system administrators, based on Debian testing. Today marks the release of Finnix 102, the eighteenth release of Finnix since its beginnings over ten years ago. Finnix 102 includes Linux kernel 3.0, a smaller distribution size, new Xen pvops and 486 support, and minor bug fixes.

  * Home page: <http://www.finnix.org/>
  * Download: <http://www.finnix.org/Download>
  * Release notes: [http://www.finnix.org/Finnix\_102\_release_notes](http://www.finnix.org/Finnix_102_release_notes)
  * Free stickers! <http://www.finnix.org/Free_stickers>

## Linux 3.0

Finnix 102 includes the recently-released Linux 3.0 kernel, and is a slight departure from usual Finnix method of closely following Debian kernel development. Config management was based on Debian pre-release kernels, but patch management was handled internally, basing only partly on Debian. Linux 3.0 support was tested heavily throughout the Linux 3.0-rc process.

## Smaller size

Finnix 102 includes XZ (LZMA2) compression of the compressed root and initrd, resulting in distribution savings of more than 20% over previous Gzip compression, and no measurable reduction of boot times.

## Xen pvops guest support

While Finnix has included Xen guest recognition since Finnix 86.1, Finnix 102's AMD64 kernel now includes built-in Xen pvops guest support. Therefore, Finnix may now be booted in a Xen environment with no extra building or configuration. Simply use the included linux64 kernel file, the initrd.xz initial ramdisk, and the Finnix 102 ISO as a virtual block device.

## 486 support

Finnix 102 is the first Finnix release, including Finnix 0.03 way back in 2000, to include 486 support, though it has not been tested. This is done by not including PAE support in the x86 kernel. The downside is x86 computers with more than 4GB of RAM can only use 4GB with the x86 kernel. However, nearly all computers with over 4GB RAM are also 64-bit capable, so the AMD64 kernel (default on capable platforms) may be used.

Anyone sending photographic proof of Finnix being booted on a 486 (showing Finnix boot plus the output of /proc/cpuinfo on the screen) will be given a free Finnix full-color CD and free Finnix stickers.

## G5 support reaffirmed

While the PowerPC G5 platform has remained a supported platform since PowerPC support was introduced in Finnix 88.0, it was never tested before release, due to lack of hardware. Now a Power Mac G5 DP/DC model is available for testing. The full list of platforms tested include: 586, 686, AMD64, G3 NewWorld, G4, G5, Xen.

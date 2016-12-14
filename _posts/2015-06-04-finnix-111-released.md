---
author: Ryan Finnie
categories:
- Announcements
- Finnix
date: 2015-06-04 08:45:17
guid: http://blog.finnix.org/2015/06/04/finnix-111-released/
id: 480
layout: post
permalink: /2015/06/04/finnix-111-released/
title: Finnix 111 released
---
Finnix is a small, self-contained, bootable Linux CD distribution for system administrators, based on Debian testing. Finnix 111 includes support for the ARM architecture, OverlayFS support, as well as other features and bugfixes.

## ARM support

Finnix 111 introduces support for the [ARM (armhf)](http://www.finnix.org/ARM) architecture, in addition to existing x86 and PowerPC archicture support. Finnix 111 for ARM is currently classified as a "technology preview", and primarily targets the Versatile Express A9 platform, as emulated by QEMU. This makes it easy to [download and test via QEMU](http://www.finnix.org/ARM) on a standard PC without special hardware.

Additional platforms are planned for the future. Finnix for ARM has been successfully tested on the Raspberry Pi 2, when combined with Raspberry Pi firmware and a custom kernel.

## OverlayFS support

Finnix 111 includes Linux kernel 4.0, which includes OverlayFS functionality. Previous Finnix releases used AUFS to overlay a ramdisk on top of a compressed root filesystem, but required a kernel patch, as AUFS is not in the upstream Linux kernel. Finnix 111 now uses OverlayFS directly, which means that special (non-upstream) kernel functionality is no longer required in Finnix kernels. This will help [VPS providers](http://www.finnix.org/Finnix_for_VPS_providers) better integrate Finnix into their platforms, and will make kernel maintenance easier for future releases.

  * Home page: <http://www.finnix.org/>
  * Download: <http://www.finnix.org/Download>
  * Release notes: [http://www.finnix.org/Finnix\_111\_release_notes](http://www.finnix.org/Finnix_111_release_notes)
  * Free stickers! <http://www.finnix.org/Free_stickers>

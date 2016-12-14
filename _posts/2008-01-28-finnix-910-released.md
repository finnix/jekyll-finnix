---
id: 66
title: Finnix 91.0 Released
date: 2008-01-28T13:51:09+00:00
author: Ryan Finnie
layout: post
guid: http://www.finnix.org/blog/2008/01/28/finnix-910-released/
permalink: /2008/01/28/finnix-910-released/
categories:
  - Announcements
  - Finnix
---
Finnix is a small, self-contained, bootable Linux CD distribution for system administrators, based on Debian testing. Today marks the release of version 91.0 for the x86/AMD64, PowerPC, and UML/Xen platforms.

Finnix 91.0 includes a new Linux kernel (2.6.24), automatic 32-bit/64-bit detection on the x86 platform, stackable RAID/LUKS/LVM detection and setup, and several bug fixes.

**Automatic 32-bit/64-bit detection (x86)**

If you press "enter" at the boot screen of Finnix 91.0 x86, the boot loader will now detect if you have a 64-bit capable CPU, and will load the appropriate kernel. You can still force 32-bit or 64-bit by entering the "finnix" or "finnix64" boot profiles. Note that this is for the x86 Finnix CD only; PowerPC G5 users will still have to enter the "finnix64" boot profile manually, as the yaboot boot loader does not have this capability.

**Stackable RAID/LUKS/LVM**

While RAID, LUKS (encryption) and LVM detection have been in Finnix for awhile now, they were loaded in a certain order, and some configurations were not detected as a result. With Finnix 91.0, most configurations should be detected. For example, an encrypted LVM set on top of two RAID disks should be set up automatically.

**Bug fixes**

While not a "major new feature", several bug fixes were made for Finnix 91.0, including LVM/LUKS fixes, and multiple-level /dev block device detection corrections.

  * Home page: <http://www.finnix.org/>
  * Download: <http://www.finnix.org/Download>
  * Release notes: [http://www.finnix.org/Finnix\_91.0\_release_notes](http://www.finnix.org/Finnix_91.0_release_notes)

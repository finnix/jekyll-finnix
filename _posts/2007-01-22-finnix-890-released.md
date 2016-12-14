---
id: 59
title: Finnix 89.0 Released
date: 2007-01-22T00:00:37+00:00
author: Ryan Finnie
layout: post
guid: http://blog.finnix.org/2007/01/22/finnix-890-released/
permalink: /2007/01/22/finnix-890-released/
categories:
  - Announcements
  - Finnix
---
Finnix is a small, self-contained, bootable Linux CD distribution for system administrators, based on Debian testing. Today marks the release of version 89.0 for the x86 (and now AMD64), PowerPC, and UML/Xen platforms.

Finnix 89.0 features Linux 2.6.18, a new "finnix64" AMD64 boot profile, netboot support with a built-in netboot setup wizard, MD RAID and LUKS crypt autodetection.

**AMD64 support**

An AMD64 kernel is now included on the Finnix x86 CD. To use this kernel on an AMD64/EM64T machine, type "finnix64" at the boot prompt. While the Finnix userland is still 32-bit, using an AMD64 kernel on a supported platform yields several advantages:

  * More than 4GB memory can be utilized natively.
  * Statically-compiled AMD64 applications can be executed.
  * You can chroot into native 64-bit AMD64 filesystems.

This addition gives a total of 6 supported kernel environments: x86, AMD64, PowerPC, PPC64, User Mode Linux, and Xen.

**Netboot support**

Finnix can now be booted via a network. A NFS server export is set up with the Finnix files in it, and the kernel and initrd are served to the user via TFTP. The Finnix CD contains a utility called finnix-netboot-server, which allows one Finnix instance to serve as a NFS/TFTP server for a Finnix netboot instance.

**RAID/LUKS autodetection**

Previous Finnix installations would detect and automatically set up LVM volumes. Finnix 89.0 goes two steps further with autodetection for md-based software RAID arrays, and LUKS-based dm-crypt encrypted partitions. Software RAID arrays are set up automatically if all array parts are found, while LUKS partitions are set up if the user types in a valid decryption password for each partition. 

  * Home page: <http://www.finnix.org/>
  * Download: <http://www.finnix.org/Download>
  * Release notes: [http://www.finnix.org/Finnix\_89.0\_release_notes](http://www.finnix.org/Finnix_89.0_release_notes)

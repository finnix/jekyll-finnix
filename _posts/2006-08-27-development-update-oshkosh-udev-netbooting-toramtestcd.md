---
categories:
- Development
date: 2006-08-27 08:10:19
layout: post
title: 'Development Update: Oshkosh, udev, Netbooting, toram/testcd'
wp_id: 55
---
One day, Finnix will be "finished", and I will be left with releasing updated ISOs every few months with a dist-upgrade and maybe a new kernel. Thankfully, that day hasn't come yet.

First up, for post-88.0 development, the new codename is [Oshkosh](http://en.wikipedia.org/wiki/Oshkosh%2C_Wisconsin), a city of about 60,000, on the west side of [Lake Winnebago](http://en.wikipedia.org/wiki/Lake_Winnebago). Oshkosh is the original home of [OshKosh B'Gosh](http://www.oshkoshbgosh.com/), a popular line of children's clothing. Oshkosh is also home to the world's busiest airport... for one week, that is. The [EAA AirVenture Fly-In](http://www.airventure.org/) is a yearly gathering of experimental aircraft enthusiasts, and the single airfield handles 10,000 to 15,000 aircraft during the week-long show.

New builds are up on the snapshots server. Here are the major developments being worked on:

  * udev support. The primary benefit of udev for Finnix is automatic generation of fstab entries. If you were to partition a hard drive, the new partitions will immediately show up in fstab, with /mnt directories created automatically.
  * Network booting. Finnix is now capable of being booted via PXE/bootp, expanding the possiblities of a sysadmin in need. Additionally, a new script is available, <tt>finnix-netboot-server</tt>, which takes care of configuring and starting TFTP and NFS servers from within Finnix itself. All you have to do is add a few lines to your DHCP server's config.
  * toram and testcd functionality has been reverted back to its "classic" file-based operations. Block-based operation was nice, but the drawbacks outweighed the benefits.
  * A new kernel is available on the x86 image, 2.6.17-3-x86-finnix, based on Debian's 2.6.17-8, which is based on 2.6.17.11 vanilla. Nothing special, it was mainly to test a new kernel build method. Future releases will have Debian-style kernel source/header packages available, which will make it easier to compile 3rd-party modules and remaster the kernel portion.

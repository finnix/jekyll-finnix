---
id: 168
title: 'Finnix 101: What to look forward to'
date: 2010-12-20T12:21:27+00:00
author: Ryan Finnie
layout: post
guid: http://blog.finnix.org/?p=168
permalink: /2010/12/20/finnix-101-what-to-look-forward-to/
categories:
  - Development
  - Finnix
---
I'll be honest, Finnix 100 was a rush job. Not a bad rush job _per se_; I have found no major problems with it and continue to use it on a daily basis. But there's nothing particularly great about it. The entire development cycle was about 2 weeks, to get a release out the door to reverse a one-year hiatus. Just enough to bring the software up to date, compile a new kernel, and run through regression testing.

Finnix 101 will be different. I've been working non-stop since October, and behind the scenes, Finnix has basically been completely re-engineered. To a casual eye, nothing will look different. Same boot menus, same minimalist boot, same quick boot times, same overall look. That's fine -- that's what gives Finnix its appeal. But the underlying architectural changes have been a long time coming, and will be useful for development and re-development (that is to say, remastering).

The current dev changelog is quite long by now, but here are a few highlights:

  * [As mentioned in a previous post](http://blog.finnix.org/2010/11/19/clarification-on-finnix-for-powerpc/), PowerPC support is coming back!
  * A new kernel, most likely. Debian testing is still on 2.6.32 due to the freeze, but I've been testing 2.6.36 for awhile and it's been stable.
  * The Finnix CD is now 100% self-building. Before you could remaster Finnix from within Finnix, using a set of downloaded scripts (which sadly, I rarely updated). But now the scripts (finnix-build-stage1 and finnix-build-stage2) are located within Finnix itself, and the build scripts on the CD are guaranteed to be the scripts used to build the official release.
  * The CD ISO layout has been completely changed. All files/directory names on the CD are now lowercase, to guard against accidental renaming when on a USB key, for example. Instead of the main compressed root in /FINNIX/FINNIX, it is now in /finnix/arch/$distarch/root.img, where $distarch is amd64, x86, ppc64 or ppc. Since Finnix is only distributed with 32-bit userlands, the locations will be /finnix/arch/x86/root.img and /finnix/arch/ppc/root.img. But if a 64-bit userland were added, amd64 and ppc64 root.img files could simply be added and Finnix would use them if available and usable. /finnix/arch.map contains a list of \`uname -m\` to $distarch mappings, so adding completely new architectures would even be easier. The map file allows for 64-bit to 32-bit fallback, which allows you to use a 64-bit kernel, and Finnix will look in, say, /finnix/arch/amd64/ first, then /finnix/arch/x86/ as a fallback.
  * With the above in place, it will now possible to make a hybrid x86/PPC CD. With the new layout, the two CDs can essentially be merged into one, and with some mkisofs magic, the combined CD can be made bootable on both arches. I don't plan on releasing a combined ISO, but I do plan on releasing the script to allow you to create one yourself.
  * A Finnix-specific SysV-compatible RC system has been created for booting the distribution. In the past, Finnix essentially fought against Debian's RC system, removing Debian's symlinks in /etc/rc\*.d/ and replacing them with Finnix-specific scripts. With Debian's move toward a concurrent boot system, this has become more difficult, so Finnix will simply be using its own separate system in /etc/finnix/rc\*.d/ instead. (Indeed, it is a fork of Debian's sysv-rc.)
  * With a Finnix-specific RC system, it is now much easier to break the Finnix sysinit boot into component scripts. All previous versions of Finnix essentially used one giant boot script, so this will allow sysinit-type tasks (such as scanning the PCI bus) to be placed separately in /etc/finnix/rcS.d/, and traditionally userland tasks (such as starting mouse services or an optional SSH daemon) in /etc/finnix/rc2.d/. The userland tasks have been split out and will be ready for Finnix 101, but the sysinit tasks may not be completely componentized for the release.
  * A new netboot helper script has been added, finnix-netboot-biginit. This allows you to create a netboot initrd that contains the entire Finnix distribution within itself. The benefit is you do not need an NFS server to netboot Finnix, only a TFTP server. The downside is you will need more than twice the memory as the size of the distribution, at least 512MB. (There are several stages during boot where the initrd will need to be stored in memory twice; the initrd system was not exactly designed for 1XXMB initrds to be loaded efficiently. Once the boot is completed though, you will only be storing 1x the distribution size in memory, plus standard OS overhead.)
  * The initrd can now automatically detect whether AUFS and/or UnionFS are available. This will help VPS providers deploy Finnix using their kernels, picking whichever module is more convenient for them to implement.
  * On x86, [Hardware Detection Tool](http://syslinux.zytor.com/wiki/index.php/Hdt_%28Hardware_Detection_Tool%29) has been added to the boot menu, which allows you to view system information quickly, without booting into a full operating system.
  * Many smaller improvements and bugfixes are of course included.

The release is feature complete, and I was hoping for a Christmas launch, but at this point I don't think I can go through the required testing and get the ISOs to the mirrors in time. 3 months since Finnix 100 will be late January, though I hope to have a release before then.
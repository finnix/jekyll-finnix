---
author: Ryan Finnie
categories:
- Development
- Finnix
date: 2012-11-01 23:33:15
guid: http://blog.finnix.org/2012/11/01/finnix-development-update-2/
id: 427
layout: post
permalink: /2012/11/01/finnix-development-update-2/
title: Finnix development update
---
About two weeks ago, I had surgery for a somewhat serious injury. The weeks leading up to and since the surgery have given me a lot of time to work on personal projects (for the weeks before the surgery I was on strong painkillers which messed up my sleep, often keeping me up in the middle of the night, and the weeks since have been in recovery), which let me get [Finnix 106](http://www.finnix.org/Finnix_106_release_notes) out the door earlier this week.

It has also given me time to make some long-desired architectural changes to the development environment, beginning with [Project NEALE](http://www.finnix.org/Project_NEALE) during the Finnix 105 development cycle. Here is a short update of what's changed lately.

As part of Project NEALE, all components of Finnix not contained in the compressed root (the CD layout, initrd, kernel and miscellaneous files) are now stored in udeb packages (neale-master, neale-initrd, neale-kernel and neale-stuff, respectively), which are extracted as part of build-neale. The method is slightly unusual; for example, the neale-kernel and neale-initrd source packages contain sources, as well as pre-built binaries for all supported architectures. But the net effect is all non-Debian sources are now contained in packages at [archive.finnix.org](http://archive.finnix.org/finnix). If you need the sources for a Finnix kernel from 106 onwards, grab the source package for neal-kernel.

Through Project NEALE, Finnix now has support for building ISOs with AMD64 userlands. While Finnix will not be releasing an official ISO with an AMD64 userland (for reasons explained on the [Project NEALE wiki page](http://www.finnix.org/Project_NEALE#AMD64_64-bit_userland_Finnix_builds)), it is a testament to the versatility and abstraction that NEALE allows versus the old, manual method of assembling releases.

Packaging for all Finnix packages are now being [managed in version control via bzr on Launchpad](https://code.launchpad.net/finnix). I [sent a mail to the debian-derivatives list](http://lists.debian.org/debian-derivatives/2012/10/msg00053.html) recently, detailing my experiences in undertaking this.

The archive at [archive.finnix.org](http://archive.finnix.org/finnix) is managed by a tool called [reprepro](http://mirrorer.alioth.debian.org/), a mid-end system for managing Debian-style apt repositories. I have written a plugin for reprepro, which takes source uploads, scans for changelog entries with "LP: #12345" (the same format Ubuntu uses), and will update the corresponding bug's status, add an "archive-fixed" tag, and add a comment with a copy of the .changes file. This is similar to what both Debian and Ubuntu do on their respective bug tracking systems.

And example of a recent Finnix bug fixed by a source upload is [here](https://bugs.launchpad.net/finnix/+bug/1072525). Originally the plugin was specific to Finnix, but I have [expanded it to be a general purpose tool](https://code.launchpad.net/~fo0bar/finnix/reprepro-launchpad-announce). So if you manage an apt repository with reprepro and also use Launchpad for bug tracking, this tool may be of use to you.

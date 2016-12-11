---
id: 39
title: Development, Development, Development, Development
date: 2006-07-02T02:13:56+00:00
author: Ryan Finnie
layout: post
guid: http://www.finnix.org/blog/2006/07/02/development-development-development-development/
permalink: /2006/07/02/development-development-development-development/
categories:
  - Development
  - Finnix
---
News from the development front...

First, a clarification about codenames. Namely, they will only be used during development. Currently, the daily builds are tagged as "Finnix version dev (Pulaski)", with "Pulaski" indicating "after 87.0 release, but before 88.0". When 88.0 is released, it will simply be called "Finnix version 88.0".

As you may have heard 2 sentences ago, yes, the next version will be numbered 88.0. The vitals are looking like the following: Linux 2.6.17 (as of this writing, Debian's 2.6.17-2), UnionFS 1.3 (no more CVS snapshots...), SquashFS 3.0. Finnix 88.0 will look a great deal like 87.0, but behind the scenes, a LOT has been done. As I mentioned before, PCI module autodetection has been completely rewritten to be much faster, "toram" and "testcd" are now more effective (in particular, "testcd" now tests the entire CD on a block level), Xen is now completely supported (both as a domU and now as a dom0, though no dom0 kernels will be distributed with the CD), and more.

I have finalized on which DOS disk I will be using for the "dos" profile. It is [FreeDOS ODIN](http://odin.fdos.org/) 0.7, which is essentially the DOS floppy equivalent of a LiveCD. I got the idea of including DOS after using a Caldera DR-DOS utility disk image that comes with Nero Burning ROM. Obviously I can't distribute DR-DOS, and FreeDOS itself does not directly distribute a non-installation disk, but thankfully I came across ODIN. It works just like the DR-DOS utility disk, even better in some places, and is only 900k compressed.

In non-development news, I have migrated some services from Sourceforge to in-house. The mailing list and bug system is gone, replaced by a forums system. Older news items have been backported from Sourceforge into the "Announcements" section of the blog, and the home page now points to this instead of Sourceforge. (New version announcements will continue to be copied to Sourceforge.) I am currently looking at integrating the snapshots system to announce to [CIA](http://cia.navi.cx/).

Oh, I guess you are wondering when 88.0 will be released. I'm thinking early August at this point, coinciding with [DEF CON](http://www.defcon.org/), which I will be attending for the 4th year. Nothing official, but I'll probably be handing out stacks of CDs. Let me know if you plan on attending.

If 4 months between releases is not good enough for you, remember that there are always the [snapshots](http://snapshots.finnix.org/), which are almost always (but not guaranteed to be) stable. Right now the uploads are triggered manually, every weekday or so. (I have many machines at work that I can test on, so I usually start uploading before I leave for work, download from work, then test.) So, at this point, if I uploaded it, it's a pretty good indication I expect it to at least boot.
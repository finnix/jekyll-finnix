---
categories:
- Development
date: 2006-03-30 06:12:47
layout: post
title: One More Feature for the Road
wp_id: 26
---
Kernel 2.6.16 has made the cut, and final CD images have been mastered. One final round of testing, and Finnix 87.0 should be released Friday!

One small new feature made it through at the last moment. One feature I always liked is in the Windows installation CDs. When you boot from the CD, it says something to the effect of "Press any key to boot from CD." If you don't press a key within a few seconds, the CD moves on to booting the first hard drive.

In previous versions of Finnix, if you did not type anything at the boot prompt, it would eventually just boot Finnix. Now, if no input is detected in 60 seconds, the CD simply boots the first hard disk. This way, you can reboot Finnix remotely, and have your normal OS load if you have a CDROM drive that likes to suck the CD back in during BIOS POST.

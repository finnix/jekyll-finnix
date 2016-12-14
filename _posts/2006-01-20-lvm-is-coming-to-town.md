---
id: 12
title: LVM is coming to town
date: 2006-01-20T00:09:13+00:00
author: Ryan Finnie
layout: post
guid: http://www.finnix.org/blog/2006/01/20/lvm-is-coming-to-town/
permalink: /2006/01/20/lvm-is-coming-to-town/
categories:
  - Development
  - Finnix
---
_It sees you when you're fscking, it knows /dev/hda..._ OK, bad joke.

One of the primary reasons for the re-incarnation of Finnix was LVM2 support. This came in the form of "apt-get install lvm2", and suited my purposes (if you knew you were on an LVM system, activating the volumes was as easy as "/etc/init.d/lvm start"), but I always meant to get around to making it a part of startup autodetection. In the next release, that will be possible. It'll scan for volumes, add to /etc/fstab and create a /mnt point (just like a normal scanned partition), and activate any LVM swap volumes. And of course there will be a "nolvm" flag, in case you want to shave 6/10ths of a second of bloat off the boot process for non-LVM systems.

`[*] Scanning for LVM volumes... VolGroup00/LogVol00 VolGroup00/LogVol01<br />
[*] Scanning for partitions and creating /etc/fstab... done<br />
[*] Activating swap... VolGroup00/LogVol01<br />
...<br />
root@tty1:~# mount /mnt/VolGroup00/LogVol00<br />
root@tty1:~#` 

This is real (not a mockup), but has had roughly 90 seconds of testing so far. Also: Fedora's default naming scheme for LVM volumes is boring, but there's not much Finnix can do about that.

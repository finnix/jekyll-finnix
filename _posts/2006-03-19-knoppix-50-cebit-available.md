---
author: Ryan Finnie
categories:
- Finnix
- Miscellany
date: 2006-03-19 20:29:00
guid: http://blog.finnix.org/2006/03/19/knoppix-50-cebit-available/
id: 21
layout: post
permalink: /2006/03/19/knoppix-50-cebit-available/
title: Knoppix 5.0 CeBIT Available
---
Yes, I'm announcing "the competition". Knoppix 5.0 was released at [CeBit](http://cebit.de/) this week. While it is not available on the main site yet, there is [a 3.5GB torrent](http://linuxtracker.org/torrents-details.php?id=1620) available of the DVD given out at the conference. It is the German version though, so for English audiences, you must type "knoppix lang=us" at the boot prompt. Beware though, isolinux is configured for a German keyboard layout, so to type a "=" sign, you must hit Shift-0 (zero). After that, everything should work as expected.

I downloaded and booted a copy, and it is rather slick. I also looked at the init scripts, to see what has changed and if anything can be ported to Finnix. The biggest change is udev support, which may eventually be rolled into Finnix, but at the moment I don't believe it is worth the extra startup time.

I was also reminded how much Finnix had diverged from Knoppix. As you may know, Finnix 84 and 85.x were "Knoppix remasters"; essentially Knoppix 4.0.2 without X functionality. Finnix 86.0 was a "rewrite", starting with vanilla Debian testing, and adding support to be booted from a CD. However, a large part of that functionality was in the form of porting Knoppix's startup scripts. In the course of the next few releases, more and more functionality was changed. Today, Finnix's initrd is 99% different from Knoppix's, and if you look at Finnix's startup script (/etc/init.d/finnix-autoconfig), you will notice it is quite different from Knoppix's (/etc/init.d/knoppix-autoconfig).

No word yet on a new Finnix release. A lot of development has happened since 86.2, but I'd still like to wait until kernel 2.6.16 is released before I go forward on a release.

---
id: 29
title: 'Finnix: On the Forefront of Ancient Hardware Technology'
date: 2006-04-02T18:59:38+00:00
author: Ryan Finnie
layout: post
guid: http://www.finnix.org/blog/2006/04/02/finnix-on-the-forefront-of-ancient-hardware-technology/
permalink: /2006/04/02/finnix-on-the-forefront-of-ancient-hardware-technology/
categories:
  - Finnix
  - Miscellany
---
For Finnix 87.0, I decided to compile the x86 kernel with i486 support. However, that made me think that I had never tested Finnix with anything less than i686 hardware. The two i586 machines I found worked great with Finnix (an AMD K6-300 and a Pentium 166), but I couldn't find an i486 machine. I ordered one from eBay (a Cyrix 486DX2-80 with PCI motherboard and 48MB RAM), but it didn't arrive in time before final ISO images were mastered.

It arrived Friday, but upon booting it, the kernel immediately segfaulted. Turns out, an i486 will not boot at all if the kernel is compiled with SMP support, even if it has "i486" support.

I thought about including a second non-SMP kernel with the distribution, but that adds another 14MB to the ISO size, for a feature that probably nobody will use. Instead, I took advantage of Finnix's new [overlay](http://www.finnix.org/Overlays) support, and created an overlay that had a new non-SMP kernel's modules in it. Then I re-created the initrd and added a "nosmp" kernel and modified the isolinux.cfg file. I booted the new modified CD and it worked great:

<pre>root@0:~# uname -a
Linux finnix 2.6.16-1-x86-nosmp-finnix #1 Sun Apr 2 05:26:53 PDT 2006 i486 GNU/Linux
root@0:~# cat /proc/cpuinfo
processor       : 0
vendor_id       : unknown
cpu family      : 4
model           : 0
model name      : 486
stepping        : unknown
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : no
cpuid level     : -1
wp              : yes
flags           :
bogomips        : 29.44</pre>

If you want to do the same, I uploaded the modified files and tarball as [finnix-87.0-nosmp.tar.bz2](http://prdownloads.sourceforge.net/finnix/finnix-87.0-nosmp.tar.bz2?download). Download the tarball and read the included README file. It takes about 5 lines of commands to extract the original Finnix ISO, extract the overlay into the tree, and re-create the modified tarball.

By the way, because of this, the next release of Finnix will have a kernel that is bumped back up to i586 minimum.

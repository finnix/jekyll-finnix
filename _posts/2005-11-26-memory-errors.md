---
id: 46
title: Memory Errors
date: 2005-11-26T14:11:23+00:00
author: Ryan Finnie
layout: post
guid: http://www.finnix.org/blog/2006/08/20/memory-errors/
permalink: /2005/11/26/memory-errors/
categories:
  - Finnix
  - Miscellany
---
Despite having a mac mini, I'm still doing Finnix development on the graphite G4. It's been very stable, up until last night, when I was compiling the latest and greatest kernel, I got the occasional failure like so:

<pre>CC drivers/pci/probe.o
include/asm/processor.h: In function 'pci_scan_child_bus':
include/asm/processor.h:186: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See &lt;url:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see &lt;url:file:///usr/share/doc/gcc-4.0/readme.bugs>.
make[2]: *** [drivers/pci/probe.o] Error 1
make[1]: *** [drivers/pci] Error 2
make: *** [drivers] Error 2</pre>

But upon, resuming the compile, the failed object would compile successfully. This happened several times, which suggested bad memory. I slept on it, and this morning, tried again:

<pre>CC [M] drivers/usb/misc/idmouse.o
fixdep: inclu`e/asm-generic/local.h: No such file or directory
make[3]: *** [drivers/usb/misc/idmouse.o] Error 2
make[2]: *** [drivers/usb/misc] Error 2
make[1]: *** [drivers/usb] Error 2
make: *** [drivers] Error 2</pre>

"inclu\`e"? Yep, that's bad ram. Too bad there's no memtestppc. I'll have to swap it out into a PC to test.

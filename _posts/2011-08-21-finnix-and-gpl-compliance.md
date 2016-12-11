---
id: 298
title: Finnix and GPL compliance
date: 2011-08-21T23:16:52+00:00
author: Ryan Finnie
layout: post
guid: http://blog.finnix.org/?p=298
permalink: /2011/08/21/finnix-and-gpl-compliance/
categories:
  - Finnix
---
Finnix is an open source product; it is comprised of many pieces of software under a variety of open source licenses, and the "glue" that holds everything in Finnix together is GPLv2, so the distribution itself is considered to be GPLv2 for convenience sake.

However, very little source is actually released by Finnix itself. The kernel sources and all Finnix-specific packages are available at [packages.finnix.org](http://packages.finnix.org/), but the majority of software included with Finnix is released binary-only. Believe it or not, this is done deliberately. Finnix is based on Debian, which has a long history of fastidious license reviews and source retention. The official line is "if you need sources, for 99% of the software in Finnix, Debian has already done the work for you".

However, that does not release Finnix from legal obligations. As detailed on the [Legal](http://www.finnix.org/Legal) page, Finnix complies with section 3(b) of the GPLv2, which requires a direct offer of source upon request if source is not provided directly with binaries. However, again, Debian does such a good job at source/licensing that nobody has yet to invoke this throughout Finnix's 11 year (and counting) history.

This method was chosen for practicality, not to avoid doing work. Indeed, it still takes a lot of work to prepare a Finnix release from a source compliance perspective. Years ago I wrote software called [damngpl](http://www.finnie.org/software/damngpl/) (name chosen with tongue firmly in cheek) to manage the various methods of making sure sources for all software in the Finnix userland are accounted for. The result is, for each Finnix release, a separate unreleased ISO of all sources for that release. (Finnix 102's source ISO was exactly 600 MiB, for example. By comparison, the released x86 binary CD was 114 MiB, and the PowerPC CD was 116 MiB.) These source ISOs are kept safe in several locations, and ready to be offered if needed.

All this leads to what I originally wanted to announce. While I had been doing this since Finnix 86.0's release in 2005, the original release of Finnix, 0.03 from 2000, did not have a source ISO available. Section 3(b) of the GPLv2 specifies that the written offer is valid for three years, but this is generally interpreted as from when the corresponding binaries are last offered from the releasing party. And Finnix 0.03 is actually still being released today (it is being distributed by the official mirror network).

Finnix 0.03 was based upon Red Hat Linux 6.1, and amazingly, The Internet does lose memory. ([As blogged about last year](http://blog.finnix.org/2010/11/07/finnix-iso-oddities/), several of Finnix's own public releases, mostly pre-releases, are presumed lost.) Red Hat Linux 6.1 sources were hard to find, and updates to RHL 6.1 were even harder. But in the end, I was able to collect SRPMs for every single package in Finnix 0.03. So now Finnix is able to account for sources for every piece of software in each of its 18 releases in its 11 year history.
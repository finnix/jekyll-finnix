---
id: 63
title: Finnix Updates
date: 2007-07-22T20:11:13+00:00
author: Ryan Finnie
layout: post
guid: http://blog.finnix.org/2007/07/22/finnix-updates/
permalink: /2007/07/22/finnix-updates/
categories:
  - Development
  - Finnix
tags:
  - trademark
---
Hi all. I haven't had the desire to work on Finnix much lately because of personal health issues, but hopefully there will be a release within a few weeks. Not much in terms of major changes, but just as a warning, the x86 CD will most likely be about 120MiB. 89.0 was released after Debian froze for the etch release, and 89.1 was released right after the etch release itself. That means that all libraries were finalized and there was very little overhead. Now that Debian lenny development is in full force, there are many cases of multiple version of libraries in Finnix, with some packages using older libraries and some using newer. That, combined with normal size creep means Finnix will be a little big these days. The kernel will most likely be based on 2.6.21, since there are some problems I haven't resolved yet with 2.6.22 and SquashFS. This version will probably also be the switch from UnionFS to AUFS, but I have a lot of testing to do before I'm comfortable with that migration. This is all behind the scenes of course, nothing should look different once you're booted into Finnix. The version will probably be 89.2, since again, nothing ground-breaking in the Finnix development itself.

On the trademark front, everything is now complete! Finnix is now a registered trademark. I'll be updating graphics on the site where appropriate.

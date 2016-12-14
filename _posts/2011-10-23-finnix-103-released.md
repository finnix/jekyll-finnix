---
id: 320
title: Finnix 103 released
date: 2011-10-23T00:00:24+00:00
author: Ryan Finnie
layout: post
guid: http://blog.finnix.org/2011/10/23/finnix-103-released/
permalink: /2011/10/23/finnix-103-released/
categories:
  - Announcements
  - Finnix
---
Finnix is a small, self-contained, bootable Linux CD distribution for system administrators, based on Debian testing. Today marks the release of Finnix 103, the nineteenth release of Finnix, and marks three months since the release of Finnix 102, and six years since the relaunch of Finnix 86.0 in 2005. Finnix 103 includes a new forensic mode, RNG entropy gathering, a minor kernel update, a large number of bug fixes, new packages and new minor features.

  * Home page: <http://www.finnix.org/>
  * Download: <http://www.finnix.org/Download>
  * Release notes: [http://www.finnix.org/Finnix\_103\_release_notes](http://www.finnix.org/Finnix_103_release_notes)
  * Free stickers! <http://www.finnix.org/Free_stickers>

## Forensic mode

Finnix 103 includes a new forensic mode. When booted with the "forensic" or "forensics" boot flags, Finnix changes its behavior to minimize the chance of loading suspect code or writing to suspect media. These changes include cryptographic hash verification of discovered Finnix CD media, locking block devices, and avoiding swap, LVM, RAID, crypt and network autodetection. For more information, see the [Forensics page on finnix.org](http://www.finnix.org/Forensics).

## Entropy generation added

Modern Linux distributions add to their random number generator (RNG) entropy pool by saving some random data before shutdown, and adding it back into the pool during startup. A LiveCD cannot normally do this, so Finnix includes a new feature to generate random data to be fed into the pool via a method that relies on the separation of a computer's CPU and RTC. By default 8 bytes are generated during each Finnix startup (due to the time it takes to generate data via this method), but a new utility wrapper, "finnix-generate-entropy" is included to generate a full pool's worth of entropy (currently 4096 bytes). For more information, see [this blog post on finnie.org](http://www.finnie.org/2011/09/25/introducing-twuewand/).

---
categories:
- Announcements
date: 2020-05-14 00:00:00-07:00
excerpt: After a 5 year hiatus, Finnix is back for its 20th anniversary.
excerpt_standalone: true
layout: post
title: Finnix 120 released... wait, what?
---
That's right: after a 5 year hiatus, Finnix — the LiveCD for system administrators and the oldest LiveCD in production — is back to celebrate its 20 year anniversary in 2020 with Finnix 120.

Finnix 120 is a complete overhaul, with a number of major changes (as well as too many minor changes to enumerate).  From the [Finnix 120 release notes](https://www.finnix.org/Finnix_120_release_notes):

* Finnix 120 is now a native 64-bit amd64 userland and kernel system.  For older 586/686/PowerPC support, [Finnix 109](https://www.finnix.org/Finnix_109_release_notes) is recommended as the last Finnix release which was well-supported on those 32-bit platforms.
* Both BIOS and UEFI booting are now available, with Secure Boot.
* Hundreds of new utility packages have been added.
* Automatic setup attempts of complex block device layouts have been removed, in favor of management via udisksctl with tab-completion.
* Other legacy features and boot modes have been discontinued or are no longer supported, in favor of core USB/CD booting.
* ISO size has increased (477 MiB, from 160 MiB), but the goal is to continue to keep it under the size of a CD-R.
* NEALE, the bespoke build system used by Finnix, has been discontinued.  Finnix is now built as a customized system based on the [debian-live](https://www.debian.org/devel/debian-live/) build software.

Please visit [finnix.org](https://www.finnix.org/) to download Finnix 120 today!

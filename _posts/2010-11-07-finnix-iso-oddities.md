---
categories:
- Miscellany
date: 2010-11-07 07:35:13
layout: post
title: Finnix ISO oddities
wp_id: 142
---
After the release of Finnix 100, I did a little housecleaning of the main dev box, and found some old/odd Finnix builds. I decided to gather the various ISOs in one place to preserve for the times. I may release these somehow, but for now I just wanted to make sure they were not lost, and to give you a glimpse of some unreleased software. This list also includes some builds that I know existed and would like to find, but are currently missing.

  * <tt>finnix-0.01.iso</tt> (circa 1999, missing) - The original build of Finnix. This was only given out to two other people, and is most likely lost forever.
  * <tt>finnix-0.02.iso</tt> (circa 1999/2000, missing) - Only given out to office staff at the ISP I worked at at the time. Also most likely lost forever.
  * <tt>knoppix-3.8.1rf-lvm2-crypt.iso</tt> (2005-04-17, 411 MiB) - A straight Knoppix remaster, with LVM2 and dm_crypt support added. This was the precursor to Finnix 84, and what got me interested in reviving the Finnix project back in 2005. Ripped from a CD I found lying on a mothballed Windows server in my employer's office server room, before we moved earlier this year.
  * <tt>finnix-84.iso</tt> (2005-04-20, 264 MiB) - Another Knoppix remaster, with much of the X environment (crudely) removed to save on space. Nothing in the ISO even mentioned "Finnix". This probably would have been another generic Knoppix remaster, but at one point I decided to revive the name "Finnix". Version "84" was chosen for no particular reason other than it had been over 5 years since the last (and first (and at the time only)) release of Finnix, and a high version number sounded good. This was technically released to the public, but never announced. I threw a torrent up on finnix.org so friends could download it, but the public never noticed.
  * <tt>finnix-85.0.iso</tt> (circa 2005, missing) - The next step after Finnix 84, only distributed to office staff. Likely lost forever.
  * <tt>finnix-85.1.iso</tt> (circa 2005, missing) - Ditto, most likely lost forever.
  * <tt>finnix-85.2.iso</tt> (2005-09-29, 178 MiB) - Further refinement and chopping from the Knoppix base. At this point it could fit on a Mini-CDR, and was distributed to office staff. Ripped from a Mini-CDR I found in my desk about a year ago.
  * <tt>finnix-85.3.iso</tt> (2005-10-01, 150 MiB) - Ditto.
  * <tt>finnix-86.0-pre1.iso</tt> (2005-10-09, 121 MiB) - The first public (pre-)release of "new" Finnix, and the first release since Finnix 0.03 built from the ground up to be "Finnix" (not a Knoppix remaster). Originally distributed via SourceForge.
  * <tt>finnix-86.0-pre2.iso</tt> (circa 2005, missing) - Originally distributed via SourceForge, but I deleted the SF archives at one point and didn't have a backup beforehand. May exist on mirrors somewhere.
  * <tt>finnix-86.0-pre3.iso</tt> (circa 2005, missing) - Ditto.
  * <tt>finnix-86.1-pre1.iso</tt> (2005-11-15, 100 MiB) - Originally distributed via SourceForge.
  * <tt>finnix-86.1-le.iso</tt> (2005-11-20, 429 MiB) - Finnix 86.1 Limited Edition. A special build containing both Finnix 86.1 and Finnix 0.03. Only distributed to friends/VIPs with a special numbered/signed printed CD. A maximum of 100 copies were planned to be made, only about 30 were distributed. This will probably never be released by me due to its (artificial) rarity.
  * <tt>finnix-light-sparc.iso</tt> (2007-08-14, 7.2 MiB) - "Finnix Light", an idea I toyed with under the Finnix name, it was merely a kernel and a decked out BusyBox install. The SILO boot profile name was "flight". I abandoned the idea due to the fact that, while I have Sparc hardware to test, it would have been a pain to keep it as a supported configuration.
  * <tt>finnix-486-92.1.iso</tt> (2008-11-24, 95 MiB) - A custom build of Finnix 92.1, with a 486-capable kernel. Ironically, the Linux kernel at the time had a bug that prevented most 486es from being bootable (probably fixed by now), and the idea was eventually scrapped.

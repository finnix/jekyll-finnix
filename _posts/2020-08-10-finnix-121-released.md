---
categories:
- Announcements
date: 2020-08-10 10:00:13-07:00
layout: post
title: Finnix 121 released
---
Today marks the release of [Finnix](https://www.finnix.org/) 121, the LiveCD for system administrators.  This release expands upon Finnix 120, and includes a number of fixes, new packages and new features.  From the [Finnix 121 release notes](https://www.finnix.org/Finnix_121_release_notes):

* Switched back to building against Debian testing
* Added packages:
    * [ranger](https://packages.debian.org/testing/ranger) (finnix/finnix#2)
    * [cpu-checker](https://packages.debian.org/testing/cpu-checker)
    * [edid-decode](https://packages.debian.org/testing/edid-decode)
    * [ipmitool](https://packages.debian.org/testing/ipmitool)
    * [lldpd](https://packages.debian.org/testing/lldpd)
    * [oathtool](https://packages.debian.org/testing/oathtool)
    * [sdparm](https://packages.debian.org/testing/sdparm)
    * [sipcalc](https://packages.debian.org/testing/sipcalc)
    * [socat](https://packages.debian.org/testing/socat)
    * [xorriso](https://packages.debian.org/testing/xorriso)
    * [zfs-fuse](https://packages.debian.org/testing/zfs-fuse)
* Removed packages:
    * sl (can be annoying; finnix/finnix#4)
    * cdbackup, dvd+rw-tools, wodim (replaced by xorriso)
    * lilo ([removed from Debian testing](https://qa.debian.org/excuses.php?package=lilo) due to GCC-10 FTBFS)
    * udisks2-vdo (removed from Debian; obsolete)
* serial-getty consoles are now usable
* Non-zero exit codes are now displayed in PS1
* Added "0" command for easier access to keyboard configuration (finnix/finnix#3)
* GRUB is now being used for both BIOS and UEFI booting
* Removed GRUB initial boot beep
* Re-added shared per-user SSH agents
* Fixed SSH remote access
* Enabled zram swap compression, 50% of physical RAM
* Release ISOs layouts are again being optimized for CD-ROMs
    * This has no negative (or positive) effect when the ISO is written to a USB key, but speeds up CD-ROM booting by placing all known files used during startup sequentially toward the end of the ISO

Please visit [finnix.org](https://www.finnix.org/) to download Finnix 121 today!

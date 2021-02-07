---
categories:
- Announcements
date: 2021-02-09 08:00:00-08:00
excerpt: Finnix 122 has been released today, containing a number of new features, fixes and new packages.
excerpt_standalone: false
headline_image: /blog-media/2021/Finnix_122_boot.png
layout: post
title: Finnix 122 released
---
<img src="{{ site.url }}{{ site.baseurl }}/blog-media/2021/Finnix_122_boot.png" alt="MECCA GPS time receiver" class="img-responsive img-rounded img-lg">

Today marks the release of [Finnix](https://www.finnix.org/) 122, the LiveCD for system administrators.  Expanding on Finnix 121 from six months ago, this release includes a number of fixes, new packages and new features.  From the [Finnix 122 release notes](https://www.finnix.org/Finnix_122_release_notes):

* Improved USB flash drive boot compatibility on older BIOSes
* Improved boot speed
* Lowered ISO size
* Added `finnix` getting started command
* Added `wifi-connect` helper script
* Manpage cache is now being generated, allowing for `man -k`/`apropos` ([finnix/finnix#9](https://github.com/finnix/finnix/issues/9))
* Redesigned boot splash screen
* Increased boot splash timeout from 15 seconds to 30 seconds
* Added packages:
    * [iozone3](https://packages.debian.org/testing/iozone3) ([finnix/finnix#8](https://github.com/finnix/finnix/issues/8))
    * [rover](https://packages.debian.org/testing/rover)
    * [iw](https://packages.debian.org/testing/iw)
    * [crda](https://packages.debian.org/testing/crda)
    * [wireless-regdb](https://packages.debian.org/testing/wireless-regdb)
    * [mscompress](https://packages.debian.org/testing/mscompress)
    * [apg](https://packages.debian.org/testing/apg)
    * [ftp](https://packages.debian.org/testing/ftp)
    * [ftp-ssl](https://packages.debian.org/testing/ftp-ssl)
    * [keyutils](https://packages.debian.org/testingkeyutils/)

Please visit [finnix.org](https://www.finnix.org/) to download Finnix 122 today!

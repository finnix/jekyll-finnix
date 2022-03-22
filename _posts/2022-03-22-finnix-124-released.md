---
categories:
- Announcements
date: 2022-03-22 10:10:00-07:00
excerpt: Finnix 124 has been released today, containing a number of new packages, features and fixes.
excerpt_standalone: false
headline_image: /blog-media/2022/Finnix_124_boot.png
layout: post
title: Finnix 124 released
---
<img src="{{ site.url }}{{ site.baseurl }}/blog-media/2022/Finnix_124_boot.png" alt="Finnix 124 boot screen" class="img-responsive img-rounded img-lg">

Today marks the release of [Finnix](https://www.finnix.org/) 124, the original utility live Linux distribution.  Expanding on Finnix 123 from six months ago, this release also celebrates the 22 year anniversary of the first public release of Finnix, version 0.03 on March 22, 2000.

Finnix 124 includes a number of fixes, new packages and new features:

  * `wifi-connect` helper utility will now display nearby access points if invoked without any command line options.
  * `ip=` kernel command line network configuration now supports netmasks in addition to prefix lengths.
  * Added a pure Python `strings` implementation. Explanation from the commit:
    I had avoided including `strings` because, while it's incredibly useful, it's the only desirable utility in the binutils package, which otherwise includes a bunch of compilation-related utilities, and the package itself is quite large.
    So in the words of the "my mechanics" YouTube channel, I make a new one! It's not a 100% complete reimplementation of GNU binutils' `strings`, but is fine for casual binary checking.
    This is also set up so that if you do `apt install binutils` in the live environment, its `strings` will take precedence over the Python version.
  * RISC-V (riscv64) unofficial build support added, in addition to amd64, i386, arm64, armhf, ppc64el, s390x. (Though as a reminder, AMD64 is the only officially supported architecture with released ISOs. For more information, see [Platform support on Finnix](https://github.com/finnix/finnix-docs/blob/main/platforms.md).)
  * Replaced the running systemd finnix.target with the more traditional multi-user.target. This is not noticeable in regular live environment use, but makes it easier for people expanding upon Finnix.
  * Added new packages:
    * [inxi](https://packages.debian.org/testing/inxi) ([finnix/finnix#23](https://github.com/finnix/finnix/issues/23))
    * [rmlint](https://packages.debian.org/testing/rmlint) ([finnix/finnix#24](https://github.com/finnix/finnix/issues/24))
    * [nwipe](https://packages.debian.org/testing/nwipe) ([finnix/finnix#25](https://github.com/finnix/finnix/issues/25))
    * [rename](https://packages.debian.org/testing/rename) ([finnix/finnix#26](https://github.com/finnix/finnix/issues/26))
    * [gdu](https://packages.debian.org/testing/gdu) ([finnix/finnix#27](https://github.com/finnix/finnix/issues/27))
    * [pwgen](https://packages.debian.org/testing/pwgen)
    * [sntp](https://packages.debian.org/testing/sntp)
    * [lz4](https://packages.debian.org/testing/lz4)
    * [lzip](https://packages.debian.org/testing/lzip)
    * [lzop](https://packages.debian.org/testing/lzop)
    * [zstd](https://packages.debian.org/testing/zstd)
  * Removed packages:
    * pppoeconf (Buggy, removed from Debian)
    * crda (Obsolete, removed from Debian)
  * Upstream Debian package updates
  * Many minor fixes and improvements

Please visit [finnix.org](https://www.finnix.org/) to download Finnix 124 today!

---

  * [finnix-124.iso](https://www.finnix.org/releases/124/finnix-124.iso) • 455 MiB ISO image • AMD64
  * [Release data](https://github.com/finnix/finnix-docs/blob/main/releases/124.json)
  * [BitTorrent download](https://www.finnix.org/releases/124/finnix-124.iso.torrent)
  * [OpenPGP signature](https://www.finnix.org/releases/124/finnix-124.iso.gpg)
  * SHA256 checksum: `ecc019eb2fb1cc6612021e3b0108801367baadc5b2704852ab0f3fb373932287`

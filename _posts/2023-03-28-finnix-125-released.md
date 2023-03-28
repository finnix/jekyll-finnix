---
categories:
- Announcements
date: 2023-03-28 12:23:00-07:00
excerpt: Finnix 125 has been released today, containing a number of new packages, features and fixes.
excerpt_standalone: false
headline_image: /blog-media/2023/Finnix_125_boot.png
layout: post
title: Finnix 125 released
---
<img src="{{ site.url }}{{ site.baseurl }}/blog-media/2023/Finnix_125_boot.png" alt="Finnix 125 boot screen" class="img-responsive img-rounded img-lg">

Today marks the release of [Finnix](https://www.finnix.org/) 125, the original utility live Linux distribution. Finnix 125 includes a number of fixes, new packages and new features:

  * Linux kernel 6.1 (Debian 6.1.0-6)
  * New packages: 2048, aespipe, iperf3 ([finnix/finnix#37](https://github.com/finnix/finnix/issues/37)), ncdu, netcat-traditional, ninvaders, vitetris
    * Note that netcat-openbsd continues to be included and is the default `nc`
  * `apt update` will now download both "testing" and "unstable" indices, to allow for installing packages which may currently be hinted out of testing. Apt pinning is configured so testing will continue to be preferred to unstable, however.
  * Updated to memtest86+ 6.10, which now includes a UEFI version which is included in the "Utilities" boot submenu when booting on a UEFI system. Note that this is not signed and will not work with Secure Boot.
  * `7z` will invoke the installed `7zr` program, unless the user explicitly installs "p7zip-full"
  * Upstream Debian package updates
  * Many minor fixes and improvements
  * Note for people who embed Finnix in other systems: `boot=live` is no longer needed to be passed as a kernel boot command line.

Please visit [finnix.org](https://www.finnix.org/) to download Finnix 125 today!

---

  * [finnix-125.iso](https://www.finnix.org/releases/125/finnix-125.iso) • 489 MiB ISO image • AMD64
  * [Release data](https://github.com/finnix/finnix-docs/blob/main/releases/125.json)
  * [BitTorrent download](https://www.finnix.org/releases/125/finnix-125.iso.torrent)
  * [OpenPGP signature](https://www.finnix.org/releases/125/finnix-125.iso.gpg)
  * SHA256 checksum: `d7f6b845c39ba0ee41075fa9a5defa4ef449f9f4fc0877bdb6afb74b8bfefb6b`

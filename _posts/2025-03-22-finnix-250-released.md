---
categories:
- Announcements
date: 2025-03-22 10:00:00-07:00
excerpt: To celebrate the 25 year anniversary of Finnix, today marks the release of Finnix 250!
excerpt_standalone: false
headline_image: /blog-media/2025/Finnix_250_boot.png
layout: post
title: Finnix 250 released
---
<img src="{{ site.url }}{{ site.baseurl }}/blog-media/2025/Finnix_250_boot.png" alt="Finnix 250 boot screen" class="img-responsive img-rounded img-lg">

Today is a very special day: March 22 is the 25 year anniversary of the first public release of [Finnix](https://www.finnix.org/), the oldest live Linux distribution still in production. Finnix 0.03 was released on March 22, 2000, and to celebrate this anniversary, I'm proud to announce the 35th Finnix release, [Finnix 250](https://www.finnix.org/)!

Besides the continuing trend of Finnix version number inflation (the previous release was Finnix 126), Finnix 250 is simply a solid regular release, with the following notes:

* Linux kernel 6.12 (Debian 6.12.17-1)
* Made automatic per-user shared ssh-agent functionality more reliable
* Added packages: util-linux-extra
* Removed packages: reiserfsprogs, reiser4progs (ReiserFS removed from Linux kernel)
* Boot initramfs now checks for build-specific media (will no longer load the first thing it sees which looks vaguely Finnix-like)
* htop display improvements (primarily better display of large numbers of CPU cores)
* Upstream Debian package updates
* Many minor fixes and improvements

Please visit [finnix.org](https://www.finnix.org/) to download Finnix 250 today!

---

* [finnix-250.iso](https://www.finnix.org/releases/250/finnix-250.iso) • 528 MiB ISO image • AMD64
* [Release data](https://github.com/finnix/finnix-docs/blob/main/releases/250.json)
* [BitTorrent download](https://www.finnix.org/releases/250/finnix-250.iso.torrent)
* [OpenPGP signature](https://www.finnix.org/releases/250/finnix-250.iso.gpg)
* SHA256 checksum: `37920e858f2339f0602ee07624ccf6fc2b38e27c2822c4be367eb118045f367a`

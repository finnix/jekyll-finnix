---
categories:
- Announcements
date: 2024-07-04 10:00:00-07:00
excerpt: Finnix 126 has been released today, containing a number of new packages, features and fixes.
excerpt_standalone: false
headline_image: /blog-media/2024/Finnix_126_boot.png
layout: post
title: Finnix 126 released
---
<img src="{{ site.url }}{{ site.baseurl }}/blog-media/2024/Finnix_126_boot.png" alt="Finnix 126 boot screen" class="img-responsive img-rounded img-lg">

Today marks the release of [Finnix](https://www.finnix.org/) 126, the original utility live Linux distribution. Finnix 126 includes a number of fixes, new packages and new features:

* Linux kernel 6.8 (Debian 6.8.12-1)
* New packages: libc6-i386 ([finnix/finnix#35](https://github.com/finnix/finnix/issues/35); not directly usable but allows for running certain i386 binaries in Finnix's amd64 userland)
* Added `0` kernel command line option which does the same as the `0` (`locale-config`) utility, but during early boot and before shell prompts
* Upstream Debian package updates
* Many minor fixes and improvements

This is the first Finnix release to contain additional "supply chain" assurances. The release was built on a public CI platform (GitHub Actions), with the ISO (`.disk/build_info`) pointing to the [URL of the build run](https://github.com/finnix/finnix-live-build/actions/runs/9750597178) which lists a SHA256 checksum of the ISO and links to [the exact commit used to build it](https://github.com/finnix/finnix-live-build/tree/8485958229824508c058709df9b571786a5119c7). Additionally, the build provides [an attestation of the build artifacts](https://github.com/finnix/finnix-live-build/attestations/1222488) through GitHub's [new attestation functionality](https://github.blog/2024-05-02-introducing-artifact-attestations-now-in-public-beta/).

Note that this release was made a few days after the [OpenSSH CVE-2024-6387 vulnerability announcement](https://www.qualys.com/regresshion-cve-2024-6387/), and to be clear, Finnix 126 does include a fixed version (Debian 9.7p1-7).

Please visit [finnix.org](https://www.finnix.org/) to download Finnix 126 today!

---

* [finnix-126.iso](https://www.finnix.org/releases/126/finnix-126.iso) • 498 MiB ISO image • AMD64
* [Release data](https://github.com/finnix/finnix-docs/blob/main/releases/126.json)
* [BitTorrent download](https://www.finnix.org/releases/126/finnix-126.iso.torrent)
* [OpenPGP signature](https://www.finnix.org/releases/126/finnix-126.iso.gpg)
* SHA256 checksum: `a74173bdf1198eafb01e52de35e08e0096587baaef8f258dd2ed66348b3fb3a1`

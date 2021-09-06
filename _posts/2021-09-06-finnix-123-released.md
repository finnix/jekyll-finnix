---
categories:
- Announcements
date: 2021-09-06 08:00:00-07:00
excerpt: Finnix 123 has been released today, containing a number of new packages, features and fixes.
excerpt_standalone: false
headline_image: /blog-media/2021/Finnix_123_boot.png
layout: post
title: Finnix 123 released
---
<img src="{{ site.url }}{{ site.baseurl }}/blog-media/2021/Finnix_123_boot.png" alt="Finnix 123 boot screen" class="img-responsive img-rounded img-lg">

Today marks the release of [Finnix](https://www.finnix.org/) 123, the LiveCD for system administrators.  Expanding on Finnix 122 from six months ago, this release includes a number of fixes, new packages and new features.  From the [Finnix 123 release notes](https://www.finnix.org/Finnix_123_release_notes):

* Added kernel command line "sshd" and "passwd" options, example: "sshd passwd=foo", "sshd passwd=root:foo passwd=finnix:bar"
* The machine ID is now, when possible, stable across reboots and being generated from the DMI. This is used for e.g. the DHCP client ID, so multiple reboots should no longer cycle through dynamic IPs on a network.
* The `finnix` command now has instructions for how to enable ZFS support
* Added a basic command-not-found handler; e.g. trying `ftp` will point out `lftp`, and will provide instructions for installing if desired explicitly.
* Added manpages for Finnix-specific commands (`wifi-connect`, `locale-config`, etc).
* Added packages: [jove](https://packages.debian.org/testing/jove)
* Removed packages: ftp, ftp-ssl, zile
* Includes package updates from upstream Debian. Normally Finnix tracks Debian testing, but as Finnix 123 was released shortly after Debian 11 "bullseye", it is being used as upstream directly.
* Plus many minor fixes and build enhancements.

Please visit [finnix.org](https://www.finnix.org/) to download Finnix 123 today!

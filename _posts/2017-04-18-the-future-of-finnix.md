---
date: 2017-04-18 14:47:36-07:00
excerpt: An update on the status of Finnix and its plans going forward.
layout: post
title: The future of Finnix
---
Finnix has a unique place in history.
The project was started in 1999, with its first public release in March 2000, making it one of the oldest LiveCDs (predated by DemoLinux and immediately preceded by the Linuxcare Bootable Toolbox).
Indeed, Finnix even predated the term "LiveCD".
It's currently the oldest actively maintained LiveCD distribution.

However, you may notice that the last release was in June 2015, in contrast to the usual release frequency of once or twice per year.
I just wanted to let Finnix users know that the project is still expected to be updated, albeit with some changes, hopefully for the better.

---

**EFI support**: In contrast to a few years ago, an increasing number of (mostly mass consumer) computers these days are EFI only, and do not have a legacy BIOS bootloader.
Finnix currently uses isolinux for the x86 bootloader, which precludes EFI support.
I am planning on switching to the GRUB bootloader which will allow for EFI boot support.

**AMD64 userland and single kernel**: Finnix's main x86 ISO currently contains a 32-bit userland and two kernels: a 32-bit and a 64-bit kernel.
This allows for the most flexibility when working on x86 systems; 32-bit CPUs/userlands are supported, and 64-bit userlands can be chrooted into by booting the 64-bit kernel, even though the CD userland is 32-bit.

However, modern kernels are very large; and two built-in kernels take up a good majority of the space on a Finnix CD.
AMD64 CPUs have been in consumer usage for 13 years now, and for most tasks, a single AMD64 kernel and 64-bit userland will be sufficient.
For working with AMD64 systems with 32-bit userlands (which are still a common minority), this will still be supported.

Of course, this means future main Finnix releases will not support CPUs released before 2004 (and even some 32-bit CPUs released after that), but for such "classic" systems, older Finnix releases will still be usable for most tasks.
In addition, Project [NEALE](https://www.finnix.org/Project_NEALE) will still be capable of building Finnix CDs with a 32-bit kernel and userland.
And indeed, NEALE is already capable of building pure-AMD64 ISOs and has been for years, so this is not much of a change from a development perspective.

**Upstream Debian kernels**: Since 2005, Finnix has used kernels based on Debian, but modified out of necessity.
This was usually to add support for code needed for an efficient LiveCD experience which had not been upstreamed (cloop, then SquashFS; UnionFS, then AUFS, then OverlayFS).
As of Finnix 111, the main requirements are SquashFS and OverlayFS, both of which are now upstreamed into the vanilla kernel, so there is no technical need for patched kernels.

Finnix still used modified kernels, mostly to remove modules which are not needed on a text-mode LiveCD (such as sound and video modules) to save space.
However, creating and packaging modified kernels is a time and labor intensive process, and with the space saved by only shipping one kernel on the CD, removing modules to save space is no longer a great concern.
As such, future Finnix releases will use unmodified Debian-based kernels.

(Sadly, this also means the end of the custom Finnix kernel CPU logos displayed on initial boot.)

**systemd init**: Finnix currently uses runit as a system init, which was small and let me sidestep sysvinit and Debian's distro rc assumptions.
(Prior to runit, Finnix build procedures involved cutting out most of the sysvinit rc functionality and putting Finnix replacements in.)
But it's very much a manual process, and as all distros are or are in the process of transitioning to systemd, now would be a good time to do the same.

systemd is large and has a reputation of wanting to consume everything, but as I've found out with a few days of research and testing, it's actually rather conducive to distribution management.
For example, one thing Finnix needs to be able to do is attempt DHCP on all network interfaces, but not block on it (getting to the command prompt quickly is the most important consideration).
I was able to quickly write a service which depended on systemd-udev-settle.service, ensuring all boot interfaces were available, write interfaces.d definitions and trigger starts of ifup@$INT.service without blocking on the getty process.
It even has the ability to pivot-root back to an initramfs at the end of system shutdown, something I needed to patch manually into runit.

**Size bloat**: Finnix's main stated goal is to be a small -- but useful -- utility LiveCD.
To keep the size down and remain a quick option for download, maximum size goals are attempted.
This was originally 100MB, and then for years the stated target was under 185MB -- the size of a Mini CD.
(This was mostly an arbitrary designation as Mini CDs were never widely popular.)

Finnix releases have always been small, but have included a lot of semi-hand optimization to keep the size down.
For example, the mastering process has a trick which is to decompress all .gz files, then to "recompress" them as gzip level 0 (which essentially adds a small header to the uncompressed file).
This sounds counterintuitive, but allows the XZ-compressed root filesystem to more efficiently compress that data later on.

In the interest of ease of maintenance and natural upstream size bloat, the new target is to keep Finnix releases under 300MB.
This is unlikely to be approached any time soon -- Finnix 111's x86 CD is 160MB, and the removal of a second kernel as mentioned above will allow for size concessions in other places -- but it's a good goal to allow for future expansions.

**PowerPC discontinuation**: Years ago, I attempted to discontinue Finnix for the PowerPC, but quickly learned there were a number of PowerPC fans who relied on Finnix.
I re-introduced the architecture, but with a caveat that it would not be a release blocker (i.e. if a large bug were discovered which affected PowerPC close to release, that particular release would not get PowerPC support).
That ended up never happening, but it was still policy.

However, things in the last year have complicated development.
Mainly, [Debian has announced it is dropping PowerPC from its next release](https://lists.debian.org/debian-devel-announce/2016/10/msg00008.html), and has already removed binary-powerpc from its testing line (which Finnix uses as a base).
[NEALE](https://www.finnix.org/Project_NEALE) builds still work against Debian unstable ([neale-ppc-unstable-standard](https://ci.finnix.org/dsari/neale-ppc-unstable-standard/), [neale-ppc-unstable-minimal](https://ci.finnix.org/dsari/neale-ppc-unstable-minimal/), though even unstable's PowerPC future is uncertain.

Finnix for PowerPC will continue to be buildable via NEALE using unstable as long as this is possible, and again, older Finnix releases will still be usable if you need to work on a PowerPC system.

Once a new Finnix release is made, I plan on rearranging the front page to highlight the latest working release for any particular architecture.

**Mirror updates**: The [Finnix mirror network](https://mirrors.finnix.org/) currently mirrors all Finnix releases, going back to version 0.03 back in 2000, and the total mirror size is about 8GB.
I plan on splitting this up into two sets of mirrors, one which contains all historical releases, and one which contains the last 2 releases, plus the last usable release for discontinued architectures as mentioned above.
Mirror administrators can then choose if they want to mirror everything, or just the most downloaded releases.

---

I've fixed all of the problems which have been preventing [NEALE builds](https://ci.finnix.org/dsari/) from completing in the last 9 months, and will be starting main development on this new iteration of Finnix, hopefully with a release later in the year.

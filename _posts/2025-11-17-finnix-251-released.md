---
categories:
- Announcements
date: 2025-11-17 10:00:00-08:00
excerpt: Finnix 251 has been released today, including new official OCI / Docker images, and containing new packages, features and fixes.
excerpt_standalone: false
headline_image: /blog-media/2025/Finnix_251_boot.png
layout: post
title: Finnix 251 released
---
<img src="{{ site.url }}{{ site.baseurl }}/blog-media/2025/Finnix_251_boot.png" alt="Finnix 251 boot screen" class="img-responsive img-rounded img-lg">

Finnix is a Linux-based utility live distribution.
Write it to a USB flash drive or burn it to a CD, boot it, and you're seconds from a root prompt with hundreds of utilities available for recovery, maintenance, testing and more.
Finnix 251 has been released today, including new official OCI / Docker images, and containing new packages, features and fixes.

---

Finnix 251 is the first release to distribute official OCI container images.
The official Finnix container contains all the same software as the ISO release, and may be launched from Podman, Docker, Kubernetes, etc.

```shell
docker run -it --rm finnix/finnix

podman run -it --rm docker.io/finnix/finnix:latest

kubectl run finnix-$(uuidgen | cut -b -4 | tr A-Z a-z) --image=finnix/finnix --restart=Never -it --rm
```

This is particularly useful for Kubernetes users, giving you a quick utility shell in the namespace of your choice.
The `finnix/finnix:latest` container currently includes architecture support for amd64, arm64 and riscv64.

Otherwise, Finnix 251 is a regular semiannual utility release:

* Linux kernel 6.16 (Debian 6.16.12-2)
* Added packages: dc3dd
* Upstream Debian package updates
* Many minor fixes and improvements

Please visit [finnix.org](https://www.finnix.org/) to download Finnix 251 today!

---

* [finnix-251.iso](https://www.finnix.org/releases/251/finnix-251.iso) • 577 MiB ISO image • AMD64
* [Release data](https://github.com/finnix/finnix-docs/blob/main/releases/251.json)
* [BitTorrent download](https://www.finnix.org/releases/251/finnix-251.iso.torrent)
* [OpenPGP signature](https://www.finnix.org/releases/251/finnix-251.iso.gpg)
* SHA256 checksum: `a635a75a155d8640956c5640fc49268b4a89ce7013fdc7d19f1dfdc8529e9a9e`

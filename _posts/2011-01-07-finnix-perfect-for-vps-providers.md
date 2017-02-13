---
date: 2011-01-07 08:12:29
layout: post
title: Finnix -- perfect for VPS providers
wp_id: 205
---
<img src="/blog-media/2010/12/finnix-boot-vps.png" alt="" title="finnix-boot-vps" width="94" height="86" style="float: right; margin-left: 0.5em; margin-bottom: 0.5em;" />

Finnix is a popular console Linux-based utility LiveCD, and is used by system administrators every day for tasks such as system maintenance and recovery, network testing, security auditing, and more. Many people and organizations rely on Finnix to help with their jobs (and their hobbies).

Finnix has had a long history of virtualization support as well. It recognizes if it is being booted in a Xen or User Mode Linux (UML) environment, and will make the necessary modifications on the fly to run correctly. Early releases of Finnix even included a package called Finnix-on-Finnix, a proof of concept system that could boot itself as a guest of itself using a UML container.

Today, Finnix is used by several Virtual Private Server (VPS) providers, such as [Linode](https://www.linode.com/) and [Panix](http://www.panix.com/), to provide their customers with the ability to quickly and easily boot Finnix in their virtual guest environments. Once booted, customers can recover lost passwords or unbootable systems, install custom Linux distributions, and much more. Finnix is well suited for this task, and customers love having this ability.

To that end, [I have created a guide specifically for VPS providers](https://www.finnix.org/Finnix_for_VPS_providers), explaining how to integrate Finnix with your VPS management platform. If you are a VPS provider, please visit this guide and consider offering Finnix as a service for your customers. If you would like assistance with deploying Finnix as a recovery distribution, please email ryan@finnie.org and I will be happy to help. If you are a VPS customer who would like your VPS provider to offer Finnix as a system administration convenience, please let them know, and direct them to this post for more information.

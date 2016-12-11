---
id: 69
title: Finnix 92.0 coming soon
date: 2008-06-14T17:01:29+00:00
author: Ryan Finnie
layout: post
guid: http://www.finnix.org/blog/?p=69
permalink: /2008/06/14/finnix-920-coming-soon/
categories:
  - Development
  - Finnix
---
Finnix 92.0 will be released soon. It will have a new 2.6.25 kernel, updated software, and, most visibly, a new boot menu.

There have been suggestions for a new boot menu for awhile now. I liked the idea _in theory_, but there were various problems with most implementations (no graphics; graphics, but no fallback to text mode; no easy way to add boot options, such as toram, testcd, etc; no way to default to 64-bit boot options). Debian's recent [announcement of debian-installer for lenny beta 2](http://lists.debian.org/debian-devel-announce/2008/06/msg00002.html) introduced a new installer boot menu system based on bootmenu.c32, which looked very nice and solved most of the problems I mentioned. However, no default 64-bit option on multi-arch CDs, which the announcement mentioned and lamented.

I used Debian's configs as a base for a Finnix test. The results were very nice, and I was ready to do as Debian did and accept that the improvements were worth the loss of 64-bit autodetection. However, an acquaintance encouraged me to look into it ("Sounds like it's time for some OPEN SOURCE MAGIC"), and within a few hours, I had a working patch.

[The debian-installer guys loved it](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=485656) and had the patch applied within an hour, and as well, it will be in Finnix 92.0. Here's a development screenshot:

[<img src="/blog-media/2008/06/finnix_dev_boot_menu1-300x225.png" alt="" title="Finnix dev boot menu" width="300" height="225" class="alignnone size-medium wp-image-71" srcset="/blog-media/2008/06/finnix_dev_boot_menu1-300x225.png 300w, /blog-media/2008/06/finnix_dev_boot_menu1.png 640w" sizes="(max-width: 300px) 100vw, 300px" />](/blog-media/2008/06/finnix_dev_boot_menu1.png)
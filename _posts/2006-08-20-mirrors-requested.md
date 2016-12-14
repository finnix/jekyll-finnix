---
author: Ryan Finnie
categories:
- Finnix
- Miscellany
date: 2006-08-20 19:23:01
guid: http://blog.finnix.org/2006/08/20/mirrors-requested/
id: 53
layout: post
permalink: /2006/08/20/mirrors-requested/
title: Mirrors Requested
---
Due to SourceForge problems, for 88.0 I secured primary mirroring with [OSU Open Source Lab](http://osuosl.org/) (thanks again!), and will not be using SourceForge for future releases. However, I am looking for secondary mirror sites. Here are the requirements:

  * Decent connectivity (DS3 or higher)
  * 24-hour availability (occasional maintenance downtime is fine, I'm talking about excluding "available 9-5" sites)
  * Enough storage space and aggregate transfer for future growth, see below
  * Ability to rsync from the main archive at least daily

Here is how things are looking for the archive currently:

  * 1.3GiB currently, growing at an average of 1.5GiB per year
  * 200GiB transfer per month, should not exceed 400GiB per month in coming years
  * Releases quarterly on average
  * Mostly compressed content in archives
  * Current archives can be browsed at <http://ftp.osuosl.org/pub/finnix/>; "current" is a symlink to the current release directory

If you are interested in providing mirror services, please email ryan@finnie.org. Thank you very much.

---
date: 2022-02-13 16:13:17-08:00
excerpt: A promised update of documentation and release data is now available. The
  finnix-docs repository has a number of pieces of current documentation which have
  been ported over from the old Finnix wiki.
excerpt_standalone: false
layout: post
title: Finnix documentation, release data available
---
As a quick follow-up to the [previous post in October](https://blog.finnix.org/2021/10/01/new-finnix-web-site-launched/), a promised update of documentation and release data is now available.
The [finnix-docs repository](https://github.com/finnix/finnix-docs) has a number of pieces of current documentation which have been ported over from the old Finnix wiki.

In addition, [release data is now available](https://github.com/finnix/finnix-docs/tree/main/releases) in a consistent machine-parsable JSON format.
When Finnix releases are made, a number of third party new and review sites would pick up on the announcement, and extract data from the release notes and software package lists on the wiki.
(And in the package lists' case, it was literally a text dump inside a wiki article.)

This new system should be more useful for data aggregators.
It is expected that the blog post will be the canonical announcement page, and all additional data can be extracted programatically from the finnix-docs repository.
This includes all prior Finnix releases, going back to Finnix 0.03 in 2000.

Finnix 124 will likely be released in the next few weeks, likely in March, but I wanted to make this announcement ahead of time to allow sites which relied on the old wiki site to switch over their processes ahead of the Finnix 124 release.
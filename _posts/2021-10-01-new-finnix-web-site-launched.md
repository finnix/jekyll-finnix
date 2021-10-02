---
date: 2021-10-01 18:42:42-07:00
excerpt: finnix.org has an all new design.
excerpt_standalone: true
layout: post
title: New Finnix web site launched
---
For the past 15 years, [the main Finnix web site, finnix.org](https://www.finnix.org/) had been a MediaWiki site, being used as a CMS.
Actually, for the first few years, it was a public wiki which anyone could edit, but spammers ruined that.
But as of today, the site has been relaunched, as a single, simple HTML page which provides the essential information to download and use Finnix.

There were a few reasons I wanted to do this:

  * The vast majority of the information on the old site just wasn't used.
    Almost all people visiting finnix.org were just there for one purpose: to download Finnix.
    The new site puts that front and center.
  * The vast majority of the information on the old site just wasn't *useful*.
    A lot of it pertained to old Finnix releases, especially releases before the relaunch in 2020.
    Some of it was bordering on archaeological, such as User Mode Linux information, or how to make USB thumb drives bootable by emulating USB Zip drives.
  * The old site was the last remaining PHP site I was maintaining, and moving to a static site means one less bit of third-party software to maintain.

I do plan on utilizing the (currently placeholder) [finnix-docs repository on GitHub](https://github.com/finnix/finnix-docs) to add back some (relevant) documentation in the future.
I will also be using the repository to have a source of machine-readable Finnix release information, including package information in each release.
There are several sites which track Finnix releases and I want to make it even easier for them.
Expect that update sometime before the release of Finnix 124 early next year.

As for the previous site, all content has been preserved as [a MediaWiki dump on archive.org](https://archive.org/details/wiki-finnix), as well as [via the Wayback Machine](https://web.archive.org/web/20211001205027/https://www.finnix.org/).
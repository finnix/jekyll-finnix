---
author: Ryan Finnie
categories:
- Finnix
date: 2011-09-18 02:36:49
guid: http://blog.finnix.org/2011/09/18/geoip-support-added-to-mirror-redirector/
id: 309
layout: post
permalink: /2011/09/18/geoip-support-added-to-mirror-redirector/
title: GeoIP support added to mirror redirector
---
All direct links to ISOs (on the [home page](http://www.finnix.org/) for example; URLs that begin with <http://www.finnix.org/releases/>) redirect the user to a mirror. In the past, this redirector was purely random, with a weight added to the randomness to prefer larger capacity mirrors to smaller mirrors.

The redirector now takes GeoIP location information into consideration when possible. It increases the chances that the user is redirected to a geographically close mirror. Weighted randomness is still a consideration, so you will not be redirected to the closest mirror every time, but the GeoIP distance adds weight to closer mirrors.

A full list of Finnix mirrors is available [here](http://www.finnix.org/Mirrors).

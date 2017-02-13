---
date: 2011-09-18 09:36:49
layout: post
title: GeoIP support added to mirror redirector
wp_id: 309
---
All direct links to ISOs (on the [home page](https://www.finnix.org/) for example; URLs that begin with <https://www.finnix.org/releases/>) redirect the user to a mirror. In the past, this redirector was purely random, with a weight added to the randomness to prefer larger capacity mirrors to smaller mirrors.

The redirector now takes GeoIP location information into consideration when possible. It increases the chances that the user is redirected to a geographically close mirror. Weighted randomness is still a consideration, so you will not be redirected to the closest mirror every time, but the GeoIP distance adds weight to closer mirrors.

A full list of Finnix mirrors is available [here](https://www.finnix.org/Mirrors).

---
id: 30
title: apt-get Broken in 87.0
date: 2006-04-03T03:17:15+00:00
author: Ryan Finnie
layout: post
guid: http://blog.finnix.org/2006/04/03/apt-get-broken-in-870/
permalink: /2006/04/03/apt-get-broken-in-870/
categories:
  - Announcements
  - Finnix
---
A rather nasty bug in unionfs for 2.6.16 has made installing via apt-get impossible. However, there is a workaround. You must move /var/lib/apt and /var/cache/apt to /tmp and reconfigure apt to use these new directories. A script has been released that makes this easier. Simply do:

<pre># sh &lt;(curl <a href="http://www.finnix.org/files/scripts/apt-get-unionfs-workaround">http://www.finnix.org/files/scripts/apt-get-unionfs-workaround</a>)</pre>

This requires about 15MB of memory available, and should be done _before_ an <tt>apt-get update</tt>, otherwise it will take up another 15MB of memory.

Let this be a lesson never to use CVS development snapshots (unionfs 1.1.3 does not compile against 2.6.16), despite the maintainers assuring that it's "stable".

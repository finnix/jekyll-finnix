---
id: 17
title: The future is now!
date: 2006-01-30T02:31:34+00:00
author: Ryan Finnie
layout: post
guid: http://blog.finnix.org/2006/01/30/the-future-is-now/
permalink: /2006/01/30/the-future-is-now/
categories:
  - Development
  - Finnix
---
So, I just found out about this new peripheral called a "mouse". Appearantly you no longer have to be confined to using a light pen; instead, you move a rodent-shaped device over your desk, and a triangle-shaped cursor mimics your moves on the compuscreen. Quite a radical idea...

Anyways, somebody used [finnix-hwsubmit](http://www.finnix.org/Help#finnix-hwsubmit) to submit a report that said everything worked fine, but there was no mouse support. Now, normally I don't use the mouse that often (on the desktop I use fluxbox, which is rather keyboard-friendly), so I didn't even consider gpm support for Finnix. Plus, with kernel 2.4, it used to be annoying setting up mouse support (PS2 port vs USB, PS2 vs ImPS2 protocol, etc), but kernel 2.6 makes it a lot easier. Now, everything is routed through /dev/input/mice, which simulates an ImPS2 device.

I haven't begun coding yet, but I have an idea of what should be done to get gpm working in Finnix. Load the base mousedev module, start gpm, load psmouse module, then usbmouse if USB was detected earlier. And of course, there will also be a "nomouse" boot option.

I'm not sure when the next version of Finnix will be released. I think I'm going to say mid- to late-March, or when 2.6.16 is released, whichever comes first.

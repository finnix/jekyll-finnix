---
date: 2020-05-19 21:19:09-07:00
layout: post
title: Behind the scenes of Finnix 120
---
The hammer is never praised.

That's a saying I've attached to Finnix for many years.  A hammer is a tool, and when it does its job, you may consciously or unconsciously appreciate it for doing its job, but there are very few hammer fan clubs.

Finnix was born out of a need, retrieving data from broken PCs when I worked at a dialup ISP in the 90s.  Throughout the 2000s, I worked in a sysadmin role where I managed hundreds of physical servers, and Finnix continued to help with my needs.  Finnix was downloaded millions of times, people would occasionally (but consistently) express their appreciation, and I loved that it's served as a useful tool for so many others.  However, Finnix was never heavily mentioned by its users in the same way a desktop like, say, Linux Mint was.  Why does the tool need to be praised?

The 2010s were much different for me than the 2000s.  I managed many thousands of physical machines (without ever stepping into the datacenters which housed them) and hundreds of thousands of cloud instances.  The individual instance was less important now than in the past.  If it was misbehaving, delete it and add another.  I had less drive to work on Finnix because of this, and usually just used an Ubuntu installation on a USB stick for the rare times I needed to boot into a machine at home.

The hammer is never praised.  In the light I just described, that might sound depressing, but it was pride for me.  I'm not usually one to seek attention.  I do something which interests me, I hope it will be useful (or at least interesting) to others, and I move on.  I find it amusing that people will often refer to me as "that guy who does X", where X is different each time.

In late 2018, I had indented to officially discontinue Finnix.  I had even written a blog post detailing why, but never ended up committing to post it.  LiveCD work is difficult.  The majority of the functionality is contained in the initramfs and early init, and had to handle a whole range of hardware and software scenarios.  In Finnix's case, these systems were homegrown over the course of over ten years, and were showing their age.  In particular, Finnix was missing UEFI support.  UEFI is really, really difficult, especially in a portable boot scenario, hybridized with BIOS.  I never ended up getting anything I was satisfied with.

I never ended up explicitly discontinuing Finnix, but I slowly worked toward it.  Most recently, a few months ago [finnix.org](https://www.finnix.org/) was converted from MediaWiki to a static snapshot of itself.

The hammer is never praised.  Then again, hammers don't suffer from bit rot.

Over the last year or so, I've had a variety of people ask me about the future of Finnix.  An updated kernel and UEFI support were, understandably, the main sticking points.  Over the weekend of May 9th, a friend asked me, and I told her it was unlikely there would be a new Finnix release.  I started looking at alternative to recommend, but there really weren't any.  There's the [debian-live](https://wiki.debian.org/DebianLive) project, but they're stretched thin and pretty much just committed to the desktop CDs.  (There had been talk in the past for a utility CD, but not much explicit interest by anyone to maintain it, so it never got off the ground.)

However, I had started looking at [live-build](https://salsa.debian.org/live-team/live-build) itself.  It's got some problems (though there is fresh blood in debian-live giving it some needed updates), but honestly, it was about 95% of what I needed.  I stepped back and asked what Finnix needed:

* High boot compatibility
* Quick boot into a root prompt
* Lots of console-based utilities
* Relatively small size
* That iconic blue and white ***root@tty1:~#*** prompt

live-build produced good compatibility BIOS+UEFI images (with Secure Boot, even).  live-config handled the initramfs and early init stuff well (and quickly).  I had the old list of utilities included in previous Finnix releases, along with a mental list of more modern utilities to add.  "Small size" was important but relative; for most of Finnix's life, "small" was about 100MB, but inflation had caught up.  I figured keeping it under CD size would be a fine goal (under 700MB, though I'm old enough that I still think a CD is 650MB / 74 minutes).

Using live-build and live-config meant giving up some autonomy, but it also meant a lot less dev.  So much so that Finnix 120's development occurred entirely on Monday, May 11, 2020.  Hardware testing and some minor tweaking took place on Tuesday, release prep tasks were done on Wednesday, and it was released on Thursday.

Yes, Finnix 120 was developed in a day, and I went from "Finnix is dead" to "here's a new Finnix" in under a week.

There are some loose ends, of course.  Finnix 120 is architecturally quite different from previous releases, and the web site will need a lot of documentation updates.  I just noticed [the Launchpad bug tracker](https://bugs.launchpad.net/finnix) has had a number of issues filed, which I didn't even know about.  (Last time I checked 5 years ago, it was only used by me for goal management.)  I'm going to work on verifying they're still relevant and moving over to [the GitHub project repository](https://github.com/finnix/finnix) if so.  Not going to [CADT](https://www.jwz.org/doc/cadt.html) that.

One thing I will be retiring is the concept of remastering Finnix.  [I have published what I used to build Finnix 120](https://github.com/finnix/finnix-live-build/tree/v120), but honestly it's a few scripts and an invocation of live-build.  Want to remaster Finnix?  Just make something similar instead!

As for community interaction, something I've never been great at maintaining...  I don't want the hassle of a mailing list, especially one not likely to be (or historically been) used often.  (Hammer.)  With some hesitation, I've created [a Discord server for Finnix](https://discord.gg/r44cv65).  Feel free to join and say hi.  I've listed two rules: be nice, and a mantra I've had for a long time, "don't be afraid to ask a question, but don't block on an answer".  I've know so many people who are afraid to publicly ask questions.  Don't be!  But, once you've asked the question, don't assume the answer will just come.  Keep working toward a solution.  Maybe the answer comes from someone else, maybe you figure it out yourself, maybe both happen and they're different solutions!

Thank you all for your support of Finnix.  Speaking of which, [free stickers by mail](https://www.finnix.org/Free_stickers) is still a thing, and I'm pretty sure I'm caught up on everyone who sent a letter.  (If you sent an SASE and never received stickers, please get in touch.)  You can also attempt to donate via that page... I think payments to that will go into my account, though PayPal has locked me out of my account and refuses to fix it until the apocalypse is over, whenever that is. (Yes, really.)

The hammer is never praised.  But I'm glad it's still on my belt.
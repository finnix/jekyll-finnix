---
id: 15
title: Works great, less filling
date: 2006-01-28T23:27:29+00:00
author: Ryan Finnie
layout: post
guid: http://www.finnix.org/blog/2006/01/28/works-great-less-filling/
permalink: /2006/01/28/works-great-less-filling/
categories:
  - Development
  - Finnix
---
After completing LVM2 autodetection last week, I took a step back and looked at the boot process as a whole. I determined one thing: there is _too much information_ being displayed during bootup. Of course, things like the amount of system memory and what swap partitions have been activated are important. But things like creating the unionfs partition happens during every boot, and only takes a matter of milliseconds. So, I have removed such lines from the final display. However, these status messages still display, the line is just cleared after successful completion. Below is an example of a normal bootup. Click the image to expand.

[<img src="/blog-media/2008/06/finnix-dev-20060123-1-300x166.png" alt="" title="Finnix dev 20060123 #1" width="300" height="166" class="alignnone size-medium wp-image-74" srcset="/blog-media/2008/06/finnix-dev-20060123-1-300x166.png 300w, /blog-media/2008/06/finnix-dev-20060123-1.png 720w" sizes="(max-width: 300px) 100vw, 300px" />](/blog-media/2008/06/finnix-dev-20060123-1.png)

Notice that the new LVM autodetection is not displayed, because no LVM groups have been found. Compare the previous screenshot to this screenshot on an LVM system:

[<img src="/blog-media/2008/06/finnix-dev-20060123-2-300x166.png" alt="" title="Finnix dev 20060123 #2" width="300" height="166" class="alignnone size-medium wp-image-75" srcset="/blog-media/2008/06/finnix-dev-20060123-2-300x166.png 300w, /blog-media/2008/06/finnix-dev-20060123-2.png 720w" sizes="(max-width: 300px) 100vw, 300px" />](/blog-media/2008/06/finnix-dev-20060123-2.png)

I also managed to get rid of the "INIT: version 2.86 booting" message using an ANSI trick: clear the line, move up a row, and clear the line.

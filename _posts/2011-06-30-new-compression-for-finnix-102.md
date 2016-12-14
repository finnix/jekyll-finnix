---
author: Ryan Finnie
categories:
- Development
- Finnix
date: 2011-06-30 14:27:47
guid: http://blog.finnix.org/2011/06/30/new-compression-for-finnix-102/
id: 246
layout: post
openid_comments:
- a:1:{i:0;s:6:"273183";}
permalink: /2011/06/30/new-compression-for-finnix-102/
title: New compression for Finnix 102
---
In my previous post, I mentioned switching to xz compression without much explanation.

Software tends to get larger over time. Finnix deals with this in two ways: looking for things to cut while still retaining as much functionality as possible, and just accepting that the size will continue to grow over time. Larger kernels, larger software, etc. The smallest release of Finnix was Finnix 86.2, at 92 MiB (x86). The last release, Finnix 101, was the largest so far at 128 MiB (x86).

During development of Finnix 102, the simple act of adding upgraded kernels and upgrading existing Debian packages to the latest versions was seriously adding to the size of Finnix, nearly 150 MiB at one point. And I had done all I could to reduce the size; there was just nothing left to cut out. Then I found out about xz compression. Xz is based on LZMA2, offers 10-20% more compression than Gzip, and in particular has optimizations for architecture-specific bytecode (program binaries, etc). Xz support was added to Linux 2.6.39, and could be used for kernel, initrd and SquashFS compression (previously, all three used Gzip compression).

So I tried it out, using Linux 3.0-rc (as of right now, if 3.0 comes out soon, it will be included with Finnix 102). I used xz compression for the kernel, initrd and SquashFS root filesystem, and was seeing 20% space savings versus using Gzip.

<pre>No compression:
  Root FS:    385,187,840
  initrd:       7,534,080
  Final ISO:  400,162,816

Gzip compression:
  Root FS:    136,921,088 (64.45%)
  initrd:       2,495,967 (66.87%)
  Final ISO:  146,857,984 (63.30%)

Xz (LZMA2) compression:
  Root FS:    109,469,696 (71.58% none, 20.05% gzip)
  initrd:       1,733,032 (77.00% none, 30.57% gzip)
  Final ISO:  118,644,736 (70.35% none, 19.21% gzip)</pre>

Overall, it looks great. Though one consideration is performance. LZMA is known for being very processor intensive. LZMA2 is more processor efficient than LZMA (and BZ2), but still slower than Gzip. Compression times are roughly 5 times slower than with Gzip. But the real question is how well decompression would work in the real world (that is, when booting Finnix). I don't have any hard numbers on that, but I did put dev builds through the gauntlet of everything from an i586 AMD K6 to a Power Mac G3 to a Core 2 Quad Q9450, and could not perceive any slowdowns.

So barring any major problems, Finnix 102 will actually be smaller than its predecessor, for the first time in over 3 years.

As a reminder, the standing goal of Finnix is to keep the distribution CD below the size of a Mini CD (185 MiB). While I doubt many people actually use Mini CDs, it's a good round goal, and while Finnix would still be within the 185 MiB limit without xz compression today, a proactive approach to keeping the distribution size low helps it from becoming a crisis too quickly.

By the way, the build scripts have been updated to allow a builder to choose which method of compression (xz, Gzip, or even none), and scripts within Finnix that rely on reading/modifying the initrd (<tt>finnix-netboot-server</tt>, for example) have been updated to detect which compression method is being used, and will use that method when rebuilding the initrd.

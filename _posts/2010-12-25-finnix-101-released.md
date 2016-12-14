---
id: 182
title: Finnix 101 released
date: 2010-12-25T00:00:08+00:00
author: Ryan Finnie
layout: post
guid: http://blog.finnix.org/?p=182
permalink: /2010/12/25/finnix-101-released/
categories:
  - Announcements
  - Finnix
---
Finnix is a small, self-contained, bootable Linux CD distribution for system administrators, based on Debian testing. Today marks the eggnog-induced release of Finnix 101, the seventeenth release of Finnix since its beginnings over ten years ago. Finnix 101 includes major behind-the-scenes architectural changes, the re-introduction of PowerPC support, new features, and minor bug fixes.

  * Home page: <http://www.finnix.org/>
  * Download: <http://www.finnix.org/Download>
  * Release notes: [http://www.finnix.org/Finnix\_101\_release_notes](http://www.finnix.org/Finnix_101_release_notes)
  * Free stickers! <http://www.finnix.org/Free_stickers>

## PowerPC support returns

After a show of public support, Finnix is once again producing PowerPC releases. Finnix is one of the only dedicated Linux LiveCDs with PowerPC support, and we are happy to continue serving the PowerPC community. Note that PowerPC releases are still not considered release goals, but in the future a lack of a PowerPC release will only happen under extraordinary circumstances.

## Behind-the-scenes re-engineering

While using Finnix still has its same familiar look, much of the core infrastructure which comprises Finnix has been re-engineered. Many of the changes are intended to make development and re-development (remastering) easier and more powerful, and to help with deployment by Virtual Private Server (VPS) providers. Changes include a new CD filesystem layout, an enclosed remastering environment, a Finnix-specific SysV-compatible RC system, and componentized Finnix RC scripts.

## Linux 2.6.36

Due to Debian testing being in deep freeze, the most recent kernel in either "testing" or "unstable" is 2.6.32. Therefore, a set of 2.6.36 kernels have been compiled based on 2.6.36-1~experimental.1 from Debian "experimental". Despite the "experimental" name, these kernels have been tested more heavily than the average Finnix release, and have proven to be very stable.

## Hardware Detection Tool (HDT) added

On the X86 CD, Hardware Detection Tool has been added to the boot menu. This allows users to view system information (processor, memory, PCI devices, etc) quickly, without booting into a full operating system.

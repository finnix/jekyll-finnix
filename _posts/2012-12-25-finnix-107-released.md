---
author: Ryan Finnie
categories:
- Announcements
- Finnix
date: 2012-12-25 00:11:45
guid: http://blog.finnix.org/2012/12/25/finnix-107-released/
id: 436
layout: post
openid_comments:
- a:1:{i:0;i:402721;}
permalink: /2012/12/25/finnix-107-released/
title: Finnix 107 released
---
Finnix is a small, self-contained, bootable Linux CD distribution for system administrators, based on Debian testing. Today I am pleased to announce the release of Finnix 107, only two months from the previous release, but packed with new functionality and bug fixes.

  * Home page: <http://www.finnix.org/>
  * Download: <http://www.finnix.org/Download>
  * Release notes: [http://www.finnix.org/Finnix\_107\_release_notes](http://www.finnix.org/Finnix_107_release_notes)
  * Free stickers! <http://www.finnix.org/Free_stickers>

## Linux 3.6

Finnix 107 includes Linux kernel 3.6, and includes a fix for the (overhyped, it seems) [ext4 corruption bug](https://plus.google.com/117091380454742934025/posts/f5a1eHxUzSh).

## Faster startup, faster shutdown

Average Finnix startup times have been reduced even further by the cleanup of legacy code. In addition, the shutdown procedure, which largely has not changed in years, got a revamp and is now noticeably quicker.

## isohybrid support included

The x86 ISO is now being built with the isohybrid method, meaning you can now [write the ISO directly to a USB flash drive](http://www.finnix.org/Bootable_USB_flash_drives) at the block level to boot it.

## findiso support added, grub-finnix utility released

Finnix 107 includes support for searching for and mounting a Finnix ISO on a filesystem (findiso=/path/to/finnix-107.iso). This can be used to create a GRUB 2 configuration on a server/workstation to boot a Finnix ISO directly. To that end, I have released a utility for Debian/Ubuntu, [grub-finnix](http://www.finnix.org/Finnix_utilities), which hooks into the update-grub2 system to automatically handle building the necessary GRUB 2 config.

## finnix-hwsubmit redesigned

The finnix-hwsubmit utility has been completely redesigned. The report format is now in a standardized machine-parsable yet easy to read format (MIME), you will be given a URL of the submitted report, and you can choose to make the report public. Public reports are available at [hwsubmit.finnix.org](http://hwsubmit.finnix.org/).

## New utilities included

A number of new packages have been included with Finnix 107, including: arping, bridge-utils, chntpw, cmospwd, ifenslave-2.6, sshfs, testdisk, udftools, zerofree. iPXE has also been added to the main x86 boot menu.

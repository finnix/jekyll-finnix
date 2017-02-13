---
categories:
- Announcements
date: 2012-07-13 07:04:04
layout: post
title: Finnix 105 released
wp_id: 409
---
Finnix is a small, self-contained, bootable Linux CD distribution for system administrators, based on Debian testing. I am pleased to announce the release of Finnix 105, a major architectural update to the Finnix series. Finnix 105 brings major organizational changes to the build and boot systems, along with the usual assortment of software updates.

  * Home page: <https://www.finnix.org/>
  * Download: <https://www.finnix.org/Download>
  * Release notes: [https://www.finnix.org/Finnix\_105\_release_notes](https://www.finnix.org/Finnix_105_release_notes)
  * Free stickers! <https://www.finnix.org/Free_stickers>

## Announcing Project NEALE

Until Finnix 105, each Finnix release had been produced by hand, essentially a remaster of the previous release. This allowed for rapid development and testing, but also allowed for individual mistakes, filesystem bloat, and trouble tracking upstream Debian packages.

Finnix 105 is the first Finnix release to be produced under Project NEALE (Normalized Extraction and Assembly of LiveCD Environments), a new set of procedures to build Finnix CDs from a minimal base Debian bootstrap. All base Finnix configuration is done via deb packages, including two new packages, finnix-base and finnix-standard, which depend on all the other software packages which normally go into a Finnix release. This allows for a consistent build process each time, and between architectures. It also allows for more future options, such as a native userland AMD64 release.

Due to the new portable nature of NEALE builds, incrementing build numbers have been retired (over 3000 builds have been produced in the last 7 years!). There are still a few rough edges regarding this transition, which will be ironed out over the next release cycle. The base build system is not yet ready for public consumption, but will be released to the public when it is. Remastering via the finnix-build-stage{1,2} scripts will continue to be supported (indeed, once the base bootstrap is completed, the build stage scripts are still called to prepare and master the ISOs).

## sysvinit replaced with runit

sysvinit, the classic userland init system -- the first process run as part of the main userland, responsible for running startup scripts and entering shutdown on command -- has been replaced with runit, a minimal init system. Due to the nature of Finnix's boot process, a statically-compiled init is needed. A manually-compiled sysvinit binary was previously provided for this purpose, and would often fall out of sync with the userland tools. However, runit's init binary is statically-compiled by design, requiring no alterations, and is much smaller, requiring less memory. runit's core operation is radically different than sysvinit, but its integration into Finnix has been designed to be as similar to previous sysvinit-run releases as possible, and should be transparent to the user.

## New archive management system, new GPG keys

Previous Finnix deb packages were managed in a manual repository, and the repository and releases were signed by Ryan Finnie's personal GPG key. Project NEALE required a more organized repository setup, prompting the creation of [archive.finnix.org](https://archive.finnix.org/), managed by reprepro. In addition, Finnix-specific GPG keys have been created for use within Finnix. Release ISOs are now signed by [Finnix Release Signing Key (4356E6C2)](http://pgp.mit.edu:11371/pks/lookup?op=vindex&search=0x7D6F85C04356E6C2), and repositories under archive.finnix.org are signed by [Finnix Archive Signing Key (A89BA58D)](http://pgp.mit.edu:11371/pks/lookup?op=vindex&search=0x8087F4EDA89BA58D). Both new keys are signed by [Finnix Signing Key (0897797F)](http://pgp.mit.edu:11371/pks/lookup?op=vindex&search=0x66FB45740897797F), which in turn is signed by both [Ryan Finnie (203ECA25)](http://pgp.mit.edu:11371/pks/lookup?op=vindex&search=0x299610A9203ECA25) (the old key used for Finnix signing) and [Ryan Finnie (86AE8D98)](http://pgp.mit.edu:11371/pks/lookup?op=vindex&search=0x7E60A3A686AE8D98) (Ryan's new personal key), maintaining the web of trust. 203ECA25 is due to be retired and revoked after the release of Finnix 105.

## Linux 3.4

Finnix 105 includes Linux 3.4, using kernel configurations based closely on Debian's Linux 3.4 sources.

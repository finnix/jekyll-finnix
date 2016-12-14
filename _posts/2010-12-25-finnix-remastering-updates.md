---
id: 191
title: Finnix remastering updates
date: 2010-12-25T11:41:32+00:00
author: Ryan Finnie
layout: post
guid: http://blog.finnix.org/2010/12/25/finnix-remastering-updates/
permalink: /2010/12/25/finnix-remastering-updates/
categories:
  - Development
  - Finnix
---
Finnix is used a lot for remastering for administrators' specific projects, so if you're a remasterer, you're going to both love and hate Finnix 101 -- love because Finnix 101 ultimately makes it a lot easier to remaster in the long run, and hate because a lot of things have changed in incompatible ways, hopefully for the better. This post should help give you a rundown on what's changed.

The following wiki guides have been updated for Finnix 101:

  * [Remastering](http://www.finnix.org/Remastering)
  * [Overlays](http://www.finnix.org/Overlays)

## CD layout

  * Almost everything with the CD layout has changed. All filenames are now lowercase, and most files have changed locations. 
      * <tt>md5sums</tt> is now on the root of the CD (<tt>/md5sums</tt>).
      * <tt>/isolinux</tt> and <tt>/boot</tt> are still the bootloader-specific directories for x86 and PowerPC, respectively.
      * <tt>/{isolinux,boot}/minirt</tt> has become <tt>/{isolinux,boot}/initrd.gz</tt>.
      * <tt>/FINNIX/FINNIX</tt> has become <tt>/finnix/arch/{x86,ppc}/root.img</tt>, where "x86" and "ppc" are the userland identifiers for the architecture (that is, you don't have to worry about 64-bit kernels on the 32-bit userland).
      * <tt>/finnix/arch.map</tt> is a text file that defines a \`uname -m\` mapping to the userland architecture. The first column is the output of \`uname -m\`, the second is the primary userland architecture, and the third is the secondary userland architecture. On 64-bit kernels ("amd64" and "ppc64"), the primary userland architecture is "amd64" and "ppc64" respectively, but since Finnix does not distribute 64-bit userlands, it will move on to the secondary columns. Once a <tt>root.img</tt> is found, that userland architecture is remembered, so overlays will not be checked in the userland architectures that are skipped over. (Short summary: don't use <tt>/finnix/arch/{amd64,ppc64}/</tt>, it's basically disabled in its current state.)</ul> 
    ## Build enviroment
    
      * The default (and recommended) build environment path has changed from <tt>/mnt/hda1/knx/</tt> to <tt>/finnix/build/</tt>. All subdirectories remain the same (<tt>source/FINNIX/</tt> for the chroot, <tt>initrd/</tt> for the initrd, <tt>master/</tt> for the CD layout).
      * The build scripts are now located in the compressed root, and are guaranteed to be the scripts that built the running Finnix version. They are <tt>finnix-build-stage1</tt> and <tt>finnix-build-stage2</tt>. Stage 1 preps the chroot and builds the <tt>root.img</tt> file, while State 2 builds the initrd and masters the CD. While the build scripts live inside the chroot, they MUST be run from outside the chroot. That is, <tt>/finnix/build/source/FINNIX/usr/sbin/finnix-build-stage1 && /finnix/build/source/FINNIX/usr/sbin/finnix-build-stage2</tt>.
    ## In the chroot
    
      * When chrooting in, you should really be doing: <tt>export FINNIXDEV=1; chroot /finnix/build/source/FINNIX /bin/bash -l</tt>. Setting FINNIXDEV=1 sets some bashrc functionality that makes it easier to work in the chroot, and will temporarily move dummy <tt>invoke-rc.d</tt> and <tt>start-stop-daemon</tt> scripts into place so installing/upgrading software within the chroot doesn't try to start daemons, and will automatically mount /proc and /sys when useful.
      * The startup system is now in <tt>/etc/finnix/rc*.d/</tt>. <tt>/etc/rc*.d/</tt> will not be checked at all during Finnix bootup. If you want to start daemons on startup, shell scripts in <tt>/etc/finnix/rc2.d/</tt> are the way to go. Additionally, much of the old <tt>finnix-autconfig</tt> functionality (the mega script that did almost all the heavy lifting) has been split up into components in <tt>/etc/finnix/rcS.d/</tt> and <tt>/etc/finnix/rc2.d/</tt>.
    ## Overlays and local startup scripts
    
      * On the CD, <tt>/FINNIX/overlay.d/</tt> has become <tt>/finnix/arch/{x86,ppc,indep}/overlays/</tt>. Use x86 and ppc for architecture-specific overlays, and "indep" for architecture-independent overlays.
      * <tt>/FINNIX/finnix.sh</tt> is gone, in favor of <tt>/finnix/arch/{x86,ppc,indep}/rc/</tt>. Here you can place multiple local startup scripts. The same architecture rules apply as above.

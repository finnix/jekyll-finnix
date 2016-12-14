---
categories:
- Announcements
date: 2006-01-15 08:26:25
layout: post
title: 'Two small updates: finnix-scripts, finnix-3ware-install'
wp_id: 9
---
A typo has been found in the finnix-hwsubmit program (included in finnix-scripts) that prevents the output of "lspci -vvn" from being included with the report. If you use finnix-hwsubmit (and if not, why aren't you?), you will want to do an "apt-get update" and "apt-get install finnix-scripts" before submitting.

Additionally, a small package called finnix-3ware-install has been released. At work, we have a great number of machines with 3ware SATA RAID controllers in them, and using the 3ware CLI management program (tw_cli) can be handy. Unfortunately, the CLI is binary-only and closed-source[0x01], so it cannot be directly distributed with Finnix. Instead, I have created a script (that comes in the finnix-3ware-install package) that shows you the 3ware EULA, then downloads and installs it automatically. If you want to use this package, "apt-get update", then "apt-get install finnix-3ware-install". Enjoy!

[0x01] Why? 3ware's drivers are GPL, and the 3ware developers work with the kernel.org people so the drivers included with vanilla Linux kernels are usually identical to the version that 3ware distributes itself. However, the array management tools are closed-source.

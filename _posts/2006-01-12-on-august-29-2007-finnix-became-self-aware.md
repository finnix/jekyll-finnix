---
id: 8
title: On August 29, 2007, Finnix became self-aware.
date: 2006-01-12T20:14:54+00:00
author: Ryan Finnie
layout: post
guid: http://blog.finnix.org/2006/01/12/on-august-29-2007-finnix-became-self-aware/
permalink: /2006/01/12/on-august-29-2007-finnix-became-self-aware/
categories:
  - Development
  - Finnix
---
I'm currently running Finnix 86.2 on a "modest" new system I built for work, a [Supermicro 6024H-T](http://www.supermicro.com/products/system/2U/6024/SYS-6024H-T.cfm), dual Xeon 3.6GHz, 8GB memory[0x01], and 6 400GB SATA drives attached to a [3ware 9550sx](http://www.3ware.com/products/Serial_ata2-9000.asp) controller. Everything works great, which is quite puzzling considering it automatically found both the 3ware controller and the onboard Marvell SATA controller, neither of which are in the pcitable database yet. Yet somehow hwsetup determined the correct modules to load for each controller. I'll have to dig through the hwdata source to figure out HOW.

[0x01] Finnix's kernel does not include PAE support, because that tends to cause problems on machines with less than 4GB of memory installed (IE, most installations these days). Finnix is stable and usable on this machine, but the kernel only sees 4GB out of 8GB.

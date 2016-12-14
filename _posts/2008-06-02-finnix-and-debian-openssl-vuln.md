---
id: 68
title: "Finnix and Debian's OpenSSL Vulnerability"
date: 2008-06-02T01:05:13+00:00
author: Ryan Finnie
layout: post
guid: http://www.finnix.org/blog/?p=68
permalink: /2008/06/02/finnix-and-debian-openssl-vuln/
categories:
  - Finnix
---
All versions of Finnix from 89.0 to 91.1 (inclusive) contain the [Debian OpenSSL predictable RNG vulnerability](http://lists.debian.org/debian-security-announce/2008/msg00152.html). The fix will be included with the next scheduled (approximately quarterly) release of Finnix in the next few weeks. In the meantime, if you use any OpenSSL-related programs (openssl itself, ssh, openvpn, etc) on Finnix, be sure to do the following as soon as you boot Finnix:

`apt-get update && apt-get install libssl0.9.8`

Finnix does not include any pre-generated keys, but any keys generated on Finnix with a vulnerable OpenSSL will be vulnerable.

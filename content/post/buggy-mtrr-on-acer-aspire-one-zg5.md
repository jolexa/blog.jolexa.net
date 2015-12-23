---
author: Jeremy Olexa
categories:
- linux
date: 2009-11-22T00:00:00Z
guid: http://blog.jolexa.net/?p=518
id: 518
tags:
- aspire1
title: Buggy MTRR on Acer Aspire One ZG5
aliases:
    - /2009/11/buggy-mtrr-on-acer-aspire-one-zg5/
---

The problem:

<pre>$ dmesg |grep mtrr
mtrr: no more MTRRs available</pre>

I found on my &#8216;new-to-me&#8217; AA1 that MTRR handling in the BIOS was messed up. Thanks to this [bug report][1] I figured out that I should compile the kernel with MTRR *sanitizer* enabled. That is:

<pre>$ zgrep -i MTRR /proc/config.gz 
CONFIG_MTRR=y
CONFIG_MTRR_SANITIZER=y
CONFIG_MTRR_SANITIZER_ENABLE_DEFAULT=1
CONFIG_MTRR_SANITIZER_SPARE_REG_NR_DEFAULT=1</pre>

And output of /proc/mtrr is as follows. Before and after.

<pre>$ cat /proc/mtrr
reg00: base=0x0fffe0000 ( 4095MB), size=  128KB, count=1: write-protect
reg01: base=0x0fffc0000 ( 4095MB), size=  128KB, count=1: uncachable
reg02: base=0x000000000 (    0MB), size=  512MB, count=1: write-back
reg03: base=0x020000000 (  512MB), size=  512MB, count=1: write-back
reg04: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable
reg05: base=0x03f600000 ( 1014MB), size=    2MB, count=1: uncachable
reg06: base=0x03f500000 ( 1013MB), size=    1MB, count=1: uncachable
reg07: base=0x000000000 (    0MB), size=  128KB, count=1: uncachable
after kernel modification:
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x03f500000 ( 1013MB), size=    1MB, count=1: uncachable
reg02: base=0x03f600000 ( 1014MB), size=    2MB, count=1: uncachable
reg03: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable
reg04: base=0x040000000 ( 1024MB), size=  256MB, count=1: write-combining</pre>

This is needed for decent video playback with the on-board Intel 945 video. <img src="http://blog.jolexa.net/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" />

 [1]: https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/370552
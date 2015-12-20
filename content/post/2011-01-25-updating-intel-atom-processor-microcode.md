---
author: Jeremy Olexa
categories:
- gentoo
date: 2011-01-25T00:00:00Z
guid: http://blog.jolexa.net/?p=784
id: 784
tags:
- aspire1
title: Updating Intel Atom processor microcode
url: /2011/01/updating-intel-atom-processor-microcode/
---

The problem:

<pre>% dmesg | grep -i micro
Atom PSE erratum detected, BIOS microcode update recommended
Atom PSE erratum detected, BIOS microcode update recommended
microcode: CPU0 sig=0x106c2, pf=0x4, revision=0x208
microcode: CPU1 sig=0x106c2, pf=0x4, revision=0x208
microcode: Microcode Update Driver: v2.00 , Peter Oruba</pre>

I found out that some recent kernel that I loaded at an unknown time, was able to point out that I had &#8216;old&#8217; microcode for my processor on my [Aspire1 ZG5][1]. I searched around for a BIOS upgrade, but since this is an older generation netbook, I quickly gave up when my searching yielded nothing useful. There is a userspace tool that you can use to &#8216;upgrade&#8217; the microcode provided by Intel on every boot. In Gentoo Linux, that is called `sys-apps/microcode-ctl`. Simply install that and enable the init script on boot.

The output after:

<pre>% dmesg | grep -i micro
Atom PSE erratum detected, BIOS microcode update recommended
Atom PSE erratum detected, BIOS microcode update recommended
microcode: CPU0 sig=0x106c2, pf=0x4, revision=0x208
microcode: CPU1 sig=0x106c2, pf=0x4, revision=0x208
microcode: Microcode Update Driver: v2.00 , Peter Oruba
microcode: CPU0 updated to revision 0x218, date = 2009-04-10
microcode: CPU1 updated to revision 0x218, date = 2009-04-10</pre>

References:

  * <https://wiki.archlinux.org/index.php/Microcode>
  * [Flameeyes&#8217;s Weblog : Microupdates for microcodes][2]

*Edit: Added a reference*

 [1]: http://blog.jolexa.net/tag/aspire1/
 [2]: http://blog.flameeyes.eu/2011/01/17/microupdates-for-microcodes
---
author: Jeremy Olexa
categories:
- gentoo prefix
date: 2010-01-18T00:00:00Z
guid: http://blog.jolexa.net/?p=627
id: 627
tags:
- efikamx
title: 'Gentoo Prefix: ARM hardware'
url: /2010/01/gentoo-prefix-arm-hardware/
---

It is no surprise that [Gentoo Prefix][1] works fine on arm-linux given the great work being done in Gentoo Linux by the ARM team (armin76, maekke, et al).

For the [Genesi Efika MX][2] ([unboxing][3]), I now have a binpkg repo setup (for Gentoo Prefix only). This was mainly a fun proof-of-concept that I did. I went from installing 70 packages in about 18 hours, to about 30 minutes using binpkgs.

**What does this mean:**  
Given the relatively small set of arm users and the highly specific use cases for arm hardware, well, there isn&#8217;t a very big percentage of users that *will* keep Ubuntu on their Efika MX when they get it. But, if they do, that means that they can get a complete toolchain and Gentoo Linux userland (including portage package manager) on the host in less than an hour. Of course, they could also get the same packages from the Ubuntu package manager but that isn&#8217;t as cool <img src="http://blog.jolexa.net/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" />

**How to install/get working:**  
Follow this easy guide that I wrote, [here][4]. All 70 packages will occupy about 580MB of space. Then you will have the toolchain and portage (emerge) at your disposal to use on your Ubuntu ARM (cortex-a8, armv7) system.

Have fun.

 [1]: http://www.gentoo.org/proj/en/gentoo-alt/prefix/
 [2]: http://www.genesi-usa.com/products/efika
 [3]: http://blog.jolexa.net/2009/12/03/gentoo-genesi-efika-mx-unboxing-and-first-impressions/
 [4]: http://dev.gentoo.org/~darkside/prefix/arm/bootstrap-arm.xml
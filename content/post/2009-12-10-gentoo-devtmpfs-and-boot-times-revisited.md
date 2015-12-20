---
author: Jeremy Olexa
categories:
- gentoo
date: 2009-12-10T00:00:00Z
guid: http://blog.jolexa.net/?p=555
id: 555
tags:
- openrc
title: 'Gentoo: devtmpfs and boot times (revisited)'
url: /2009/12/gentoo-devtmpfs-and-boot-times-revisited/
---

There was alot of of talk/flames on the LKML about devtmpfs. Looks like a big push for this was for embedded devices, android, etc. Since I read that it may give a boot time speed up, I was slightly intrigued. <http://lkml.org/lkml/2009/4/30/182>, yes&#8230;it is an old topic but it finally was released in stable .32 kernel.

So, bootcharts:  
[bootchart-2.6.31.6.png][1] 39 seconds  
[bootchart-2.6.32-no-devtmpfs.png][2] 37 seconds  
[bootchart-2.6.32-devtmpfs.png][3] 37 seconds  
[bootchart-2.6.32-openrc.png][4] 26 seconds (devtmpfs)

So, where is the real win here? Well, as I wrote [before][5], use openrc.

 [1]: http://dev.gentoo.org/~darkside/perm/bootchart/bootchart-2.6.31.6.png
 [2]: http://dev.gentoo.org/~darkside/perm/bootchart/bootchart-2.6.32-no-devtmpfs.png
 [3]: http://dev.gentoo.org/~darkside/perm/bootchart/bootchart-2.6.32-devtmpfs.png
 [4]: http://dev.gentoo.org/~darkside/perm/bootchart/bootchart-2.6.32-openrc.png
 [5]: http://blog.jolexa.net/2008/09/22/gentoo-improve-boot-time/
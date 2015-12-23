---
author: Jeremy Olexa
categories:
- gentoo
date: 2008-09-22T00:00:00Z
guid: http://jolexa.wordpress.com/?p=107
id: 107
tags:
- boot time
- openrc
- performance
title: 'Gentoo: Improve boot time&#8230;'
aliases:
    - /2008/09/gentoo-improve-boot-time/
---

Switch to baselayout-2 and openrc..the speed up **is** noticeable. Especially if you enable `rc_parallel="YES"` in /etc/rc.conf. Anyway, others have wrote about it already, including a bootchartd of before and after [here][1].

Anyway, this *should* be hitting stable soonish and when it does be sure to read the migration [guide][2] because some things have indeed changed.

For me, I count to 10 slowly and my laptop is at the xdm prompt&#8230;very cool and good job [Roy][3]!

 [1]: http://www.void.gr/kargig/blog/2008/04/09/gentoo-baselayout-2-and-openrc-impressions/
 [2]: http://www.gentoo.org/doc/en/openrc-migration.xml
 [3]: http://roy.marples.name/openrc
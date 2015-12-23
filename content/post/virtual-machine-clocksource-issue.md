---
author: Jeremy Olexa
categories:
- gentoo
date: 2010-03-05T00:00:00Z
guid: http://blog.jolexa.net/?p=638
id: 638
tags:
- vps
title: Virtual Machine clocksource issue
aliases:
    - /2010/03/virtual-machine-clocksource-issue/
---

You have probably seen the [Host Virtual][1] advertisements on the sidebar of [gentoo.org][2] website.

I ran into a weird clocksource issue on my VPS that I haven&#8217;t seen elsewhere. This issue was that my time would progressively get worse and worse and eventually NTP could not keep up because the clock was so far out of date. This happened on a pretty quick interval, about 1-2 days until I had to manually reset it. I opened up a support case with Host Virtual and the suggestion was to change the kernel&#8217;s clocksource to jiffies, from tsc, or vice versa. (or use a newer kernel, but I was already at the latest 2.6.32.x kernel at the time) My kernel&#8217;s clocksource was at the default and I had to research the issue some more because I haven&#8217;t heard of this before.

In the kernel&#8217;s Documentation directory, I found some info. (`Documentation/kernel-parameters.txt`). There is quite some details in there, but the summary is that the default clocksource was &#8216;tsc&#8217; on x86. I changed my kernel&#8217;s clocksource by the `clocksource=jiffies` kernel parameter. Rebooted the virtual machine and NTP has been able to keep time since.

I don&#8217;t really know the difference here and don&#8217;t care to research much more. It is fixed and maybe this info will help someone else someday.

 [1]: http://vr.org/
 [2]: http://www.gentoo.org/
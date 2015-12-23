---
author: Jeremy Olexa
categories:
- gentoo
- linux
date: 2008-09-02T00:00:00Z
guid: http://jolexa.wordpress.com/?p=62
id: 62
tags:
- bad drivers
- intel
- iwl3945
- wireless
title: 'Intel: iwl3945 madness'
aliases:
    - /2008/09/intel-iwl3945-madness/
---

As jaervosz [wrote][1] the other day, the iwl3945 driver has some serious issues with it. I think I have it narrowed down to what conditions cause the problem.

**Problem:** When downloading large files for non-trivial amounts of time, the download speed drops to <80 K/s. This is unacceptable, the whole pipe is limited to that by the way. I am not sure *what* exactly causes this but I have narrowed down the conditions to which it happens.

Encryption does not matter.. it falters on wep/wpa{1,2} or open networks. However, I found that this condition only exists on mode B APs. This includes &#8220;mixed&#8221; APs as well. I do not know enough about drivers but if the AP offers B & G, then it should select G, right? Well, based on the condition of the speeds, I would have to say that it is selecting B mode and then hitting this bug again.

Anyway, for the time being&#8230;Do not use B APs. Easier said that done because I&#8217;m sure most every sys-admin would select Mixed AP over G only. So, if you are experiencing this issue as well, please comment on the [upstream bug][2], which has been open for 7 months by the way. Annoying. Maybe we can convince them to look at this issue some more? Even intel employees are CC&#8217;d on the bug because they have the issue too..

**Workaround:** Convert your AP to G only or use G only APs.

 [1]: http://home.coming.dk/index.php/2008/08/15/p822
 [2]: http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1592
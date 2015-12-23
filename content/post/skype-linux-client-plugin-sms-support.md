---
author: Jeremy Olexa
categories:
- gentoo
date: 2009-03-20T00:00:00Z
guid: http://blog.jolexa.net/?p=305
id: 305
tags:
- skype
title: Skype Linux Client plugin (SMS support)
aliases:
    - /2009/03/skype-linux-client-plugin-sms-support/
---

I was pretty upset after reading that the last status update on the Skype Linux client was [back in January][1]. Since I was using Skype on Windows all week last week, I didn't know how bad it was on Linux until I got back home. What a bummer that all Linux gets is v2.0, while Windows gets v4.0. In particular, I needed the SMS feature. So, now Gentoo has this feature via plugin now too.

Simply emerge [net-im/skysentials][2] (which pulls in [dev-python/skype4py][3]) and run `skysentials.py`

It is not the best <span style="text-decoration: line-through;">solution</span> hack, but I am afraid it is all that we will get for quite some time based on frequency of Linux client status updates&#8230;

 [1]: http://share.skype.com/sites/linux/
 [2]: http://packages.gentoo.org/package/net-im/skysentials
 [3]: http://packages.gentoo.org/package/dev-python/skype4py
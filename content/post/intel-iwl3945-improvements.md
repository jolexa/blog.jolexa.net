---
author: Jeremy Olexa
categories:
- gentoo
- linux
date: 2008-10-31T00:00:00Z
guid: http://jolexa.wordpress.com/?p=143
id: 143
tags:
- bad drivers
- intel
- iwl3945
- wireless
title: 'Intel: iwl3945 improvements'
aliases:
    - /2008/10/intel-iwl3945-improvements/
---

**Better** but not *great*.

As I previously wrote about how much [iwl3945 sucked][1]. The .27 kernel seems like there has been many iwl improvements. When I say, &#8220;seems&#8221; &#8211; that is what I mean. I mean that it seems like there is improvements, and the [changelogs][2] show alot of iwl activity. So, my current experiences with iwl3945 still show some &#8220;troubles&#8221; with being on B networks. But this time, mixed networks work better and G networks work flawlessly. Even people with @intel.com email address are having issues with it, frankly, I am surprised that [this bug][3] has not been fixed yet. But hey, it did get a new assignee last week, maybe that is an improvement?

(Above observed results are with the 2.6.27.4 vanilla kernel)

 [1]: http://jolexa.wordpress.com/2008/09/02/intel-iwl3945-madness/
 [2]: http://git.kernel.org/?p=linux%2Fkernel%2Fgit%2Fstable%2Flinux-2.6.27.y.git&a=search&h=HEAD&st=commit&s=iwl
 [3]: http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1592
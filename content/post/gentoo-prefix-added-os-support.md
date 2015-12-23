---
author: Jeremy Olexa
categories:
- gentoo prefix
date: 2009-02-05T00:00:00Z
guid: http://blog.jolexa.net/?p=227
id: 227
tags:
- aix
- ia64
title: Gentoo Prefix &#8211; added OS support
aliases:
    - /2009/02/gentoo-prefix-added-os-support/
---

[Gentoo Prefix][1] now supports Itanium Linux and AIX-6.1 (with caveats).

ia64-linux mostly works out of the box. There is one small issue with scanelf which I would like to fix if I ever find the time. (&#8216;scanelf(9292): unaligned access to ...' &#8211; low priority because everything still appears to work). We previously supported ia64-linux but it was removed because we didn't think anyone used it &#8211; and no one responded when we asked. It was added back, by me, to support a work endeavour.

AIX-6.1 &#8211; whew..this one was a pain to bootstrap a prefix env. I took the lazy way and put my AIX-5.3 prefix last in my PATH so I had working tools to start with. Now, after I got it all working, there is some sort of hiccup with bash/python(?). Something is causing something to hang when python's workdir is trying to get cleaned up after the emerge. There is a hanging file descriptor out there (.nfs). Again, not easy to debug. (Don't even bother telling me about lsof, I know, I know...). So AIX-6.1 works, but maybe not very well. YMMV 😉

As a side note, we are up to ~2100 packages in the prefix tree thanks to some helpful Prefix users.

 [1]: http://www.gentoo.org/proj/en/gentoo-alt/prefix/index.xml
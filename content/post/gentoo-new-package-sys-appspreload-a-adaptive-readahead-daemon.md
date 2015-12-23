---
author: Jeremy Olexa
categories:
- gentoo
date: 2008-10-17T00:00:00Z
guid: http://jolexa.wordpress.com/?p=133
id: 133
tags:
- preload
- readahead
title: 'Gentoo: New package, sys-apps/preload, a adaptive readahead daemon'
aliases:
    - /2008/10/gentoo-new-package-sys-appspreload-a-adaptive-readahead-daemon/
---

Hey all,  
I just put *preload* into portage. I found this one by researching readahead stuff. Preload is an adaptive readahead daemon. This is a cool little app that I have been running all day now. The short story is that it scans /proc every 20 seconds and will maintain its own "database" of files to keep loaded in memory.

The long story is: The author's [whitepaper][1] on preload. And more details can be found [here][2].

Anyway, I could use testers on this package. I have observed **noticable** speedups on the first launch of apps like firefox, thunderbird, & vim. This does work and it is very smart. It cannot use "all your ram" and it has tons of configuration options. Please provide feedback, and file bugs as appropriate. Thanks.

 [1]: http://www.techthrob.com/tech/preload_files/preload.pdf
 [2]: http://www.techthrob.com/tech/preload.php
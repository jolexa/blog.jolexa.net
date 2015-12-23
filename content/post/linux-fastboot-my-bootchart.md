---
author: Jeremy Olexa
categories:
- gentoo
date: 2008-10-14T00:00:00Z
guid: http://jolexa.wordpress.com/?p=120
id: 120
tags:
- fastboot
title: 'Linux: fastboot / my bootchart'
aliases:
    - /2008/10/linux-fastboot-my-bootchart/
---

Hmm, there is alot of buzz around the [fastboot][1] [craze][2] and now hitting the proverbial 5 second [boot][3]. This is turning out to be a fun thing to follow. Linus doesn't like the fastboot [patches][4] but developers are adopting some of the patches that these guys have created (see lwn article, X devs offered to help, etc).

Anyway, many kudos to Intel for supporting the open source community, Powertop, latencytop, X, kernel..cool. Thank you Intel for your support. <img src="http://blog.jolexa.net/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" /> As such, I will support Intel with my purchasing power. *Editted to add: (10/15/2008) As so kindly pointed out by leio on irc, &#8220;AMD does offer resources freely and contribute to OSS as well. For example, they are one big driving force and helper for the free firmware story -- a story that GNU has at second position in free software important projects.&#8221; -leio. My opinion doesn't really change here and this is getting to be out of scope for this particular post.*

Without modifications to practically anything on my system. I have a working laptop in ~30 seconds. I plan on tweaking this some and hopefully I can shave it down to less than 20. 10-15 would be excellent, but not a big goal for me.

<p style="text-align:center;">
  <a href="http://jolexa.files.wordpress.com/2008/10/bootchart1.png"><img class="size-medium wp-image-122 aligncenter" src="http://jolexa.files.wordpress.com/2008/10/bootchart1.png?w=118" alt="" width="118" height="300" /></a>
</p>

<p style="text-align:left;">
  I find it rather interesting that there is <strong>no</strong> CPU or I/O activity until ~5 seconds. I'll have to work on that I guess. <em>Editted to add: (10/15/2008) See comments for hint on how to get bootchart to display the first 5 seconds. Thanks Donnie.</em>
</p>

 [1]: http://lwn.net/Articles/299483/
 [2]: http://www.google.com/search?q=lwn+fastboot
 [3]: http://www.youtube.com/watch?v=s7NxCM8ryF8
 [4]: http://lkml.org/lkml/2008/10/10/411
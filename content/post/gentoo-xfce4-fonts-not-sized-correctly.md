---
author: Jeremy Olexa
categories:
- gentoo
date: 2008-08-02T00:00:00Z
guid: http://jolexa.wordpress.com/?p=44
id: 44
tags:
- fonts
- xfce
title: 'Gentoo: xfce4 fonts not sized correctly'
aliases:
    - /2008/08/gentoo-xfce4-fonts-not-sized-correctly/
---

Quick tip:

Problem: When installing Gentoo, Xfce4 on my new amd64 laptop, the fonts were extremely goofy compared to my old installation on x86. Meaning that terminal fonts looked ok, but gtk based fonts were large and small. I couldn&#8217;t figure this out and finally found a solution on [XUbuntu&#8217;s blog post.][1] I will reiterate it here for my future reference and maybe help someone else with this same problem.

Solution: In ~/.config/xfce4, append to the Xft.xrdb file (or create the file):  
`Xft.dpi: 96`.

Then, log out and log back in. The fonts look normal sized again. I&#8217;m not sure what Xfce4 defaults to but whatever it was, it was clearly incorrect for my laptop.

**Update:** [nightmorph][2], a fellow Gentoo developer, explains how to use the Xfce GUI to change the DPI setting as well. Please see the comments of this post.

 [1]: http://xubuntu.wordpress.com/2006/08/09/howto-fix-xfce-fonts/
 [2]: http://dev.gentoo.org/~nightmorph/
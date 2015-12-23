---
author: Jeremy Olexa
categories:
- gentoo prefix
date: 2009-07-23T00:00:00Z
guid: http://blog.jolexa.net/?p=445
id: 445
tags:
- aix
title: 'AIX: Argument list too long (quick tip)'
aliases:
    - /2009/07/aix-argument-list-too-long-quick-tip/
---

If you happen to be on an AIX 5.x host using [Gentoo Prefix][1]. Then you might see something like this eventually:

<pre><blockquote>
  /bin/sh[3]: /home/jolexa/portage/aix-5.3/bin/chmod: arg list too long
</blockquote></pre>

This is caused by build systems that use wildcards or even ebuilds that have no issues on a normal GNU/Linux system. To work around this, you need to change the *ARG/ENV list size in 4K byte blocks*. The default value in AIX 5.x is *6*. This is way too small. You will either need root access or kindly ask your system administrator to change this value. To change it, you have two options: use `smitty` (a curses sys-admin tool on AIX) or do `root# chdev -l sys0 -a ncargs=40` on the command line

If you use smitty, you are looking for this:

<pre>root# smitty
=&gt; System Environments
    =&gt; Change / Show Characteristics of Operating System
         ARG/ENV list size in 4K byte blocks                [40]</pre>

40 seems to be a good number. It would be hard to guess the smallest number possible. This is not a problem in AIX 6.1, because the default seems to be &#8216;256'

 [1]: http://www.gentoo.org/proj/en/gentoo-alt/prefix/
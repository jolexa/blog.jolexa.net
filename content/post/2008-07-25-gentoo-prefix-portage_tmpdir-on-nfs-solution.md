---
author: Jeremy Olexa
categories:
- gentoo prefix
date: 2008-07-25T00:00:00Z
guid: http://jolexa.wordpress.com/?p=37
id: 37
tags:
- nfs
- portage
title: 'Gentoo Prefix: PORTAGE_TMPDIR on NFS solution.'
url: /2008/07/gentoo-prefix-portage_tmpdir-on-nfs-solution/
---

[Gentoo Prefix][1] allows you to place a &#8220;prefixed environment&#8221; wherever you would like. So, if you want to be able to access your prefix on a NFS network it would make sense to put the prefix in /home for example. I don&#8217;t have any solid numbers but I can imagine that the IO for the nfs server is pretty high when emerging. I would rather not suffer the penalties of compile on NFS but also I WOULD like to access PORTAGE\_TMPDIR from any host. For the longest time, I was trying to think of a solution for this, that is..to not compile on a NFS share but also be able to see/access PORTAGE\_TMPDIR no matter what host I am on in the network. This is a tricky situation that can be solved by setting PORTAGE_TMPDIR to another NFS mount which just happens to reside on the local machine!

I like it!!

My solution is to symlink $EPREFIX/var/tmp to the other NFS mount on the localhost. In my case, /net/$(hostname)/public/tmp.

**UPDATE**: The above &#8216;solution&#8217; isn&#8217;t that great. It resulted in a total time increase of about 12%. However, making the symlink point to the local hard drive resulted in a total time decrease of about 31%. (on emerge -e system) Therefore, my latest recommendation is to create the symlink as described originally and override it with PORTAGE_TMPDIR set to the local path.

 [1]: http://www.gentoo.org/proj/en/gentoo-alt/prefix/index.xml
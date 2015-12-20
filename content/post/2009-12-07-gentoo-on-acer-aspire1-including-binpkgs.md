---
author: Jeremy Olexa
categories:
- gentoo
date: 2009-12-07T00:00:00Z
guid: http://blog.jolexa.net/?p=574
id: 574
tags:
- aspire1
- linode
title: Gentoo on Acer Aspire1, including binpkgs
url: /2009/12/gentoo-on-acer-aspire1-including-binpkgs/
---

About a month ago, I installed Gentoo on the new-to-me [Acer Aspire1][1]. Installation went like anything else, it is just a normal x86 host after all. I don&#8217;t have *everything* on it working, because I don&#8217;t care. If you are looking for additional resources on getting the extras working, you may want to look [here][2] or [here][3].

The exciting part, that I got working and am ready to announce publicly, is my new **atom-x86 binpkg repo**. What makes this repo different than the binpkgs located on [tinderbox.dev.gentoo.org/default-linux][4] is that this repo has CFLAGS specific to the Intel Atom processor. I identified the compiler flags by using the following gcc command: `gcc -Q --help=target -march=native` and set the following `-march=prescott -mtune=generic -msahf`. On my linode ([review][5]) host, I have a chroot that builds all new packages in **my** world file once a day which comes from the aspire1. In this manor, I am able to always have binary packages available to me whenever I update my aspire1. Now, I have all the benefits of a source distro **and** the speed of a binary distro. <img src="http://blog.jolexa.net/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" />

If you would like to use this repo, set PORTAGE_BINHOST in /etc/make.conf and add &#8216;getbinpkg&#8217; to FEATURES (or use the emerge options directly). Be advised, that thought this works for me, I make no guarantees for you.

`PORTAGE_BINHOST="http://tinderbox.jolexa.net/atom-x86/"<br />
FEATURES="${FEATURES} getbinpkg"`

I also have an [html view][6] of the packages available.

 [1]: http://www.acer.com/aspireone/aspireone_8_9/
 [2]: http://wiki.debian.org/DebianAcerOne
 [3]: http://wiki.archlinux.org/index.php/Acer_Aspire_One
 [4]: http://tinderbox.dev.gentoo.org/default-linux/
 [5]: http://blog.jolexa.net/2009/05/13/in-depth-linode-vps-review/
 [6]: http://tinderbox.jolexa.net/html/atom-x86/
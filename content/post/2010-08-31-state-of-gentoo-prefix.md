---
author: Jeremy Olexa
categories:
- gentoo prefix
date: 2010-08-31T00:00:00Z
guid: http://blog.jolexa.net/?p=731
id: 731
title: State of Gentoo Prefix
url: /2010/08/state-of-gentoo-prefix/
---

The [Gentoo Prefix][1] project is still alive and still kicking. There has not been any major noteworthy highlights so you may not heard from us in some time. The number of users increases and the number of active contributors seems to stay the same or increase much more slowly. Gentoo Prefix was the reason I become a Gentoo Linux developer, so get involved..it is an easy gateway to being a Gentoo Developer if you are interested. <img src="http://blog.jolexa.net/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" />

Some interesting things to note that I have been working on:

  * My [~x86-linux binpkg repo][2] for Gentoo Linux hosts is still running every night. I use this to easily find simple build errors in packages before they hit *too* many users.
  * I started a ~amd64-linux binpkg repo to add coverage to my nightly automated testing. So, I&#8217;ve updated the [instructions][3] from the above post. This means that you can install your very own Gentoo Prefix installation on a Gentoo Linux host in 5 minutes for 32bit *or* 64 bit now.
  * While those are *updating* everynight. I am now **bootstrapping** everynight too. I set up a small script that debootstraps a Debian Lenny chroot and then sets up an Gentoo Prefix inside the chroot. This will help finding bootstrapping bugs that brand new users may hit. Often times bootstrapping is more sensitive/fragile to tree changes than just updating.
  * We are still migrating packages from the Gentoo Prefix tree to the Gentoo Linux tree. This is going slower than planned but there are not too many people working on it. Current: Over ~2000 packages migrated, still over 700 to go in our [overlay][4]. (Gentoo Prefix tree has [over 7000 packages][5] in it, but not all are tested/keyworded.)

 [1]: http://www.gentoo.org/proj/en/gentoo-alt/prefix/
 [2]: http://blog.jolexa.net/2010/03/23/installing-gentoo-prefix-on-a-gentoo-linux-host/
 [3]: http://dev.gentoo.org/~darkside/prefix/gentoo/bootstrap-gentoo.xml
 [4]: http://overlays.gentoo.org/proj/alt/browser/trunk/prefix-overlay/
 [5]: http://stats.prefix.freens.org/keywords-packages.png
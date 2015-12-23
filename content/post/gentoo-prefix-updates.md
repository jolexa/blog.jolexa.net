---
author: Jeremy Olexa
categories:
- gentoo prefix
date: 2008-12-12T00:00:00Z
guid: http://jolexa.wordpress.com/?p=176
id: 176
title: Gentoo Prefix Updates
aliases:
    - /2008/12/gentoo-prefix-updates/
---

It has been awhile since I last wrote about the [Gentoo Prefix][1] project. I will update the inquiring minds that want to know...

  * Gentoo Prefix's irc channel is now [#gentoo-prefix][2]. We use to inhabit #gentoo-alt but had some reports that new users were looking for us in -prefix. Also no one involved with the Prefix project had administrative powers over the old channel either. Since we were the only users of the -alt channel, I also had a redirect set up from there to the new channel.
  * New style profiles are done. Before I joined the Prefix project, our Linux support needed some love. The old profiles were mimicking the default-linux ones in gentoo-x86 but they didn't do inheritance very well. The new style profiles for Linux inherit the 2008 Gentoo profiles and allow Gentoo Prefix users to exploit the work done by the x86 & amd64 arch teams automatically. The old profiles contained a static multilib mask and other files.  Since Gentoo Prefix is anything but 'default' we chose a new root directory in $PORTDIR/profiles/ called 'prefix' -- this seemed to make the most sense. The new profiles are designed to go into the portage tree when appropriate without any major structure changes. Long story short, soon we will be deprecating the default-prefix/ profiles in favor of the new style.
  * We set up another rsync mirror. As expected, the load is [balanced][3] pretty well now.
  * Over 2000 [packages][4] in the Prefix tree.  Roughly 15% of the Gentoo portage tree.

I'm excited for this project (still). It seems that we have a new active user or two every week, submitting bug reports, helping out in irc, etc.

Thanks for listening.

 [1]: http://www.gentoo.org/proj/en/gentoo-alt/prefix/index.xml
 [2]: irc://irc.gentoo.org/#gentoo-prefix
 [3]: http://stats.prefix.freens.org/rsync-usage.png
 [4]: http://stats.prefix.freens.org/keywords-packages.png
---
author: Jeremy Olexa
categories:
- gentoo
date: 2011-04-10T00:00:00Z
guid: http://blog.jolexa.net/?p=813
id: 813
title: 'Gentoo: Infra team update'
url: /2011/04/gentoo-infra-team-update/
---

It has been awhile since I&#8217;ve posted about what I&#8217;ve been doing with Gentoo Linux. So, here is a general update for the team that I have been spending most of my time with.

  * You may have seen the [Bugzilla][1] upgrade that Christian was working on. Gentoo moved from the bottom of the [list][2] provided from one of the upstream devs to the top of the list. (As of April 2011)
  * I finally put an idea of mine into reality of graphing the number of &#8220;emerge &#8211;sync&#8217;s&#8221; against the rsync.gentoo.org rotation. [Full graph][3] and [last 4 weeks][4]
  * A new reporting website was born: <http://qa-reports.gentoo.org/> &#8211; The vision was: &#8220;Many Gentoo devs have useful scripts and many people complain that there is not a central place to see all the output.&#8221; This site is a solution, and open for all. repo: [qa-scripts.git][5]
  * A new &#8220;Get Gentoo at a glance&#8221; website was born: <http://get.gentoo.org/> that Matthew is still working on, so maybe expect some layout changes &#8211; The motivation for this was inspired from [bug 350271][6], repo: [get-gentoo.git][7] 
      * Some behind the scenes work involving our mastermirror service. The current hardware running this important service is one of the oldest hosts we have.</ul> 
    Of course, there is always the untold hours to keep Gentoo Linux infrastructure running happily for all customers. As a final note, if you have a good idea, feel free to propose it via bugs or IRC. We will listen and definately avoid [NIH][8] syndrome if we can. Cheers.

 [1]: http://bugs.gentoo.org
 [2]: http://lpsolit.wordpress.com/bugzilla-usage-worldwide/
 [3]: http://mirrorstats.gentoo.org/rsync/rsync-usage.png
 [4]: http://mirrorstats.gentoo.org/rsync/rsync-usage-last4weeks.png
 [5]: http://git.overlays.gentoo.org/gitweb/?p=proj/qa-scripts.git;a=summary
 [6]: https://bugs.gentoo.org/show_bug.cgi?id=350271
 [7]: http://git.overlays.gentoo.org/gitweb/?p=proj/get-gentoo.git;a=summary
 [8]: http://en.wikipedia.org/wiki/NIH_syndrome
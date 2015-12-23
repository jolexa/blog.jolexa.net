---
author: Jeremy Olexa
categories:
- gentoo
date: 2010-06-13T00:00:00Z
guid: http://blog.jolexa.net/?p=699
id: 699
title: 'Gentoo Mirrors: Mixed IPv4/IPv6 rotations'
aliases:
    - /2010/06/gentoo-mirrors-mixed-ipv4ipv6-rotations/
---

*Prenote: According to [tunnelbroker.net][1] there are only 426 days until IPv4 exhaustion, at the time of this writing.*

You might have seen me say that the mirror-admin team will support IPv6 rotations &#8220;soon&#8221; multiple times. It took much discussion, mainly because it is a low priority subject, and thus much time as well. I say it is low priority because on our official IPv6 (*rsync.ipv6.gentoo.org*) rotation we only see about ~10-15 client syncs per day out of ~23000. *Yes, there will be some stats generated &#8220;soon&#8221; for some value of soon <img src="http://blog.jolexa.net/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" />*. We decided to move away from dedicated v4 and v6 rotations and instead used mixed rotations.

But, I digress, the point of this post is to highlight that the *rsync.de.gentoo.org* rotation will be the first to get full IPv6 support. That is, if the sponsor has IPv6. I just added one IPv6 mirror to the rotation now. In a few days, I'll make a call to other members in the de rotation and then it will be declared full support to the extent possible. From there, the timeline will go something like this:

  1. Call for more .de mirrors that have IPv6 to get added to the rotation
  2. Call for the rest of the community mirrors that have IPv6 to get added to the rotations, not just .de.
  3. Wait some time to let that settle out and see if there are any problems that develop.
  4. Enable mixed rotations on the country rotations using the individual country v6 addresses collected above.
  5. Enable mixed rotation on *rsync.gentoo.org* and deprecate *rsync.ipv6.gentoo.org*

For clients, the default behavior of rsync on an IPv6 capable system is to use IPv6 if the DNS query returns some v6 address. If you want to explicitly use IPv4 you need to pass &#8220;-4&#8243; to rsync. You can specify that in `/etc/make.conf` with the `PORTAGE_RSYNC_EXTRA_OPTS` variable. Rsync does the proper thing most of the time as my [testing][2] has revealed. With that said, I don't anticipate any issues here, but please file a bug to mirror-admins if something comes up. I would be very interested in hearing about it. I'm assuming no issues, so the future plans will not be announced and it will just happen.

 [1]: http://tunnelbroker.net/
 [2]: http://dev.gentoo.org/~darkside/perm/ipv6-tests.txt
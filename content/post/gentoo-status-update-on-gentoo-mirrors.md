---
author: Jeremy Olexa
categories:
- gentoo
date: 2010-03-29T00:00:00Z
guid: http://blog.jolexa.net/?p=657
id: 657
title: 'Gentoo: Status update on Gentoo Mirrors'
aliases:
    - /2010/03/gentoo-status-update-on-gentoo-mirrors/
---

In the past few months, there have been a number of things going on. I want to share those with the readers:

  * New Document: <http://www.gentoo.org/main/en/mirrors-rsync.xml> The tools-portage team has made [app-portage/mirrorselect][1] use this document to help users select rsync mirrors in a similar fashion as distfile mirrors. Additionally, I have a [bug][2] open to include this page in docs and/or the homepage.
  * [http://mirrorstats.gentoo.org][3] -- tracks community distfile mirrors for freshness. This page has been around before, but now it supports rsync and IPv6 as well.
  * <http://mirrorstats.gentoo.org/rsync> -- tracks community gentoo-portage mirrors for freshness. This page is brand new. There was an old implementation but it wasn't kept up to date as we added new mirrors.
  * New mirror-admin team member, Mark (Halcy0n).

Coming up next: Better IPv6 support, including new rotations for IPv6 only and mixed rotations.

 [1]: http://packages.gentoo.org/package/app-portage/mirrorselect
 [2]: http://bugs.gentoo.org/309073
 [3]: http://mirrorstats.gentoo.org/
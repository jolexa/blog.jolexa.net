---
author: Jeremy Olexa
categories:
- gentoo
date: 2009-08-01T00:00:00Z
guid: http://blog.jolexa.net/?p=472
id: 472
tags:
- xfce
title: 'Gentoo: How to handle &#8220;xfce extras&#8221;?'
aliases:
    - /2009/08/gentoo-how-to-handle-xfce-extras/
---

We are cleaning up the XFCE ebuilds via a [new eclass][1]. The current eclasses do not make maintenance any easier, like they should. Some other things on the TODO list include:

  * Remove xfce-4.4 from the tree. 4.6.1 has long since been stable. Caveats: We promised mips that they could have a ~month to keyword 4.6.1. [Gentoo Prefix][2] can't easily use 4.6.1 due to the xorg-server dependency.
  * Rename plugins to match what upstream calls them. For example, what Gentoo calls `xfce-extra/xfce4-cpu-freq`, upstream calls `xfce4-cpufreq-plugin` This is true of all plugins.
  * Remove the meta extras package, `xfce-base/xfce4-extras`.

The last bullet point is where I would like to gain input on how to provide the best user experience for xfce users on Gentoo. We are contemplating on removing the meta package because: it is tricky to add new plugins to it (requires more arch team work via rev bumps). Renaming plugins will require more work because of the meta package. And finally, what is the point of this meta package (some would ask) -- outdated, etc.

So some possible options:

  1. Remove the meta package completely and let the user emerge what they want. We are leaning towards this one.
  2. Provide an USE flag for `xfce-base/xfce4` to emerge all these extras, since it is a meta package anyway. This allows arch teams to mask the use flag if they don't want to deal with all the plugins. Not a good option though, in my opinion.
  3. Revbump the meta package everytime there is a new plugin added to the tree.
  4. Other option that I haven't thought of?

So, what is it? What would provide the best XFCE experience on Gentoo?

 [1]: http://archives.gentoo.org/gentoo-dev/msg_1b936bfecc26ef53d2572006d4556aef.xml
 [2]: http://www.gentoo.org/proj/en/gentoo-alt/prefix/
---
author: Jeremy Olexa
categories:
- gentoo
date: 2012-02-14T00:00:00Z
guid: http://blog.jolexa.net/?p=929
id: 929
tags:
- linode
title: 'Linode: don&#8217;t use barriers and ext-4'
aliases:
    - /2012/02/linode-dont-use-barriers-and-ext-4/
---

On my [Linode][1] running [Gentoo Linux][2], I converted to ext4 some time ago and didn&#8217;t have any issues until now for some reason, mostly because I don&#8217;t reboot *that* often to notice. The symptoms are :

Every reboot, you will see:

`EXT4-fs error (device xvda): ext4_journal_start_sb:296: Detected aborted journal<br />
EXT4-fs (xvda): Remounting filesystem read-only<br />
`  
and a subsequent reboot fixes this by a forced run of fsck. Now that is an annoying one, every other reboot results in a crippled system and otherwise a fsck &#8220;fixes&#8221; it and you have no issues.

So, after some research I found that [barriers are enabled by default][3] and they don&#8217;t really make sense on a hosted vm guest. I qualify the last statement by google research, not an expert but it seems that the common knowledge is that disabling barriers is safe for battery backed up storage, and Linode disabled barriers completly.

The solution to the above problem is simply disabling barriers. Like so:

In /etc/fstab:  
`/dev/xvda   /            ext4    noatime,barrier=0              0 1`

Source: [Linode Forums][4]

 [1]: http://www.linode.com/?r=b4fa70eb87c890e08baf7b0c7852fb7cecd8963b
 [2]: http://www.gentoo.org/
 [3]: http://kernelnewbies.org/Ext4#head-25c0a1275a571f7332fa196d4437c38e79f39f63
 [4]: http://forum.linode.com/viewtopic.php?t=8259
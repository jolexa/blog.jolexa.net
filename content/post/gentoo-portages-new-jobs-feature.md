---
author: Jeremy Olexa
categories:
- gentoo
- gentoo prefix
date: 2008-07-24T00:00:00Z
guid: http://jolexa.wordpress.com/?p=17
id: 17
tags:
- portage
title: 'Gentoo: Portage's new --jobs feature'
aliases:
    - /2008/07/gentoo-portages-new-jobs-feature/
---

Yesterday, zmedico wrote about <a href="http://planet.gentoo.org/developers/zmedico/2008/07/23/portage_parallel_builds" target="_blank">building multiple packages in parallel</a> with Portage-2.2_rc2. In [Gentoo Prefix][1], we had a sneak peak to this feature, so I have had some time to play with it on my dual-quad core box. Some timing results that you may like:

emerge -e system (excluding sys-devel/gcc)

As a baseline:

> `With --jobs=1 and MAKEOPTS=16, load-average=9:<br />
real    77m54.290s<br />
user    41m46.086s<br />
sys     29m14.598s`

Because I was skeptical of what `--jobs` could really do, I decided to start with small number of parallel jobs:

> `With --jobs=3, MAKEOPTS=16, load-average=9:<br />
real    61m30.181s<br />
user    42m23.398s<br />
sys     32m32.009s`

While that was running, I noticed a very significant amount of time where my cores were idle, thanks to the handy little xfce-extra/xfce4-cpugraph widget. So, I turned `--jobs` up again:

> `With --jobs=5, MAKEOPTS=16, load-average=9:<br />
real    58m5.388s<br />
user    42m35.721s<br />
sys     34m46.950s`

Meh, not much improvement there. Surprising, but I suspect that I may be reaching the limits of the parallelization (dependencies, etc).

> `With --jobs=10, MAKEOPTS=16, load-average=9:<br />
real    58m9.824s<br />
user    42m43.525s<br />
sys     37m57.234s`

(And actually, a quick visual scan showed load averages staying below 4. Only a few times did I see the average above 8 )

Relying solely on load-average to keep my system usable:

> `With --jobs=40, MAKEOPTS=40 load-average=15:<br />
real    58m45.106s<br />
user    43m15.129s<br />
sys     40m47.949s`

The highest load average I visually saw was 23. But my load average was mostly always greater than 4, so this means that my procs are obviously getting used more but I must have hit another bottleneck.

> `NOTES:<br />
-emerge -pe system was preformed before each time trial to assume the depgraph was in cache.<br />
-84 packages total<br />
-no ccache/distcc running`

Conclusion: 20 minutes? ~30% speedup. Wow. Good! Quite significant even. Assuming you have cores/procs to spare, go ahead and crank up those `--jobs`. It is nice to be able to make the `./configure` step not be the bottleneck anymore. 😉 I will keep testing and see if I can get the time down even farther (although, unlikely based on the last time trial).

Test requests? Please leave a comment.

 [1]: http://www.gentoo.org/proj/en/gentoo-alt/prefix/index.xml
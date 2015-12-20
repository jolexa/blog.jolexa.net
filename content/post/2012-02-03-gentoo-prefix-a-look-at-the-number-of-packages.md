---
author: Jeremy Olexa
categories:
- gentoo prefix
date: 2012-02-03T00:00:00Z
guid: http://blog.jolexa.net/?p=919
id: 919
title: 'Gentoo Prefix: A look at the number of packages'
url: /2012/02/gentoo-prefix-a-look-at-the-number-of-packages/
---

[Gentoo Prefix][1] is still alive and going strong. In my opinion, Gentoo Prefix remains a strong point of Gentoo Linux and really establishes that Gentoo Linux **is** a [metadistribution][2]. In this post I want to focus on the numbers. The number of packages in the Gentoo Prefix tree, specifically. But first, a history lesson. It wasn&#8217;t until EAPI3 in Gentoo that &#8220;allowed&#8221; Gentoo Prefix variables into the main Gentoo Linux tree. That was in late 2011, but Gentoo Prefix existed much before then, all the way back to [2006][3] (at least). Before EAPI3, the prefix team made slight modifications to ebuilds and placed them in a [repo][4] and called it the tree of packages for Gentoo Prefix. This worked fine, but we had growing pains. The major issue was that we were getting too successful to manage the increased contributions from users. In other words, as the number of &#8220;forked&#8221; packages grew, the amount of maintenance time increased greatly &#8211; this is due to the fact that it is a chore to keep our forks synced. At least, a large chore for a small team. This is why we looked for help and adoption from the other pool of 200 Gentoo Developers, hence EAPI3 and beyond. Since supporting Gentoo Prefix is not a big use of overall developer time, this has gone over quite well in my opinion &#8211; yes, there are some pain points at times I do realize. Enough history, here are the numbers:

  * Number of packages in Gentoo Linux: **15554** packages in 154 categories.
  * Number of total* packages in Gentoo Prefix: 9483 packages in 154 categories.
  * Number of KEYWORDED packages in Gentoo Prefix: About **3000** for the most popular arch
  * Number of packages still NOT in the main Gentoo Linux tree: 369 packages

* The total packages in the tree also contains non-keyworded packages because that just makes life simple. Once packages started migrating to the main tree, I helped think of this &#8220;[whitelist][5]&#8221; concept. The short version of the whitelist is that if a package is listed in that text file, it gets included in the Gentoo Prefix tree as a direct copy of the version in the Gentoo Linux tree. The presense of the package in the old repo means that it is used instead. *Eventually*, this concept will go away and we will overlay the Gentoo Linux tree directly.

So why is it taking so long to migrate ALL packages to the Gentoo Linux tree? Well, that is where the rubber meets the road and we get into roadblocks. A roadblock for us could be a number of things, such as a disagreement with the Gentoo Linux maintainer, some patches existing that we don&#8217;t feel are a good fit for Gentoo Linux, or even us being lazy and not submitting stuff to upstream. We also don&#8217;t want to push invasive changes to Gentoo Linux for critical packages, like the toolchain for example.

It has long since been our agenda to not add anymore packages to the old repo and going forward only adding new stuff to Gentoo Linux directly. I hope we can make a dent in those remaining 369 in 2012!

 [1]: http://www.gentoo.org/proj/en/gentoo-alt/prefix/
 [2]: http://goo.gl/px3KW
 [3]: http://stats.prefix.freens.org/keywords-packages.png
 [4]: http://overlays.gentoo.org/proj/alt/browser/trunk/prefix-overlay
 [5]: http://overlays.gentoo.org/proj/alt/browser/trunk/prefix-overlay/whitelist.txt
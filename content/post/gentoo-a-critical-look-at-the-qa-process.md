---
author: Jeremy Olexa
categories:
- gentoo
date: 2010-12-29T00:00:00Z
guid: http://blog.jolexa.net/?p=760
id: 760
title: 'Gentoo: A critical look at the QA process'
aliases:
    - /2010/12/gentoo-a-critical-look-at-the-qa-process/
---

*This post will probably annoy some people, or bring bad &#8220;spotlight&#8221; to Gentoo Linux. I call it a case study, but it is just my opinions...*

The QA team has said that there is some sort of &#8220;policy&#8221; on masking packages that break reverse dependencies. I'll subscribe that that policy for the sake of not breaking users machines on purpose, however, let's take a look at the current case study: **poppler-0.16**

package.mask (in context, name removed because it isn't needed):  
+# Masked because of ABI change, breaks  
+# depending packages. Keep masked until depended packages  
+# got fixed (adjusted dependency or fixing version bump).  
+# tracer bug 349918  
+=app-text/poppler-0.16.0

...and there was some discussion on IRC. The QA team (at least a few members) says that the *&#8220;tree is broken&#8221;* with poppler-0.16. At time of this writing, 7 packages were reported on the tracker bug and 2 were fixed already. So, it is my opinion that progress for Gentoo is hampered because of this masking. I'll explain why but first the different theories to package testing that I have observed.

<u>Theory 1:</u>  
Run full arch for stability. The problem with this theory is that some group of people/machines need to test ~arch packages first and report issues, otherwise they will hit the stable users and the concept of the arch/~arch tree will break down. The advantage being less compilation in general, and the goal being stability or less breakage. I consider this theory for people that are new to Gentoo.

<u>Theory 2:</u>  
Run full ~arch to find interaction issues. This is a fine theory, but not for me. Even though I am a Gentoo dev, I don't have copious amounts of free time to contribute how I want if I am running ~arch. It is my personal opinion that users should **not** run full ~arch if they do not want to be bothered contributing back to gentoo/upstream, via bug reports, patches, etc. The advantage here, is that full ~arch users/machines will be able to find issues with the package before it is deemed &#8220;stable&#8221; &#8211; in theory, finding issues fast and being fixed fast. The downside being more compilation, occasional breakage, and/or random mistakes (devs are human, after-all). The Gentoo Handbook [says][1] that ~arch needs more testing and isn't enabled by default. I'd consider this theory for power users. &#8220;I only want the latest packages&#8221; is no excuse for using this theory if you are going to complain about the above mentioned downsides.

<u>Theory 3:</u>  
Run mostly arch and a few ~arch packages. This is what most of my machines run. That is, arch (stable) system and ~arch for packages that I maintain (or help maintain). The advantage here is what I consider *real* integration testing. The theory is that everything in ~arch will become arch, at one point. These ~arch packages are coming in one-by-one, so it makes no sense to *only* test a full ~arch tree if the package will be entering the arch tree. This is what the arch team does when they mark packages stable. The downside being, more management, maybe some dependency issues if they aren't stated properly, etc. I'd consider this theory for people that prefer stability but enjoy the latest packages for some apps.

*I think it is valuable to have a user base that is doing all of those theories. ...back to poppler.*

As we have seen in the past, once a package is &#8220;masked for testing&#8221; &#8211; it may take years to lift that mask because no one actually tests it. And why should you? It is masked and therefore not even in the *testing* category (~arch)!! Bingo, the crux of this case study. Technically speaking, there is nothing wrong with poppler-0.16.0, it is perfectly fine to be in ~arch by its own criteria. On the other hand, it's ABI change breaks packages that haven't been fixed to work with the new ABI yet. By masking a package that changes ABI with a soname change, it could (and should, in my opinion) be considered slowing progress for Gentoo. It should **not** be considered that the &#8220;[whole] tree is broken&#8221; &#8211; these 7 packages may just be the tip of the iceberg in the breakage category, but we won't know if it is masked and users are not contributing. Let's remind ourselves that the arch tree is still functioning properly at this point and &#8220;stable&#8221; users won't see any issues...now. For them, thankfully, the ~arch users (including devs) are contributing to Gentoo via bug reports & patches. It should also be noted that nothing is being broke &#8220;on purpose&#8221; here, bugs are being filed and bugs are being fixed &#8211; this is the goal of a software project, right?

So, the way I see it, is a chain reaction.

  1. Package enters the tree that causes a slight nuisance. 7/14205 known packages affected or 0.04 % of the tree.
  2. The QA team deems this problem package as too severe to allow in ~arch and masks it. (Personal opinion is the 0.04% of the tree is not a servere problem)
  3. The maintainer of the problem package is trying to identify breakages by leaving it in ~arch (and relying on the power users)
  4. Since the package is masked, the effects of this problem package will be prolonged because &#8220;no one&#8221; will be testing it in ~arch.
  5. The 7 affected packages are fixed, the problem package is unmasked
  6. A new set of affected packages are found
  7. repeat above

And now for some hard questions:

  * How should Gentoo make it easier to add packages that break reverse dependencies if ~arch isn't appropriate and nothing really happens when package.mask'd?
  * Is ~arch becoming a second stable tree and thus losing value in general?
  * Related, are overlays hurting Gentoo? The Xfce team subscribes to the theory that ~arch is *the* place to get useful testing feedback. The Xfce pre releases are in ~arch so the final release is ready for arch asap. This means that we have less work in the long run because we are maintaining less versions sooner and in better quality. The GNOME team subscribes to the theory that their overlay is for new releases and it takes longer to get packages in ~arch and thus longer to arch (my observation only, not official)
  * portage-2.2 has this cool &#8220;preserved-libs&#8221; feature that wouldn't help compilation issues in this case but might help runtime issues by keeping the old lib(s) around. I like this feature but it is still masked for majority of the users, even though many devs are using it &#8211; is it time to release it to the world with all the [bugs][2] it has?
  * Related, does masking a feature block contributors? I want to say yes simply due to exposure.

*Disclaimer: This was in NO WAY meant to be a personal attack against anyone. I can live with agreeing to disagree with people. But I can't agree with not bringing something up because it is a controversial topic.*

 [1]: http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=1#doc_chap5
 [2]: http://bugs.gentoo.org/240323
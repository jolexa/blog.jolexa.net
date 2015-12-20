---
author: Jeremy Olexa
categories:
- gentoo
date: 2009-02-25T00:00:00Z
guid: http://blog.jolexa.net/?p=259
id: 259
title: 'Gentoo: Yearly Releases &#8211; help or hurt Gentoo?'
url: /2009/02/gentoo-yearly-releases-help-or-hurt-gentoo/
---

I have been thinking for awhile now and can&#8217;t convince myself of an answer.

**Does the lack of yearly releases help or hurt Gentoo?**

I enjoy Gentoo because I never have to re-install my host. The &#8220;rolling release&#8221; model is great, a model shared by nearly all(?) source-based distros. However, with our new automated weekly stages &#8211; which I think are a great idea, we lose a few things. In no particular order, we lose:

  * PR &#8211; new &#8216;releases&#8217; generate a buzz on the distro sites and blog-o-sphere around the world.
  * Ability to say &#8220;we no longer support base installs before 20XX.Y&#8221; &#8211; repo changes, bash versions, portage upgrades, etc.
  * The appearance of activity. (This point is debatable)

However, with that being said, I think that yearly releases are also pointless with the presence of weekly stages, because:

  * &#8216;releases&#8217; mean nothing to existing hosts &#8211; the only thing you have to do is update your make.profile symlink. There is no other direct benefit unless we tie features to a new profile.
  * It is a metric ton of workload to get a stage out there that is guaranteed to work for a year.
  * Missing man-power for the release schedule. As evident by the regular occurrence of releases slipping behind schedule.
  * Obviously it is easy to script or automate. Good job release team on getting this done.
  * By the end-of-life date of the stage (normally a year, sometimes longer), you have a ton of old packages to update. Meaning, weekly stages provide a much faster complete install.

So, how do I solve the above? Well I&#8217;m not exactly sure. One idea I have is to **automatically create new profiles every 6 months**. This would allow PR to continue. Individual arch teams can decide how long to keep old profiles &#8211; I&#8217;d recommend one year. However, updates to the profiles would only go into the latest profile &#8211; so it would be advantageous to update the profile asap for users. One particular downside about **not** creating new profiles is that they will never be eligible for EAPI upgrades, only new profiles are eligible. I don&#8217;t exactly see a downside to this idea besides it being some work every 6 months for someone.

Does anyone else have opinions on this subject? Or other ideas on how to gain back what we lose as presented above?
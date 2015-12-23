---
author: Jeremy Olexa
categories:
- gentoo
date: 2009-10-03T00:00:00Z
guid: http://blog.jolexa.net/?p=503
id: 503
tags:
- linode
title: Re-locating a linode installation
aliases:
    - /2009/10/re-locating-a-linode-installation/
---

I recently had a bit of downtime on my linode. If you are wondering what a &#8216;*linode*&#8216; is, check out my [review][1] or the [website][2]. And a big thank you to the folks that used my [referral code][3] when they got setup with linode themselves, you guys rock!

So, about my recent 1/2 day downtime. It was self-inflicted because I wanted to move to a different datacenter. I moved my linode from Newark, NJ to Dallas, TX. It is quite a long story, but it boils down to a problem with my ISP (Comcast). I was only able to pull 100K/s from the Newark datacenter and 2-3M/s from the others. This was unacceptable. I tried to get it escalated past Comcast's frontline support but they kept asking me questions like *"Do you use a router? If so, each computer only gets 1/2 the speed"* & *"Every computer is different. I'm glad that you can get 3M/s from another host, that is really good"* **Sigh.**

At least Linode's customer server was helpful and allowed me to work around the <censored> ISP. The steps to move a linode are as follows:

  1. File a support request. (My initial request was answered in 11 minutes)
  2. Shutdown your linode
  3. Hit the &#8216;migrate' button, after support sets up your migration
  4. Wait for the transfer. My total transfer time was ~43 minutes (~6G to transfer). This was pretty fast throughput, in my opinion
  5. Meanwhile, update your DNS for your new IP.
  6. Since you can queue up a boot job, I just let it go and checked in on it a couple hours later. Magic, it was online. <img src="http://blog.jolexa.net/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" />

So, to finish the story off. Linode++, Comcast--. I wish I didn't need to do something like this, I wish my ISP was...I don't know...smart?

 [1]: http://blog.jolexa.net/2009/05/13/in-depth-linode-vps-review/
 [2]: http://linode.com
 [3]: http://www.linode.com/?r=b4fa70eb87c890e08baf7b0c7852fb7cecd8963b
---
author: Jeremy Olexa
categories:
- gentoo
date: 2009-05-13T00:00:00Z
guid: http://blog.jolexa.net/?p=367
id: 367
tags:
- linode
title: In depth Linode (VPS) review
url: /2009/05/in-depth-linode-vps-review/
---

This is a follow up to my [initial linode post][1].

[Linode][2] is a VPS provider. Linode stands for &#8220;Linux Node.&#8221; They offer relatively up to date initial Gentoo installations, among other distros.

Overall Grade: 9.5/10 (because no one is ever perfect)

## <span style="text-decoration: underline;">Performance:</span>

This is probably the one area that everyone is concerned about from VPS providers. Linode provides linodes on pretty beefy hardware, 4 CPUs/host:

`%% cat /proc/cpuinfo |grep "model name"<br />
model name      : Intel(R) Xeon(R) CPU           L5420  @ 2.50GHz`

With the Linode 360 plan, there are 40 guests on [each host][3]. That means I am splitting the cpu time with 39 others evenly and I have the full potential of CPU time if no one else is using the CPU cycles. I am a nice citizen of the host and only have my MAKEOPTS set to -j2. With that I get times like this:

`%% genlop -t gcc<br />
Mon Apr  6 04:54:53 2009 >>> sys-devel/gcc-4.3.2-r3<br />
merge time: 24 minutes and 9 seconds.<br />
%% genlop -t www-servers/lighttpd<br />
Fri Jan  2 19:48:06 2009 >>> www-servers/lighttpd-1.4.20<br />
merge time: 1 minute and 38 seconds.`

The above times compare very nicely to my personal hardware that I have, so I cannot complain about CPU contention.

I do notice some I/O contention during &#8220;peak&#8221; hours. This will result in some slower compile times for the short packages. Since the 360 only offers 360MB of RAM, I cannot leverage that either. This is not a large concern on my part and I am sure it is alot better than other companies that may oversell their hardware.  
`<br />
%% sudo hdparm -Tt /dev/xvda<br />
/dev/xvda:<br />
Timing cached reads:   7350 MB in  1.99 seconds = 3685.77 MB/sec<br />
Timing buffered disk reads:   36 MB in  3.12 seconds =  11.54 MB/sec`

These timings are not great, I agree.

## <span style="text-decoration: underline;">Customer Service / Service Requests:</span>

I have not had a reason to submit a hardware service request. So, my experience in this area is limited to two administrative issues that I needed to take care of with regards to billing changes. Linode gets a 10/10 in this area. The customer service staff member (Tom Asaro) resolved my requests within hours at very *odd* times. I normally do most of my hobby work during the evening, I submitted these requests around midnight (GMT -5) and they were resolved by the time I woke up. Keep in mind, that my requests were not even close to top priority &#8211; I would have been happy if they were resolved within a week.

Regarding hardware issues, the Linode staff members are very responsive to any DDoS attacks, host crashes, etc. The forums activity by staff members is top notch, always keeping us informed. You can find staff members in the irc channel very frequently, even answering my stupid questions. 😛

## <span style="text-decoration: underline;">Hosted Services:</span>

My Linode host runs only 3 domains (incl this blog) and email. I share it with 2 other friends, we all host pet projects on it. (As an aside, splitting it is a very cheap way to get a VPS)

    
    %% rc-status
    Runlevel: default
    dovecot                                                            [ started  ]
    lighttpd                                                           [ started  ]
    local                                                              [ started  ]
    mysql                                                              [ started  ]
    net.eth0                                                           [ started  ]
    netmount                                                           [ started  ]
    ntpd                                                               [ started  ]
    postfix                                                            [ started  ]
    rsyncd                                                             [ started  ]
    saslauthd                                                          [ started  ]
    sshd                                                               [ started  ]
    syslog-ng                                                          [ started  ]
    uptimed                                                            [ started  ]
    vixie-cron                                                         [ started  ]
    xinetd                                                             [ started  ]
    

## <span style="text-decoration: underline;">UI / Admin Interface:</span>

The administrative interface is a pleasure to use. I can see my bandwidth usage, cpu usage, and I/O usage very easily. They look like the standard munin graphs &#8211; very handy.

DNS Manager: This is a VERY handy tool, especially when you don&#8217;t have the patience/time to set up your own DNS solution. The DNS manager is a very nice interface to Linode&#8217;s DNS servers. It is esentially one click DNS management. Nothing more to say, it rocks.

The admin interface get a 8.5/10.

## <span style="text-decoration: underline;">Other Thoughts:</span>

  * Well, everyone I have talked to has been thrilled with Linode. In my opinion, they have great products and at great prices. I must say I have **not been disappointed** one bit in the 3 months of experience I have with them.
  * <span style="text-decoration: line-through;">My current uptime is 80 days. This is so low because I choose to reboot the host when testing to make sure that all my services were set-up correctly.</span>
  * My current uptime is 6 days, because I choose to reboot to take advantage of the **free** space upgrade. <img src="http://blog.jolexa.net/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" />
  * 10% off if you prepay for a year, no contracts so you can cancel at any time.
  * I did some stress testing, I can invoke the OOM killer with `MAKEOPTS="-j5" & --jobs=2` while emerging. I think it happened during glibc emerge. I guess this is to be expected for what I have access to.

### <span style="text-decoration: underline;">Shameless Plug:</span>

If you decide to get a Linode plan after reading this, please use my referral code: <http://www.linode.com/?r=b4fa70eb87c890e08baf7b0c7852fb7cecd8963b><img src="http://blog.jolexa.net/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" /> Thanks!

 [1]: http://blog.jolexa.net/2009/02/04/new-online-home/
 [2]: http://linode.com
 [3]: http://www.linode.com/faq.cfm#how-many-linodes-share-a-host
---
author: Jeremy Olexa
categories:
- linux
date: 2011-05-06T00:00:00Z
guid: http://blog.jolexa.net/?p=824
id: 824
tags:
- linode
- vps
title: 'Linode: Migrating from HE.net IPv6 tunnel to native IPv6'
url: /2011/05/linode-migrating-from-he-net-ipv6-tunnel-to-native-ipv6/
---

A few days ago, [Linode.com][1] [announced][2] native IPv6 [roll out][3] in their datacenters. Now, while I haven&#8217;t wrote about Linode in the past 6 months, I am still a happy customer. I am documenting the steps I took to migrate *away* from my HE.net [tunnel][4].

  1. Set the TTL low on any DNS addresses that you will be changing. Ideally, do this a fair amount ahead of time.
  2. Send in a support ticket to get your /64 allocated. Sidenote: response time: 4 minutes
  3. Reboot &#8216;node so the backend system deploys your IPv6 after it was allocated. [Verify][5] IPV6 status on your &#8216;node.
  4. From a different IPv6 host, run `nmap -6` on the existing address to verify listening services.
  5. Update DNS, define static networking, be happy.

 [1]: http://www.linode.com/index.cfm
 [2]: http://blog.linode.com/2011/05/03/linode-launches-native-ipv6-support/
 [3]: http://www.linode.com/IPv6/
 [4]: http://blog.jolexa.net/2010/04/16/gentoo-static-ipv4-ipv6-he-net-tunnel/
 [5]: http://library.linode.com/networking/ipv6
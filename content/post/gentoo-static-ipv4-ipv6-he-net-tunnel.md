---
author: Jeremy Olexa
categories:
- gentoo
date: 2010-04-16T00:00:00Z
guid: http://blog.jolexa.net/?p=669
id: 669
tags:
- linode
- vps
title: 'Gentoo: static IPv4 &#038; IPv6 (HE.net tunnel)'
aliases:
    - /2010/04/gentoo-static-ipv4-ipv6-he-net-tunnel/
---

For some reason, [Linode.com][1] (my [review][2]) sets up their hosts to use dhcpd to grab the static IPv4 address on boot. This is in contrast to [Host Virtual][3] which uses the "Gentoo-way" to set static addresses. Now, there isn't anything exactly *wrong* with using dhcpd on hosts with static addresses, actually, it may be simpler (and this is probably why they did it). However, I don't like it for a few reasons, booting takes longer as it probes for IPs and it uses extra space for dhcpd binary on a low resource host -- this includes extra time for updating. I know these are minor issues, but they bother me, at least. So, let's take the easy way and assign eth0 the IP is should have:

    
    Snippet from: /etc/conf.d/net
    config_eth0=(
        "69.164.197.24 netmask 255.255.255.0 broadcast 69.164.197.255"
        )
    routes_eth0=(
        "default via 69.164.197.1"
        )

So, that makes sense for all the right reasons and there is not much more to say. Let's shift the attention to IPv6. Linode doesn't offer IPv6 by default unlike their competition. To be honest, I don't **need** IPv6, but it is something fun to play with and I have been learning something. It turns out that my tunnel from [HE.net][4] (free) is actually lower latency to some parts of the world than my IPv4 route and almost always less hops. Using the great [examples][5] from Robin (robbat2), I was able to put my IPv6 tunnel in `/etc/conf.d/net` too, so that is it created on reboot as tun0. Makes sense to do, right?

    Snippet from: /etc/conf.d/net
    HE="2001:0470" # 2001:470::/32 is the HE.net allocation
    v6net64="${HE}:1f0f:2a0" # your initial /64 allocation from HE.net
    
    # HE.net tunnel configuration
    link_tun0="eth0" # tunnel IFACE (internet-facing iface, eg ppp0/eth0)
    # tunnel IPv4 endpoint, remote, HE.net tells you this
    iptunnel_tun0_remote="216.218.224.42"
    # tunnel IPv4 endpoint, local
    # this is the address of IFACE ${link_tun0}
    iptunnel_tun0_local="69.164.197.24"
    
    iptunnel_tun0="mode sit remote ${iptunnel_tun0_remote} local
    ${iptunnel_tun0_local} ttl 255 dev ${link_tun0}"
    mtu_tun0=1280
    config_tun0="${v6net64}::2/64" # /126
    routes_tun0="default via ${v6net64}::1"

This is not *exactly* perfect, because I am using my tunnel's /64 as my IPv6 address. The purists might say something about this practice, I respect that, but don't really mind for my personal use. Of course, if you didn't have a tunnel and instead had *native* IPv6, it would look a lot simpler because you just add the IP and route to the interface it is on, probably eth0.

 [1]: http://www.linode.com/index.cfm
 [2]: http://blog.jolexa.net/2009/05/13/in-depth-linode-vps-review/
 [3]: http://vr.org/
 [4]: http://tunnelbroker.net/
 [5]: http://robbat2.livejournal.com/235829.html
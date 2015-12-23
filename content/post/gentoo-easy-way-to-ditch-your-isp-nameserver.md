---
author: Jeremy Olexa
categories:
- gentoo
date: 2010-01-12T00:00:00Z
guid: http://blog.jolexa.net/?p=619
id: 619
tags:
- dns
- linode
title: 'Gentoo: Easy way to ditch your ISP nameserver'
aliases:
    - /2010/01/gentoo-easy-way-to-ditch-your-isp-nameserver/
---

My [linode][1] is now my *personal* DNS resolver. I have officially ditched the ISP nameservers from this point forward now that I found [unbound][2]. Unbound is a lightweight, recursive resolver that is perfect for your LAN, co-located host, or even a single host.

For your single host, `emerge unbound`, start the service, add 127.0.0.1 to the first nameserver in `/etc/resolv.conf`. Unbound is setup (by default) to accept connections from localhost and refuse anything else. **If** you are using dhcp at home (likely) then also `emerge openresolv` and uncomment `name_servers=127.0.0.1` in `/etc/resolvconf.conf`, openresolv then "intercepts" dhcpcd when it tries to write to `/etc/resolv.conf` and adds 127.0.0.1 as your first nameserver <img src="http://blog.jolexa.net/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" /> For your LAN, just configure your router to look to the host that you setup unbound on, with additional configuration.

Finally, you can also have unbound run on your co-located host. Just edit `/etc/unbound/unbound.conf` to a) listen on an outside interface and b) allow your other host to query it. This will be left as an exercise for the reader, it is easy to figure out.

Lastly, a shout-out to Linux Gazette for an excellent write-up on [GoogleDNS][3] (and why you should use something like unbound) and [DNS/LAN metaphors][4]. Suggested reading if you feel out of your league with DNS internals, like me. <img src="http://blog.jolexa.net/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" />

A quote from the above linked article: **"*Why outsource to anyone, when you can do a better job locally, at basically no cost in effort?*"** and really, that is the truth. Have fun.

 [1]: http://blog.jolexa.net/tag/linode/
 [2]: http://unbound.net/
 [3]: http://linuxgazette.net/170/googledns.html
 [4]: http://linuxgazette.net/170/lan.html
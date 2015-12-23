---
author: Jeremy Olexa
categories:
- linux
date: 2014-09-07T00:00:00Z
guid: http://blog.jolexa.net/?p=5334
id: 5334
title: Bypassing Geolocation ...
aliases:
    - /2014/09/bypassing-geolocation/
---

By now we all know that it is pretty easy to bypass geolocation blockage with a web proxy or vpn service. After all, there is over 2 million google results on "bbc vpn" ... and I wanted to do just that to view a BBC show on privacy and the dark web.

I wanted to set this up as cheaply as possible but not use a service that I had to pay for a month since I only needed one hour. This requirement directed me towards a do-it-yourself solution with an hourly server in the UK. I also wanted reproducibility so that I could spin up a similar service again in the future.

My first attempt was to route my browser through a local SOCKS proxy via ssh tunneling, *ssh -D 2001 user@uk-host.tld*. That didn't work because my home connection was not good enough to stream from BBC without incessant buffering.

Hmm, if this simple proxy won't work then that strikes out many other ideas, I needed a way to use the BBC iPlayer Downloader to view content offline. Ok, but the software doesn't have native proxy support (naturally). Maybe you could somehow use TOR and set the exit node to the UK. That seems like a poor/slow idea.

I ended up routing all my traffic through a personal OpenVPN server in London and then downloaded the show via the BBC software and watched it in HD offline. The goal was to provision the VPN as quickly as possible (time is money). A [Linode StackScript][1] is a feature that Linode offers, it is a user defined script ran at first boot of your host. Surprisingly, no one published one to install OpenVPN yet. So, I did: "[Debian 7.5 OpenVPN][2]" -- feel free to use it on the Linode service to boot up a vpn automatically. It takes about two minutes to boot, install, and configure OpenVPN this way. Then you download the ca.crt and client configuration from the newly provisioned server and import it into your client.

**End result**: It took 42 minutes for me to download a one hour show. Since I shut down the VPN within an hour, I was charged the Linode minimum, $.015 USD. Though I recommend Linode (you can use my [referral link][3] if you want), this same concept applies to any provider that has a presence in the UK, like Digital Ocean who charges $.007/hour.

*Addendum: Even though I abandoned my first attempt, I left the browser window open and it continued to download even after I was disconnected from my UK VPN. I guess BBC only checks your IP once then hands you off to the Akamai CDN. Maybe you only need a VPN service for a few minutes?*

I also donated money to a BBC sponsored charity to offset some of my bandwidth usage and freeloading of a service that UK citizens have to pay for, I encourage you to do that same. For reference it costs a UK household, $.02 USD tax per hour for BBC. ([source][4])

 [1]: https://www.linode.com/stackscripts
 [2]: https://www.linode.com/stackscripts/view/10219
 [3]: https://www.linode.com/?r=b4fa70eb87c890e08baf7b0c7852fb7cecd8963b
 [4]: https://en.wikipedia.org/wiki/BBC#Finances
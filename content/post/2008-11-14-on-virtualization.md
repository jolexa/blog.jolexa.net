---
author: Jeremy Olexa
categories:
- gentoo
date: 2008-11-14T00:00:00Z
guid: http://jolexa.wordpress.com/?p=153
id: 153
tags:
- kvm
- virtualization
title: On virtualization&#8230;
url: /2008/11/on-virtualization/
---

Well, I quit using VirtualBox for my virtualization needs. I am now using kernel based virtualization, or [kvm][1]. Kvm offers many advantages, in my opinion, the key being the simplicity and ease of use. I did not like the VBox abstraction.

  * kvm&#8217;s core code is \*in\* the kernel, userspace tools are in a package. Kvm is part of Linux and uses the regular Linux scheduler and memory management. This means that kvm is much smaller and simpler to use. [[1][2]]
  * kvm is Free Software released under the GPL.
  * kvm uses processor extensions (HVM) for virtualization.
  * kvm supports 64bit guests out of the box.

Also, kvm is a breeze to setup. In a nutshell, create the img. `kvm-img create gentoo-amd64.img 10G` then boot the gentoo live cd. `kvm -hda gentoo-amd64.img -cdrom /path/to/iso -boot d`. Then follow the gentoo install handbook. Simple.

Lastly, kvm images are easily transportable and will run on other hosts (within reason, can&#8217;t run a 64bit guest on a 32bit host, etc). As a matter of fact, I present to a amd64 guest if you would like to use it*, [here][3]. Unpack it, and it will decompress to 15-16G (sparse files). Then you can start it by simply running `kvm /path/to/img`. In that guest you will find a pretty recent stage 3 install and emerge -e world done. There are a few other essential apps on there (vim & dhcpcd). From there, you can emerge xorg-x11, a DE, do whatever you want, really. I am using that guest to test out xfce development efforts and to be sure that we can bring you guys xfce-4.6 asap, once it is ready <img src="http://blog.jolexa.net/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" /> Cheers, and have fun playing with kvm!

###### *I do not wish to support this in ANY way, shape, or form. Use it how you wish, but do not expect help with it. Sorry.

 [1]: http://kvm.qumranet.com/kvmwiki
 [2]: http://kvm.qumranet.com/kvmwiki/FAQ#head-7fc0bdcb32a3280f74bc0436f0528a4f4a3539bb
 [3]: http://tinderbox.dev.gentoo.org/virtualization/amd64/
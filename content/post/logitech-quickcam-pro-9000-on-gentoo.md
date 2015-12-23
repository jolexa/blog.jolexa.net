---
author: Jeremy Olexa
categories:
- gentoo
date: 2009-01-08T00:00:00Z
guid: http://jolexa.wordpress.com/?p=204
id: 204
tags:
- logitech
- webcam
title: Logitech Quickcam Pro 9000 on Gentoo
aliases:
    - /2009/01/logitech-quickcam-pro-9000-on-gentoo/
---

Since there isn't anything extremely relevant in google when searching for "gentoo quickcam pro 9000" -- I hope this helps someone.

I [solicited][1] advice from the community for a webcam a couple months back and my girlfriend used the comments to buy me this model for Christmas. It works great, so thanks for recommending it people. =)

As Marcus Hanwell [wrote][2] some 7 months ago, it **is** easy to setup. To set this cam up, make sure you have a recent kernel (>=2.6.26 -- don't quote me on exact version. I used 2.6.27.10 at the time of this writing) and then make sure you have at least these two things enabled:

  1. `CONFIG_USB_VIDEO_CLASS`
  2. `CONFIG_SND_USB_AUDIO`

After that, plug the cam in and verify that the drivers pick up the cam and usb mic with `dmesg`. **That's it**. You can test the webcam by installing a tool called `media-video/luvcview`, I have found that this tool tends to crash while resizing the window or for random reasons -- this is not of concern because it still allows us to verify the cam is working.

As for skype, I just had to change the 'sound in' device to the usb mic on this thing and then it worked fine.

 [1]: http://blog.jolexa.net/2008/11/13/gentoo-best-webcam/
 [2]: http://blog.cryos.net/archives/183-New-Webcam-and-Linux.html
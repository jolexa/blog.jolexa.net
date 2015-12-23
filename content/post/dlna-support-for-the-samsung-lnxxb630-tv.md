---
author: Jeremy Olexa
categories:
- linux
date: 2009-12-27T00:00:00Z
guid: http://blog.jolexa.net/?p=589
id: 589
tags:
- dlna
- samsung
title: DLNA support for the Samsung LNxxB630 TV
aliases:
    - /2009/12/dlna-support-for-the-samsung-lnxxb630-tv/
---

[DLNA][1] (Digital Living Network Alliance) is a standard to allow entertainment devices within the home to share their content with each other across a home network. In other words, stream content from my computer to the TV across the LAN. The cool part about this, is that my TV, the [LN40B630][2], can play HD content native, meaning that the computer's only function is to stream (not process the content, meaning my low power computer can &#8216;power' the HD content). The catch is that you have to use firmware not newer than 001012, the 001013 firmware that my TV came with removes the DLNA feature. (I assume they meant for it to only be available on more expensive models).

In my opinion, the easiest way to get DLNA to work for this TV is to use [mediatomb][3]. The reason is that this TV needs the mimetype of avi/mkv's to be video/mpeg and (so far) I have not found any other DLNA software that is able to modify mimetypes like this. You also need to set a custom http header, as I found [here][4].

Here is my [config.xml][5] that I am using to stream to the TV. It is not perfect but the majority of the work is done. Tested with mediatomb-0.11.0 only.

 [1]: http://en.wikipedia.org/wiki/Dlna
 [2]: http://www.samsung.com/us/consumer/tv-video/televisions/lcd-tv/LN40B630N1FUZA/index.idx?pagetype=prd_detail
 [3]: http://mediatomb.cc/
 [4]: http://forums.cnet.com/5208-13973_102-0.html?messageID=3028811#3028811
 [5]: http://jolexa.net/perm/mediatomb-0.11.0-config.xml
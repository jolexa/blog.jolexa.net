---
author: Jeremy Olexa
categories:
- gentoo
date: 2008-10-16T00:00:00Z
guid: http://jolexa.wordpress.com/?p=131
id: 131
tags:
- fastboot
- moblin
- sreadahead
title: 'Linux: in response to &#8216;5 second boot' (naive attempt at sReadahead)'
aliases:
    - /2008/10/linux-in-response-to-5-second-boot-naive-attempt-at-sreadahead/
---

(In response to my own post, [here][1])

I tried out sReadahead this morning. That experience was very disappointing initial testing. I will describe the process here:

  1. Download the source, from [moblin.org][2] and compile it.
  2. Install [readahead-list][3], created by our own [Robbat2][4]
  3. Use the file lists from readahead-list and pass it to sreadahead's generate_fileset command  
    `cd /etc ; generate_filelist /etc/readahead-list/runlevel-boot`  
    (I actually tried to concatenate both runlevel-boot and runlevel-default with no additional results.)
  4. Shove sreadahead in the readahead-list init scripts
  5. reboot

**End result**: No improvement in boot time with either readahead-list or sReadahead.  
*Disclaimer*: This was a naive attempt and I'm sure I need additional kernel patches or something. But that is non obvious to me at this point. Anyway, if others want to expand on this...feel free to contact me.

Additional reading:  
[Improving boot time on a general Linux distribution, not an easy task][5] (Mandriva dev)  
LWN's [response][6] to above post.

 [1]: http://blog.jolexa.net/2008/10/14/linux-fastboot-my-bootchart/
 [2]: http://www.moblin.org/downloads/super-read-ahead-002
 [3]: http://packages.gentoo.org/package/sys-apps/readahead-list
 [4]: http://robbat2.livejournal.com/
 [5]: http://blog.crozat.net/2008/09/improving-boot-time-on-general-linux.html
 [6]: http://lwn.net/Articles/300873/
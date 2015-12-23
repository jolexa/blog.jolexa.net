---
author: Jeremy Olexa
categories:
- gentoo
date: 2009-10-29T00:00:00Z
guid: http://blog.jolexa.net/?p=506
id: 506
tags:
- linode
- rtorrent
title: Using sshfs with rtorrent
aliases:
    - /2009/10/using-sshfs-with-rtorrent/
---

I had this genius idea about using sshfs with rtorrent. I thought that this use case would fit best in situations where you have good bandwidth but not much diskspace, such as my linode VPS ([review][1]). So, I'll attempt to share my findings in this regard.

If you are not familiar with rtorrent. You just need to know that it is a powerful, lightweight bittorrent client. It has a &#8220;watch&#8221; feature that watches a directory for new torrents, and obviously it can put downloaded files in a specified location. I tried both of these with sshfs.

**First**, I was having trouble with rtorrent just *&#8216;freezing'* up when I put a torrent file in the sshfs accessible watch dir. I didn't quite know what was wrong here. Research led me to [rtorrent bug 322][2] and that sshfs did not support filesystems without mmap properly. Darn. More research led me to a recent [kernel commit][3] that looked promising. Low and behold, reboot my host with 2.6.31.x kernel and rtorrent works with sshfs watch and destination directory. Yay.

Well, not so fast&#8230;

The performance is quite poor with the destination directory on sshfs. This is to be expected because now your download speed for torrents is limited to the download speed of your final destination. But, rtorrent was only giving me a sustained speed of 1/4 of that demonstrated with a simple file copy to the destination. I speculate that this is from the rtorrent overhead or maybe fragmenting? Not sure exactly and I don't care. My solution to this was to use the rtorrent &#8220;move on finished&#8221; feature that downloads the file to local disk and then moves it to sshfs destination after it is finished. Amazingly, this works quite well.

My testing scenario was the following:  
-79MB Gentoo 2008.0 install cd torrent. With the complete sshfs solution, it took ~6 minutes to download (to the sshfs destination) and then 5 minutes to check the hash. So, **roundtrip of 11 minutes** from start download to seeding. With the on_finished solution, it took 1 minute to download (to local disk) and 1 minute to check the hash and move to the sshfs destination. For a **roundtrip of ~2 minutes** from start of download to seeding.

In conclusion, this isn't the perfect solution because you impose a large bottleneck into the mix and unintended I/O activity on the local disk. However, it works for me and what I am doing. Maybe it will give someone else some ideas in the future.

 [1]: http://blog.jolexa.net/2009/05/13/in-depth-linode-vps-review/
 [2]: http://libtorrent.rakshasa.no/ticket/322
 [3]: http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=9eead2a8115d2a6aecf267c292f751f7761fa5f8
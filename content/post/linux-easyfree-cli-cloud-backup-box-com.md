---
author: Jeremy Olexa
categories:
- gentoo
date: 2012-08-10T00:00:00Z
guid: http://blog.jolexa.net/?p=964
id: 964
title: 'Linux: Easy/Free CLI Cloud Backup (box.com)'
aliases:
    - /2012/08/linux-easyfree-cli-cloud-backup-box-com/
---

*Preface: I use to use [rsync.net][1] for my offsite backup needs. They offer a nice solution, especially with the F/OSS contributor discount, but my needs were lesser than their offerings and I didn't quite feel comfortable paying monthly for such needs. That is, get my critical (but small) backups off my host, MySQL, a few important files, etc. Most of my online world is now externally hosted (cloud) or easily rebuilt with key pieces of info.*

My current free 5G offsite backup solution is with [box.com][2]. I don't really use box.com as intended -- 'a collaborative file sharing platform' but instead take advantage of the [WebDAV][3] access that they provide. So, a quick walk-through:

  1. `emerge davfs2` (I pushed fixes in version >=1.4.7 in Gentoo Linux, I recommend that version)
  2. `echo "https://www.box.com/dav /mnt/box.com davfs rw,user,noauto 0 0" >> /etc/fstab ` 
  3. Mount the mountpoint as your user (enter your box.com credentials), copy files to the mounted filesystem.

(*There are some finer details, like modifying $HOME/.davfs2/secrets and turning off use_locks, but I'm sure you smart people can figure that out via google.*)

Personally, I have a simple cron job that mounts, rsyncs, umounts that runs daily. Now, I have an accessible location to restore critical files as needed, just don't look at the webui since it doesn't understand compressed tarballs that well and is useless, heh.

 [1]: http://rsync.net/
 [2]: https://www.box.com/
 [3]: http://en.wikipedia.org/wiki/Webdav
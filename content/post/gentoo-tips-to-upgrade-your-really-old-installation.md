---
author: Jeremy Olexa
categories:
- gentoo
date: 2009-03-25T00:00:00Z
guid: http://blog.jolexa.net/?p=325
id: 325
title: 'Gentoo: Tips to upgrade your <u>really</u> old installation'
aliases:
    - /2009/03/gentoo-tips-to-upgrade-your-really-old-installation/
---

Let me start out this post by making it clear. You should **really** upgrade your Gentoo installation on a regular basis. If not, you might run into [some][1] [problems][2].

This post attempts to help out someone that is trying to bring an unmaintained installation up to date. Under most circumstances it is probably easier to reinstall after a certain point. These instructions have been created by an active contributor to Gentoo, Nick Fortino, to take a **2006.1** installation and update it to a current stable system. (Which I hope is much more extreme than anyone needs).

> `Version 0, written by Nick Fortino<br />
#March 23, 2009<br />
#This has been tested only in chroot, bringing 2006.1-amd64-stage3 upto<br />
#a stable amd64 system`
> 
> `#This is an experimental guide on how to upgrade an old system to get to<br />
#portage 2.1.6.7. Once this state is achieved, portage can do the rest, with<br />
#decent dependency resolution.<br />
`  
> `###########################################################################<br />
#Between the first tar command and the success of 'emerge -uDN system', the<br />
#true state of the system, and the state according to portage are different.<br />
#This is rather unsafe, so be sure you understand what you are doing.<br />
#Consider this your big red warning to backup important files before attempting<br />
#an update, and consider a re-install if possible.<br />
###########################################################################`
> 
> `#It may be wise to use the default make.conf, as we would like to rebuild<br />
#as few packages as possible before the toolchain has been updated, and use<br />
#flags will bring in a bunch of dependencies<br />
`  
> `#Update the symlink to an existing profile<br />
unlink /etc/make.profile<br />
ln -s ../usr/portage/profiles/default/linux/amd64/2008.0 /etc/make.profile<br />
`  
> `#Fetch and forcefully upgrade python, bash, and portage with prebuilt sources<br />
wget http://tinderbox.dev.gentoo.org/default-linux/amd64/dev-lang/python-2.5.2-r7.tbz2<br />
wget http://tinderbox.dev.gentoo.org/default-linux/amd64/app-shells/bash-3.2_p39.tbz2<br />
wget http://tinderbox.dev.gentoo.org/default-linux/amd64/sys-apps/portage-2.1.6.7.tbz2<br />
cd /<br />
tar xfpj root/python-2.5.2-r7.tbz2<br />
tar xfpj root/bash-3.2_p39.tbz2<br />
tar xfpj root/portage-2.1.6.7.tbz2`
> 
> `#remove the obsolete block from bash for portage; we got around it with a binary<br />
#update (adding to /etc/portage/profile/package.provided would seem more<br />
#elegant, but doesn't work?)<br />
cd /usr/portage/app-shells/bash<br />
nano /usr/portage/app-shells/bash/bash-3.2_p39.ebuild<br />
repoman manifest<br />
cd /<br />
`  
> `#See what will be upgraded, there should be no unresolved blockers<br />
emerge -puDNv system<br />
#Perform the update, this command will likely make good progress, and then fail<br />
emerge -uDN system<br />
`  
> `############<br />
#Known failures and solutions<br />
############`
> 
> `#Cracklib wants -unmerge-orphans<br />
FEATURES='-unmerge-orphans' emerge -1 cracklib<br />
#continue the upgrade<br />
emerge -uDN system`
> 
> `#Python updater and python split, creating a confilct, resolve by removing<br />
#the old file<br />
rm /usr/sbin/python-updater<br />
emerge -1 python-updater<br />
#continue the upgrade<br />
emerge -uDN system<br />
`  
> `############<br />
#Cleanup<br />
############<br />
`  
> `#Update the current terminal<br />
env-update<br />
source /etc/profile<br />
#Deal with the many /etc files which need updating<br />
emerge gentoolkit<br />
dispatch-conf<br />
`  
> `#At this point, the toolchain has been rebuilt, which likely involved an upgrade<br />
#of gcc. Follow http://www.gentoo.org/doc/en/gcc-upgrading.xml to finish the<br />
#upgrade. A lot of what is requested there has likely been done automatically,<br />
#so in summary:<br />
`  
> `#Check that gcc-config is using the correct compiler, if not, follow the above<br />
#guide<br />
gcc-config -l`
> 
> `#Replace your make.conf/update to whatever profile you choose/etc.<br />
#Rebuild the system with the new toolchain, and custom settings<br />
emerge -eav system<br />
#Rebuild and update world with new toolchain and settings<br />
emerge -eav world<br />
`  
> `#Finally, remove any old packages which still survived the process<br />
emerge --depclean -a<br />
`

Which I made available [here][3].

So, please people. Update on a regular basis so you don&#8217;t have to go through this stuff.

 [1]: http://bugs.gentoo.org/263521
 [2]: http://forums.gentoo.org/viewtopic-t-748073-start-0-postdays-0-postorder-asc-highlight-.html?sid=221191716d0fd211eec30535cd64cad3
 [3]: http://dev.gentoo.org/~darkside/perm/update-old-host.sh
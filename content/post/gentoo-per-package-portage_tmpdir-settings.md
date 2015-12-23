---
author: Jeremy Olexa
categories:
- gentoo
date: 2011-09-16T00:00:00Z
guid: http://blog.jolexa.net/?p=831
id: 831
title: 'Gentoo: per-package PORTAGE_TMPDIR settings'
aliases:
    - /2011/09/gentoo-per-package-portage_tmpdir-settings/
---

I don&#8217;t know how many people know about per-package environment variables in portage since 2.1.9 or so. (ref: <a href="https://bugs.gentoo.org/show_bug.cgi?id=44796" target="_blank">bug 44796</a>) It is a worthwhile enhancement to know about, regardless. Like most people, I have my PORTAGE_TMPDIR on tmpfs to speed up compilation times and reduce I/O usage. My 2G tmpfs mounted on /var/tmp/portage is large enough for almost all packages, even multiple jobs at once, however, not all. Solution:

% cat /etc/portage/package.env  
app-office/libreoffice notmpfs.conf  
% cat /etc/portage/env/notmpfs.conf  
PORTAGE_TMPDIR=&#8221;/var/tmp/notmpfs&#8221;

(More info available in the portage man page)

Now, when I find my next package that needs notmpfs, it is as easy as: `echo "cat-egory/pkg notmpfs.conf" >> /etc/portage/package.env` which is much easier than bashrc hacks or something else insane that I have seen. Of course you can extend that to most `make.conf` settings, hope that helps someone.
---
author: Jeremy Olexa
categories:
- linux
date: 2012-01-24T00:00:00Z
guid: http://blog.jolexa.net/?p=909
id: 909
tags:
- solaris 11
title: 'Solaris 11: Where is /usr/ucblib? Quick tips to install &#8216;ucb&#8217;
  package'
url: /2012/01/solaris-11-where-is-usrucblib-quick-tips-to-install-ucb-package/
---

Well&#8230; I finally figured out that the ucb package isn&#8217;t installed on Solaris 11 by default ([resource][1]). Unfortunately, the *Oracle* docs are confusing to follow. Here is a cheatsheet for installing the ucb package on your shiny Solaris 11 install.

  1. Figure out the IPS installer, read man pages, get frustrated at lack of detail, run to Google.
  2. Find the package you want on <http://pkg.oracle.com/>, in this case *compatibility/ucb*
  3. Add the *publisher* link to your config, by the way, this link is not documented that I can find so I had to guess and check. A publisher is a package list of sorts, I guess.  
    `# pkg set-publisher -G '*' -M '*' -g http://pkg.oracle.com/solaris/release solaris`
  4. Install the package, `# pkg install compatibility/ucb`

> \# pkg install compatibility/ucb  
> Packages to install: 1  
> Create boot environment: No  
> Create backup boot environment: No
> 
> DOWNLOAD PKGS FILES XFER (MB)  
> Completed 1/1 80/80 0.4/0.4
> 
> PHASE ACTIONS  
> Install Phase 166/166
> 
> PHASE ITEMS  
> Package State Update Phase 1/1  
> Image State Update Phase 2/2

  1. Behold, that you now have the compatibility libs for software that may need to use them

Whew&#8230;now, you might wonder what is so hard about that. Well, traversing Oracle docs is the hard part.

Here are the docs that I had open in my browser, they may or *may not* help and I fully expect the links to break in the future because Oracle is good at that.

  * [Copying and Creating Oracle Solaris 11 Package Repositories][2]
  * [Oracle Solaris 11 Package Repository][3]
  * [Oracle Solaris 11 Package Management with IPS][4]
  * [Image Packaging System Man Pages][5]

 [1]: http://www.scalingbits.com/node/186
 [2]: http://docs.oracle.com/cd/E23824_01/html/E21803/toc.html
 [3]: http://pkg.oracle.com/solaris/release/en/index.shtml
 [4]: http://www.oracle.com/technetwork/server-storage/solaris11/technologies/ips-323421.html
 [5]: http://docs.oracle.com/cd/E23824_01/html/E21796/pkg-1.html
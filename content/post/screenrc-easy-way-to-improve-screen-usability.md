---
author: Jeremy Olexa
categories:
- gentoo
date: 2009-11-30T00:00:00Z
guid: http://blog.jolexa.net/?p=534
id: 534
title: screenrc -- easy way to improve screen usability
aliases:
    - /2009/11/screenrc-easy-way-to-improve-screen-usability/
---

I've used a custom ~/.screenrc file for at least a year now. I find that this snippet helps improve the usability for me.

<pre>#Custom Stuff
caption always "%{= wb}$USER @ %H >> %-Lw%{= r}%50>%n* %t%{-}%+Lw%&lt; %-=&lt;&lt; (%c.%s)"

activity "%c activity -> %n%f %t"
bell "%c bell -> %n%f %t^G"
vbell_msg " *beep* "

startup_message off

defscrollback 500

multiuser off
# Always start screen with utf8 enabled. (screen -U)
defutf8 on</pre>

Output (caption at bottom):  
<img src="/wp-content/uploads/2009/11/screenrc.jpg" alt="screenrc" title="screenrc" width="494" height="343" class="alignleft size-full wp-image-535" />
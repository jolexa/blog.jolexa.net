---
author: Jeremy Olexa
categories:
- gentoo
date: 2011-11-11T00:00:00Z
guid: http://blog.jolexa.net/?p=869
id: 869
title: 'Gentoo: Colemak keymap support'
aliases:
    - /2011/11/gentoo-colemak-keymap-support/
---

[Colemak][1] is my new keymap of choice. Luckily, Gentoo Linux supports it well. Unlike some of the crazy instructions people have [posted][2] out [there][3], you only need to edit *2 files* to convert your console and Xorg server. Note, I'm taking the time to write this because I **couldn't** find easy instructions out there&#8230;

`<br />
% cat /etc/conf.d/keymaps<br />
# Use keymap to specify the default console keymap.  There is a complete tree<br />
# of keymaps in /usr/share/keymaps to choose from.<br />
keymap="en-latin9"<br />
<...><br />
`

    
    % cat /etc/X11/xorg.conf.d/30-keyboard.conf 
    Section "InputClass"
            Identifier "keyboard-all"
            Option "XkbVariant" "colemak"
    EndSection

 [1]: http://colemak.com/
 [2]: http://siavashs.org/blog:dvorak_and_colemak_keyboard_layouts_on_gentoo
 [3]: http://forums.gentoo.org/viewtopic-t-639368-start-0.html
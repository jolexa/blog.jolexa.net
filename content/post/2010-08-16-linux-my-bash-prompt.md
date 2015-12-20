---
author: Jeremy Olexa
categories:
- gentoo
- linux
date: 2010-08-16T00:00:00Z
guid: http://blog.jolexa.net/?p=738
id: 738
title: 'Linux: My bash prompt'
url: /2010/08/linux-my-bash-prompt/
---

There seems to be a semi-meme [going][1] [around][2] on some of the planets I read.

My concern is long directory paths and I wanted a dymanic solution for it. Surely, I cannot be the first person to think of it, but I haven&#8217;t seen it in use anywhere else.

<pre><div style="background-color: #000000; font-style: normal; font-family: Georgia;">
  <span style="color: #333399;"><strong><span style="color: #3366ff;">jolexa</span> <span style="color: #00ff00;">@</span> <span style="color: #3366ff;">helios</span> <span style="color: #999999;">::</span> <span style="color: #ffffff;">~</span> <span style="color: #999999;">%%</span></strong></span>
</div>


and



<div style="background-color: #000000; font-style: normal; font-family: Georgia;">
  <span style="color: #333399;"><strong><span style="color: #3366ff;">jolexa</span> <span style="color: #00ff00;">@</span> <span style="color: #3366ff;">helios</span> <span style="color: #999999;">::</span> <span style="color: #ffffff;">~</span> <span style="color: #999999;">%% </span></strong></span><span style="color: #00ff00;">cd projects/prefix-tinderbox/really_long_dirname_so_that_binpkgs_can_be_shortened/a/b/</span>
  <span style="color: #333399;"><strong><span style="color: #333399;"><span style="color: #333399;"><strong><strong><span style="color: #3366ff;">jolexa</span> <span style="color: #00ff00;">@</span> <span style="color: #3366ff;">helios</span> <span style="color: #999999;">::</span> <span style="color: #ffffff;">.../a/b</span> <span style="color: #999999;">%%</span></strong></strong></span></span></strong></span>
</div>

</pre>

(the colors and wrapping are representitive only)

and the code that produces that:

    _chomp_path() {
        local path=${1/${HOME}/\~}
        local last=${path} sedout= count=0 count2=0
        sedout=$(echo ${path} | sed -e 's:/: :g')
        for i in ${sedout}; do
            (( count++ ))
        done
        if ((count > 2)); then
            last="..."
            for i in ${sedout}; do
            (( count2++ ))
            if (( count2 >=  count - 1 )); then
                last+="/$i"
            fi
            done
        fi
        echo ${last}
    }
    
    PS1='\[\033[1;34m\]\u \[\033[1;32m\]@\[\033[1;34m\] \h \[\033[1;30m\]::\[\033[1;37m\] $(_chomp_path $(pwd)) \[\033[1;30m\]%%\[\033[0m\] '

If anyone wants to improve that function, let me know. It &#8220;fails&#8221; on directories with spaces in it.

 [1]: http://ahenobarbi.wordpress.com/2010/06/22/new-terminal-prompt/
 [2]: http://www.linuxized.com/2010/08/quicky-changing-your-shell-prompt
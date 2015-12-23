---
author: Jeremy Olexa
categories:
- gentoo
date: 2011-10-24T00:00:00Z
guid: http://blog.jolexa.net/?p=849
id: 849
title: 'Tip: "Intelligent" bugzilla mail threading in GMail using procmail'
aliases:
    - /2011/10/tip-intelligent-bugzilla-mail-threading-in-gmail-using-procmail/
---

*(Preface: Target audience for this post is Gentoo Devs + GMail WebUI users, however, anyone that forwards bugmail to GMail and has procmail between them could also use this.)*

I find it annoying that the GMail web interface chooses to thread messages based on subject name alone, this creates **two** threads for every new bug report sent to you from bugzilla. Sadly, we can't control the threading that Google tells us is "the only way" (subject based threading or email header based threading, which bugzilla does correctly). If you want to <a href="http://blog.mozilla.com/nnethercote/2011/06/09/gmail-and-bugzilla/" target="_blank">follow</a> the <a href="http://blog.mozilla.com/nnethercote/2011/06/10/gmail-and-bugzilla-an-update/" target="_blank">rabbit</a> <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=650575" target="_blank">trail</a> <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=528889" target="_blank">that</a> I <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=650575#c23" target="_blank">went</a> <a href="https://bugs.gentoo.org/370977" target="_blank">on</a> <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=663747" target="_blank">regarding</a> this subject, I won't <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=589128" target="_blank">stop</a> you...

Or you can use procmail to rewrite the subject, that is, remove "New: " from the first email:

    # Remove "New: " from the subject so threading in gmail works
    SUBJ_=`formail -xSubject: | expand | tr -d '\n' | sed -e 's/^[ ]*//g' -e 's/New: //'`
    :0
    * ^From: bugzilla-daemon@gentoo.org
    {
        :0 fwh
        | formail -i"Subject: ${SUBJ_}"
    }

Tangentially related that may be useful, is this rule that kills duplicate messages when you report a bug and are assigned the same bug (or in CC). The bugzilla software has no way of knowing what email aliases you may be in.

    # Kill duplicate messages. If I am the reporter *and* the bug is assigned to a
    # team I am in, delete the mail to me directly
    :0
    * ^To: username@gentoo.org
    * ^From: bugzilla-daemon@gentoo.org
    * ^X-Bugzilla-Reporter: username@gentoo.org
    * ^X-Bugzilla-(Assigned-To|CC):.*(team1|team2)@gentoo.org
    /dev/null</pre>
    <p></p>
    
    
    *I like the GMail WebUI. I use it. Please don't suggest that I should use other clients, I already know that other clients can handle the threading fine.*
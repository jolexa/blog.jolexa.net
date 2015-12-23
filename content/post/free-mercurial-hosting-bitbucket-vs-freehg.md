---
author: Jeremy Olexa
categories:
- linux
date: 2008-09-11T00:00:00Z
guid: http://jolexa.wordpress.com/?p=90
id: 90
tags:
- mercurial
- vcs
title: Free mercurial hosting -- bitbucket vs freehg
aliases:
    - /2008/09/free-mercurial-hosting-bitbucket-vs-freehg/
---

**Update: (04/14/11)** I see that freehg now links to an adult site. Hence, I have removed all the links.

Just a small post to document the options with regards to "free" mercurial repo hosting. Many options are located on mercurial's homepage [here][1]. I choose to compare offerings from [bitbucket][2] and freehg. I was rooting for freehg in my comparisons because they sound more "free"

Anyway, the numbers don't lie.

> %% time hg push http://freehg.org/u/jolexa/personal/  
> pushing to http://freehg.org/u/jolexa/personal/  
> searching for changes  
> no changes found
> 
> real 0m4.221s  
> user 0m0.103s  
> sys 0m0.011s

vs

> %% time hg push http://bitbucket.org/jolexa/personal/  
> pushing to http://bitbucket.org/jolexa/personal/  
> searching for changes  
> no changes found
> 
> real 0m0.665s  
> user 0m0.109s  
> sys 0m0.011s

and..

> %% time hg pull http://freehg.org/u/jolexa/personal/  
> pulling from http://freehg.org/u/jolexa/personal/  
> searching for changes  
> no changes found
> 
> real 0m2.099s  
> user 0m0.105s  
> sys 0m0.011s

vs

> %% time hg pull http://bitbucket.org/jolexa/personal/  
> pulling from http://bitbucket.org/jolexa/personal/  
> searching for changes  
> no changes found
> 
> real 0m0.479s  
> user 0m0.107s  
> sys 0m0.009s

So, even though bitbucket has limitations on their free account, I don't anticipate ever having more than 150 MB of data and more than one repo. 4 seconds is a long time to wait for a change in state. I guess that I will use bitbucket after all. Works for me, hope this helps someone in the future.

**Update: (9/17/08)** As I gain more experience with mercurial, I didn't like having to enter my username and password every time I push/pulled. So I inquired about this with a friend and the solution was to edit the repo path with <user>:<pass>@blah, the only problem was that this was a world readable file..not the end of the world but it still didn't sit well with me. I digged into this and found another benefit of bitbucket, they allow you to upload your ssh public key! Now I don't have my password in any files and I don't have to enter it in every time. It is a win-win, right? Wrong...using ssh, naturally, kills any speed improvements that it has over freehg. This is another "oh well" scenario -- I would rather have the ssh access.

 [1]: http://www.selenic.com/mercurial/wiki/index.cgi/MercurialHosting
 [2]: http://www.bitbucket.org/
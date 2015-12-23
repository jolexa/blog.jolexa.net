---
author: Jeremy Olexa
categories:
- gentoo
date: 2011-02-11T00:00:00Z
guid: http://blog.jolexa.net/?p=798
id: 798
title: 'Tip: Single Purpose Password-less SSH Key'
aliases:
    - /2011/02/tip-single-purpose-password-less-ssh-key/
---

**Scenario**: You need to setup a service that requires ssh access to a remote host, possibly/probably by the root user. This service needs to run at regular intervals and it is critical that it works without a human entering a passphrase (even *once*).

**Solution**: The obvious solution that comes to mind is a ssh key. But a password-less key that allows root login? **RED FLAG**. However, there is a way to accomplish this without allowing a root login completely. That is to create, what I call, a single purpose key. I feel like this <u>not</u> a widely known trick, so I am archiving it so I don&#8217;t forget myself.

**Details:**  
(Where local host is the host that needs ssh access and remote host is the host that you are &#8220;opening&#8221; up or allowing ssh access to)

  1. On the local host, create a ssh key without a passphrase for the root user, this is widely documented via other sources
  2. On the remote host, add the key to the `/root/.ssh/authorized_keys` file. However, start the line in that file with `command="/root/bin/validate-ssh.sh"`
  3. On the remote host, the `/root/bin/validate-ssh.sh` script is a simple script that allows access to your service and exits for anything else. An example of allowing rsync access [only]: 
        
        % cat /root/bin/validate-ssh.sh 
        #!/bin/bash
        case "$SSH_ORIGINAL_COMMAND" in
        	rsync\ --server*)
        		# uncomment for debug
        		# echo "$(date +%Y%m%d): $SSH_ORIGINAL_COMMAND" >> /var/log/ssh-cmd.log
        		$SSH_ORIGINAL_COMMAND
        		;;
        	# debug
        	testconnect)
        		echo "You successfully connected to $(hostname)"
        		;;
        	*)
        		echo "Sorry, command '$SSH_ORIGINAL_COMMAND' is not allowed"
        		exit 1
        		;;
        esac
        

  4. Optional, if you only want to allow this access from a small set of hosts add `from="192.168.1.11,10.80.80.1"` to the same line in `/root/.ssh/authorized_keys`

So, now, you can use that password-less ssh key as root (assuming the remote host *allows* root logins via ssh) and you should see something. `ssh root@remote testconnect` will return that string. `rsync root@remote:/file` will work. Everything else will get the message that indicates it wasn&#8217;t allowed. This is expandable to just about everything provided that you know the &#8220;$SSH\_ORIGINAL\_COMMAND&#8221; &#8211; on another host I use it to allow password-less sshfs access, so `SSH_ORIGINAL_COMMAND=/usr/lib/misc/sftp-server` and so-forth.

Naturally, this will work for other users/uses as well. I&#8217;ve seen references that some admins are using this to allow access if and only if they enter a sekrit token, etc. I&#8217;ll also say that you should be smart with this, opening up root access is a hole &#8211; if anyone compromises the local host, I suppose they could get access to the remote host if they knew how.
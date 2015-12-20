---
author: Jeremy Olexa
categories:
- linux
date: 2009-12-20T00:00:00Z
guid: http://blog.jolexa.net/?p=587
id: 587
tags:
- linode
title: About PHP_FCGI_MAX_REQUESTS and lighttpd
url: /2009/12/about-php_fcgi_max_requests-and-lighttpd/
---

If you are running PHP on a limited-resource box, like a [VPS][1] then you may have seen your PHP pages randomly hang. I was able to trace this issue down because the PHP pages were hung up and the normal html pages were still being served. The problem was *&#8216;solved&#8217;* when I restarted the web server. Some research later, and talking to Thilo (bangert), I found out about `PHP_FCGI_MAX_REQUESTS`. This is an environment variable that PHP respects, it basically tells how many requests to serve before respawning fcgi. In my case, 500 seemed like a good number after testing. Your mileage may vary, but it is worth a try if you have those symptoms.

    
    %% cat /etc/lighttpd/mod_fastcgi.conf 
    server.modules += ("mod_fastcgi")
    fastcgi.server = ( ".php" =>
        ( "localhost" =>
            (
                "socket"   => "/var/run/lighttpd/lighttpd-fastcgi-php-" + PID + ".socket",
                "bin-path" => "/usr/bin/php-cgi",
                "max-procs" => "2", # default 4
                "bin-environment" => (
                    "PHP_FCGI_CHILDREN" => "2", # default 1
                    "PHP_FCGI_MAX_REQUESTS" => "500" #default 1000
                )
            )
        )
    )

 [1]: http://blog.jolexa.net/tag/linode/
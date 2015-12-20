---
author: Jeremy Olexa
categories:
- gentoo
date: 2009-09-18T00:00:00Z
guid: http://blog.jolexa.net/?p=495
id: 495
tags:
- lighttpd
title: Intelligent lighttpd directory structure w/evhost.path-pattern
url: /2009/09/intelligent-lighttpd-directory-structure-wevhost-path-pattern/
---

Searched high and low to find this silly little info. Finally found it [here][1].

    
    # define a pattern for the host url finding
    # %% => % sign
    # %0 => domain name + tld
    # %1 => tld
    # %2 => domain name without tld
    # %3 => subdomain 1 name
    # %4 => subdomain 2 name
    
    # Set default vhost server location here
    evhost.path-pattern = "/www/%0/htdocs"
    
    # If we don't have a %3, default to htdocs
    $HTTP["host"] =~ "^[^.]+\.[^.]+$" {
        evhost.path-pattern = "/www/%2.%1/htdocs/"
    }
    
    # If we don't have a %4, find the subdomain
    $HTTP["host"] =~ "^[^.]+\.[^.]+\.[^.]+$" {
        evhost.path-pattern = "/www/%2.%1/subdomains/%3/"
    }
    
    # If we have a %4, find the subdomain2.subdomain1. If we have have %4+, use %4
    # anyway. If you have 4+, write a explicit rule for doc-root.
    $HTTP["host"] =~ "^.+\.[^.]+\.[^.]+\.[^.]+$" {
        evhost.path-pattern = "/www/%2.%1/subdomains/%4.%3/"
    }

*Now* my only wishlist is to do something similar for var.logdir, but %[1-4] is only set up with evhost. **So, do you do anything smarter than this for your server?**

 [1]: https://log.logfish.net/node/8
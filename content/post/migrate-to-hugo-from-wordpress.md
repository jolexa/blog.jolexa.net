+++
author = "Jeremy Olexa"
categories = ["technology"]
date = "2015-12-27T02:41:45Z"
tags = ["hugo", "wordpress", "amazon"]
title = "Migrate to Hugo from Wordpress"
+++

I have now liberated myself away from Wordpress. Launching new site today, now.
This site has substantial archetechure changes compared to the old one.

|  | Old Blog | New Blog |
|-----|------|-----|
| Software | Wordpress | [Hugo](http://gohugo.io) |
| Hosting | Linode | Amazon S3 |
| Deployment | Maintain software stack, CMS | Soon to be automated |
| Source Control | None | [GitHub](https://github.com/jolexa/blog.jolexa.net) |
| Editor | Web App | Any editor, just text files. Markdown format |
| Security | Self Secured (PHP based app) | Static Files, protect the AWS keys, etc |
| Time to maintain | Relatively lots | Relatively Zero |
| Optimization, CDN, Speed | Self optimization from single point | CloudFlare fronted, AWS SLA, small files, less moving parts |

## Why switch?
I know static site generators are the new fashion now-days. Whether the site is
hosted on GitHub Pages, Amazon S3, or self hosted, it is just simpler to
maintain. This is most advantageous to me, as I don't have a desire to tinker
with a server anymore (or time). Hosting my own server was fun and provided much
background context that helped me with the beginning of my career. Now that
context is there and more context is needed around the next generation of
services. Another big point is security, having a Web/PHP/MySQL stack exposed to
the internet is eventually going to be trouble if not maintained. A minor point
is cost, but this blog should cost me less than 1 USD per month, so ~90% cost
reduction.

## Why Hugo?
There are [many static site generators](https://www.staticgen.com/) out there
but I picked Hugo because of a few reasons. The main reason was that it was
written in [Go](https://golang.org/) and I'm betting that I will desire some Go
experience in my future. (Buzzword: Microservices). In addition, the theme
engine seems pretty good to me. I was able to fork a theme and get immediate
feedback on the changes I was making, this is fun since now I can extend my own
themes and make modification on the fly. This current theme is a
[fork](https://github.com/jolexa/vienna/tree/blog.jolexa.net) of another
project.

## How?
There are a bunch of tools out there, especially since Wordpress is such a
popular platform. I'm not going to rehash it here, but essentially it was:

* Convert from Wordpress to Jekyll format (the Hugo tool didn't work out of the
  box)
* Convert from Jekyll to Hugo (built in to Hugo)
* Hack on theme, make small data mods, rebuild, push to S3, repeat until happy
* Change CloudFlare DNS to S3 bucket

I picked CloudFlare because it should save me money with the caching it
provides. It also seemed like the easiest way for me to enforce https, though
the CloudFront method didn't seem that hard either. CloudFlare provides
"Universal SSL" for free and basically obsoletes the personal management of a
SSL certificate, which is good for me.

## Future
This _platform_ that I have created for myself has me excited for the ease of use
and the results it provides. In the future, I will document my use of AWS Lambda
to update the content every time I do a `git push` - which means I will have
complete server-less delivery using extremely applicable technologies in modern
software.

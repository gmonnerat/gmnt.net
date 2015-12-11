+++
categories = ["http", "web"]
date = "2015-12-11T00:56:07+01:00"
description = "Moving from Nginx to Caddy with HTTPS"
keywords = ["nginx", "caddy"]
title = "Moving from Nginx to Caddy"

+++

After see the release of [Caddy 0.8 with Let&#39;s Encrypt integration](https://caddyserver.com/blog/caddy-0_8-released).

I installed Caddy downloading the package from this [page](https://caddyserver.com/download).

After download and extract the binary, I ran it with my initial [Caddyfile](https://caddyserver.com/docs/caddyfile):


    gmnt.net, www.gmnt.net {
      gzip
      root /home/gabriel/gmnt.net/public 

      log /home/gabriel/caddy/blog.log {
        rotate {
          size 100 # Rotate after 100 MB
          age  14  # Keep log files for 14 days
          keep 10  # Keep at most 10 log files
        }
      }
    }

I know that exists one extension to integrate [Caddy](https://caddyserver.com/) and [Hugo](http://gohugo.io/), but specifing the [root](https://caddyserver.com/docs/root) of the site is enough for me.

After run, automatically I got this blog running in HTTPS. _o/

To access my applications, I add subdomains to the Caddyfile, for example:

    xyz.gmnt.net {
      proxy / localhost:1234 {
        proxy_header X-Real-IP {remote}
      }
    }

Congratulations to [Caddy](https://caddyserver.com/) and [Let&#39;s Encrypt](https://letsencrypt.org/) for the nice work!

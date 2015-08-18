+++
categories = ["mutt", "tool", "web"]
date = "2015-08-18T03:55:44+02:00"
description = "Share your terminal as a web application using GoTTY"
keywords = []
title = "Using mutt in the browser"

+++

Today I saw a nice and easy to use command line tool, called [GoTTY](https://github.com/yudai/gotty).

I just did:

    $ go get github.com/yudai/gotty

    $ gotty -p 8081 -w mutt

Done. With this, I am able to use my favorite e-mail client, [mutt](http://www.mutt.org/), in the browser.

For now, I used [Port Forwarding](https://support.ssh.com/manuals/server-admin/32/Port_Forwarding.html)
because there is no authentication support yet. But, when added will be
interesting.

+++
categories = ["go", "web"]
date = "2016-04-15T00:38:21+02:00"
description = "My skeleton to write web applications with Golang"
keywords = ["go", "web"]
title = "Skeleton to my web applications in Go"

+++

I just published my skeleton that I use to write Web Applications,
[go-web-application-skeleton](https://github.com/gmonnerat/go-web-application-skeleton).

Ever since I started to study [Go](https://golang.org/), I was trying to create web applications in only one binary file.

And with [go-bindata](https://github.com/jteeuwen/go-bindata) it is possible.

I can send(or move) the binary to my server without problems:

    $ make build
    go-bindata static/... templates/...
    $ go build
    $ mv go-web-application-skeleton /tmp/
    $ cd /tmp/
    $ ./go-web-application-skeleton

    $ curl -i http://localhost:8080/static/favicon.ico | head -n 1
        HTTP/1.1 200 OK

No access to the file system!

To avoid run go-bindata command every time, I use
[goat](https://github.com/yosssi/goat) and to restart the server when
there are changes, I use [fresh](https://github.com/pilu/fresh).

OBS: This skeleton is not used production yet and there is no tests for it. So, please only use it to prototype new applications.

Enjoy! Feel free to report issues.

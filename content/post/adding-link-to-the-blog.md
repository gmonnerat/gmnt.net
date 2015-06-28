+++
categories = []
date = "2015-06-28T23:46:37+02:00"
description = "In Hugo, is possible add a link in your blog easily"
keywords = []
title = "Adding link to the blog"

+++

In [Hugo](http://gohugo.io/), is possible add a link in your blog easily.

One option is add .Site.Menus.main to the theme.

In the theme [Hyde-X](https://github.com/zyro/hyde-x) is already done with those lines:

    {{ range .Site.Menus.main }}
    <li class="sidebar-nav-item"><a href="{{ .URL | absURL }}">{{ .Name }}</a></li>
    {{end}}

Then, in my config.toml I added:

    [[menu.main]]
    name = "Subscribe"
    identifier = "subscribe"
    url = "/index.xml"

Done! Nothing to change except my configuration file.

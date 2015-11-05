+++
categories = ["mail"]
date = "2015-11-04T23:57:59+01:00"
description = "Configuring my mail server in order not to be considered as a spammer"
keywords = ["mail"]
title = "Configuring DKIM"

+++

After reading the post [Debian Mail Server, Part II: SPF and
DKIM](https://scaron.info/blog/debian-mail-spf-dkim.html), I checked my mail
server with [mail-tester.com](https://www.mail-tester.com/) and I got 6/10.
With this score, my email can be consired as spam.

After configure DKIM and DMARC, I got 10/10.

Sending an empty e-mail to
[check-auth@verifier.port25.com](mailto:check-auth@verifier.port25.com), I got
a SPF/DKIM report by mail that looks like:

    SPF check:          pass
    DomainKeys check:   neutral
    DKIM check:         pass
    Sender-ID check:    pass
    SpamAssassin check: ham

Much better now.

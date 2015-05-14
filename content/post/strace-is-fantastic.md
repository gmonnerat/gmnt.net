+++
categories = []
date = "2015-05-06T22:24:02+02:00"
description = "Use strace to help you to debug"
tags = ["linux"]
title = "strace is fantastic"

+++

From time to time, I have issues with some software that I cannot see errors in logs or when running manually, nothing happens. This is very hard to debug.

<!--more-->

For example, rsync sleeping forever or Libreoffice daemon quitting without raise any exception.

To understand more, I use [strace](http://linux.die.net/man/1/strace). Is an excellent tool.

It intercepts and records the system calls which are called by a process and the signals which are received by a process.

<pre>
$ strace sleep 10
execve("/bin/sleep", ["sleep", "10"], [/* 19 vars */]) = 0
brk(0)                                  = 0x608000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f5e461fc000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3

....

nanosleep({10, 0}, NULL)                = 0
close(1)                                = 0
close(2)                                = 0
exit_group(0)                           = ?
</pre>

You can also write the trace output to a file.

<pre>
$ strace -o output.txt ls
</pre>

Or intercept from a specific process.

<pre>
$ strace -p 1234
</pre>

Also, with 'man strace' you can find all information to help you.

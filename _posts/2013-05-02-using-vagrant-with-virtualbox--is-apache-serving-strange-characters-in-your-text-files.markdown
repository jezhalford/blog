---
layout:	post
title:	"Using Vagrant with VirtualBox? Is Apache Serving Strange Characters in Your Text Files?"
date:	2013-05-02
---

  Yes? The same thing happened to me! But it’s easy to fix.

This happens when Apache tries to serve the file contents without reading it first. It’s a performance enhancement that basically means that Apache is asking the Linux Kernel to stream the data directly down the wire.

Apache knows it can do this for static files like JavaScript and CSS, but if those files live in a shared filesystem location (like they might if you’re using Vagrant) then sometimes the kernel will get confused and throw some binary data into the mix, generally on the last line of any file.

So, if you’re seeing those fun diamonds-with-question-marks-in, then add the following to your Apache config –

<Directory "/path-to-files"> EnableSendfile Off </Directory>Reload Apache and you should be good to go.

See <http://httpd.apache.org/docs/current/mod/core.html#enablesendfile>

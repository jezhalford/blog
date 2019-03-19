---
layout:	post
title:	"PHP’s mail() function, Linux and an external SMTP server"
date:	2015-01-28
---

  If you find yourself needing to move some PHP code from Windows to Linux, you might become disappointed when you come to look at the mail() function. In Windows, you can specify an external SMTP server in your php.ini, and the mail() function will send all your email over to that for delivery. In Linux, things aren’t so simple. Fortunately, there is a relatively simple solution.

The usual advice for those wishing to send email from PHP is to avoid the mail() function entirely and use one of the many excellent libraries instead — [Swiftmailer](http://swiftmailer.org/) is a good choice. But what if you’re in the unusual position of having a big chunk of legacy code to and no time to deal with it?

Enter [msmtp](http://msmtp.sourceforge.net/). It’s a nice, stable tool that speaks the same language as *sendmail*, which is what PHP on Linux expects you to use if you’re doing this properly. No one is going to suggest you do that, though.

Instead, assuming you have an SMTP server standing by that’s ready to go, you can try this –

sudo apt-get install msmtpNext, create a config file for msmtp to use –

sudo nano /etc/msmtp\_phpAdd the following –

defaults syslog on account my\_external\_smtp host my.smtp.example.com port 25 from webmaster@example.com auth off account default : my\_external\_smtpNow set some permissions –

sudo chmod 600 /etc/msmtp\_php sudo chown www-data:www-data /etc/msmtp\_phpOpen your php.ini and find the line that starts –

;sendmail\_path =and change it to –

sendmail\_path = "/usr/bin/msmtp -C /etc/msmtp\_php -a my\_external\_smtp -t"Finally, restart Apache or FPM or whatever you’re running PHP with.

That should be it! You can now use mail() again. If you’re in the slightly more complicated situation of having an SMTP server that requires TLS, authentication or both, there’s some really useful advice at <http://freebsd.hypermart.net/msmtp.html>. It should just be a case of modifying your /etc/msmtp\_php file.

*Originally published at *[*jezhalford.com*](https://jezhalford.com/2015/01/28/php-mail-function-linux-and-an-external-smtp-server/)* on January 28, 2015.*

  
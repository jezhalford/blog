---
layout:	post
title:	"Denser, Cooler, Faster, Stronger: PHP On ARM Microservers"
date:	2015-12-30
---

  [ARM](http://www.arm.com/) are the world’s largest designer of semiconductors. They design the processors that run 90% of the world’s smartphones, as well as countless chips inside cars, home electronics, and more-or-less any other thing you can think of the has some electronic smarts to it. They are not so well known as designers of server CPUs, but that may all be about to change.

Last year ARM hired me to help move the PHP-based [arm.com](http://arm.com/) away from the ageing Windows servers it was running on, and onto shiny new ARM-based microservers. The idea being that if ARM servers were now a serious proposition for enterprise data centres, it would certainly make sense for ARM themselves to be using them.

The hardware of choice was HP’s [Moonshot](https://www.hpe.com/uk/en/servers/moonshot.html) platform, a microserver chassis providing power, cooling and networking for up to 45 microserver cartridges, in this case the [ProLiant m400](http://www8.hp.com/uk/en/products/proliant-servers/product-detail.html?oid=7398907).*

![](/img/0*JGnSU2_IPJtsl5uI.jpg)A fully-loaded HP Moonshot chassis, without the top cover.

The m400 packs quite a punch for something no larger than the average paperback book –

CPU AppliedMicro™ X-Gene™ ARMv8 (eight 64-bit cores at up to 2.4GHz) Memory 64GB of DDR3 PC3L-12800 (1600 MHz) SODIMM Low Voltage Memory Storage 120GB / 240GB /480GB SSD Networking 2x 10 Gigabit NICs

While the stats above are impressive, they’re clearly not quite at the same level as the latest Intel 3GHz, 18-core-monsters. The idea, however, is that you can fit 45 of them into the space of one or two traditional servers, and they produce less heat while using less power, which gives you a lower total cost of ownership.

These servers all run the latest Ubuntu Linux, which fully supports the 64 bit ARM CPU architecture. It is therefore not especially challenging to get a simple PHP application up and running on a single ARM server — you install a basic stack using apt-get, and off you go. The interesting part comes with scaling and fault tolerance.

Web traffic can be spread across several machines easily enough — we nominated two cartridges (sharing a single virtual IP address) to run [nginx](https://www.nginx.com/) as a reverse proxy. This balanced traffic across six other cartridges acting as web servers. Since the cartridges come with so much memory we were also able to configure these to act as caches for static assets, allowing us to handle more traffic.

Scaling the database was a more tricky problem. The most common way to make a database handle more traffic is to install it on a larger machine. With microsevers this is obviously not an option. Instead, we went for [MySQL Percona XtraDB Cluster](https://www.percona.com/software/mysql-database/percona-xtradb-cluster) (or PXC for short). This is a modified form of MySQL that provides horizontal scaling across multiple machines. It’s a bit of pain to configure, but once it’s up and running it’s quite reliable. Quite rightly it prioritises data consistency over availability, so if you manage to get it into a state where it isn’t sure that all of its members have a clear picture of the database (and we did) then it will stop responding to queries, bringing down your website (and it did). In our case this was down to tables that didn’t have a primary key (remember, this was a legacy code base filled with all kinds of surprises). We installed PXC on five cartridges, giving us plenty of capacity to handle load and plenty of failure tolerance.

A multi-node database requires something to load balance it, and [HAProxy](http://www.haproxy.org/) was our tool of choice here. It offers built-in support for load balancing MySQL, and is pretty straightforward to configure. After much deliberation we opted to install a separate HAProxy instance on each web server, avoiding each individual web server having any single point of failure besides itself.

Session storage is a problem common across most serious PHP implementations, and ours was no different. We went for Memcache, which made sense given the amount of memory available on the ProLiant cartridges, and given our collective experience with it, but I’m not a huge fan of this approach. We also needed to use Memcache to store a few bits of application data and mixing all of that up together seems like bad news. If I did the project again I’d be keen to try [Redis Cluster](http://redis.io/topics/cluster-tutorial), which seems like a great fit.

On the web servers themselves we kept things fairly simple — we had to use Apache, since it hooked into an Enterprise Single Sign-On service that ARM was already using. We used [msmtp](https://jezhalford.com/2015/01/28/php-mail-function-linux-and-an-external-smtp-server/) to make PHP’s mail() function work as it did on the old Windows server, and we updated a hundred or so MSSQL queries to work with MySQL.

For file storage, we considered clustering the web nodes together using [Ceph](http://ceph.com/) or [Gluster](https://www.gluster.org/), but in the end kept things simple by mounting an external file server that ARM already had available. Since there were so many logs being generated on so many machines, we also configured log aggregation from the various web, database and load-balancer nodes to a single “management” node using [rsyslog](http://www.rsyslog.com/). This was a fairly basic solution, and something like [logstash](https://www.elastic.co/products/logstash) would have been nice to try if we’d had the time. Finally, a multi-server architecture really highlights the advantage of a configuration management tool. We used [Ansible](http://www.ansible.com/) to provision and control the various nodes.

*ARM don’t manufacture any hardware themselves, they license their designs to manufacturers. You’ll therefore never see an ARM-branded server, but the m400s have ARM-designed CPUs inside.

*Originally published at *[*jezhalford.com*](https://jezhalford.com/2015/12/30/denser-cooler-faster-stronger-php-on-arm-microservers/)* on December 30, 2015.*

  
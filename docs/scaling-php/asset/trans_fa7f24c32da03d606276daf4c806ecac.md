
1 > apt-get install haproxy  
2 > vi /etc/haproxy/haproxy.cfg  

4 global  
5 maxconn 50000  
6 user haproxy  
7 group haproxy  
8 stats socket /tmp/haproxy  
9 node lb1  
10 nbproc 1  
11 daemon  

13 defaults  
14 log     global  
15 retries 3  
16 option  dontlog-normal  
17 option  splice-auto  
18 timeout connect 200ms  
19 timeout client  2s  
20 timeout server  2s  
21 maxconn 50000  

24 listen mysql 192.51.100.100:3306  
25 mode tcp  
26 balance leastconn  

28 server slave01 192.51.100.1:3306 check  
29 server slave02 192.51.100.2:3306 check  
30 server slave03 192.51.100.3:3306 check  

32 listen stats *:1936  
33 mode http  
34 stats enable  
35 stats uri /  
36 stats hide-version  
37 stats auth Username:Password  

HAProxy won’t run until you enable the init.d script, so let’s do that now.  

1 > vi /etc/default/haproxy  
2     # Set ENABLED to 1 if you want the init script to start haproxy.  
3     ENABLED=1  

5 > service haproxy start  

With this configuration, we set up three database slaves, each defined with a `server` line. Now, all we have to do is modify our code to connect to HAProxy’s IP Address instead of the slave IP Address. (The HAProxy IP is defined in the configuration file in the `listen` setting. In this example, it’s `192.51.100.100`.)  

1 <?php  
2 $mysqli = new mysqli("192.51.100.100", "username", "password");  

Now, every time you make a MySQL connection, you will connect to HAProxy instead of directly to the MySQL slave. HAProxy will choose the slave with the least amount of connections and connect you to that slave. You can also use `balance roundrobin` as your balancing strategy if you want HAProxy to use less intelligence when picking slaves.  

Since we set `timeout connect` as `200ms`, if a connection to a slave fails to happen in in less than 200 milliseconds, HAProxy will try another slave instead. Failed or overloaded MySQL slaves are now a non-issue.  

With `timeout client` and `timeout server` both set at `2s`, it means that a long-running client or hung query will get disconnected after 2 seconds. Having a very low query timeout threshold makes sense for a web application, but obviously not for any kind of analytics or background processes, so you’ll want to connect directly to the slaves or set up a secondary HAProxy `listen` block with different timeouts for those scenarios.  

The best feature, in my opinion, is that failed slaves are automatically removed from the pool and re-added once they come back up. Until we ran this setup in production on Twitpic, I’d have to wake up in the middle of the night to manually remove broken slaves from our configuration files. It was a real pain-point for us as we grew to more and more slaves.  

You also get a really nice web interface for viewing the status of your MySQL slaves.  

![](images/06----haproxy.png)  

### Accepting the Master as a SPOF  

When you choose to use MySQL, you need to learn to accept and understand that your master server is always going to be a single point of failure. Of course, there are solutions and workarounds like [DRBd](http://dev.mysql.com/doc/refman/5.0/en/ha-drbd.html), [Percona XtraDB Cluster](http://www.percona.com/software/percona-xtradb-cluster), and MySQL Master-Master Replication. The downside, though, is that they are often slow and extremely complex.  

The alternative is to accept and deal with the fact that your master database server is going to be a single point of failure. You can work around the problem by scripting the failover process and dealing with the situation with as little downtime as possible. Check out [JetPants](http://tumblr.com) by Tumblr as a starting point for a MySQL master failover/slave promotion toolkit.  

#### What really happens when your master fails?  

I used to be worried that if our master database crashed, we would lose data and be faced with an enormous amount of downtime. When I thought about it, though I realized a few things-  

**The site won’t go down**  

Since we only write data to the master, and never read from it, it’s really just a glorified coordinator of data. If it crashes, our site just goes into a read-only state, but it’s still up and functioning.  

**We won’t lose data**  

Because we make daily, off-site backups, even in the event of a catastrophic failure, losing just the master is even less of a big deal because data is replicated and stored safely on all of the slaves.  

Using [semi-synchronous replication](http://dev.mysql.com/doc/refman/5.5/en/replication-semisync-installation.html) in MySQL 5.5 is needed to guarantee that we don’t lose *anything* in the event of a master crash. With the default asynchronous replication, it’s possible to lose data that has been written to the master but not yet replicated to the slaves during a crash. Semi-synchronous replication, instead, guarantees that new data is replicated to at least one slave.  

#### Promoting a slave as the master  

Okay, so your master database has failed. What is next? Well, we need to promote a slave to be the new master to get it up and running as quickly as possible.  

Let’s quickly go through a high level overview of the slave to master promotion process.  

**Assumptions**  

*   Your master server is named `master01`, and you have five slaves, `slave01-05`.  

*   You want to promote `slave01` to be the new master.  

*   `master01` is still up-and-running.  

*   Your code writes to the MySQL using the database user `app_user`.  

If `master01` is still up-and-running, it’s important to disable writes to it before failing over to the new master so your data doesn’t get out of sync. On `master01`, first delete the user that your application uses (`app_user`), so it won’t be able to establish any new connections. Next, put the database in read-only mode:  

1 > DROP USER `app_user`  
2 > SET GLOBAL read_only=1;  
3 > FLUSH TABLES WITH READ LOCK;  

At this point, your database cluster is in a total read-only mode. If `master01` has crashed or become unavailable, this step is unnecessary because your cluster is already effectively in a read-only state.  

Next, we need to pick a slave to be the new master. In this scenario, we’ve decided to promote `slave01`. On `slave01`, you’ll want to copy over your `my.cnf` from `master01`, particularly the `log-bin` setting, and restart MySQL. It’s helpful to have a backup master server already configured for this purpose.  

On `slave01`, you’ll want to run `SHOW MASTER STATUS` to determine the binlog position.  

1 mysql> show master status \G  
2 *************************** 1. row ***************************  
3 File: master-bin.000001  
4 Position: 98  

Now that you know the position of the binlog, you can connect to the rest of your slaves and reconfigure them to use `slave01` as the new master server with the `CHANGE MASTER TO` command.  

1 mysql@slave02> STOP SLAVE;  
2 mysql@slave02> CHANGE MASTER TO	MASTER_HOST="slave01",  
3 MASTER_LOG_FILE="master-bin.000001", MASTER_LOG_POS=98;  
4 mysql@slave02> START SLAVE;  

Lastly, update your application configuration to write to `slave01` instead of `master01`.  

Doing it manually isn’t the best scenario, and a good portion of this can be scripted. Instead of scripting it yourself, though, it’s worth checking out [mysql-master-ha](http://code.google.com/p/mysql-master-ha/) which can handle automatic master failover by scripting the solution described above.  

#### Further research and reading  

The topic of MySQL Master Failover is huge and could easily take up its own book, so it’s impossible for me to cover all of the possible solutions here. For most people, taking it into a read-only state and manually promoting a new master is the simplest and best approach. Unfortunately, it’s not a solution that works for everyone, so here are some further places to look for more information on some more robust (and more complex) solutions for handling master failure.  

*   [Automated Master Failover (Slides)](http://www.slideshare.net/matsunobu/automated-master-failover)  

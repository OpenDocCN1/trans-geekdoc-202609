
Ahh… the database file system wars. There are plenty of options and a thousand opinions available on the internet. Let’s talk about hard numbers- I’ve compared and benchmarked the two most recommended MySQL file systems, `ext4` and `XFS`. We use ext4 on Twitpic, and from the research I’ve done, I expected it to perform equally as well as XFS - not to mention, ext4 is the default file system choice for most Linux distros nowadays.

Anyways, using `sysbench` (covered at the end of the chapter), I performed a read/write MySQL benchmark comparing XFS to ext4 and the results surprised me. I ran the test on a 16-core machine to make sure that benchmark wouldn’t become CPU bound and skew the results. It created a table that was a bit larger than the `innodb_buffer_pool_size`, so not all of the data could be fit into memory, forcing it to hit the disk for some reads.

Comparing ext4 to XFS, I found that XFS was extremely more performant on a benchmark of 100,000 read **and** write queries.

| XFS || ext4 |
| --- | --- |
| 21,755 qps || 16,560 qps |

By the way, to install XFS on Ubuntu, you just need to install `xfsprogs` and run `mkfs.xfs` on the device you want to format.

```
1 > apt-get install xfsprogs
2 > mkfs.xfs /dev/sdf1
```

*The tests were done using a dedicated disk for the MySQL data files, so there was no I/O competition from other system processes.*

##### Raw Device Mode

You can even use InnoDB in something called **Raw Device Mode**, where it writes data directly to an unformatted disk or partition without using any file system at all. I highly recommend not using it, even though it’s slightly faster, because it makes managing your data a complete nightmare. You lose all visibility in the database files that you would otherwise have when using a normal file system. Additionally, benchmarks show that `ext4` and `XFS` are only a tiny bit slower than using a raw device.

For the curious, you can use raw device mode by changing the `innodb_data_file_path` setting-

```
1 innodb_data_home_dir=
2 innodb_data_file_path=/dev/sda1:500Gnewraw
```

Restart MySQL, it will create the data file, then change `innodb_data_file_path` again.

```
1 innodb_data_file_path=/dev/sda1:500Graw
```

##### The future of file systems

It’s worth quickly mentioning [`ZFS`](http://en.wikipedia.org/wiki/ZFS) and [`btrfs`](http://en.wikipedia.org/wiki/Btrfs). Both are pretty cool and likely the future of file systems, because they support modern features like copy-on-write, SSD caching, and de-duplication, but `ZFS` doesn’t have great support on Linux yet and `Btrfs` is still too experimental to use in production.

### Load balancing MySQL Slaves

Having multiple read-only MySQL slaves are great, but you need a way to load balance them in your code. By default, PHP doesn’t handle this for you at all, and it’s something you need to code in yourself. I’m going to show you a few ways to do it below.

#### Database Class

The easiest way is to do it within code using a simple database class. Select a slave at random and return a database connection depending on the one you chose.

```
 1 <?php
 2 class Database {
 3   static function connect() {
 4   	// Assuming your slave hosts come from a configuration file, but
 5   	// for brevity, we just define them here.
 6     $slaves = array('192.51.100.1', '192.51.100.2', '192.51.100.3');
 7     $slave  = $slaves[array_rand($slaves)];
 8     
 9     return new mysqli($slave, 'user', 'password');
10   }
11 }
12 
13 $slave = Database::connect();
```

The downside of handling slave selection this way, and doing it in code in general, is that if one of your slaves crash, it will not be handled gracefully while it waits for the connection to timeout. Of course, you can remove the slave from your configuration manually when it goes down, but that’s a manual process and I’m not a huge fan of waking up in the middle of the night to update configuration files.

#### Extending PDO

Similarly to the above, if you’re using PDO, you can handle load balancing a bit more elegantly, but with the same downsides as the Database class used in the previous section (ungraceful handling of down slaves).

```
 1 <?php
 2 class SlavePDO extends PDO {
 3 
 4   public function __construct($dsn, $user=null, $pw=null, $options) {
 5   	// Assuming your slave hosts come from a configuration file, but
 6   	// for brevity, we just define them here.
 7     $slaves = array('192.51.100.1', '192.51.100.2', '192.51.100.3');
 8     $slave = $slaves[array_rand($slaves)];
 9     
10     $dsn .= ";host={$slave}";
11     parent::__construct($dsn, $user, $pw);
12 
13   }
14 
15 }
16 
17 $slave = new SlavePDO('mysql:dbname=test', 'user', 'password');
```

#### Using the mysqlnd_ms plugin

The *MySQL Native Driver* is an alternative MySQL driver written by the PHP team that was first included in PHP 5.3. It was added to remove PHP’s dependency on `libmysql` and tie MySQL further into the core of PHP. The MySQL Native Driver also added in the ability for developers to create both PHP and C plugins to add functionality PHP’s MySQL Driver. Since MySQLND is used internally, MySQLND plugins work with any interface that you use to interact with MySQL- PDO, MySQLi, and even the old-school, deprecated, unrecommended [MySQL extension](http://us1.php.net/manual/en/book.mysql.php).

First, you need to install the `mysqlnd_ms` PECL plugin.

```
1 > pecl install mysqlnd_ms
```

Next, add a configuration file to your app. For the example, let’s say it’s stored in `./config/db.conf`

```
 1 > vi ./config/db.conf
 2   { "app" : {
 3     "master": [ { "host": "192.51.100.10" } ],
 4     "slave": [
 5       { "host": "192.51.100.1" },
 6       { "host": "192.51.100.2" },
 7       { "host": "192.51.100.3" }]
 8     },
 9     "failover": { "strategy": "loop_before_master" }
10   }
```

And then enable `mysqlnd_ms` in your application.

```
1 <?php
2 ini_set("mysqlnd_ms.enable", 1);
3 int_set("mysqlnd_ms.config_file", "./config/db.conf");
```

Now, whenever you want to make a MySQL connection (this works with both PDO and mysqli), you just pass in `app` as the host.

```
1 <?php
2 $mysqli = new mysqli("app", "username", "password");
```

The cool thing here is that not only will it round robin between your slaves, it will also send any write queries to your Master database. The failure handling is still sub-optimal, though.

The plugin lets us set a failure strategy in the configuration. In the example, I’ve set it as `loop_before_master`, which means that it will try the other slaves and then try the master when a slave fails. This is great, but it doesn’t remember failed slaves between requests, so you’ll still pay the cost of waiting for the slave to timeout, every single time. This is, however, better than just outright failure.

#### Using HAProxy

The best way to handle slave load balancing is to use a software load balancer like HAProxy. As discussed in Chapter 4, HAProxy can do Layer 4 load balancing, i.e., raw TCP sockets. While most people use this functionality load balancing HTTP, it can be used equally as well for internally load balancing your MySQL connections as well.

Why is HAProxy the best solution? For two reasons-

1.  When it detects a database slave as unresponsive (crashed, down, whatever), it removes it from the load balancer pool and stops using it. It does this detection quickly and is completely transparent. No configuration changes, no downtime, no waiting for connections to timeout, and**, best of all, no waking up in the middle of the night**.

2.  HAProxy lets you set very granular timeouts down to the millisecond. This lets you side step the poor MySQL timeout management in PHP (which is limited to 1 second, minimum) and set more reasonable timeouts.

The installation and setup is pretty similar to how we setup our HTTP Load Balancer.

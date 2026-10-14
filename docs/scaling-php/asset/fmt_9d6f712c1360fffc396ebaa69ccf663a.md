
Lists are great for storing, well, lists of data. You can add, remove, trim, push, and pop items from the list all atomically. I love to use lists for time ordered data, because they are naturally sorted by insertion time when you use `lpush`.

A great use case is for notification feeds, where you have a list for every user and push new notifications to the front of the list.

Lists are also the basic primitive that our queuing system, Resque, uses as it’s underlying data structure.

#### Sets and Sorted Sets

Sets are similar to lists in that you can store a bunch of data in single key. The main differences are that sets are completely unordered and can not contain any duplicate data. Unlike lists, sets give you more robust features- checking to see if a value is inside of a set, unioning sets together and even calculating intersections and differences. There is a lot of power here.

```
1 <?php
2 
3 $r->sadd("names", "steve", "john", "alice");
4 $r->scard("names"); // returns 3
5 $r->sismember("names", "steve"); // returns true
```

On top of sets, we also have sorted sets which are slower but allow you to order your set as they are normally completely unordered.

One use case for sets is storing lists of data that you want to guarantee is unique- usernames, category names, or titles. You can quickly use `sismember` to determine if a value is part of your set.

#### Transactions

You can also group commands together into a transaction. Transactions are faster for issuing a lot of commands because it only involves one roundtrip to Redis.

```
1 <?php
2 
3 $r->multi()
4   ->set("key", "value")
5   ->set("foo", "bar");
6   ->hset("user:2", "name", "Steve")
7   ->exec();
```

Transactions also run as an atomic unit, but you can disable that by passing `Redis::PIPELINE` to `multi()`, which transmits the commands to the server in one block, but doesn’t guarantee that the commands will execute atomically.

#### Pub/Sub

Redis includes a really cool publish and subscribe feature that’s great for doing cross-process, asynchronous communication.

Imagine we had two scripts, in the subscriber:

```
1 <?php
2 
3 $r->subscribe(array('updates'), function($r, $channel, $data) {
4   echo "Received {$data}\n";
5 });
```

And in the publisher:

```
1 <?php
2 
3 $r->publish('updates', "Some new data");
```

The subscriber would receive our message from the publisher, like magic. Multiple subscribers can listen into the same channel and you can have multiple channels. It’s pretty powerful and can be leveraged for backend script communication, implementing a chat room, and for streaming services over websockets.

### The importance of Atomic Operations

All commands in Redis are atomic. What that means is that each command is isolated and doesn’t impact the state of any other commands. Let’s look at an example of where this matters (and why atomic counters are important).

The niave way of counting might look like this:

```
1 $v = $r->get("key");  // $v is 1
2 $r->set("key", $v+1); // Now setting "key" as 2
```

That would be wrong, though, because if another process changed the value of `key` to 2 between our `get` and `set` commands running, we’d set it at 2 again and lose the increment.

In Redis (and Memcached and APC), we can solve this by using atomic counters. Effectively, we tell the counter how much we want to increase the counter by, and it does the math on the server.

```
1 $v = $r->incr("key"); // Returns the new value of "key"
```

With Redis, the `watch()` command lets you do check-and-set operations, so while using `incr()` is preferred, you could fix the first example like this:

```
1 $ret = false;
2 while ($ret == false) {
3   $r->watch("key");
4   $v = $r->get("key");
5   
6   // Will return false if "key" was modified by another client
7   // between watch() and exec().
8   $ret =  $r->multi()->set("key", $v+1)->exec();
9 }
```

### Performance Limitations of Redis

Unlike Memcached (which is multi-threaded), Redis is single-threaded and is evented. What that means is that each Redis server can only take advantage of a single CPU core. This isn’t usually a problem because most Redis commands are `O(1)` or `O(n)`, so they don’t burn up much CPU. In the case of needing to scale your Redis CPU usage, you can run multiple Redis daemons, using different ports, on the same server.

Redis uses more memory to store the same data on a 64-bit system than on 32-bit system because pointers are 8 bytes on 64-bit systems and 4 bytes on 32 bit systems. Each item that you store in Redis uses atleast one pointer (3 for lists, 8+ for a sorted set), so if you have lots of small keys the memory difference can become significant.

One way around it is to run your system in 32-bit mode with PAE (Physical Address Extension), which allows your kernel to address 36-bits of address space (64GB of memory). Even with PAE, each process can only see 4GB of memory, so you’d have to run 16 separate Redis daemons to use all of the free memory.

In practice, does it matter? Not really. Suck it up, use a 64-bit system, and just add more memory. PAE is a kludgy kernel hack anyways.

### Installing Redis from Dotdeb

Ubuntu bundles an old version of Redis and the Redis website only provides the source code, so we need to install it from [Dotdeb](http://dotdeb.com). Of course, you could compile Redis from scratch, but I prefer to use packages when possible.

Setting up Dotdeb is as easy as adding another apt source (you can skip this if you already used DotDeb for installing PHP 5.4).

```
1 > vi /etc/apt/sources.list.d/dotdeb.list
2 
3 deb http://packages.dotdeb.org squeeze all
4 deb-src http://packages.dotdeb.org squeeze all
5 
6 > wget http://www.dotdeb.org/dotdeb.gpg
7 > cat dotdeb.gpg | sudo apt-key add -
8 > apt-get update
```

Installing Redis is as easy as running `apt-get`.

```
1 > apt-get install redis-server
2 > service redis-server start
```

At the time of writing, Redis 2.6 was *just* released. It’s preferable to always run the latest release because new features and optimizations are always being added between versions.

### Installing the `phpredis` C extension

There are some pure PHP redis libraries, like [Predis](https://github.com/nrk/predis) and [Redisent](https://github.com/jdp/redisent) that do a good job of implementing a Redis library without any C code, but it comes at a cost- they’re 3-4x slower.

The best C extension for connecting PHP to Redis is [phpredis](https://github.com/nicolasff/phpredis)\- it’s frequently updated and works very consistently. Unfortunately, it doesn’t use [hiredis](http://github.com/redis/hiredis) *yet*, but it still works very well.

Note: PHPRedis is not included in the PECL Repository. You may skip the installation steps below by just using `pecl install redis`.

Installing it takes a tiny bit more work than usual, because it’s not in the official PHP PECL repository.

```
 1 # You might not need these if you already have them
 2 > apt-get install git build-essential
 3 
 4 # First install igbinary
 5 > pecl install igbinary
 6 
 7 > git clone git://github.com/nicolasff/phpredis.git
 8 > cd phpredis
 9 > phpize
10 > ./configure --enable-redis-igbinary
11 > make && make install
12 > vi /etc/php5/conf.d/phpredis.ini
13   extension=redis.so
```

After that, you’ll need to restart PHP-FPM.

| ![information](images/leanpub_information.png) || **What’s igbinary?**Igbinary is a replacement for the out-of-the-box PHP serializer. Normally, PHPs serializer is string based and serializes objects into an ASCII-based format. Not only is this slow, but it’s also not space efficient, which makes a big difference when you’re storing PHP objects (such as arrays, database results, and models in your cache). Igbinary, instead, replaces the serializer with one that outputs binary instead. |

| --- | --- |

### Tuning Redis for Performance

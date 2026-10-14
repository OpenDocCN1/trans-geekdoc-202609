
Still with me? Great. I want to walk you through this problem like we’re working on the project together. I think the **process** it’s what’s helpful here— the answer itself isn’t that valuable, that’s why I’m walking you through the entire problem from start to finish instead of just giving you the solution.

My initial assumptions were that the increase in `502 Bad Gateway` errors were caused by one of the following problems.

1.  Too many connections to Memcached due to reloading PHP

2.  Reloading PHP-FPM (`kill -USR2`) wasn’t working as expected

3.  Zend OpCache taking time to warm up, causing many PHP requests to run without compiled bytecode and spiking CPU usage

### Busting the assumptions

The first step to being able to test the three assumptions was to be able to replicate the problem. Unfortunately, it was nearly impossible to replicate this on a development server, because without a heavy flow of real traffic, code would deploy without issue. I segregated a production server that was serving traffic and force deployed to it over and over. Bingo— CPU spike, 502 errors, the works.

I can replicate the issue over and over again. Now I’m ready to start testing my assumptions, one by one.

#### Too many connections to Memcached from reloading PHP

My first assumption was that during the graceful reload of PHP, the old workers might still be holding onto their old connection to Memcached while the new ones start up. Memcached has a connection limit, if we exceed this, the memcached client will start throwing exceptions and these exceptions could be causing the problems we’re experiencing.

Easy to test— if we force a deploy on our test box with 256 PHP-FPM workers, we should see the number of connections on our Memcached server go up by exactly 256. We can easily monitor this with `telnet`.

```
1 telnet memcache_server.ip 11211
2 > STATS
3 < STAT curr_connections 3840
4 ...
```

Okay, we have 3840 connections to our memcache server, if we watch it while force deploying on our test box, we should see it blip up to 4096.

Deploy.. wait… and.. Nope. That wasn’t it, after the deploy I see the number of connections hold steady at 3840. Myth busted.

#### Reloading PHP-FPM (`kill -USR2`) doesn’t work as expected

When we deploy code, we gracefully reload PHP-FPM. Why reload PHP-FPM on deploy? We have `opcache.validate_timestamps=0` and `opcache.revalidate_freq=0` set in our `php.ini`. What these settings do is make it so that once Zend OpCache compiles the bytecode for a particular PHP file, it will never check the file for updates again. That is to say, if the file is modified or changed (manually or by a deploy), PHP will not read the latest updates until PHP-FPM is restarted or reloaded.

| ![question](images/leanpub_question.png) || What does graceful reloading do? When you send the PHP-FPM master process the `USR2` signal, it waits for each child process to finish the current request and then replaces the old process with a new one. This allows PHP to gracefully restart without dropping any requests. |

| --- | --- |

This one is easy to test. Instead of force deploying PHP, I just need to manually `kill -USR2` it on my test box and check for a spike in errors. So, I run:

```
1 $ kill -USR2 `cat /var/run/php-fpm5.pid`
```

And what do I see! A small jump in `502 Bad Request` errors. Is this it? Did we figure out our culprit? No, but it led me to discovering a small contributer. After reading the PHP-FPM source, I discovered that I needed to set `process_control_timeout` in my `fpm.conf` file, otherwise PHP-FPM will stall and wait forever for all of the children to finish their request. Setting `process_control_timeout=10s` made gracefully reloading PHP much smoother. But the main issue still persisted— a deploy, even with this change, still causes high CPU and 502 errors. Onwards.

#### Zend OpCache is taking a long time to warm up

The assumption here is that the OpCache takes a little while to warm up and that without the compiled PHP bytecode, the servers are running the PHP code slower and using much more CPU.

I was writing a bunch of logic in Chef to pre-warm the cache before deploying, I decided I should spend a few minutes testing this assumption before investing a ton of time trying to fix it.

I proved this assumption wrong in two ways:

The first (and easiest) way— I disabled Zend OpCache completely with `opcache.enable=0` in `php.ini` and reloaded PHP. While I saw that load was certainly higher, the server was not throwing `502 Bad Gateway` errors nor was the CPU at 100%. Busted.

The other way I tested was restarting PHP and after the first request printing the contents of `opcache_get_status()`. This function shows all of the files currently cached by Zend OpCache. It turns out that even with a very heavy framework like CakePHP, almost 75% of the code was compiled to bytecode after the first request.

Bummer! We’re out of assumptions. Back to the drawing board.

### Now what? I’m out of ideas

All of the assumptions that I had went down the tube as I systematically debunked each one. I was SURE that I knew what the problem was, but as it turns out, I was completely wrong. I’m out of ideas and what do I besides give up and pull out my hair?

#### `strace` to the rescue!

When you need a partner to help you debug, `strace` has got your back. It’s one of my favorite tools on Linux and while you can spend an entire semester learning about all of the features it has, the simplest use-case can often be all that you need.

`strace` gives you the ability to attach to a running, live process (while marginally impacting performance— okay for our use, but don’t `strace` a production MySQL server, for instance) and view what system calls it is making. Sure, you can’t see the exact code that’s executing, but you can see external network requests, filesystem calls, and other low-level stuff.

So, I deploy once again, and find myself a PHP-FPM worker to attach to:

```
1 $ ps aux | grep php-fpm
2 
3 myapp 128131  2.9  0.0 324132 57396 ?        R    10:54  11:50 php-fpm: pool w\
4 ww
5 ...
```

Perfect, quickly I attach to this process `128131` and start `strace`‘ing it, to see what it’s up to. Lo and behold, I see something interesting right away. The output flies by at mach-1, but sure enough it keeps pausing for several seconds after this block of system calls… it’s stalling here!

```
1 open("/tmp/cake_core_file_map", O_RDWR|O_CREAT, 0666) = 10
2 fstat(10, {st_mode=S_IFREG|0666, st_size=29199, ...}) = 0
3 lseek(10, 0, SEEK_CUR)                  = 0
4 close(15)                               = 0
5 flock(10, LOCK_EX)                      = 0
```

So what the hell is this? Well, PHP is stalling at the last call to `flock`. What’s `flock`? It’s a system call to obtain a lock on the file, so no other programs can write to it. Why, it’s waiting to get an exclusive file lock and blocking until it can get one. What file is it trying to obtain an exclusive lock on? OUR CAKEPHP SYSTEM CACHE FILES! Somewhere in the internal CakePHP code, it’s locking the files before writing to them!

And that’s the core problem. We found it. When we deploy a new code release, we’re wiping out our `/tmp` directory— we WANT the CakePHP cache files to be refreshed after a deploy because a database table or model may change. But what’s happening is that a stampede of 256 PHP-FPM workers are trying to update the cache simultaneously, each requesting an exclusive file lock to do so. And that’s where it’s blocking— because of the competition over obtaining a file lock. The blocking causes requests to pile up, which causes our socket backlog to fill up, and forces Nginx to start throwing 502 Bad Gateway errors. That’s it!

### The solution(s)

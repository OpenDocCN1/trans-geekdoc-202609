
-   [Still with me? Great. 我想要向你详细说明这个问题，就像我们在一起合作完成项目一样。我认为**process** 才是关键所在——答案本身并不那么重要，所以我选择从头到尾一步步带你完成整个问题的解决过程，而不是直接给出答案。]

-   [我的初始假设是 `502 Bad Gateway` 错误的增加是由以下原因之一导致的。]

-   [1. 由于重新加载 PHP，Memcached 的连接数过多]

-   [2. 重新加载 PHP-FPM（`kill -USR2`）没有按预期工作]

-   [3. Zend OpCache 需要时间进行预热，导致大量 PHP 请求在未编译字节码的情况下运行，进而引起 CPU 使用率飙升]

-   [### Busting the assumptions]

-   [第一步是能够测试这三个假设，需要能够复制问题。不幸的是，在没有大量真实流量的开发服务器上几乎无法复制此问题，因为没有流量，代码会直接部署成功。于是我隔离了一个正在提供流量的生产服务器，并反复强制将其部署到该服务器上。Bingo— CPU 飙升，502 错误，一切如预期。]

-   [我可以一遍又一遍复制此问题。现在我已准备好逐个测试我的假设。]

-   [#### 过多的 Memcached 连接来自 PHP 重新加载]

-   [我的第一个假设是：在 PHP 的优雅重载过程中，旧工作进程可能仍然保留着对 Memcached 的旧连接，而新工作进程正在启动。Memcached 有连接上限，如果超过该上限，memcached 客户端会开始抛出异常，这些异常可能正是我们所遇到的问题的根源。]

-   [Easy to test— 如果我们在测试机上强制部署 256 个 PHP-FPM 工作进程，Memcached 服务器上的连接数应该正好增加 256。我们可以使用 `telnet` 来监控此情况：]

-   ```
- 1 telnet memcache_server.ip 11211
- 2 > STATS
- 3 < STAT curr_connections 3840
- 4 ...
- ```

- [OK, 我们的 memcache 服务器上有 3840 个连接，如果在测试机上强制部署，我们应该看到连接数瞬间上升到 4096。]

- [Deploy.. wait… and.. Nope. 部署后连接数保持在 3840 不变。假设被推翻。]

-   [#### 重新加载 PHP-FPM（`kill -USR2`）效果不如预期]

-   [在部署代码时，我们会优雅重载 PHP-FPM。为什么要优雅重载 PHP-FPM？我们在 `php.ini` 中将 `opcache.validate_timestamps=0` 与 `opcache.revalidate_freq=0` 设置在一起。这些设置的作用是：一旦 Zend OpCache 为某个 PHP 文件编译完成字节码，就永远不会再检查该文件是否有更新。也就是说，如果文件被手动修改或通过部署更新，PHP 将不会读取最新内容，直到 PHP-FPM 被重启或重载。]

- [| ![question](images/leanpub_question.png) || What does graceful reloading do? When you send the PHP-FPM master process the `USR2` signal, it waits for each child process to finish the current request and then replaces the old process with a new one. This allows PHP to gracefully restart without dropping any requests. |]

- [| --- | --- |]

- [这一步很容易测试。与其强制部署 PHP，我只需在测试机上手动执行 `kill -USR2` 并检查错误是否有轻微上升。于是我运行：]

- ```
- 1 $ kill -USR2 `cat /var/run/php-fpm5.pid`
- ```

- [And what do I see! A small jump in `502 Bad Request` errors. Is this it? Did we figure out our culprit? No, but it led me to discovering a small contributer. After reading the PHP-FPM source, I discovered that I needed to set `process_control_timeout` in my `fpm.conf` file, otherwise PHP-FPM will stall and wait forever for all of the children to finish their request. Setting `process_control_timeout=10s` made gracefully reloading PHP much smoother. But the main issue still persisted— a deploy, even with this change, still causes high CPU and 502 errors. Onwards.]

-   [#### Zend OpCache 正在花费大量时间预热]

-   [假设是 Zend OpCache 需要一段时间预热，而没有编译的字节码会导致 PHP 代码运行变慢，从而消耗大量 CPU。]

- [I was writing a bunch of logic in Chef to pre-warm the cache before deploying, I decided I should spend a few minutes testing this assumption before investing a ton of time trying to fix it.]

- [I proved this assumption wrong in two ways:]

- [The first (and easiest) way— I disabled Zend OpCache completely with `opcache.enable=0` in `php.ini` and reloaded PHP. While I saw that load was certainly higher, the server was not throwing `502 Bad Gateway` errors nor was the CPU at 100%. Busted.]

- [The other way I tested was restarting PHP and after the first request printing the contents of `opcache_get_status()`. This function shows all of the files currently cached by Zend OpCache. It turns out that even with a very heavy framework like CakePHP, almost 75% of the code was compiled to bytecode after the first request.]

- [Bummer! 我们已经没有任何假设可以测试了，回到原点。]

-   [### Now what? I’m out of ideas]

-   [All of the assumptions that I had went down the tube as I systematically debunked each one. I was SURE that I knew what the problem was, but as it turns out, I was completely wrong. I’m out of ideas and what do I besides give up and pull out my hair?]

-   [`strace` to the rescue!]

-   [When you need a partner to help you debug, `strace` has got your back. It’s one of my favorite tools on Linux and while you can spend an entire semester learning about all of the features it has, the simplest use-case can often be all that you need.]

-   [`strace` gives you the ability to attach to a running, live process (while marginally impacting performance— okay for our use, but don’t `strace` a production MySQL server, for instance) and view what system calls it is making. Sure, you can’t see the exact code that’s executing, but you can see external network requests, filesystem calls, and other low-level stuff.]

-   [So, I deploy once again, and find myself a PHP-FPM worker to attach to:]

-   ```
- 1 $ ps aux | grep php-fpm
- 2 
- 3 myapp 128131  2.9  0.0 324132 57396 ?        R    10:54  11:50 php-fpm: pool w\
- 4 ww
- 5 ...
- ```

- [Perfect, quickly I attach to this process `128131` and start `strace`‘ing it, to see what it’s up to. Lo and behold, I see something interesting right away. The output flies by at mach-1, but sure enough it keeps pausing for several seconds after this block of system calls… it’s stalling here!]

-   ```
- 1 open("/tmp/cake_core_file_map", O_RDWR|O_CREAT, 0666) = 10
- 2 fstat(10, {st_mode=S_IFREG|0666, st_size=29199, ...}) = 0
- 3 lseek(10, 0, SEEK_CUR)                  = 0
- 4 close(15)                               = 0
- 5 flock(10, LOCK_EX)                      = 0
- ```

- [So what the hell is this? Well, PHP is stalling at the last call to `flock`. What’s `flock`? It’s a system call to obtain a lock on the file, so no other programs can write to it. Why, it’s waiting to get an exclusive file lock and blocking until it can get one. What file is it trying to obtain an exclusive lock on? OUR CAKEPHP SYSTEM CACHE FILES! Somewhere in the internal CakePHP code, it’s locking the files before writing to them!]

- [And that’s the core problem. We found it. When we deploy a new code release, we’re wiping out our `/tmp` directory— we WANT the CakePHP cache files to be refreshed after a deploy because a database table or model may change. But what’s happening is that a stampede of 256 PHP-FPM workers are trying to update the cache simultaneously, each requesting an exclusive file lock to do so. And that’s where it’s blocking— because of the competition over obtaining a file lock. The blocking causes requests to pile up, which causes our socket backlog to fill up, and forces Nginx to start throwing 502 Bad Gateway errors. That’s it!]

-   [### The solution(s)]


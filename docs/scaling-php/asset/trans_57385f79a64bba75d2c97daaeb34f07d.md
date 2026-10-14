
-   [什么时候应该使用 Memcached 而不是 Redis？](https://wiki.example.org/memcached_vs_redis) 对于 `MOST` 的目的，我更倾向于使用 Redis。Redis 非常快速，拥有 Memcached 所没有的多种便捷数据类型（如 Sets 和 Lists），并且会将数据存储到磁盘。Redis 非常适合在重启后保持缓存数据持久化。例如，重启 Memcached 后，缓存为空（cache 是 cold）会导致站点变慢，MySQL 因缺乏缓存而受到大量压力。使用 Redis 可以完全避免这个问题，因为缓存会立即变热（尽管在重启后，Redis 可能需要 60 秒或更长时间将数据读取到内存中）。

对于大多数部署，我建议只使用 Redis。在基础设施中添加一个新的组件并不值得，因为 Redis 可以完成 Memcached 的所有功能（甚至更多）。然而，Memcached 具有以下两个关键优势：

1.  它是多线程的。Redis 是事件驱动的，在同一时刻只能处理一个连接。即使没有线程，Redis 也极其快速，但多线程的 Memcached 可以接受并处理更多连接，并充分利用所有可用的 CPU 核心（Redis 只能使用一个核心）。

2.  它使用更少的内存。Redis 为每个存储的项保存多个指针。Memcached 通过 slab 分配内存，完全避免 `malloc`，并能降低管理开销。虽然可以通过在 Redis 中使用 Hashes 来缓解此问题（提示：这很丑陋），但从项到项来看，Memcached 使用的内存更少。在小规模数据量下差异不明显，但在数百万甚至数亿个键的规模下，这可能会节省大量昂贵的内存。

### 安装 Memcached

在 Ubuntu 上安装 Memcached 非常简单，能让你获得一个非常新的版本。

```
1 $ apt-get install memcached
```

编辑配置文件 `/etc/memcached.conf` 并修改最大内存（`-m`）、最大连接数（`-c`）和最大线程数（`-t`）。我通常以 CPU 核心数量为初始线程数。同时，还需要提高打开文件的限制，并通过 sys.exit 等方式调整系统网络参数（如前面章节所述）。请记住，内存限制（`-m`）是硬性上限——当 memcached 达到此限制时，会开始驱逐旧数据。

配置文件调整后，应类似以下内容：

```
 1 	# 以守护进程方式运行 memcached。此命令是隐含的，不需要在本配置中指定。
 2 	# 守护进程运行。请参阅随包含的 README.Debian 获取更多信息。
 3 	-d
 4 	 
 5 	# 将 memcached 的输出记录到 /var/log/memcached
 8 	logfile /var/log/memcached.log
 9 	 
10 	# 设置更详细的日志级别
11 	# -v
12 	 
13 	# 设置更详细的日志级别（打印客户端命令）
14 	# -vv
15 	 
16 	# 默认使用 64 兆字节的内存。这是合理的，守护进程默认不会立即占用这么多内存
21 	-m 24000
22 	 
24 	# 默认连接端口是 11211
25 	-p 11211
26 	 
27 	# 默认以 root 运行。如果配置文件中未指定 -u 参数，启动脚本会默认以 root 运行
28 	-u memcached
29 	 
30 	# 指定监听的 IP 地址。默认监听所有地址。该参数是 memcached 仅有的安全措施，确保其仅在防火墙接口上监听。
33 	-l 10.0.1.10
34 	 
35 	# 限制同时接受的连接数。默认值为 1024
37 	-c 4096
38 	 
39 	# 锁定所有分页内存。在执行前请参阅 README 和官网文档
41 	# -k
42 	 
43 	# 当内存耗尽时返回错误（而不是删除数据）
44 	# -M
45 	 
46 	# 最大化核心文件限制
47 	# -r
```

| ![question](images/leanpub_question.png) || **当 Memcached 运行出错时会发生什么？** Memcached 使用 LRU（最近最少使用）算法跟踪键的请求次数。当 Memcached 耗尽空间且没有过期键可删除时，它会开始驱逐使用次数最少的键。你可以在 stats 中查看 `evictions` 关键字来监控 churn 率。通常，高 eviction 数量表明需要更多缓存空间。

| --- | --- |

### 将 PHP 与 Memcached 连接

如果查看 PHP 的 PECL 扩展，你会发现两种 Memcached 扩展可供选择。它们的区别很细微，但可能产生影响——有 [`memcache`](http://pecl.php.net/package/memcache) 扩展和 [`memcached`](http://pecl.php.net/package/memcached) 扩展（注意 **d**）。

*`memcache`* 扩展是较旧的版本，功能较少，并使用自研库来连接和交互 Memcached。虽然可以通过指定 `state=beta` 来安装新的 beta 版本，但最新的稳定版本已经多年未更新。**我建议避免使用此扩展**。

更新颖、更优的选择是 `memcached` PECL 扩展。它使用 `libmemcached` 与 Memcached 通信，因此拥有良好的支持和测试的连接机制。此外，`memcached` 扩展提供了旧版 `memcache` 扩展所不具备的众多新特性。

安装方法如下：

```
1 $ pecl install memcached
```

### 协议

客户端连接到 Memcached 服务器时有两种通信方式——ASCII 协议和二进制协议。默认使用 ASCII 协议，它便于调试（因为可以直接阅读通信内容），但在生产环境中并非必要，且会增加网络开销。建议改为二进制协议：

```
1 $m = new Memcached;
2 $m->setOption(Memcached::OPT_BINARY_PROTOCOL, true);
```

顺便提一下，ASCII 协议非常简单，我会在本章末尾展示如何通过 telnet 调试 Memcached。

下面是 ASCII 协议的示例：

```
1 $ telnet localhost 11211
2 > GET hello        # 获取名为 'hello' 的键
3 < VALUE world 0 5  # 服务器返回值 'world'
```

### 压缩与序列化

使用 Memcached 的常见场景是存储更复杂的值，如 PHP 数组或对象。通常，如果可能，最好完全避免这种做法。序列化对象会占用大量空间，且对象越大，消耗的内存越多。如果你发现自己经常需要存储复杂对象或数组，建议考虑 Redis，因为它提供更适合此类工作的更复杂数据类型。

尽管如此，如果你必须在 Memcached 中存储数组或对象，这很简单。只需将它们传递给 `set` 函数。Memcached 客户端的默认行为是使用 PHP 内置的 `serialize` 函数对对象进行序列化，从而可以利用 PHP 魔术方法 `__serialize()` 来自定义序列化逻辑，例如处理嵌套对象或仅返回子集值。

多年前，我遇到一位同事坚持通过 `explode` 将数组用逗号分隔后存储在 Memcached 中，并在获取时通过 `implode` 重新组合。不要做这种事。PHP 已经为你处理了序列化。如果你经常需要更高级的数据类型，那你需要 Redis。
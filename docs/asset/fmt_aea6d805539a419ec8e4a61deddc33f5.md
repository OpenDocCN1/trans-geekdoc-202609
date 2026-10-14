
在拥有专用从属服务器进行备份之前，我们会在生产从属服务器上执行备份，导致备份过程长达 24 小时以上，严重影响从属服务器的性能。此外，`mysqldump` 需要加写锁，这在生产环境中不可接受，导致备份不一致且无法实现真正的“点‑时间”恢复，整体情况堪忧。

备份耗时超过 24 小时已是不可接受的局面，因此我决定采用更 robust 的方案。

在新的备份系统中，我设定了以下“完美”目标：

1. 不影响生产系统的速度。  
2. 备份速度快，理想情况下在 1 小时内完成，以便一天内多次备份。  
3. 本地保留最近的备份，所有备份需同步至远程存储。  
4. 系统需简洁易用，复杂度越低越易验证备份流程是否正常。

### 专用备份服务器

第一步是部署专用备份服务器。硬件无需特别高端：大容量 RAID‑1 用于存储本地备份，快速磁盘用于运行 MySQL 实例。内存需求也不高，因为只读服务器不需要大的 InnoDB 缓冲池。

### Percona XtraBackup

我使用改装自 Owen Carter 脚本（[原始脚本链接](https://gist.github.com/931358)）并通过 Cron 定时执行，以实现数据库备份。该脚本能确保备份一致、支持点‑时间恢复，且不会阻塞或减慢复制进程。多个备份甚至可以同时进行。

强烈建议在脚本的 `USEROPTIONS` 变量中加入 `slave-info` 选项，这样备份时会包含 `Master_Log_Pos` 与 `Master_Log_File`，便于使用备份数据重新搭建从属服务器。

[更多 XtraBackup 配置选项请参考](http://www.percona.com/doc/percona-xtrabackup/innobackupex/innobackupex_option_reference.html)

### 数据保留与长期存储

我决定保留 7 天的本地备份，而将长期归档放在 Amazon S3 上，期限无限。7 天的本地备份足以用于快速搭建新从属服务器。

由于不想在本地存储数 terabytes 的 MySQL 备份，我们使用 Amazon S3 保留一部分数据库备份。借助 [boto](https://github.com/chapmanb/cloudbiolinux/blob/master/utils/s3_multipart_upload.py) 脚本，脚本内的备份 cron 可轻松实现多段上传。注意：当文件超过 5GB 时必须使用多段上传 API。

- 我们以压缩形式存储数据，在压缩 MySQL 备份时实现了超过 100% 的存储空间节省。你可以使用 `gzip` 获得最大的存储空间节省，但它非常慢。相反，对于大型备份，我建议使用 `lzop`（http://www.lzop.org/）。`lzop` 是一个文件压缩工具，运行速度显著更快，但压缩效率稍低。此外，`lzop` 支持并行压缩，从而进一步提升速度。

### 通知

最后，我想让备份系统非常显眼。由于我们使用 [Campfire](http://campfirenow.com/) 进行团队沟通，我能够通过 API 在备份脚本运行时每次都在 Campfire 中发送消息。每天早上醒来，看到“MySQL Backup Finished”在 Campfire 中发布，真是令人安心。

这很简单，只需在备份脚本中加入类似下面的内容：

```
1 SIZE=`ls -sh $THISBACKUP.tar.gz | cut -f 1 -d " "`
2 curl -i -u $KEY:X -H 'Content-Type: application/json' -d "{\"message\":{\"body\
3 :\"MySQL Backup Finished (size: $SIZE)\"}}" $CAMPFIRE_URL
```

# 案例研究：Async APIs w/ Kestrel 救了我的命

对于网站的扩展来说，后台任务是一个相当新的技术。3 到 4 年前，社交 API 并不常见，将网页请求的部分在后台执行几乎是未闻名的，只有最大的网站才涉及。

Twitpic 依赖 Twitter API 实现许多站点功能。当你上传新图片时，可以选择将其发布到 Twitter 或 Facebook。当你对照片评论时，我们也会将该评论推送到你的 Twitter 流中。

最初，代码是采用笨拙的方式编写的。为什么？我们根本不知道更好的做法。我们是草根、自筹的程序员，在远超想象的规模下工作。你可以想象我们的代码大致像这样：

```
 1 <?php
 2 class Image_Controller extends Controller {
 3 
 4   // 当有人上传新图片时...
 5   public function create() {
 6   	
 7     $image = new Image();
 8     $image->process_image_upload();
 9     $image->save();
10     
11     // 生成要发送到 Twitter 的推文文本...
 12     // 即，“Check out this cool pic. http://twitpic.com/abc123”
13     $tweet = $image->tweet();
14     
15 	 // 通过 API 向 Twitter 发送推文。
16     Twitter::post_tweet($image->user, $tweet);
17   
18   }
19 }
```

从程序角度来看，这很合理。但这是处理第三方 API 时的*错误*做法，无论规模大小都如此。即使你仍然很小，情况也很糟糕。因为即使是最佳情况，PHP 会阻塞等待 I/O，API 请求处理需要 1-2 秒，无可避免。每次用户上传图片时，我们都会额外花费 1 到 2 秒来向 Twitter 发送推文。

你可以说这不算大问题，因为用户正在上传文件，不会注意到几秒的延迟。但对于评论呢？我们想在用户评论时立即发布推文，而这种本应快速的操作因 API 交互而变慢。

而且，这并非针对 Twitter。**所有** HTTP API 都慢。当你通过网络跨国访问 API 时，这本就是常态，会产生延迟。

### 最坏的情况

别提用户体验了，这种做法还会带来严重问题。你的网站会**依赖**于其他服务。记得 Twitter 曾经每周都会崩溃吗？如果你像我们一样使用 Twitter API，Twitter 的宕机就会直接导致你的网站崩溃！.fail whale 无处不在。

我之前说每个棘手的 API 调用需要 1-2 秒，因为 PHP 会阻塞等待响应。那么，如果 API 请求耗时很长（5 秒以上）会发生什么？PHP 会一直等待响应，无法处理新的 HTTP 请求。当 Twitter 宕机时，这些“阻塞”的 PHP 进程会一直等待响应或超时。

在繁忙的网站上，这会**迅速**耗尽所有可用的 PHP 进程。例如，当每秒上传 100 多张图片并发送到 Twitter 时，若 Twitter 宕机，每秒就会有 100 多个 PHP 进程被阻塞，无法服务任何其他请求。

这会引发连锁反应，最终导致整个网站瘫痪，因为没有可用的（非阻塞）PHP 进程。

当 Twitter 严重宕机时，我们也彻底倒霉。情况很糟糕。

### 转向 Kestrel 的道路

fed up with 将我们的可用性依赖于其他公司的可用性，我决定绳之以系，开始研究解决方案。

我的第一个念头是使用数据库（*不要这样做*）。我建了一个表，将推文写入，并启动一个后台进程来发送它们。正如第 8 章讨论的，如果有多个后台工人，除非使用 MySQL 锁定，否则会出现竞争条件。MySQL 锁定虽可行，但它会在队列上产生全局锁，是一个不适合并行和并发的方案。**数据库不是队列**。

因此，我的首次尝试在后台中进行推文发送导致了重复推文和各种失败。我坦白说，我当时并不清楚自己在做什么。

我开始研究其他方案。找到了一些关于 [Starling](https://github.com/starling/starling)（Twitter 的第一个排队守护进程，用 Ruby 编写）的文章。不幸的是，Ruby（或 PHP）并不是构建高并发、高可用排队系统的最佳选择，这引发了大量负面评论。于是，我找到了它的开源后继——Kestrel。

Kestrel 用 Scala 编写，运行在 JVM 上，并使用 memcached 协议，因此无需额外客户端，只需将 Memcached 客户端指向它即可！当时 Resque 还未出现，Kestrel 是最佳（也最简洁）的解决方案。最终，我们迁移到了 Resque，但无论使用哪种队列服务，概念都是一样的。

于是，我设置了 Kestrel，并将 Twitter API 调用推入队列。不再在 web 请求期间执行这些调用，而是将它们移到后台“ eventualy” 处理。

### 赢

使用 Kestrel 是巨大的胜利，解决了早期的宕机问题。与其在 Twitter 宕机时直接崩溃，我们的网站现在运行 **快速**——我们只会看到 Kestrel 队列中积压大量任务。一旦 Twitter 恢复，所有任务都会被处理！不再有宕机，不再有数据丢失。

这已经是巨大的收获。但也提升了用户体验。记得我之前说，最佳情况下向 Twitter 发送推文需要 1 到 2 秒？这意味着发布新图片或评论需要额外 1-2 秒。有了后台工作者后，新评论**立即**通过，图片上传速度提升了 25%。

# 案例研究：Memcached 的缺失指南

Memcached 很酷。它是早期扩展领域的“坏男孩”之一，也是许多最大网站的核心基础。为什么？它简单、快速且便捷。Memcached 可以轻松安装在几乎所有平台，配置也很简单。

tempting 考虑市面上各种 Memcached 替代品。我看到一些“现代版本”使用相同协议但实现于 Golang 或 Scala。我建议避免在严肃环境中使用用垃圾回收语言实现的 Memcached 服务器——你不希望你的站点瓶颈因 Memcached 服务器的 **stop-the-world** 垃圾回收而出现。

原生的 C 语言 memcached 仍是绝佳选择——它简单、稳定且可靠。

### 为何选择 Memcached 而非 Redis？

- [什么时候应该使用 Memcached 而不是 Redis？](https://wiki.example.org/memcached_vs_redis) 对于 `MOST` 的目的，我更倾向于使用 Redis。Redis 非常快速，拥有 Memcached 所没有的多种便捷数据类型（如 Sets 和 Lists），并且会将数据存储到磁盘。Redis 非常适合在重启后保持缓存数据持久化。例如，重启 Memcached 后，缓存为空（cache 是 cold）会导致站点变慢，MySQL 因缺乏缓存而受到大量压力。使用 Redis 可以完全避免这个问题，因为缓存会立即变热（尽管在重启后，Redis 可能需要 60 秒或更长时间将数据读取到内存中）。

对于大多数部署，我建议只使用 Redis。在基础设施中添加一个新的组件并不值得，因为 Redis 可以完成 Memcached 的所有功能（甚至更多）。然而，Memcached 具有以下两个关键优势：

1. 它是多线程的。Redis 是事件驱动的，在同一时刻只能处理一个连接。即使没有线程，Redis 也极其快速，但多线程的 Memcached 可以接受并处理更多连接，并充分利用所有可用的 CPU 核心（Redis 只能使用一个核心）。
2. 它使用更少的内存。Redis 为每个存储的项保存多个指针。Memcached 通过 slab 分配内存，完全避免 `malloc`，并能降低管理开销。虽然可以通过在 Redis 中使用 Hashes 来缓解此问题（提示：这很丑陋），但从项到项来看，Memcached 使用的内存更少。在小规模数据量下差异不明显，但在数百万甚至数亿个键的规模下，这可能会节省大量昂贵的内存。

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

| ![question](img/leanpub_question.png) || **当 Memcached 运行出错时会发生什么？** Memcached 使用 LRU（最近最少使用）算法跟踪键的请求次数。当 Memcached 耗尽空间且没有过期键可删除时，它会开始驱逐使用次数最少的键。你可以在 stats 中查看 `evictions` 关键字来监控 churn 率。通常，高 eviction 数量表明需要更多缓存空间。 |

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

PHP 内置的序列化可能相当沉重。由于它是基于 ASCII 的序列化，因此占用的字节数并不理想。有一个名为 `igbinary` 的可选扩展可以让你使用一种更复杂但占用空间更小的二进制序列化方式。安装该模块后，它可以“无缝”地工作。如果你打算在 Memcached 中存储大量序列化数据，`igbinary` 是必备的。

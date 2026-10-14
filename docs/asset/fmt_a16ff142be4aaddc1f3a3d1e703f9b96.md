
你懂 `opcache.memory_consumption` 的含义，但到底该设多少？32 够不够？太少又如何？Google 搜不到答案，只能凭感觉。

如果直觉错了，你是否愿意把服务器可用性押在猜测上？

不，我不会。

我有个习惯，研究得像疯狂的科学家，结果花三小时去查一些奇怪的设置，然后翻到 PHP 源码。

与其让这些知识白白浪费，我决定与你共享。我从一款每日处理 117 百万 HTTP 请求的应用的 `php.ini` 中提取出最佳 **实战** 设置，并解释每个参数的作用和重要性，帮助你为自己的环境进行调优。

### OpCache 推荐设置

#### `opcache.revalidate_freq`
控制字节码缓存多久失效一次（以秒为单位）。0 表示每个请求都检查代码是否改动，这会产生大量的 `stat` 系统调用。在开发环境建议设为 0。生产环境可不必太在意，因为下一设置会起作用。

#### `opcache.validate_timestamps`
开启后，PHP 会在每次 `opcache.revalidate_freq` 间隔内检查文件的时间戳。

关闭后，`opcache.validate_timestamps` 被忽略，PHP 永远不会检查代码更新。如果你修改代码，改动直到重启或发送 `SIGUSR2` 信号让 PHP 重新加载才会生效。虽然这很烦人，但强烈建议使用它。因为在更新或部署代码时，新文件可能与旧文件混在一起，导致不可预测的结果，风险极高。

#### `opcache.max_accelerated_files`
限制一次性可以驻留在内存中的 PHP 文件最大数量。确保你的项目文件数量小于该值。我的代码库有 6000 个文件，我使用质数 7963 作为 `max_accelerated_files`。

你可以运行 `find . -type f -print | grep php | wc -l` 快速统计代码库中 PHP 文件的数量。

#### `opcache.memory_consumption`
默认 64 MB，我将其设为 192 MB，因为代码量很大。可以使用 `opcache_get_status()` 查看 OpCache 当前占用的内存，并在需要时调增（下周再详细说明）。

#### `opcache.interned_strings_buffer`
一个文档较少的好设置。PHP 采用字符串内部化技术：如有 1000 个 “foobar” 字符串，内部会创建一个不可变变量并为其余 999 次使用提供指针。这个设置把内部字符串池从每个 php‑fpm 进程独立提升为所有进程共享，从而节省内存并提升大型应用的性能。

取值单位是 MB，建议设为 “16” 表示 16 MB。默认仅 4 MB。

#### `opcache.fast_shutdown`
另一个文档不明的设置。“允许更快的关闭”。听起来不太有用。实际上，它提供了更快的调用代码在请求结束时的析构函数的机制，加速响应并让 PHP 工作进程更快就绪，以便处理下一个请求。将其设为 1 并开启。

### TL;DR‑在 `php.ini` 中的推荐配置

```
1 opcache.revalidate_freq=0
2 opcache.validate_timestamps=0   (在开发环境请注释掉)
3 opcache.max_accelerated_files=7963
4 opcache.memory_consumption=192
5 opcache.interned_strings_buffer=16
6 opcache.fast_shutdown=1
```

### APC（仅 PHP 5.4 及以下版本）

APC 是成熟的字节码缓存，未来可能会被整合进 PHP。它通常是首选。APC 以 PHP 扩展形式发布，使用 PECL 安装非常简便：

```
1 > pecl install apc
2 > service php5-fpm restart
```

真的很简单。在繁忙服务器上，你会立即看到 CPU 使用率急剧下降，甚至直线式掉下来。

有一个需要注意的地方（gotcha）关于 APC。如果你使用 git、svn、capistrano 或 rsync 部署代码，请确保在 `php.ini` 中设置配置值 `apc.stat_ctime=1`。否则，每次向应用服务器推送新代码时可能会出现错误或旧代码。 **为什么？** 因为在大多数部署设置中——尤其是使用 capistrano 时，当新代码部署时，只有文件元数据被更新。这导致只有 `ctime` 被更新，而 `mtime` 没有被更新。默认情况下，APC 只通过比较 `mtime` 来检测代码变化，因此即使你部署了新代码，APC 仍会查看 `mtime` 并认为它与缓存中的相同。通过使用 `apc.stat_ctime`，告诉 APC 也检查 `ctime`，从而完全解决这个问题。

### XCache

APC 的替代方案是 XCache，它在功能上基本上提供相同的功能，尽管它是由独立开发者编写的，并不随 PHP 一起捆绑。不过，它会频繁发布新版本——例如，在 APC 稳定版仍未支持 PHP 5.4 时，就已经发布了兼容 PHP 5.4 的稳定版。

我提到它的原因是因为我们在 Twitpic 使用它，具体原因在本章末尾的案例研究中解释。

```
1 > apt-get install php5-xcache
2 > service php5-fpm restart
```

### 替代方案

未来可能会看到更多使用长期运行的 PHP 应用服务器的趋势，即 PHP 应用只启动一次并进入循环等待新的 HTTP 请求（这类似于 Ruby 的 `unicorn` 或 Python 的 `gunicorn`）。这种方式不需要 opcode 缓存，因为 PHP 进程不会为每个请求重启，所以代码只需解释一次。

我还没有尝试过 [Photon](http://www.photon-project.com/)，但它是一个非常有前景的 PHP 应用服务器示例，看起来很有意思。

### 调优 Linux 为 PHP

默认情况下，Linux 可以在不进行太多调优的情况下处理大量 PHP 请求。不过，我们可以进行一些微调，以改善 nginx 与 PHP-FPM 之间的通信，以及在 PHP 需要访问磁盘时提升 I/O 性能。

我也会讨论一些反模式（anti-patterns），即看似能提升性能的做法，但实际上会产生负面影响或收益微乎其微。

#### 最大打开文件数

类似于我们的负载均衡器，每个进程允许的最大打开文件数设置得非常低（1024）。由于 nginx 通过 Unix socket 与 PHP-FPM 通信，而 Unix socket 在 Linux 系统中被视为文件，这实际上限制了 nginx 可以同时与 PHP-FPM 通信的连接数量。

```
1 > vi /etc/security/limits.conf
2     * soft  nofile  100000
3     * hard  nofile  100000
4 > ulimit -n 100000
```

#### 关闭文件访问时间

默认情况下，大多数 Linux 发行版会跟踪文件何时被访问或读取。这在大多数情况下并不有用，并且在每次读取文件（例如 PHP 解释器读取源代码）时都会产生一次 I/O 操作。我们可以通过修改存放 PHP 文件的分区来禁用此行为。打开 `/etc/fstab` 并查找你的主分区。我的示例如下：

```
1 /dev/sdb1   /   ext4    errors=remount-ro 0 1
```

将其修改为：

```
1 /dev/sdb1   /   ext4    noatime,nodiratime,errors=remount-ro 0 1
```

`noatime` 告诉文件系统在读取文件时不跟踪文件的访问时间，`nodiratime` 则告诉文件系统在读取目录时不跟踪目录的访问时间。

你可以在不重启的情况下重新挂载文件系统（无需重启！）使用命令 `mount -o remount /dev/sdb1`（将 `/dev/sdb1` 替换为你在 `/etc/fstab` 中需要修改的分区）。

#### 使用 `tmpfs` 存储临时文件

如果你的应用程序处理大量用户上传，可以通过使用 `tmpfs`（内存文件系统）为 `/tmp` 目录来减少 I/O 开销。`/tmp` 是 PHP 和 nginx 用于缓冲上传文件的目录，直到它们被应用程序处理。

使用内存文件系统存储临时文件是个好主意，因为它允许文件上传在内存中缓冲，而无需写入磁盘。这对于处理小图片上传（如头像或照片）非常合适，但对于用户上传非常大的文件（如视频）则不适用。

在 `/etc/fstab` 文件中添加以下行：

```
1 tmpfs /tmp tmpfs defaults,nosuid,noatime 0 0
```

然后使用 `mount /tmp` 挂载新文件系统。如果运行 `df -h`，你会在输出中看到新的 `tmpfs` 文件系统：

```
1 tmpfs   2.0G  4.0K  2.0G   1% /tmp
```

#### 调优 php.ini 以提高性能

默认的 `php.ini` 文件非常大，包含了几乎所有已知的 PHP 配置选项。直接删除它！你不需要所有这些默认设置。

```
 1 > vi /etc/php5/fpm/php.ini
 2     [PHP]
 3     engine = On
 4     expose_php = Off
 5 
 6     max_execution_time = 5
 7     memory_limit = -1
 8     error_reporting = E_ALL & ~E_DEPRECATED
 9     display_errors = Off
10     display_startup_errors = Off
11     html_errors = Off
12     default_socket_timeout = 5
13 
14     file_uploads = On
15     upload_tmp_dir = /tmp/php
16     upload_max_filesize = 50M
17     post_max_size = 50M
18     max_file_uploads = 20
19 
20     date.timezone = 'UTC'
21 
22     cgi.fix_pathinfo = 0
```

我们将 `max_execution_time` 设置为合理的 5 秒，因为对于快速的 Web 应用来说，长时间运行的请求通常意味着出错。我们的目标是让页面响应时间在 300-500ms 以内！

#### 反模式：在 Ramdisk 上存储代码

逻辑推理：如果我的代码存储在磁盘上，而 PHP 解释器为每个请求从磁盘读取源代码，我可以通过将代码存储在 Ramdisk（即直接映射到文件系统的内存区域）来加速过程。这听起来很合理，而且我在 StackOverflow 上看到过不少这类提问。

之所以它是反模式，原因很简单。**Linux 已经为你完成了这件事！** Linux 内核会在第一次从文件系统读取文件后，自动使用几乎所有空闲内存来缓存文件。这是完全透明的，并且在内存压力大时，内核会自动释放缓存，而使用 Ramdisk 则无法做到这一点。

更甚的是，它不会带来额外的复杂性，并且在内存压力下，内核会释放缓存，而使用 Ramdisk 则不会。

#### 反模式：关闭访问日志和错误日志

nginx 的访问日志和错误日志非常有价值。它们不仅有助于调试生产环境中的问题，还用于聚合流量统计、追踪滥用者（如 DDoS）以及确保一切正常运行。

尽管如此，在繁忙服务器上，禁用这些日志以“提升性能”是很诱人的。写入磁盘每个请求似乎不合理，对吧？错！实时日志的好处远大于可能节省的微小性能收益。

1.  即使是旋转非 SSD 的硬盘，也能很好地处理顺序写入，速度可达 100MB/s 以上。
2.  在最繁忙的服务器（每秒 20,000+ 连接）上，nginx 仅产生 1-2MB 的日志数据/秒，这占 I/O 利用率的不到 1%。
3.  Nginx 是事件驱动的，因此不会因为写日志而阻塞。此外，nginx 会缓冲日志写入以提高效率。

-   [在负载均衡章节中，我们完全禁用了日志文件，因为信号噪声比远远过高。但，在应用服务器上，每个服务器只处理一部分流量，日志在实时中变得更加有价值和有用。]

### 缩放会话处理

会话是每个 Web 应用的重要组成部分——它们允许你在请求之间保持状态并记住用户。PHP 的默认会话配置是将会话数据存储在应用服务器的文件系统中。每个用户会话都会被分配一个唯一的令牌，该令牌存储在浏览器的 Cookie 中，随后该令牌用作在文件系统中存储会话数据的文件名。

#### 基于文件系统的会话无法缩放，原因有两个。

第一个原因是它会产生不必要的 I/O 开销。对于每个请求，PHP 需要访问文件系统来读取会话数据，并在 web 请求结束时重新写入文件，以保存在此期间新增或修改的会话数据。

第二个原因是它将你锁定在单个服务器上。由于会话数据文件是单独存储在单个应用服务器上的，会话数据对集群中的其他服务器不可见。例如，如果用户在 `app01` 上登录，刷新页面后 HAProxy 将其路由到 `app02`，由于 `app02` 上不存在有效的会话数据文件，用户将被带回登录页面。

绕过这些限制的方法包括使用网络文件系统或在负载均衡器上启用“粘性会话”，但这些都是不太理想的选择——它们更像是一种临时 workaround 而非长期解决方案。网络文件系统非常慢，而“粘性会话”会在应用集群中产生热点和冷点。

另一个经常在论坛和 StackOverflow 等站点上被推荐的糟糕建议是将会话数据存储在关系数据库中，例如 MySQL。数据库-backed 会话可以稍微扩展规模，但会为本不应存储在数据库中的数据（因为每个 web 请求都需要从数据库读取和写入）创建巨大的 I/O 压力。**会话是临时的、有限时的数据片段——不是关系数据。**

幸运的是，PHP 提供了插件式的会话接口，可以通过 `session.save_handler` 的 ini 设置进行配置。该接口允许 PHP 扩展提供插件，这些插件的行为和功能类似于原生 PHP 会话，从而让我们能够以可扩展的方式使用 `$_SESSION` 变量。

下面将介绍三种可插拔的后端，并随后逐一说明。

#### Memcached

绕过文件系统限制最简便的方法是部署一个或多个 memcache 服务器，并使用 [`memcached`](http://pecl.php.net/package/memcached) 扩展提供的会话处理器。

**重要提示**：我说的是 [`memcached`](http://pecl.php.net/package/memcached) 扩展，而不是 `memcache`。这两个扩展是不同的，`memcached` 扩展在诸多方面都更优越，主要是因为它基于 `libmemcached`，后续章节将详细说明。

最近，有人批评在 memcache 中存储会话数据，因为它是基于内存的、非文件系统的存储方式。如果 memcache 崩溃或重启，你将失去所有会话数据，导致所有用户被迫退出，并删除会话中存储的任何内容。这对存储重要数据（如购物车信息等）而言是一个巨大的缺点。

这里的权衡在于速度。memcache 极其快速且易于设置——我们在 Twitpic 使用它来存储会话，单台服务器即可为成千上万的并发用户提供会话后端。由于它是中央资源，所有应用服务器都能访问相同的会话数据，从而能够水平扩展，不再受文件系统限制！

在使用 memcache 存储会话之前，我们首先需要安装 [PECL Memcached](http://pecl.php.net/package/memcached) 扩展。幸运的是，这很容易：

```
1 > apt-get install php5-memcached
```

会话保存处理器可以在 `php.ini` 中注册，但更建议在应用代码中设置。如果在 `php.ini` 中设置，它将全局影响所有运行的 PHP 代码，包括其他应用，这可能导致不期望的行为。

```
1 ini_set('session.save_handler', 'memcached');
2 ini_set('session.save_path', '192.0.2.25:11211,192.0.2.26:11211');
3 
4 # 会话令牌会像常规一样存储在用户的浏览器 Cookie 中，
5 # 但会话数据不会存储在文件系统上，而是会自动保存在 memcache 中。
6 session_start();
7 $_SESSION['foo'] = 'bar';
```

#### Redis

如果你的会话数据很重要，且因服务器崩溃而丢失所有数据是不可接受的，你应该考虑使用 Redis 作为会话数据的后端。Redis 是一种数据结构服务器（第 7 章有详细说明），它与 memcache 类似，因为工作数据保存在内存中，但可以通过 `save` 和 `appendfsync` 配置选项将数据持久化到磁盘。

你需要 [`phpredis`](https://github.com/nicolasff/phpredis) 扩展。

```
1 ini_set('session.save_handler', 'redis');
2 ini_set('session.save_path',
3     'tcp://192.0.2.5:6379?timeout=0.5,tcp://192.0.2.6:6379?timeout=0.5');
4 
5 # 会话令牌会像常规一样存储在用户的浏览器 Cookie 中，
6 # 但会话数据会自动存储在 Redis 中，而非文件系统。
7 session_start();
8 $_SESSION['foo'] = 'bar';
```

#### Cookies

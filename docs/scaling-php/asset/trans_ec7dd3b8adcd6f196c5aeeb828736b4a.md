
如果你对Capistrano为你的开发流程带来的易用性还不满意，考虑以下内容。

Capistrano 部署是原子化的。这意味着在部署代码的同时，它不会影响任何正在运行的代码。

想一想：如果你手动部署网站，通过 FTP 上传文件或手动运行 `git pull` 时，在将新代码传输到远程服务器的过程中，旧文件和新文件会混在一起。比如，你同时修改了 `foo.php` 和 `bar.php`，由于文件是依次传输的，在一段时间内，旧的 `foo.php` 和新的 `bar.php` 会同时在服务器上运行。

这会导致各种糟糕的情况——崩溃、异常和数据丢失，因为你同时运行的是旧代码和新代码的混合体，结果会如何无法预知。文件越多，情况越糟糕。

Capistrano 的工作方式不同。

1. PHP-FPM 被配置从一个符号链接（例如 `/u/apps/my_app/current`）读取代码。

2. 使用 Capistrano 部署新代码时，它会在 `/u/apps/my_app/releases`（即 `/u/apps/my_appl/releases/749847589`）创建一个新目录并下载你的代码。

3. 当所有代码传输完成后，它会将 `/u/apps/my_app/current` 的符号链接移动到新创建的目录 `/u/apps/my_appl/releases/749847589`。

4. 跳起来跳下去！Capistrano 原子化部署了你的代码。所有东西在同一时刻变化，所有新代码一起工作。

这种方式还能让回滚糟糕的部署变得容易。假设你部署了一段包含隐藏缺陷的代码，导致网站崩溃（这在现实中从未发生……对吧！？）。如果你使用传统的手动部署方式，你需要找回旧文件并将其转移回来，这会增加停机时间。

相反，由于 Capistrano 为每个部署创建独立目录，它可以通过将 `/u/apps/my_app/current` 重新指向旧发布版本来快速回滚，只需一条命令！

```
1 > cap deploy:rollback
```

轻松极了。我可以写一本关于 Capistrano 的专著，但这仅仅触及表面——但要做！它是一个非常棒的工具，也是“最佳实践”。查看更多文档，请参阅 [Capistrano wiki](https://github.com/capistrano/capistrano/wiki)。

### 使用 strace 进行 PHP 实时调试

我要坦白：`strace` 是我调试时最爱的工具，它救过我无数次，如果你学会使用它，它也会救你。

`strace` 是一个 Unix 工具，可以附加到正在运行的进程并监控该进程发出的系统调用，从而让你了解程序如何与操作系统交互。`strace` 可以用于多种用途，但在生产环境中调试奇怪问题时，它是救命稻草。

假设你有一段 PHP 代码使用了 Memcached，而 Memcached 服务器宕机。理想情况下，你应该有监控或日志系统能提醒你这个问题，但如果没有，你将一无所知——你的网站会崩溃，很可能因超时而失败，尤其是如果没有为 Memcached 设置合适的超时时间。

该怎么办？你可以手动检查每个 Memcached 服务器，但这在有多个 Memcached 服务器时会非常不方便——你需要登录每个服务器，判断哪个出问题并导致超时。

首先，我们需要找到一个正在运行的 `php-fpm` 进程来附加到它。

```
1 > ps ax | grep php-fpm
2 
3 11662 ?    S      0:03 php-fpm: pool www
4 11663 ?    Sl     0:06 php-fpm: pool www
5 11698 ?    S      0:04 php-fpm: pool www
6 11721 ?    S      0:04 php-fpm: pool www
7 11745 ?    Sl     0:11 php-fpm: pool www
```

我们有多个 `php-fpm` 进程在运行，让我们跟踪 `11662`。

```
 1 > strace -r -p 11662
 2 
 3  0.000000 restart_syscall(<... resuming interrupted call ...>) = 0
 4  4.720248 socket(PF_INET6, SOCK_DGRAM, IPPROTO_IP) = 3
 5  0.000110 close(3)                  = 0
 6  0.000145 gettimeofday({1361146314, 442683}, NULL) = 0
 7  0.000115 socket(PF_INET, SOCK_STREAM, IPPROTO_IP) = 3
 8  0.000086 fcntl(3, F_GETFL)         = 0x2 (flags O_RDWR)
 9  0.000097 fcntl(3, F_SETFL, O_RDWR|O_NONBLOCK) = 0
10  30000.000079 connect(3, {sa_family=AF_INET, sin_port=htons(11211), sin_addr=i\
11 net_addr("192.150.0.10")}, 16) = -1 EINPROGRESS (Operation now in progress)
```

很快，我们就能在最后一行看到，它正在尝试连接到 `192.150.0.10` 的 11211 端口，这正是我们 10 个 Memcached 服务器中的一个。现在我们可以立即进入该服务器进行修复，因为我们已经锁定了罪魁祸首。

另一个使用 `strace` 进行实时调试的场景是当你使用第三方 API 时，它导致你的代码变慢——你可以用 `strace` 查看连接耗时。这可能是我最常用的“oh-shit-the-site-is-down”应对方法。

在 CakePHP 缓存文件案例研究中，我展示了 `strace` 如何帮助我精准定位代码中的错误。

#### 真实 strace 场景

上周，我正在沙发上刷 NetFlix 的新剧集。

*Ding* … *Ding*

短信？这么晚？不可能是好事。

 reluctantly，我暂停 NetFlix 几秒钟（“How it’s made” 太上瘾了）去查看信息……

“PagerDuty：你的 API 宕机！”

 fuck！这条消息让我一惊。我正试图学怎么做剪指甲，该死。赶紧回到电脑。

我坐下，尝试打开 api.myjob.com，什么都没响应，Chrome 只显示那个循环的小蓝色圆圈，永远转不完。

我的网站DOWN了，而且非常严重。请求超时。

你会用什么策略？好的答案可能包括：

* 检查自动化警报，比如 Nagios 发送的警报

* 查看你的警报/可视化系统，如 Copperegg 或 Graphite

* 验证“常见罪魁祸首”，如 Memcache 或 MySQL 是否健康

但我没做这些。猜猜我做了什么？

我登录到 PHP 服务器，抓取一个 PHP-FPM 工作进程的 PID，然后运行 `strace -p`。

如果你平时不常用 `strace`，你正在对自己做极大的不服务。它是快速脏捷 debugging 的完美工具。当然，理想情况下，你会收到精确的警报，明确指出哪个服务宕机了，但我是现实主义者，我知道这并非总是如此。

当你的网站宕机时，希望拥有更好的警报系统不是答案。你需要立刻让 API 重新上线。其他一切都可以排在后面。

所以，我通过 SSH 登录到我的 web 服务器，运行 `ps` 抓取一个随机的 PHP-FPM 进程 ID，比如：

```
1 	$ ps aux | grep php-fpm
2 	myapp 128131 2.9 0.0 324132 57396 ? R 10:54 11:50 php-fpm: pool www
```

看 128131？这是我可以通过 `strace` 窥探的进程 ID。

接下来，我附加 `strace` 到该进程，看看发生了什么……

```
1 	$ sudo strace -p 128131
2 	gettimeofday({1399247077, 563898}, NULL) = 0
3 	sendto(17, "\372\0\0\0\3SELECT * FROM users WHERE id ="..., 254, MSG_DONTWAIT\
4 , NULL, 0) = 254`
```

我看到最后一行显示它等待了几秒，正在通过 `sendto` 发送 SQL 查询到数据库服务器，并在等待响应。看来我的数据库服务器又出问题了！于是，我立刻知道如何快速诊断并解决问题，修复数据库服务器，然后回到看“How It’s Made”。

**一位好朋友是规模化专家……**

他是那种既能写代码，又能长时间讨论深度 Linux 内部机制的人。我问他— *“如果你只能教大家其中一件关于扩展的事，你会教什么？”* 


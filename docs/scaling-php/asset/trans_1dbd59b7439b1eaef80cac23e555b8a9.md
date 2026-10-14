
![Scaling PHP](images/title_page.png)

## Scaling PHP

#### Steve Corona

这本书在 [`http://leanpub.com/scalingphp`](`http://leanpub.com/scalingphp`) 售卖。

这版本出版于 2014-05-23

![publisher's logo](images/leanpub-logo.png)

\*   \*   \*   \*   \*

这是一本 [`Leanpub`](`http://leanpub.com`) 的书籍。Leanpub 赋能作者和出版商使用 Lean Publishing 流程。[`Lean Publishing`](`http://leanpub.com/manifesto`) 是使用轻量工具和多次迭代在进度中发布电子书，收集读者反馈，迭代直到获得正确的书籍，并在达到目标后建立影响力。

\*   \*   \*   \*   \*

© 2012 - 2014 Steve Corona 

## 目录

*   [`前言](#chap00.xhtml#leanpub-auto-preface)` 

    *   [`本书缘起](#chap00.xhtml#leanpub-auto-how-this-book-came-to-be`)

    *   [`本书设计理念](#chap00.xhtml#leanpub-auto-how-this-book-is-designed`)

    *   [`适合阅读此书的人群](#chap00.xhtml#leanpub-auto-who-should-read-this-book`)

    *   [`本书所需条件](#chap00.xhtml#leanpub-auto-what-you-need-for-this-book`)

    *   [`你将学到什么](#chap00.xhtml#leanpub-auto-what-youll-learn`)

    *   [`为何需要本书](#chap00.xhtml#leanpub-auto-why-you-need-this-book`)

    *   [`规则第一条](#chap00.xhtml#leanpub-auto-rule-numero-uno`)

*   [`放弃 LAMP 栈](#chap01.xhtml#leanpub-auto-ditching-the-lamp-stack)` 

    *   [`LAMP 有什么问题？](#chap01.xhtml#leanpub-auto-whats-wrong-with-lamp`)

    *   [`可扩展栈](#chap01.xhtml#leanpub-auto-the-scalable-stack`)

*   [`DNS：为何需要关注](#chap02.xhtml#leanpub-auto-dns-why-you-need-to-care)` 

    *   [`DNS 负载分布](#chap02.xhtml#leanpub-auto-dns-load-distribution`)

    *   [`DNS 解析](#chap02.xhtml#leanpub-auto-dns-resolution`)

*   [`使用 HAProxy 进行负载均衡](#chap03.xhtml#leanpub-auto-load-balancing-with-haproxy)` 

    *   [`HAProxy](#chap03.xhtml#leanpub-auto-haproxy-1`)

    *   [`选择最佳硬件](#chap03.xhtml#leanpub-auto-choosing-the-best-hardware`)

    *   [`使用 keepalived 实现自动故障转移](#chap03.xhtml#leanpub-auto-automatic-failover-with-keepalived)

    *   [`调优 Linux 以应对网络重负载](#chap03.xhtml#leanpub-auto-tuning-linux-for-a-network-heavy-load`)

    *   [`在规模下的问题](#chap03.xhtml#leanpub-auto-issues-at-scale`)

*   [`应用服务器：使用 Nginx 和 PHP-FPM 实现水平扩展](#chap04.xhtml#leanpub-auto-app-server-horizontal-scaling-with-nginx-and-php-fpm)` 

    *   [`选择合适的 PHP 版本](#chap04.xhtml#leanpub-auto-choosing-the-right-version-of-php`)

    *   [`Nginx 与 PHP-FPM](#chap04.xhtml#leanpub-auto-nginx-and-php-fpm`)

    *   [`为应用服务器选择最佳硬件](#chap04.xhtml#leanpub-auto-choosing-the-best-hardware-for-your-application-server`)

    *   [`使用 PHP 字节码缓存](#chap04.xhtml#leanpub-auto-using-a-php-opcode-cache`)

    *   [`调优 Linux 以适应 PHP](#chap04.xhtml#leanpub-auto-tuning-linux-for-php`)

    *   [`扩展会话处理](#chap04.xhtml#leanpub-auto-scaling-session-handling`)

*   [`数据库服务器：终极 MySQL 调优指南](#chap05.xhtml#leanpub-auto-database-server-ultimate-mysql-tuning-guide)` 

    *   [`从 MySQL 获取 NoSQL 性能](#chap05.xhtml#leanpub-auto-getting-nosql-performance-out-of-mysql`)

    *   [`处理 libmysql 无法设置超时的问题](#chap05.xhtml#leanpub-auto-dealing-with-libmysqls-inability-to-set-timeouts`)

    *   [`调优 MySQL 配置](#chap05.xhtml#leanpub-auto-tuning-your-mysql-configuration`)

    *   [`调优 Linux 以适应高强度数据库](#chap05.xhtml#leanpub-auto-tuning-linux-for-an-intensive-database`)

    *   [`MySQL 从属服务器负载均衡](#chap05.xhtml#leanpub-auto-load-balancing-mysql-slaves`)

    *   [`接受主服务器为单点故障 (SPOF)](#chap05.xhtml#leanpub-auto-accepting-the-master-as-a-spof`)

    *   [`理解 NUMA 问题](#chap05.xhtml#leanpub-auto-understanding-issues-with-numa`)

    *   [`选择最佳硬件](#chap05.xhtml#leanpub-auto-choosing-the-best-hardware-1`)

    *   [`在线 schema 变更](#chap05.xhtml#leanpub-auto-online-schema-changes`)

    *   [`进一步主题](#chap05.xhtml#leanpub-auto-further-topics`)

*   [`缓存服务器：使用 Redis](#chap06.xhtml#leanpub-auto-cache-server-using-redis)` 

    *   [`Redis、Memcached 与 APC 的选择](#chap06.xhtml#leanpub-auto-choosing-between-redis-memcached-and-apc`)

    *   [`Redis 命令](#chap06.xhtml#leanpub-auto-redis-commands`)

    *   [`原子操作的重要性](#chap06.xhtml#leanpub-auto-the-importance-of-atomic-operations`)

    *   [`Redis 性能限制](#chap06.xhtml#leanpub-auto-performance-limitations-of-redis`)

    *   [`从 Dotdeb 安装 Redis](#chap06.xhtml#leanpub-auto-installing-redis-from-dotdeb`)

    *   [`安装 phpredis C 扩展](#chap06.xhtml#leanpub-auto-installing-the-phpredis-c-extension`)

    *   [`调优 Redis 以提升性能](#chap06.xhtml#leanpub-auto-tuning-redis-for-performance`)

    *   [`将 Redis 扩展到多台服务器](#chap06.xhtml#leanpub-auto-scaling-redis-to-multiple-servers`)

    *   [`“狗堆”（Dogpile）](#chap06.xhtml#leanpub-auto-the-dogpile`)

    *   [`俄罗斯套娃缓存（Russian Doll Caching）](#chap06.xhtml#leanpub-auto-russian-doll-caching`)

    *   [`Redis 比特图（Redis Bitmaps）](#chap06.xhtml#leanpub-auto-redis-bitmaps`)

    *   [`Redis 通知流（Redis Notification Feeds）](#chap06.xhtml#leanpub-auto-redis-notification-feeds`)

*   [`工作服务器：使用 Resque 进行异步处理](#chap07.xhtml#leanpub-auto-worker-server-asynchronous-resque-workers)` 

    *   [`为何使用队列？](#chap07.xhtml#leanpub-auto-why-use-queues`)

    *   [`开始使用 Resque 和 php-resque](#chap07.xhtml#leanpub-auto-getting-started-with-resque-and-php-resque`)

    *   [`编写 Resque 作业（Job）](#chap07.xhtml#leanpub-auto-writing-a-resque-job`)

    *   [`Resque 的替代方案](#chap07.xhtml#leanpub-auto-alternatives-to-resque`)

    *   [`应将放入队列的事项](#chap07.xhtml#leanpub-auto-things-you-should-put-in-a-queue`)

*   [`在规模下编写和调试代码](#chap08.xhtml#leanpub-auto-coding-and-debugging-at-scale)` 

    *   [`扩展你的代码](#chap08.xhtml#leanpub-auto-scaling-your-code`)

    *   [`使用 Capistrano 进行代码部署](#chap08.xhtml#leanpub-auto-capistrano-for-code-deployment`)

    *   [`使用 strace 实时调试 PHP](#chap08.xhtml#leanpub-auto-live-debugging-php-with-strace`)

*   [`告别建议](#chap09.xhtml#leanpub-auto-parting-advice)` 

    *   [`想升级？](#chap09.xhtml#leanpub_auto-want-to-upgrade`)

    *   [`发送反馈和推荐语](#chap09.xhtml#leanpub_auto-sending-feedback-and-testimonials`)

    *   [`陷入深渊需要立即帮助？](#chap09.xhtml#leanpub_auto-in-too-deep-need-help-asap`)

    *   [`更新？](#chap09.xhtml#leanpub_auto-updates`)

    *   [`关于作者](#chap09.xhtml#leanpub_auto-about-the-author`)

*   [`案例研究：水平扩展用户上传`](chap10.xhtml#leanpub-auto-case-study-horizontally-scaling-user-uploads)

*   [`案例研究：DNS 导致 Twitpic 宕机 4 小时`](chap11.xhtml#leanpub-auto-case-study-how-dns-took-down-twitpic-down-for-4-hours)

*   [`案例研究：垂直扩展 MySQL（10 到 3 台 MySQL 服务器 w/ SSDs）`](chap12.xhtml#leanpub-auto-case-study-scaling-mysql-vertically-10-to-3-mysql-servers-w-ssds)

*   [`案例研究：使用 Percona 进行热 MySQL 备份`](chap13.xhtml#leanpub-auto-case-study-hot-mysql-backups-w-percona) 

    *   [`从 mysqldump 迁移到 Percona XtraBackup`](chap13.xhtml#leanpub-auto-moving-from-mysqldump-to-percona-xtrabackup)

*   [`案例研究：使用 Kestrel 的异步 API 为我挽救了情况`](chap14.xhtml#leanpub-auto-case-study-async-apis-w-kestrel-saved-my-butt)

*   [`案例研究：Memcached 的缺失指南`](chap15.xhtml#leanpub-auto-case-study-the-missing-guide-to-memcached) 

    *   [`为何选择 Memcached 而非 Redis？`](chap15.xhtml#leanpub_auto-choosing-memcached-over-redis)


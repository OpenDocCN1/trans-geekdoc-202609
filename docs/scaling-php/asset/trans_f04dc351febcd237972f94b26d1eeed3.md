
`pm.max_requests` 是单个子进程在被杀死并重新生成之前可以服务的请求数量。它用于防止内存泄漏，因为 PHP 的垃圾回收器并不设计用于长时间运行。PHP 5.3 为内存管理带来了一些改进，因此可以将其设置得相当高。我建议将其至少设为 1000，具体取决于你的代码以及是否使用 PHP 扩展，因为不同扩展的泄漏情况各不相同。

### 选择适合你应用服务器的硬件

**快速 CPU，大量内存**

预计每个 PHP‑FPM 进程会使用多达 20 MB 的内存，假设 `pm.maxchildren` 设为 100，你至少需要 2 GB 的内存来支撑服务器。

相反，Nginx 记忆消耗极低——即使是负载重的应用服务器，Nginx 的总内存占用也仅 60‑80 MB。

你需要最快的 CPU 以及尽可能多的核心。虽然 PHP 是单线程的，只要 PHP‑FPM 进程的数量多于 CPU 核心数，就能充分利用每个核心。

截至撰写时，Intel Xeon SandyBridge 26xx 系列是性价比最高的选择。它们支持双 CPU 配置，每个 CPU 最多 8 核，启用 Hyper‑Threading 后可提供 32 个可用核心供应用服务器使用。

### 使用 PHP 字节码缓存

PHP 是解释型语言。每次运行 PHP 应用时，解释器需要读取源码、将其转换为内部字节码程序，然后执行这些字节码。可以把字节码程序看作解释器能更好理解的中间语言——实际上是一个虚拟机。

将 PHP 源码翻译成字节码需要非平凡的开销，通过缓存这种 PHP → 字节码的转换结果并重复使用，可以大幅节省开销。那么我们该如何实现呢？使用字节码缓存扩展。如果你目前还没有使用，只需安装一个即可实现 200‑300 % 的 CPU 使用率下降。这真是易如反掌！

自 PHP 5.5 起，Zend OpCache 已随 PHP  bundled。要启用它，只需在 `php.ini` 中加入 `opcache.enable=1`。超级简单。唯一的缺点是，APC 的用户空间 memcache 组件不再包含在 Zend OpCache 中。如果你依赖这个共享缓存，可以安装类似 [APCu](http://pecl.php.net/package/APCu) 的扩展，它在 PHP 5.5 中恢复了 APC 的用户空间缓存功能。我在《CakePHP 缓存文件案例研究》中详细描述了从 APC 迁移到 Zend OpCache 所遇到的心酸史。

如果你使用的是 PHP 5.4 或更低版本，还有其他字节码缓存方案可供选择，下面会逐一说明。

有没有使用字节码缓存的缺点？在大多数配置中，答案是 **没有**。唯一的 *注意点* 是：如果你使用了 PHP 编码/混淆器（如 [ionCube](http://www.ioncube.com/) 或 [Zend Guard](http://www.zend.com/en/products/guard/）），则无法使用字节码缓存。这只会影响少数运行闭源、授权 PHP 代码的用户。

#### 调优 Zend OpCache（仅 PHP 5.5）

常见痛点：“我想使用 Zend Optimizer，但完全不知道怎么设置。”

你有没有发现，花几小时阅读文档却仍然对设置一无所知？

你懂 `opcache.memory_consumption` 的含义，但到底该设多少？32 够不够？太少又如何？Google 搜不到答案，只能凭感觉。

如果直觉错了，你是否愿意把服务器可用性押在猜测上？

不，我不会。

我有个习惯，研究得像疯狂的科学家，结果花三小时去查一些奇怪的设置，然后翻到 PHP 源码。

与其让这些知识白白浪费，我决定与你共享。我从一款每日处理 117 百万 HTTP 请求的应用的 `php.ini` 中提取出最佳 **实战** 设置，并解释每个参数的作用和重要性，帮助你为自己的环境进行调优。

**opcache.revalidate_freq** – 控制字节码缓存多久失效一次（以秒为单位）。0 表示每个请求都检查代码是否改动，这会产生大量的 `stat` 系统调用。在开发环境建议设为 0。生产环境可不必太在意，因为下一设置会起作用。

**opcache.validate_timestamps** – 开启后，PHP 会在每次 `opcache.revalidate_freq` 间隔内检查文件的时间戳。

关闭后，`opcache.validate_timestamps` 被忽略，PHP 永远不会检查代码更新。如果你修改代码，改动直到重启或发送 `SIGUSR2` 信号让 PHP 重新加载才会生效。虽然这很烦人，但强烈建议使用它。因为在更新或部署代码时，新文件可能与旧文件混在一起，导致不可预测的结果，风险极高。

**opcache.max_accelerated_files** – 限制一次性可以驻留在内存中的 PHP 文件最大数量。确保你的项目文件数量小于该值。我的代码库有 6000 个文件，我使用质数 7963 作为 `max_accelerated_files`。

你可以运行 `find . -type f -print | grep php | wc -l` 快速统计代码库中 PHP 文件的数量。

**opcache.memory_consumption** – 默认 64 MB，我将其设为 192 MB，因为代码量很大。可以使用 `opcache_get_status()` 查看 OpCache 当前占用的内存，并在需要时调增（下周再详细说明）。

**opcache.interned_strings_buffer** – 一个文档较少的好设置。PHP 采用字符串内部化技术：如有 1000 个 “foobar” 字符串，内部会创建一个不可变变量并为其余 999 次使用提供指针。这个设置把内部字符串池从每个 php‑fpm 进程独立提升为所有进程共享，从而节省内存并提升大型应用的性能。

取值单位是 MB，建议设为 “16” 表示 16 MB。默认仅 4 MB。

**opcache.fast_shutdown** – 另一个文档不明的设置。“允许更快的关闭”。听起来不太有用。实际上，它提供了更快的调用代码在请求结束时的析构函数的机制，加速响应并让 PHP 工作进程更快就绪，以便处理下一个请求。将其设为 1 并开启。

**TL;DR‑在 `php.ini` 中的推荐配置**

```
1 opcache.revalidate_freq=0
2 opcache.validate_timestamps=0   (在开发环境请注释掉)
3 opcache.max_accelerated_files=7963
4 opcache.memory_consumption=192
5 opcache.interned_strings_buffer=16
6 opcache.fast_shutdown=1
```

#### APC（仅 PHP 5.4 及以下版本）

APC 是成熟的字节码缓存，未来可能会被整合进 PHP。它通常是首选。APC 以 PHP 扩展形式发布，使用 PECL 安装非常简便：

```
1 > pecl install apc
2 > service php5-fpm restart
```

真的很简单。在繁忙服务器上，你会立即看到 CPU 使用率急剧下降，甚至直线式掉下来。


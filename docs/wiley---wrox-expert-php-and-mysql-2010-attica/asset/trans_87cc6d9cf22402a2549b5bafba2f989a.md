
![](img/88e43d4c6a3d0e0d1f265975ce2f9f50_178_0.png)

## 图 4-5

缓存的另一个好处是它赋予你使用各种有用技巧的灵活性。你可以使用缓存来执行“延迟”处理。例如，想象一个处理 RSS 源的应用程序，它需要将源的组件存储到数据库中，并为 AJAX 客户端应用程序提供源的 JSON 缓存以供显示。

应用程序的一部分，通过 Web 请求运行，从互联网上请求一个 RSS 源。它获取 RSS 源内容，即一个 XML 文件。然后应用程序将此 XML 文件解析为 DOM Perl 对象并将 XML 转换为 JSON。然后 JSON 存储在 memcached 中，并可供应用程序提供给 AJAX 客户端。XML DOM 对象作为单独的对象存储在 memcached 中，并在队列表中创建一个条目，其中包含 DOM 对象的键。通过某种机制，要么是 cron 作业，要么是对队列表的 UDF 的触发，另一个进程（非 Web）从队列表中读取，该表获取存储在此队列表中的所有键，并使用这些键值检索 memcached 中存储的 DOM 对象。此过程随后遍历每个 DOM 对象，将每个源项存储到数据库中。此过程还删除队列表中的条目并从 memcached 中删除已处理的 DOM 对象。

所有这些意味着，一个通常会在 Web 应用程序层执行所有这些操作的应用程序，现在可以通过 memcached 分成两个进程：一个主要负责获取和缓存的 Web 应用程序，以及一个可以异步运行、与 Web 请求分开的非 Web 应用程序，该应用程序负责在所需频率下进行更重的数据库处理。

## Gearman 是什么？

Gearman 是来自创建 memcached 的同一批人——Danga、Brian Fitzpatrick 等人的又一个有用项目。它是一个服务器，用于将作业分派、分配或“分发”给比发起调用的机器更适合运行这些任务的机器。这允许任务并行运行，从而实现负载均衡和更好的扩展，并且能够调用未使用与应用程序代码相同编程语言编写的函数。

Gearman 由一个服务器——有趣的是称为 gearmand——和客户端组成：调用客户端，它们向服务器发出请求，以及可以执行客户端请求的 worker。有 PHP、Perl、Ruby、Python 等的客户端 API。

你可以使用 Gearman 来处理诸如 memcached 中存储的项目处理（写通缓存）以及你想要分发以减轻主服务器负载的任何处理。

> 在第 10 章中，你将看到 Gearman 有多么有用，通过构建搜索引擎应用程序的演示，作为你如何使用 Gearman 的实际示例。

## 缓存策略

你可以为不同类型的数据采用不同类型的缓存策略，具体取决于该数据更改的频率和存储的数据类型，如表 4-1 所示：

表 4-1：缓存策略

| 策略 | 描述 |
|---|---|
| 确定性缓存 | 读穿缓存示例中描述的缓存。客户端应用程序请求数据。如果数据在 memcached 中，则直接返回。如果不在，则从 MySQL 获取数据，写入 memcached，然后返回给请求者。 |
| 非确定性缓存 | 你假设始终存在于 memcached 中的数据。这对于更静态的数据特别有用。这也要求数据始终加载到 memcached 中，例如 Web 服务器启动时。此外，如果可能，你应该尝试将此缓存保留在其自己的服务器上，如果它有其他类型的存储对象，可能会通过 LRU 机制导致更静态的数据被替换。 |
| 会话或状态缓存 | 用于存储诸如用户会话数据之类的数据的缓存。它对于购物车等应用程序特别有用。 |
| 主动缓存 | 类似于非确定性缓存，即数据在数据库写入时自动在缓存中更新。你可以使用触发器和用于 MySQL 的 Memcached 函数来实现这一点，这些函数在第 5 章中介绍。 |
| 文件系统或页面缓存 | 缓存构成网站设计的模板或 HTML 代码。这使你避免使用文件系统来获取网站内容。 |
| 部分页面缓存 | 存储页面组件的位置。允许你避免每次显示页面时使用提供计算的昂贵查询，例如评论或故事受欢迎程度。相反，你可以定期构建这些组件然后将它们存储在 memcached 中。当页面显示时，它只需从 memcached 获取这些预构建的组件并显示它们！ |
| 缓存复制 | 内置于应用程序中的功能，为每个存储的项目将数据写入多个 memcached 服务器。这确保了你具有冗余。 |

## 安装 Memcached

安装 memcached 非常简单。你可以使用大多数 Linux 发行版的包安装程序或编译源代码。memcached 仅要求一个先决条件包——libevent。Libevent 是一个 API，memcached 使用它来扩展任意数量的打开连接。你也可以在大多数 Linux 发行版上使用包管理或源代码安装它。

### CentOS

要在 CentOS Linux 服务器上安装 memcached，请按照以下步骤操作：

- 1. 首先运行

```
[root@testbox ~]# yum search memcached
```

这会产生各种结果。最重要的两个是（这是 64 位 CPU 上的；32 位上可能是 i386）：

```
memcached.x86_64: High Performance, Distributed Memory Object Cache
memcached-selinux.x86_64: SELinux policy module supporting memcached
```

SELinux 包是为了确保 memcached 具有正确的防火墙设置以允许运行。Memcached 默认在端口 11211 上运行。你也可以同样轻松地设置防火墙以允许 11211 通过。

2. 接下来运行安装：

```
[root@testbox ~]# yum install memcached.x86_64
....
Dependencies Resolved
================================================================================
Package              Arch      Version          Repository    Size
================================================================================
Installing:
 memcached            x86_64    1.2.5-2.el5      epel         59 k
Installing for dependencies:
 libevent             x86_64    1.1a-3.2.1       base         21 k

Transaction Summary
================================================================================
Install      2 Package(s)
Update       0 Package(s)
Remove       0 Package(s)

Total download size: 80 k
Is this ok [y/N]:
```

正如你所见，libevent 作为依赖项自动包含，因此无需专门安装它。

3. 选择“y”完成安装。安装程序还将设置在操作系统启动时启动 memcached 的 init 脚本。

### Ubuntu

对于 Ubuntu，使用 apt-cache search：

```
$ apt-cache search memcached
libcache-memcached-perl--Cache::Memcached--client library for memcached
libmemcache-dev--development headers for libmemcache C client API
libmemcache0--C client API for memcached memory object caching system
memcached--A high-performance memory object caching system
```

所有这些包都是你最好安装的。libmemcached 包是用于高性能客户端库 Libmemcached 的，后者在本书的后面章节中解释。使用 apt-get install 安装这些包：

```
$ apt-get install memcached libmemcache-dev
libmemcache0
Reading package lists.. Done
Building dependency tree
Reading state information.. Done
The following extra packages will be installed:
 libevent1
```

```
The following NEW packages will be installed:
libevent1 libmemcache-dev libmemcache0
memcached
0 upgraded, 6 newly installed, 0 to remove and 96 not upgraded.
Need to get 227kB/278kB of archives.
After unpacking 946kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
```

与 yum 一样，apt-get 确保 libevent 已安装，处理任何依赖项。

### OpenSolaris

对于 OpenSolaris，你可以从包管理器 GUI 安装，或从命令行安装：

```
$ pfexec pkg install SUNWmemcached
DOWNLOAD          PKGS      FILES      XFER (MB)
Completed         1/1       11/11      0.1/0.1

PHASE             ACTIONS
Install Phase     43/43
```

### 从源码安装 Memcached

你也可以从源码安装 memcached。这可能是你首选的选项，尤其是当你想要最新最好的版本时。你可以在 Danga.com 上找到 memcached 的网页：http://www.danga.com/memcached/。从那里你会找到指向最新源码或 git 或 subversion 中的仓库的链接。如果你没有使用打包版本的 libevent，你也需要获取它——来自 http://monkey.org/~provos/libevent/。

现在，按照以下步骤操作：

- 1. 下载 libevent：
   ```
   $ wget http://monkey.org/~provos/libevent-1.4.10-stable.tar.gz
   ```
- 2. 编译并安装 libevent：
   ```
   $ tar xzvf libevent-1.4.10-stable.tar.gz
   $ cd libevent-1.4.10-stable
   $ ./configure
   $ make
   $ make install
   ```
- 3. 下载 memcached：
   ```
   $ wget http://memcached.googlecode.com/files/memcached-1.4.4.tar.gz
   ```
   或使用 git：
   ```
   $ git clone git://github.com/memcached/memcached.git
   ```

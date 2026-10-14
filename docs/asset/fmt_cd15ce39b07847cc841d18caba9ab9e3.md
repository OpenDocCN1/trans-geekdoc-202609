
另一种存储会话数据的方法是使用自定义会话处理器，将所有会话数据存储在用户浏览器的 Cookie 中。只要会话数据量不大，这种方式是可扩展的——因为 Cookie 在每次 HTTP 请求中都会被发送回服务器，因此最好只用于存储少于 1KB 的会话数据。此外，大多数浏览器对单个 Cookie 的大小限制约为 4KB，这限制了会话数据的存储量。

关于 Cookie 的一个担忧是私密性——会话数据（而不仅仅是令牌）会存储在用户的浏览器中，可通过像 [Firebug](http://getfirebug.com/) 这样的工具查看，因此不建议存储不想让用户看到的敏感信息。除非使用 SSL，否则 Cookie 数据在传输过程中也会被明文暴露。

但如果用户修改 Cookie 数据呢？如果操作正确，则不能。我们使用一种称为 HMAC（基于哈希的消息验证码）的技术对 Cookie 数据进行签名，这样在从用户处接收会话数据时，我们可以 100% 确定其未被篡改。

基于 Cookie 的会话处理不是 PHP 内置功能，但使用 PHP 5.4 的 [SessionHandlerInterface](http://www.php.net/manual/en/class.sessionhandlerinterface.php) 可以轻松集成。`SessionHandlerInterface` 的行为可以通过 `session_set_save_handler()` 向后兼容到较旧的 PHP 版本，但这对读者是一个练习。

下面我提供了一个工作示例类，演示如何实现我们自己的 `SessionHandlerInterface`。此外，我已将这段代码开源并在 [GitHub](https://github.com/stevecorona/SessionHandlerCookie)（因为我热爱分享和回馈），并在 [Packagist](http://packagist.org/packages/session-handler-cookie/session-handler-cookie) 上发布，以便轻松安装。

- [确保此技术安全的关键在于在部署代码之前，你必须将 `HASH_SECRET` 更改为一个 128 个字符以上的随机字符串]

```
 1 <?php
 2 
 3 class SessionHandlerCookie implements SessionHandlerInterface {
 4 
 5   private $data      = array();
 6   private $save_path = null;
 7 
 8   const HASH_LEN    = 128;
 9   const HASH_ALGO   = 'sha512';
10   const HASH_SECRET = "YOUR_SECRET_STRING";
11 
12   public function open($save_path, $name) {
13     $this->save_path = $save_path;
14     return true;
15   }
16 
17   public function read($id) {
18 
19     // Check for the existance of a cookie with the name of the session id
20     // Return an empty string if it's invalid.
21     if (! isset($_COOKIE[$id])) return '';
22 
23     // We expect our cookie to be base64 format, so decode it.
24     $raw = base64_decode($_COOKIE[$id]);
25     if (strlen($raw) < self::HASH_LEN) return '';
26 
27     // The cookie data contains the actual data w/ the hash concatonated
28     // to the end, since the hash is a fixed length, we can extract the
29     // last HMAC_LENGTH chars to get the hash.
30     $hash = substr($raw, strlen($raw)-self::HASH_LEN, self::HASH_LEN);
31     $data = substr($raw, 0, -(self::HASH_LEN));
32 
33     // Calculate what the hash should be, based on the data. If the data
34     // has not been tampered with, $hash and $calculated
35     // will be the same
36     $calculated = hash_hmac(self::HASH_ALGO, $data, self::HASH_SECRET);
37 
38     // If we calculate a different hash, we can't trust the data.
39     // Return an empty string.
40     if ($calculated !== $hash) return '';
41 
42     // Return the data, now that it's been verified.
43     return (string)$data;
44 
45   }
46 
47   public function write($id, $data) {
48 
49     // Calculate a hash for the data and append it to the end of the
50     // data string
51     $hash = hash_hmac(self::HASH_ALGO, $data, self::HASH_SECRET);
52     $data .= $hash;
53 
54     // Set a cookie with the data
55     setcookie($id, base64_encode($data), time()+3600);
56   }
57 
58   public function destroy($id) {
59     setcookie($id, '', time());
60   }
61 
62   public function gc($maxlifetime) {}
63   public function close() {}
65 }
66 
67 $handler = new SessionHandlerCookie;
68 session_set_save_handler($handler, true);
69 session_start();
```

# Database Server: Ultimate MySQL Tuning Guide

数据库是应用的核心和灵魂。它安全存储你的数据，并将数据传输到所有的应用服务器。在与和采访了数百位读者后，大多数人都告诉我，他们的数据库是堆栈中最难扩展的部分。

尽管 MySQL 无疑是最流行的数据库之一，但关于如何从最初的“基本”配置扩展数据库的有用信息却非常有限。在线搜索往往得不到满意结果，即使找到了，也往往是直接复制粘贴别人的 100 行 `my.cnf` 文件（显而易见没有解释为什么它有效），或者是一些自诩高手的“圣者”——建议你雇佣 DBA。雇佣 DBA 固然很好，但如果你是一个只有 5-10 名程序员的小公司，甚至只是两个在公寓里工作的家伙，那你就无法合理为雇佣 DBA 找到理由了。

让我告诉你一个秘密。数据库的优化和配置并不是某种只有完成了 10 个神圣任务才能学会的神秘手艺。事实上，它可以分解为几条简单的规则。

本章我们将专注于 MySQL，因为大多数人已经使用它，而且切换到其他数据库并不容易。不过，大多数数据库（包括 NoSQL 数据库）都遵循相同的扩展原则。虽然设置名称可能不同，但本章的内容对其他数据库同样适用。

## 从 NoSQL 获得 MySQL 的性能提升

MySQL 经常受到批评，说它不是最快的。但这里有个秘密：通过正确的调优，MySQL 完全可以与 NoSQL 媲美。NoSQL 在水平扩展和集群管理方面表现出色，例如 Cassandra 可以自动启动数百个新节点并自动加载数据，无需任何手动配置。相比之下，为 MySQL 添加新的从库或分片需要手动配置并迁移数据，可能需要数小时。

不过，你完全可以在单台服务器上通过只读从库来获得不错的性能。Twitter 和 Facebook 仍在使用 MySQL，这足以说明问题。37Signals 经常提到他们利用摩尔定律（Moore’s Law）进行水平扩展，而无需复杂的分片方案。虽然水平扩展和迁移到 NoSQL 数据库是不错的选择，但它代价巨大：需要重新组织和导入数据，并重写代码。我是 NoSQL 的大支持者，但我也坚信要用对工具做对工作，对于大多数场景，**MySQL 是正确的选择**。

获得 MySQL 的最佳性能需要对配置进行调整，我会涵盖所有最重要的设置。然而，MySQL 有数千个可配置的选项，我无法逐一说明。这里我提供“精华版”，帮助你快速获得最大收益。

如果你想了解每一个配置选项的具体作用以及 MySQL 的深层工作原理，建议参考权威的 MySQL 书籍《High Performance MySQL: Optimization, Backups, Replication, and More》。这是一本 700 页的权威著作，涵盖了高级 MySQL 调优的所有内容。

| ![question](img/leanpub_question.png) || **What is a slave?**In MySQL, we can scale out using a “Master/Slave” setup. That is to say, we designate a single server as the authoritative owner. All data from that server, or *master*, is replicated to *slave* servers, which provides fault-tolerance and more database capacity. Since the data flows in **one direction** only (from the master to the slaves), the slaves are read-only replicas and **all writes must go through the master**. If you write data to a slave server directly, it will not be replicated and will cause data fragmentation and inconsistency. |

| --- | --- |

### 选择正确的 MySQL 版本

你应该始终使用当前可用的最新主要版本的 MySQL。Oracle 每隔几个月就会发布新版本，保持更新至关重要，因为每个版本通常包含显著的性能提升。当时出版时，5.5 是最新的主要版本，但 5.6 即将发布。相同查询在 5.1 和 5.5 上的运行速度差异可能惊人，因此升级到最新版本始终是明智之举。

此外，基准测试显示，在 SSD 驱动器上，5.5 版本比 5.1 的 I/O 性能提升约 20%。

好了，选择最新版本 MySQL 很简单。但等等，还有另一个值得探索的选项——[Percona 的 MySQL 分支](http://www.percona.com/)。

#### 为什么使用 Percona 的 MySQL 分支？

Percona 是一家著名的 MySQL 咨询公司，其 [MySQL Performance Blog](http://www.mysqlperformanceblog.com) 以专业著称。他们还撰写了《High Performance MySQL: Optimization, Backups, Replication, and More》这本书（前文已提及）。因此，当我说他们在 MySQL 领域是专家时，我是真心实意的。

Anyways，“Percona Server”是 MySQL 服务器的 100%免费的即插即用替代品，并且不断基于最新的 MySQL 代码进行基线更新，因此始终与最新的 MySQL 发行版保持同步。你的现有代码和数据库无需任何修改即可在 Percona Server 上运行，并且使用更少的资源、更快。

* 它的运行速度比标准 MySQL 服务器快 40%。
* 提供比 MySQL 服务器更一致的性能。
* 包含 XtraDB（InnoDB 的分支），提供更好的可调度性和更高效的内存使用。
* 更多的调优选项，赋予你更大的控制权和更多功能。你可以 [查看功能对比这里](http://www.percona.com/doc/percona-server/5.5/feature_comparison.html)。

![](img/06----perconavsmysql.png)

此外，还需提及的是，Percona Server 非常稳健。我们在 Twitpic 的生产环境中已使用超过一年，未出现任何崩溃、数据丢失或问题。而且，其他大型平台如 Flickr、Tumblr、Etsy、Engineyard 和 37Signals 也在生产环境中使用 Percona Server。

##### 安装 Percona Server

```
1 > gpg --keyserver  hkp://keys.gnupg.net --recv-keys 1C4CBDCDCD2EFD2A
2 > gpg -a --export CD2EFD2A | sudo apt-key add -
3 > vi /etc/apt/sources.list.d/percona.repo.list
4 	deb http://repo.percona.com/apt precise main
5 	deb-src http://repo.percona.com/apt precise main
6 > apt-get update
7 > apt-get install percona-server-server-5.5 percona-server-client-5.5
```

#### 是否需要对数据进行分片？

大概不需要！当然，如果不了解你的数据，很难下定论，但在大多数情况下，使用 MySQL 进行分片是使用了错误的工具来完成错误的工作。当你分片数据时，你失去了 MySQL 擅长的所有优势，却获得了 MySQL 擅长的所有缺点（尤其是集群管理）。由于你需要重写大部分现有代码才能实现分片，通常更明智的做法是转向支持原生分片的数据库，例如 [MongoDB](http://www.mongodb.org/) 或 [Apache Cassandra](http://cassandra.apache.org/)。

| ![information](img/leanpub_information.png) || **What is Sharding?**Sharding 是将数据分布在多台服务器上，使得单台服务器不再保存全部数据。分片能够在单台服务器无法满足高负载需求时更有效地扩展数据库。虽然许多 NoSQL 数据库内置分片支持，但 MySQL 不提供。使用 MySQL 进行分片会导致无法在整个数据集上运行查询，并且通常需要编写自定义代码来交互数据库。 |

| --- | --- |

### 处理 libmysql 无法设置超时的问题

让我们稍微聊一下 PHP 如何与 MySQL 通信。无论你使用 `mysql`、`mysqli` 还是 `PDO`，内部 PHP 都是通过 `libmysql` 或 `mysqlnd` 与 MySQL 服务器建立连接并进行通信。

当 PHP 5.3 发布时，新增了 `mysqlnd`（MySQL Native Driver）这一功能。`mysqlnd` 是 PHP 团队自行编写的定制 C 语言库，专门用于处理 MySQL 连接。在此之前，PHP 使用 `libmysql`，这是 MySQL 自带的标准 C 库。

由于 `mysqlnd` 是 PHP 专属的实现，它更贴合 PHP，能够更好地与 PHP 集成。例如，你可以用纯 PHP 代码子类化 `mysqlnd`，从而注入或修改 PHP 与 MySQL 的交互方式。开发者利用这一特性实现了查询日志、[负载均衡](http://www.php.net/manual/en/book.mysqlnd-ms.php)以及甚至基于 PHP 的[查询缓存](http://www.php.net/manual/en/book.mysqlnd-uh.php)。

但 `libmysql` 与 `mysqlnd` 都有一个主要缺陷：它们都不能以小于 1 秒的精度设置连接超时，也都不支持设置查询超时。这意味着，如果 MySQL 服务器不可达，你能做的最短等待时间就是 1 秒——在高负载环境中显然远远不够。

#### 使用 PDO 设置连接超时

```
1 <?php
2 $pdo = new PDO("mysql:host=localhost;dbname=test", "username", "password");
3 $pdo->setAttribute(PDO::ATTR_TIMEOUT, 1);
```

#### 使用 mysqli 设置连接超时

与 `mysqli` 的做法类似，但要注意代码中的注释。不能像往常一样使用构造函数（`$mysqli = new mysqli('localhost')`）来创建对象，必须先使用 `mysqli_init()` 创建对象。

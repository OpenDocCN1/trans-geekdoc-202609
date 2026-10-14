
Anyways，“Percona Server”是MySQL服务器的100%免费的即插即用替代品，并且不断基于最新的MySQL代码进行基线更新，因此始终与最新的MySQL发行版保持同步。你的现有代码和数据库无需任何修改即可在Percona Server上运行，并且使用更少的资源、更快。

* 它的运行速度比标准MySQL服务器快40%。

* 提供比MySQL服务器更一致的性能。

* 包含XtraDB（InnoDB的分支），提供更好的可调度性和更高效的内存使用。

* 更多的调优选项，赋予你更大的控制权和更多功能。你可以 [查看功能对比这里](http://www.percona.com/doc/percona-server/5.5/feature_comparison.html)。

![](images/06----perconavsmysql.png)

此外，还需提及的是，Percona Server非常稳健。我们在Twitpic的生产环境中已使用超过一年，未出现任何崩溃、数据丢失或问题。而且，其他大型平台如Flickr、Tumblr、Etsy、Engineyard和37Signals也在生产环境中使用Percona Server。

###### 安装Percona Server

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

大概不需要！当然，如果不了解你的数据，很难下定论，但在大多数情况下，使用MySQL进行分片是使用了错误的工具来完成错误的工作。当你分片数据时，你失去了MySQL擅长的所有优势，却获得了MySQL擅长的所有缺点（尤其是集群管理）。由于你需要重写大部分现有代码才能实现分片，通常更明智的做法是转向支持原生分片的数据库，例如 [MongoDB](http://www.mongodb.org/) 或 [Apache Cassandra](http://cassandra.apache.org/)。

| ![information](images/leanpub_information.png) || **What is Sharding?**Sharding是将数据分布在多台服务器上，使得单台服务器不再保存全部数据。分片能够在单台服务器无法满足高负载需求时更有效地扩展数据库。虽然许多NoSQL数据库内置分片支持，但MySQL不提供。使用MySQL进行分片会导致无法在整个数据集上运行查询，并且通常需要编写自定义代码来交互数据库。 |

| --- | --- |

### 处理libmysql无法设置超时的问题

让我们稍微聊一下PHP如何与MySQL通信。无论你使用`mysql`、`mysqli`还是`PDO`，内部 PHP 都是通过 `libmysql` 或 `mysqlnd` 与 MySQL 服务器建立连接并进行通信。

当 PHP 5.3 发布时，新增了 `mysqlnd`（MySQL Native Driver）这一功能。`mysqlnd` 是 PHP 团队自行编写的定制 C 语言库，专门用于处理 MySQL 连接。在此之前，PHP 使用 `libmysql`，这是 MySQL 自带的标准 C 库。

由于 `mysqlnd` 是 PHP 专属的实现，它更贴合 PHP，能够更好地与 PHP 集成。例如，你可以用纯 PHP 代码子类化 `mysqlnd`，从而注入或修改 PHP 与 MySQL 的交互方式。开发者利用这一特性实现了查询日志、[负载均衡](http://www.php.net/manual/en/book.mysqlnd-ms.php)以及甚至基于 PHP 的[查询缓存](http://www.php.net/manual/en/book.mysqlnd-uh.php)。

但 `libmysql` 与 `mysqlnd` 都有一个主要缺陷：它们都不能以小于 1 秒的精度设置连接超时，也都不支持设置查询超时。这意味着，如果 MySQL 服务器不可达，你能做的最短等待时间就是 1 秒——在高负载环境中显然远远不够。

##### 使用 PDO 设置连接超时

```
1 <?php
2 $pdo = new PDO("mysql:host=localhost;dbname=test", "username", "password");
3 $pdo->setAttribute(PDO::ATTR_TIMEOUT, 1);
```

##### 使用 mysqli 设置连接超时

与 `mysqli` 的做法类似，但要注意代码中的注释。不能像往常一样使用构造函数（`$mysqli = new mysqli('localhost')`）来创建对象，必须先使用 `mysqli_init()` 创建对象。

```
1 <?php
2 // 注意：在使用 mysqli 设置连接超时时，
3 // 必须使用 mysql_init()（返回 mysqli 对象）来创建对象，不能直接使用构造函数。
4 $mysqli = mysqli_init();
5 $mysqli->options(MYSQLI_OPT_CONNECT_TIMEOUT, 1);
6 $mysqli->real_connect("localhost", "username", "password", "test");
```

#### 查询超时

如果没有查询超时机制，一个异常的查询可能会阻塞 PHP-FPM 进程长达 `max_execution_time`（在 `php.ini` 中设置，本章节我们将其设为 5 秒）的时间。但这仍然太长了！在理想情况下，所有查询的执行时间都可预测，但现实并非理想。同一查询在不同的 `WHERE` 条件下可能生成截然不同的执行计划。例如，下面两条查询：

![](images/06----explain.png)

在包含 17 亿行数据的表（即 17 亿，英文 **B**）上运行同一查询。MySQL 完全可以通过本章节的调优轻松应对千万甚至上亿级别的数据；唯一的区别在于第一条查询的 `IN` 语句全是整数，而第二条查询多了一个非整数参数。第一条查询会利用 `PRIMARY` 索引生成执行计划，几乎瞬间返回；第二条查询则会进行全表扫描，遍历全部 `1,719,843,109` 行，极有可能需要数小时才能完成。

即使 PHP 的 `max_execution_time` 终止 PHP-FPM 进程，查询仍会在 MySQL 服务器上继续运行，持续占用 CPU 并严重影响性能。这确实是一个大缺陷！

实际上，解决方案并不简单。PHP 本身没有提供查询超时的直接机制，MySQL 也没有一个可以直接设置的服务器级别超时选项。这在我看来是一个相当大的疏忽。

有两种可行的办法：

##### 借助 HAProxy 的超时功能

在后文“使用 HAProxy 为 MySQL 进行负载均衡”章节中，我介绍了如何使用 HAProxy 为 MySQL 从库提供负载均衡。HAProxy 还支持 TCP 超时设置，这实际上可以将 MySQL 的连接超时和查询超时精确到毫秒级。相关配置位于 `/etc/haproxy/haproxy.cfg`：

```
1 timeout connect 500ms
2 timeout client  1000ms
3 timeout server  1000ms
```

##### 使用 Percona Toolkit 的 `pt-kill`

Percona Toolkit 包含一个名为 `pt-kill` 的工具，能够监控 MySQL 并杀死运行时间过长的查询。当然，有些长时间运行的查询是合法的（如后台任务或 OLAP 系统），因此我通常会为应用创建专用的 MySQL 用户，并使用 `--match-user` 选项仅针对该用户的长时间查询进行杀戮，从而避免影响其他合法查询。

```
1 > pt-kill --daemonize --kill --busy-time 60s --match-user webuser
```

在使用 `pt-kill` 前，需要先安装 `percona-toolkit` 包。如果你遵循上面“安装 Percona Server”部分的步骤，只需执行以下命令即可安装：

```
1 > apt-get install percona-toolkit

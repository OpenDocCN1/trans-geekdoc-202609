
## 使用示例

以下是使用 Gearman UDF 将作业提交到 Gearman 作业服务器以将工作分配给您已启动的反向 worker 的一些示例：

```
mysql> select gman_servers_set('127.0.0.1');
+-------------------------------+
| gman_servers_set('127.0.0.1') |
+-------------------------------+
| NULL                          |
+-------------------------------+
```

```
mysql> select gman_do('reverse', 'This is a test');
+-------------------------------+
| gman_do('reverse', 'This is a test') |
+-------------------------------+
| tset a si sihT                |
+-------------------------------+
```

```
mysql> select gman_do_background('reverse', 'This is a test');
+------------------------------------------+
| gman_do_background('reverse', 'This is a test') |
+------------------------------------------+
| H:hanuman:940                            |
+------------------------------------------+
```

```
mysql> set @a = gman_do_background('reverse', "XYZ");

mysql> select @a;
+------------+
| @a         |
+------------+
| H:hanuman:945 |
+------------+
```

```
mysql> set @a = gman_do('reverse', "XYZ");

mysql> select @a;
+------+
| @a   |
+------+
| ZYX  |
+------+
```

如 gman_do_background() 的输出所示，它返回主机名和作业编号。

## PHP 和 Gearman

使用 Gearman 与 PHP 相结合无疑是理想的组合且易于使用。您拥有一个 Gearman client，它通常位于您的应用程序中，是向 Gearman 作业服务器发送作业的代码。您还拥有 worker 组件，它使用 PHP Gearman worker 库将自身注册为处理命名作业，然后指定作业的函数名。

编写 Gearman 启用的 PHP 应用程序非常简单，如以下简短示例所示。

首先是一个客户端，client.php：

```
<?

$client= new GearmanClient();
$client->addServer('127.0.0.1');
for ($i = 0; $i <= 360; $i++) {
print "sine $i: " . $client->do("sine", $i) . "\n";
}

?>
```

在此客户端示例中，实例化了一个 GearmanClient 对象。接下来，调用 Gearman client API addServer() 方法添加用于客户端连接的服务器。如果需要，可以添加多个服务器。空参数将是本地主机，这里为了清晰明确指定了。启动一个从 0 到 360（度）的循环，并对每次迭代调用 Gearman client API 方法。

接下来是 worker，worker.php。实例化一个 GearmanWorker 对象，就像客户端一样，addServer() 添加一个服务器。接下来，worker 添加一个函数 — 注册一个用于工作的函数 — 以处理 “sine” 作业的作业请求，而 “my_sine_function” 函数执行工作。while 循环运行 Gearman 服务器 API 方法 work()，直到 worker 被关闭或终止。函数 my_sine_function() 是指定用于处理 “sine” 作业的函数名，其中包含实现，该实现传递来自 Gearman 服务器 API 方法 workload() 的值，该值是客户端在向作业服务器发送作业时传递的参数。正如您所回忆的，对于此测试，它将是 0 到 360 的值。

```
<?php

$worker= new GearmanWorker();
$worker->addServer('127.0.0.1');
$worker->addFunction("sine", "my_sine_function");
while ($worker->work());

function my_sine_function($job)
{
    return sin(deg2rad($job->workload()));
}

?>
```

为了说明其工作原理，图 10-2 显示了客户端、作业服务器和 worker 的关系。

![](img/88e43d4c6a3d0e0d1f265975ce2f9f50_445_0.png)

图 10-2

第一步，sine 客户端向 Gearman 作业服务器发送作业 'sine'，值为 45。接下来，Gearman 作业服务器使用 Gearman client API 调用（使用 PECL/ Gearman）do() 发送 45 的值，sine worker 从 Gearman worker API 调用 workload() 读取该值。my_sine_function() 将值 0.70710678... 返回给 Gearman 作业服务器，然后 Gearman 作业服务器通过 Gearman client API 将其返回给 sine 客户端。

首先您需要确保 gearmand 正在运行。接下来，在一个终端中运行 worker：

```
patg@hanuman:~/wrox$ php worker.php
```

在另一个终端中运行客户端：

```
patg@hanuman:~/wrox$ php client.php
sine 0: 0
sine 1: 0.0174524064373
...
sine 29: 0.484809620246
sine 30: 0.5
sine 31: 0.51503807491
...
sine 44: 0.694658370459
sine 45: 0.707106781187
sine 46: 0.719339800339
...
sine 89: 0.999847695156
sine 90: 1
sine 91: 0.999847695156
...
sine 209: -0.484809620246
sine 210: -0.5
sine 211: -0.51503807491
...
sine 269: -0.999847695156
sine 270: -1
sine 271: -0.999847695156
sine 359: -0.0174524064373
```

而且它有效！

您也可以从 UDF 中使用它：

```
mysql> select gman_do('sine',45);
+------------------+
| gman_do('sine',45) |
+------------------+
| 0.707106781187   |
+------------------+

mysql> select gman_do('sine',90);
+------------------+
| gman_do('sine',90) |
+------------------+
| 1                |
+------------------+
```

```
mysql> select gman_do('sine',361);
+-----------------+
| gman_do('sine',361) |
+-----------------+
| 0.0174524064373 |
+-----------------+
```

而且它也有效。

所以，到现在为止，您应该已经明白使用 Gearman 是多么简单。此外，您可以看到，使用 Gearman client 和 worker API 结合 Gearman 作业服务器，调度和管理以及网络通信都已处理完毕，因此您可以专注于开发应用程序。现在您大概可以想象出您可能会使用它的各种方式——可能性是无穷的！

## NARADA：一个搜索引擎应用程序

您对刚刚读到的关于 Gearman 的内容应该感到好奇。现在您将真正看到 Gearman 以及 MySQL、memcached、memcached Functions for MySQL、Sphinx、Apache 和 PHP 的实际应用！

搜索引擎是应用程序中最有可能拥有大量移动部件和功能的应用，它们需要提供信息并成为分布式应用程序的良好示例。在本章作者之前的一本书中，这一想法在 Perl 中得到了演示。书出版后，Eric Day 与作者合作将这一想法变成了一个实际项目，名为 Narada，以印度教传统中名为 Narada 的神圣圣人的名字命名，他在宇宙中旅行弹奏 Tambura 并访问遥远的世界（梵语中的 “Lokas”）。这似乎是搜索应用程序的一个好名字，因为它需要获取远程内容，从某种意义上说，“穿越宇宙”。

Eric Day 还说服作者用 PHP 编写此应用程序以匹配 Perl 版本，作为 Gearman 真正语言无关性的良好练习。这是为了响应需要在 Java One 上展示 Narada 的需求，这要求 Narada 需要使用新的 Drizzle RDBMS 作为数据存储在会议上以 Java 重新实现。Sun 希望使用 Narada 来演示它如何在其云计算平台（http://www.sun.com/solutions/cloudcomputing/index.jsp）上运行。由此，Narada 在 PHP 和 Java 上都重新实现了，尽管您可以根据实现语言互换使用其中的任何一个部分。

Narada 有相当多的移动部件——有点像 Rube Goldberg 装置——但以好的方式！Narada 是一个很好的应用程序，可以演示当这些新技术——特别是 Gearman、Sphinx 和 memcached——一起使用来开发分布式应用程序时是多么有用。Narada 仍然有点原型，可能会随着人们想要贡献的更好的想法而改变或变化。本演示的主要目的是向您展示使用 Gearman 如何让您将处理分散到各种作业和各种服务器上，从而减轻 Web 应用程序的工作量。

## 获取 Narada

获取 Narada 源代码的最佳方式是访问 https://launchpad.net/narada，在那里您可以获得源文件或简单地使用 bazaar 版本控制系统检出源。从您文档根目录中可以运行 PHP 的任何目录中，输入以下内容：

```
bzr clone lp:narada
```

代码结构基本上是四个顶级目录——php、perl、sphinx 和 sql。php 目录包含设置基于 PHP 的 Narada所需的所有源代码，您可以将其复制到 Web 服务器文档根目录中的任何目录。sphinx 目录包含 sphinx.conf 文件，您将其复制到保存 sphinx.conf 的位置（/usr/local/sphinx/etc）。sql 目录包含模式文件 narada.sql，用于创建由 Narada 使用的表，无论是基于 PHP 的 Narada 还是基于 Perl 的 Narada。确保为 Narada 创建数据库/模式并授予您选择的任何用户权限，然后运行此模式文件以创建表。

## Narada 组件

此应用程序有两个主要部分：

- 用于数据检索、存储和创建全文索引的数据收集系统
- 搜索引擎用户应用程序

Narada 由表 10-1 中列出的组件组成。

表 10-1：Narada 组件

| 组件 | 描述 |
|---|---|
| Gearman | `gearmand` 正在运行，以及 worker 和 client。 |
| Narada.php | 实现 Narada 类，其中包含索引页面和各个 worker 使用的方法。 |
| NaradaConf.php | 这是全局变量配置文件。提供各个 worker 使用的全局设置。 |
| index.php | 显示搜索页面，允许您输入要获取的 URL 以及用于搜索 Sphinx 已索引内容的搜索词。 |
| NaradaFetch.php | 给定一个 URL，它会检索该 URL 处的页面并解析该 URL 处的文档，对找到的任何 URL 调用插入 worker (`NaradaInsert.php`)。此外，还会调用索引 worker NaradaIndex 并检查是否应重新生成 Sphinx 索引。最后，获取的内容存储在 MySQL 中。 |

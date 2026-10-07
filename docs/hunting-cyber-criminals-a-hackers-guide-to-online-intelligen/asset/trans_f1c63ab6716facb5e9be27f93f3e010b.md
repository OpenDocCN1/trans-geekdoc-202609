

# 第 14 章 公开访问的数据存储 299

CSF 能够搜索公开访问的 Amazon S3 桶、Digital Ocean Spaces 以及 SpiderOak 共享文件夹。CloudStorageFinder 可于：https://github.com/digininja/CloudStorageFinder。

CSF 通过对 URL 进行暴力破解来工作，但你的词表越好，获得的结果就越多。请参阅第 2 章中关于创建优秀暴力破解词表的方法。

CSF 拥有三个关键工具：bucket_finder.rb、ocean_finder.rb、space_finder.rb 和 spider_finder.rb。正如你可能想象的，`bucket_finder.rb` 用于寻找 Amazon S3 桶，而 `space_finder.rb` 用于寻找 SpiderOak 共享文件夹。

这三个程序的选项和参数非常相似，主要区别在于区域（region）参数。在每情况下，公共存储位于不同的区域，因此此参数可能会根据你正在寻找的不同服务而更改。

CSF S3 存储桶查找器的参数包括：

```
--help -h: 显示帮助
--download, -d: 下载文件
--log-file, -l: 输出日志的文件名
--region, -r: 使用的区域，选项有：
  us - 美国标准
  ie - 北加利尼亚
  si - 新加坡
  to - 东京
--v: 详细

wordlist: 使用的词表
```

## Amazon S3

假设你准备好了暴力破解词表，运行 CSF 非常简单。对于我们的初始扫描，我们将针对美国区域运行 `bucket_finder`，并使用 `-d` 下载我们遇到的所有内容：

```
[root@ost] > ./bucket_finder.rb -us -d wordlist.txt -l logfile.txt
```

我们初始扫描的输出看起来如下：

```
Bucket ie redirects to: i3.amazaws.com
Bucket does not exist: endofspecialwords
Bucket does not exist: Aarhus
Bucket found but access denied: Aaron
Bucket does not exist: Ababa
Bucket found but access denied: aback
```

Bucket does not exist: abaft
Bucket does not exist: abandoned
Bucket does not exist: abandoning
Bucket does not exist: abandonment
Bucket does not exist: abandons
Bucket found access denied: abase

CSF 做的一件事情是不允许使用 S3 API 密钥进行存储桶身份验证。这将在本书稍后使用 NoScrape 工具进行介绍。

## Digital Ocean Spaces

Digital Ocean 是我的云提供商。Digital Ocean 最近发布了“Spaces”功能，这是另一种类型的公共桶，类似于 Amazon S3。这非常棒，因为我总是喜欢查看新服务，因为它们开箱即用时很大可能出现配置错误。

> 当你注册 Digital Ocean space 时，注册过程会询问你是希望具有公开访问权限，还是仅限具有正确密钥的用户访问。

Amazon 的初始设置和配置要复杂得多，所以我个人认为这里不会有很大的错误空间，除非有人意外创建了公共空间并忘记了它。尽管如此，我们应该尝试。

运行 CSF 的 `space_finder` 的主要区别在于参数的细微变化。以下参数包括：

```
Usage: space_finder [OPTION] --wordlist
-h, --help: 显示帮助
-d, --download: 下载文件
-l, --log-file: 输出日志的文件名
-h, --hide: 隐藏私有空间，仅显示公共空间
-n, --hide-not-found: 隐藏未找到的空间
-r, --region: 要检查的区域，选项有：
 all 所有区域
nyc 纽约
ams 阿姆斯特丹
sgp 新加坡
-V: 详细
```

wordlist: 使用的词表

对于我们的测试，我们将尝试使用 `-r all` 参数针对所有区域运行 `space_finder`。其他都相同。针对所有区域运行工具意味着我们将为每个区域发送三个不同的请求：

```
[ root@osint ] > ./space_finder -r all -d wordlist.txt -l logfile.txt
```

# 第 14 章 - 公开访问的数据存储 301

输出如下：

```
Space does not exist in region am3: Backup
Space does not exist in region nyc3: Backup
Space does not exist in region sql1: Backup
Space does not exist in region am3: warez
Space does not exist in region nyc3: warez
Space does not exist in region sql1: warez
Space does not exist in region am3: prøn
Space does not exist in region nyc3: prøn
Space does not exist in region sql1: prøn
Space does not exist in region am3: porn
Space does not exist in region nyc3: porn
Space does not exist in region sql1: porn
Space does not exist in region am3: Scripts
Space does not exist in region nyc3: Scripts
Space does not exist in region sql1: Scripts
Space does not exist in region am3: IISHelp
Space does not exist in region nyc3: IISHelp
Space does not exist in region sql1: IISHelp
Space found in region nyc3: vinnyria
(https://vinnyria.nyc3.digitaloceanspaces.com )
<Private> https://vinnyria.nyc3.digitaloceanspaces.com/test/
```

如果你足够幸运找到了一个公共空间，它看起来会像之前我个人空间的输出。现在，让我们转向 NoSQL 数据库以及可以发现的奇迹。

## NoSQL 数据库

传统的关系型数据库在可扩展性和模式灵活性方面存在问题，这导致了 NoSQL 数据库的出现。如今大多数现代 Web 应用程序使用 NoSQL 数据库。在 NoSQL 数据库中，一切都是基于文档的。除了速度和灵活性外，这些数据库系统还需要比 SQL 数据库更高级的安全配置。例如，Elasticsearch 数据库默认是公开的，除非你在前面放置了防火墙或阻止访问端口 9200。

本节将查看查看 MongoDB、Elasticsearch 和 CassandraDB。

## MongoDB

MongoDB 是最流行的 NoSQL 数据库类型之一。MongoDB 将数据存储在灵活的 JSON 类文档中，这意味着它不像传统的 SQL 表结构。你可以通过多种方式查询 MongoDB，包括 Mongo 命令行工具和 RobotMongo 等 GUI 应用。

> 专家：BOB DIA

对我来说很有趣，因为我想他们过去犯过错误。在早期的版本中，他们决定不对默认配置进行授权。完整的凭据只是密码，所以你不需要暴力破解。

## Robot 3T

Robot 3T 是用于访问和操作 MongoDB 数据库的免费 GUI 工具。Robot 3T 还有一个名为 Studio 3T 的高级版本，包含了从 Mongo 数据库导入导出的功能。直接开始，如果你在 3T 中没有连接，第一个屏幕将提示你输入信息（图14.1）。本节将显示来自真实服务器的屏幕。由于我不知道，相关信息将被隐藏。

# 第 14 章 » 公开访问的数据存储 303

在你输入目标服务器的 IP 地址并点击保存后，你将进入 MongoDB 连接列表（如图14.2 所示）。

点击连接按钮将连接你到你的 MongoDB 服务器。你在左列首先注意到的是一个树形菜单，列出了可用数据库和集合的列表。图14.3 显示了测试服务器上的可用数据库。

展开每个数据库将显示每个数据库的集合列表。图14.4 显示了每个数据库展开后的集合列表。由于 PrivateDB 看起来最有趣，让我们继续探索这个数据库。在 PrivateDB 中，我们可以看到八不同的集合。点击“users”集合将展开应用程序窗口并向我们展示该集合中的可用文档列表（图14.5）。


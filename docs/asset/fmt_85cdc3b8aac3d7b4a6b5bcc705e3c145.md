
## 62.93.70.34 的详情

- IP: 62.93.70.34
- 十进制: 1046360/194
- 主机：monitor.jm-data.at
- ASN: 25447
- ISP: JM-DATA GmbH
- 组织: JM-DATA GmbH
- 服务: 未检测到
- 类型: 宽带
- 分配: 静态 IP
- 黑名单: 点击检查黑名单状态
- 大洲: 欧洲
- 国家: 奥地利
- 州地区: 提罗尔
- 城市: Dereegen 的 Hopfgarten
- 纬度: 46.9247 (46° 55' 29.92" N)
- 经度: 12.4958 (12° 29' 44.88" E)
- 邮编: 9961

## 图 13.13

> 注意：在《黑暗主宰》的官方调查报告中，你可以找到将 Cypher 置于奥地利或附近的额外细节。

## 总结

本章专注于挖掘互联网各个分散角落的隐藏信息。这包括用于广泛信息收集的`Harvester`工具，以及用于收集 GitHub 信息的更有针对性的`Gitrob`工具。

本章提供的详情和示例说明，最随机（以及最隐晦）的地方如论坛、粘贴板、代码库和 wiki 页面可以提供意想不到的结果，有时在调查中提供突破性的线索。

在下一章中，我们将进一步扩大搜索范围，从 MongoDB 和 Elasticsearch 等公开数据库中查找信息。

# 第 14 章

## 14 公开数据存储

## 公开数据存储

数据泄露（或数据外泄）绝不是容易的事。我的意思是，一旦你发现了漏洞或泄露，如何处理这种情况，根据我的经验，这是最困难的部分。

本章提供的详情和示例说明，最随机（以及最隐晦）的地方如论坛、粘贴板、代码库和 wiki 页面可以提供意想不到的结果，有时在调查中提供突破性的线索。

在下一章中，我们将进一步扩大搜索范围，从 MongoDB 和 Elasticsearch 等公开数据库中查找信息。

## 第三部分 —— 掘金

数据泄露（或数据外泄）绝不是容易的事。我的意思是，一旦你发现了漏洞或泄露，如何处理这种情况，根据我的经验，这是最困难的部分。

本章提供的详情和示例说明，最随机（以及最隐晦）的地方如论坛、粘贴板、代码库和 wiki 页面可以提供意想不到的结果，有时在调查中提供突破性的线索。

在下一章中，我们将进一步扩大搜索范围，从 MongoDB 和 Elasticsearch 等公开数据库中查找信息。

## 第 14 章 » 公开访问的数据存储

这意味着，任何尝试通过 IP 地址在 9200 端口访问你的 Elasticsearch 数据库的人，只需通过查询 URL 获得对你数据的完整 CRUD（创建、读取、更新、删除）权限。保护你的 ES 集群的方法是将所有内容都放在防火墙后面，使 IP 地址不会在公网中暴露。

## 数据归属

发现导出数据集的所有者通常是调查中最困难的部分，因为你唯一可以依靠的仅仅是一个 IP 地址，而托管公司在没有正式法律请求的情况下，永远绝不会交出该地址的所有者。

虽然我通常会在与其他人交谈很久以前联系相关机构，但这次情况不同。尝试识别一个 IP 地址的所有者可能是你执行过的最艰巨、最精疲力竭的任务之一，因此我招募了几人来帮助。

我花了整整一个月的时间才弄清楚 Exactis 数据的实际主人。在连续几周无法找到所有者后，我联系了执法部门和可能提供帮助的记者。

当我们最终确定 Exactis 是这些泄露服务器的所有者时，我已经在与《连线杂志》（Wired）的 Andy Greenberg 合作了。当我们查明真相后，我立即联系了 Exactis，建议他们将数据下线，因为这些数据处于完全开放状态。

我解释说，我已经通知了执法部门，因为这些数据似乎包含了几乎每一位美国公民的信息，而且我在调查期间一直与《连线杂志》合作。我强烈建议他们与 Andy 谈谈，将他们的说法记录在案，以帮助进行损害控制。

《连线杂志》报道发表后 Exactis 遭遇的后果是可以预料到的，那天我对此仍感到很遗憾。那家公司破产了，其所有者 Steve Hardie 目前面临着严厉的集体诉讼。某一天晚上，我收到 Steve 发来的短信，问我为什么要毁掉了他的生活。

我不撒谎，那种感觉确实很糟糕，我知道其中包含事实。另一方面，他是那家让所有数据都暴露在外的公司首席执行官。在某个时刻，这是他的责任。坦率地说，考虑到有这么多研究人员在寻找开放的数据存储，某人发现这些数据只是早晚的问题。

根据《连线杂志》最新的报道，该 CEO 声称数据仅开放了“几天”。根据我找到这些数据所花费的时间，我对这一问题有不同的看法。

话虽如此，我的“话语”并无意义。在调查员的职业生涯中，总会有需要用事实来支撑你的言论的时候，正是这种情况教会了我几个全新的、奇妙且实用的 Shodan 技巧。

## Shodan 的命令行选项

大多数研究人员使用 Shodan 的 Web 界面，但许多人可能没有意识到（正如我以前那样）通过 Shodan 的命令行工具可以使用所有扩展功能。

Shodan 命令行工具结果的一个巨大优势是，能够下载特定类型数据库的所有查询结果。

例如，一个用途是让 Shodan 提供所有公开的 Elasticsearch 数据库的 IP 地址。这需要两个独立的命令：第一个用于下载数据，第二个用于将其解析为可用的格式。这就是我用来揭露 Exactis 数据泄露时使用的精确过程。

我们可以首先使用以下语法告诉 Shodan 工具下载所有的 Elasticsearch：

```
shodan download --limit (结果数量) (你的文件名) (查询)
```

为了完全下载所有公开的 Elasticsearch 数据库，我将限制设置为 50,000 条目。Web UI 显示大约有 30,000 条目，我特意设置了这个数字以确保所有内容都被包含在：

```
root:~$ shodan download --limit 50000 elasticdata product:Search query:

Total number of results: 28289

Query credits left: xxxx

Output file: elasticdata.json.gz
```

现在我们已经有了下载后的结果，可以使用 `parse` 命令提取我们需要的相关数据。在这种情况下，我通常使用以下命令提取 IP 和端口号：

```
shodan parse -fields ip_str.port --separator , elasticdata.json.gz
```

这将创建一个解析后的 IP 地址和端口号列表。在本章的稍后部分内容中，我们将使用这些信息来自动化识别可能泄露信息的服务器的过程。

## 查询历史数据

在本节的早些部分，我提到过 Exactis 的案例让我真正了解了 Shodan 的命令行工具。除了能够轻松查询和下载原始数据外，Shodan 的工具还允许你搜索有关 IP 地址的历史信息。这意味着在任何给定的时间段，Shodan 不仅会识别 IP 地址上哪些端口是开放的，还会保留该数据的历史记录供你查询。让我们将其应用到 Exactis 的 IP 上，看看我们能发现什么。

Exactis 有三个与它的 Elasticsearch 集群相关的 IP 地址：

- 172.106.108.69
- 172.106.108.73
- 172.106.108.77

作为调查的一部分，你可能会（而且极可能）被要求提供某种程度的证据（或证词），关于 IP 地址或数据在线的时间长度。在对《连线杂志》的后续访谈中，Exactis 的 CEO 坚持认为数据仅暴露了几天。让我们看看 Shodan 告诉我们什么。以下语法将查询 IP 地址的历史信息：

```
shodan host --history -S --format pretty ip
```

运行其中一个 Exactis 的 IP 将返回以下内容：

```
shodan host --history -S --format pretty 172.106.108.69

172.106.108.69
172.106.108.73
172.106.108.77
172.106.108.69
  Ports: 9200/open
  Last seen: 2019-04-11 06:43:05
  City: Ashburn
  Country: United States
  Organization: Exactis
172.106.108.73
  Ports: 9200/open
  Last seen: 2019-04-11 06:43:05
  City: Ashburn
  Country: United States
  Organization: Exactis
172.106.108.77
  Ports: 9200/open
  Last seen: 2019-04-11 06:43:05
  City: Ashburn
  Country: United States
  Organization: Exactis
```

（注：由于原文此处 Shodan 输出部分存在大量重复和乱码，译文已根据逻辑提取了核心信息，并保持了格式一致）

> 注意：我猜最后对他生活的伤害并不大，因为 Steve 已经通过他的新公司 BrightSpeed (www.brightspeed.com) 重新开始了。

## CloudStorageFinder

CloudStorageFinder (`CSF`) 是由 Robin Wood 编写的一个开源工具，其功能正如其名——它能寻找公开暴露的云存储桶。

# 第 14 章 公开访问的数据存储 299

`CSF` 能够搜索公开访问的 Amazon S3 桶、Digital Ocean Spaces 以及 SpiderOak 共享文件夹。CloudStorageFinder 可于：https://github.com/digininja/CloudStorageFinder。

`CSF` 通过对 URL 进行暴力破解来工作，但你的词表越好，获得的结果就越多。请参阅第 2 章中关于创建优秀暴力破解词表的方法。

`CSF` 拥有三个关键工具：`bucket_finder.rb`、`ocean_finder.rb`、`space_finder.rb` 和 `spider_finder.rb`。正如你可能想象的，`bucket_finder.rb` 用于寻找 Amazon S3 桶，而 `space_finder.rb` 用于寻找 SpiderOak 共享文件夹。

这三个程序的选项和参数非常相似，主要区别在于区域（region）参数。在每情况下，公共存储位于不同的区域，因此此参数可能会根据你正在寻找的不同服务而更改。

`CSF` S3 存储桶查找器的参数包括：

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

假设你准备好了暴力破解词表，运行 `CSF` 非常简单。对于我们的初始扫描，我们将针对美国区域运行 `bucket_finder`，并使用 `-d` 下载我们遇到的所有内容：

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

`CSF` 做的一件事情是不允许使用 S3 API 密钥进行存储桶身份验证。这将在本书稍后使用 NoScrape 工具进行介绍。

## Digital Ocean Spaces

Digital Ocean 是我的云提供商。Digital Ocean 最近发布了“Spaces”功能，这是另一种类型的公共桶，类似于 Amazon S3。这非常棒，因为我总是喜欢查看新服务，因为它们开箱即用时很大可能出现配置错误。

> 当你注册 Digital Ocean space 时，注册过程会询问你是希望具有公开访问权限，还是仅限具有正确密钥的用户访问。

Amazon 的初始设置和配置要复杂得多，所以我个人认为这里不会有很大的错误空间，除非有人意外创建了公共空间并忘记了它。尽管如此，我们应该尝试。

运行 `CSF` 的 `space_finder` 的主要区别在于参数的细微变化。以下参数包括：

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
```

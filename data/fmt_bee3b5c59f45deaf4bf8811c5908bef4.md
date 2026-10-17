
[recon-ng][default] > help
Commands (type [help|?] <topic>):
---------------------------------
back           退出当前上下文
dashboard      显示活动摘要
db             与工作区数据库接口
exit           退出框架
help           显示此菜单
index          创建模块索引（仅限开发）
keys           管理第三方资源凭据
marketplace    与模块市场接口
modules        与已安装的模块接口
options        管理当前上下文选项
pdb            启动 Python 调试会话（仅限开发）
script         记录并执行命令脚本
shell          执行 shell 命令
show           显示各种框架项
snapshots      管理工作区快照
spool          将输出缓存到文件
workspaces     管理工作区
[recon-ng][default] >

在使用 Recon-ng 工具开始收集信息之前，你先了解有哪些可用模块。（你可以从示例 3-11 中的初始屏幕中看到 Recon-ng 中当前安装的模块数量。）Recon-ng 自带了一个“市场（marketplace）”，你可以在其中搜索要安装的可用模块。你可以使用 `marketplace search` 命令来搜索 Recon-ng 中所有可用的模块，如图 3-5 所示。

![FIGURE 3-5 Recon-ng 市场搜索](img/03fig05.jpg)

**图 3-5** Recon-ng 市场搜索

图 3-5 仅显示了 Recon-ng 中可用的前几个模块。图 3-5 表头中的字母 D 表示该模块具有依赖项。字母 K 表示需要 API 密钥才能使用特定模块中使用的资源。例如，路径为 `recon/companies-contacts/censys_email_address` 的模块具有依赖项，并且需要一个 API 密钥来查询 Censys 数据库。（Censys 是查询 OSINT 数据的一个非常流行的资源。）

你可以通过 `marketplace refresh` 命令来刷新可用模块的数据，如示例 3-13 所示：

```
[recon-ng][default] > marketplace refresh
[*] Marketplace index refreshed.
```

让我们进行一次快速搜索，以找到我的其中一个域名（[h4cker.org](http://h4cker.org)）的不同子域名。我们可以使用 `bing_domain_web` 模块尝试利用 Bing 搜索引擎查找任何子域名。你可以通过使用 `marketplace search <keyword>` 命令对任何模块进行关键词搜索，如示例 3-14 所示：

```
[recon-ng][default] > marketplace search bing
[*] Searching module index for 'bing'...
+---------------------------------------------------------------------+
|           Path             | Version |     Status    |    Updated   |
D | K |
+---------------------------------------------------------------------+
| recon/companies-contacts/bing_linkedin_cache   | 1.0     | not
installed | 2019-06-24 |   | * |
| recon/domains-hosts/bing_domain_api             | 1.0     | not
installed | 2019-06-24 |   | * |
| recon/domains-hosts/bing_domain_web             | 1.0     | not
installed | 2019-06-24 |   | * |
| recon/hosts-hosts/bing_ip                        | 1.0     | not
installed | 2019-06-24 |   | * |
| recon/profiles-contacts/bing_linkedin_contacts | 1.0     | not
installed | 2019-06-24
+-----------------------------------------------------+

  D = 具有依赖项。请查看详细信息。
  K = 需要密钥。请查看详细信息。
```

多个结果匹配了关键词 `bing`。然而，我们感兴趣的是 `recon/domains-hosts/bing_domain_web`。你可以通过使用 `marketplace install` 命令安装该模块，如示例 3-15 所示。

**示例 3-15** 安装 Recon-ng 模块

点击此处查看代码图像

```
[recon-ng][default] > marketplace install recon/domains-hosts/bing_domain_web
[*] Module installed: recon/domains-hosts/bing_domain_web
[*] Reloading modules...
[recon-ng][default] >
```

你可以使用 `modules search` 命令（如示例 3-16 所示）：

```
[recon-ng][default] > modules search
  Discovery
  ---------
    discovery/info_disclosure
  Recon
  -----
    recon/domains-hosts/bing_domain_web
    recon/domains-hosts/brute_hosts
    recon/domains-hosts/certificate_transparency
    recon/domains-hosts/netcraft
    recon/profiles-contacts/bing_linkedin_contacts
[recon-ng][default] >
```

要加载你想使用的模块，请使用 `modules load` 命令，如示例 3-17 所示。在示例 3-17 中，`bing_domain_web` 模块已加载。注意提示符已变为包含模块名称。模块加载后，你可以使用 `info` 命令显示模块选项（如示例 3-17 所示）：

```
[recon-ng][default] > modules load recon/domains-hosts/bing_domain_web
[recon-ng][default][bing_domain_web] > info
    Name: Bing Hostname Enumerator

    Author: Tim Tomes (@lanmaster53)
   Version: 1.1
Description:
  Harvests hosts from Bing.com by using the 'site' search operator.
Updates the 'hosts' table with the results.

Options:
  Name    Current Value  Required  Description
  ------  -------------  --------  -----------
  SOURCE  example.com    yes       source of input (see 'info' for
details)

Source Options:
  default         SELECT DISTINCT domain FROM domains WHERE domain IS
NOT NULL
  <string>        string representing a single input
  <path>          path to a file containing a list of inputs
  query <sql>     database query returning one column of inputs
[recon-ng][default][bing_domain_web] >
```

例如，你可以使用 `options set SOURCE` 命令更改源（用于查找其子域名的域名），如示例 3-18 所示。设置源域名后，你可以输入 `run` 来运行查询（如示例 3-18 所示）：

```
[recon-ng][default][bing_domain_web] > options set SOURCE example.com
[*] SOURCE set to example.com
[recon-ng][default][bing_domain_web] > run
```

```
[recon-ng][default][bing_domain_web] > options set SOURCE h4cker.org
SOURCE => h4cker.org
[recon-ng][default][bing_domain_web] > run
----------
H4CKER.ORG
----------
[*] URL: https://www.bing.com/search?first=0&q=domain%3Ah4cker.org
[*] Country: None
[*] Host: bootcamp.h4cker.org
[*] Ip_Address: None
[*] Latitude: None
[*] Longitude: None
[*] Notes: None
[*] Region: None
[*] --------------------------------------------------
[*] Country: None
[*] Host: webapps.h4cker.org
[*] Ip_Address: None
[*] Latitude: None
[*] Longitude: None
[*] Notes: None
[*] Region: None
[*] --------------------------------------------------
[*] Country: None
[*] Host: lpb.h4cker.org
[*] Ip_Address: None
[*] Latitude: None
[*] Longitude: None
[*] Notes: None
[*] Region: None
[*] --------------------------------------------------
[*] Country: None
[*] Host: malicious.h4cker.org
[*] Ip_Address: None
[*] Latitude: None
[*] Longitude: None
[*] Notes: None
[*] Region: None
[*] --------------------------------------------------
[*] Sleeping to avoid lockout...
[*] URL: https://www.bing.com/search?first=0&q=domain%3Ah4cker.
org+-domain%3Abootcamp.h4cker.org+-domain%3Awebapps.h4cker.org+-
domain%3Alpb.h4cker.org+-domain%3Amalicious.h4cker.org
-------
SUMMARY
-------
[*] 4 total (0 new) hosts found.
[recon-ng][default][bing_domain_web] >
```

示例 3-18 中的高亮行显示，使用 `bing_domain_web` 模块发现了四个子域名。

### 提示

你还可以结合其他模块来查找有关特定目标的额外信息。例如，你可以使用 `recon/domains-hosts/brute_hosts` 模块利用词汇表并进行 DNS 查询以查找额外的子域名。黑客攻击的核心在于确定端口是否开放的过程。例如，使用 `SYN scan` 时，工具向目标发送一个 `SYN` 包。如果响应是 `SYN/ACK`，则表示该端口正在监听。如果响应是 `RST`（重置），则表示端口已关闭。如果 `SYN` 探测没有收到任何响应，`Nmap` 将其标记为 `filtered`（已过滤）。这也被称为半开放扫描，因为它没有建立完整的 TCP 连接。`Nmap` 在使用 `nmap` 时定义了 SYN 响应。

示例 3-19 展示了如何通过指定 `-sS` 选项对 IP 地址为 192.168.88.251 的主机运行 TCP SYN 扫描。如你所见，该系统有几个开放的端口。在某些情况下，你可能希望在扫描中使用许多不同的 Nmap 选项来获取所需的结果。接下来的章节将介绍 Nmap 中可用的一些常用选项和扫描类型。

### Nmap 扫描类型

以下章节涵盖了一些最常用的 Nmap 扫描选项。这些扫描技术将在后续章节中讨论特定场景。

### TCP 连接扫描 (`-sT`)

TCP 连接扫描实际上利用了底层操作系统的网络机制，与被扫描的目标设备建立完整的 TCP 连接。因为它创建了完整的连接，所以会产生更多的流量（因此运行时间更长）。这是在 `nmap` 命令中未指定扫描类型时使用的默认扫描类型。然而，通常只在无法使用 SYN 扫描时使用它，例如当运行 `nmap` 命令的用户在操作系统上没有原始数据包权限时，因为许多 Nmap 扫描类型依赖于写入原始数据包。本节说明了 TCP 连接扫描的工作原理，并提供了一个来自 Kali Linux 系统的扫描示例。表 3-3 定义了 TCP 连接扫描的响应。

**表 3-3** TCP 连接扫描响应

| Nmap 报告的端口状态 | 目标的响应 | Nmap 分析 |
| --- | --- | --- |
| Open (开放) | TCP SYN-ACK | 服务正在端口上监听。 |
| Closed (关闭) | TCP RST | 服务未在端口上监听。 |
| Filtered (过滤) | 目标无响应 | 端口受防火墙保护。 |

图 3-9 展示了 TCP 连接扫描的工作原理。示例 3-20 显示了完整 TCP 连接扫描的输出。

![FIGURE 3-9 TCP 连接扫描插图](img/03fig09.jpg)

**图 3-9** TCP 连接扫描插图

**示例 3-20** Nmap TCP 连接扫描示例输出

点击此处查看代码

```
[root@websploit] ~
# nmap -sT 192.168.88.251
Starting Nmap 7.80 ( https://nmap.org ) at 2021-06-21 12:48 EDT
Nmap scan report for 192.168.88.251
Host is up (0.00024s latency).
Not shown: 992 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
139/tcp  open  netbios
445/tcp  open  microsoft
3306/tcp open  mysql
8888/tcp open  sun
9000/tcp open  zeus
MAC Address: 1E:BD:4F:AA:C6:BA (Unknown)

Nmap done: 1 IP address (1 host up) scanned in 0.16 seconds
```

示例 3-20 中的输出显示了 TCP 连接扫描的结果。如你所见，结果表明目标上有多个 TCP 端口正在监听，这些结果与示例 3-19 非常相似。完整的 TCP 连接扫描要求扫描器每次扫描发送一个额外的数据包，这增加了网络噪声并可能触发报警。安全工具和底层系统、入侵检测系统（IDS）同样可能对来自同一主机的 TCP 连接触发报警。

**提示**

Nmap 对每个协议只扫描 1000 个常用端口。你可以使用 `-p` 选项指定要扫描的额外端口。你可以从 `https://nmap.org/book/port-specification.html` 获取有关端口规范和扫描的更多信息。我还创建了一个包含所有选项的 Nmap 备查表，可以在我的存储库中找到：`https://github.com/The-Art-of-Hacking/h4cker/blob/master/cheat_sheets.md`。

### UDP 扫描 (`-sU`)

大多数情况下，你将扫描 TCP 端口，因为这是连接到大多数运行系统的服务的方式。然而，你可能会遇到某些需要扫描 UDP 端口的情况——例如，如果你正在尝试枚举 DNS、SNMP 或 DHCP 服务器。这些服务使用 UDP 进行客户端和服务器之间的通信。要扫描 UDP 端口，Nmap 向命令行配置中指定的所有端口发送 UDP 数据包。它等待目标的响应。如果收到来自目标的 ICMP 不可达（unreachable）消息，该端口被标记为关闭。如果未从目标端口收到响应，Nmap 将该端口标记为 `open/filtered`（开放/过滤）。表 3-4 显示了 UDP 扫描响应。

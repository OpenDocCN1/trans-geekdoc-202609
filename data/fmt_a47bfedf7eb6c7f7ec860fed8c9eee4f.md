
你对知道哪些风力涡电机具有可访问的 IP 地址感兴趣吗？问 Shodan。想知道哪些 Elasticsearch 或 MongoDB 数据库可以在没有密码的情况下访问？想知道哪些摄像头或家用路由器仍在使用默认密码？Shodan 拥有这些答案。

> 注意：Shodan 提供的免费查询次数有限，如果你想能够进行更多搜索并执行诸如通过 API 批量下载数据列表等酷操作，你需要付费访问。

Shodan 的搜索设计非常出色，并提供了使用高级搜索操作符（dorks）快速搜索特定目标的能力。以下是你在使用 Shodan 时使用的基础过滤器：

- `city`: 查找特定城市的设备
- `country`: 查找特定国家的设备
- `geo`: 使用地理坐标
- `hostname`: 查找匹配特定主机名的设备
- `net`: 根据 IP 或 CIDR 搜索
- `OS`: 根据操作系统进行搜索
- `port`: 查找特定端口
- `before/after`: 查找时间范围内的结果
- `Org`: 搜索特定的组织名称

我们可以这样搜索特定的组织：

```
Org: Company Name
```

要将 Pepsi 作为组织搜索，我们可以使用以下搜索：

```
Org: Pepsi
```

如果使用 org 搜索参数范围太广，我们可以尝试通过查找具有特定主机名的任何结果来缩小搜索（见图 3.8）：

```
Hostname:pepsi.com
```

这为我们提供了 28 个与 `pepsi.com` 相关的结果，这是一个很好的开始。如果你无法在 Shodan 中搜索特定的主机名，或者你只是想做得更彻底一些，可以尝试搜索一个域的 IP。

在 `cyper.org` 的情况下，主机名搜索返回 0 个结果。我们可以使用 `Dig` 快速找到与 `cyper.org` 关联的 IP：

```
root@OSINT: dig cyper.org

>>> DIG 9.10.6 <<< cyper.org
```

# 第 3 章 手动网络探索

```
global options: +cmd
;; Got answer:
;; --HEADER<< opcode: QUERY, status: NOERROR, id: 127771
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1
```

```
; OPT PSEUDECTION:
; EDNS version: 0, flags; udp: 4096
; QUESTION SECTION:
; cyper.org
		IN		A

;; ANSWER SECTION:
cyper.org		3155		IN		A		162.210.102.59
```

| TOTAL RESULTS |
| :--- |
| 28 |
| TOP COUNTRIES |
| Uzbekistan | 14 |
| Pakistan | 12 |
| Guatemala | 2 |
| TOP SERVICES |
| SMTP | 2 |
| POP3 + SSL | 2 |
| IMAP + SSL | 2 |
| HTTPS | 2 |
| IMAP | 2 |

```
图 3.8
```

现在让我们检查 Shodan 上基于该 IP 的任何命中（也称为反向 DNS 查询）。此输出中没有子域名；相反，我们获得了来自此 IP 的大量元数据，包括其他关联域名。

我们将在本书的第二部分（网站信息收集）中更详细地讨论反向 DNS (`RDNS`) 查询——特别是在查看域名时。顾名思，反向 DNS 查询获取一个 IP 地址并返回与该 IP 关联的所有域名。

## Censys（子域名查找）

`Censys.io` (`www.censys.io`) 是与 Shodan 非常相似的服务，两者都提供了连接到互联网的可见性。像 Shodan 一样，Censys 是一个帮助组织了解他们在互联网上暴露了哪些服务器和设备的工具。`Censys.io` 可用于搜索特定网络上的资产，甚至发现可能被员工创建并忘记的主机。开放基础设施的发现是渗透测试中非常重要的一部分，因为它识别了开放端口或信息泄露源。

在我看来，Shodan 和 `Censys.io` 的主要区别在于 Censys 提供历史数据。这些数据需要付费，因为 Censys 比 Shodan 贵。尽管如此，在我们讨论潜在调查途径时，你会发现历史数据可以是整个调查的基础。

## Censys 子域名查找

`Censys Subdomain finder` (`https://github.com/christophe/censys-subdomain-finder`) 是一个易用的命令行工具，使用 Censys API 返回可用子域名列表。我的结果在 Shodan 和 Censys（或任何其他子域名研究工具）之间经常会有，这是快速查询 Censys 以检查额外命中的绝佳方法。

对于技术背景的读者，该脚本使用证书透明度 (`CT`) 日志查询 Censys 获取可用子域名列表。证书透明度日志非常神奇，可以用于多种类型的归因。我们将在第 10 章更详细地介绍 CT。

通过我们的两个示例，首先对 `pepsi.com` 的搜索显示了 42 个唯一的子域名：

```
root@OSINT: python censys_subdomain_finder.py pepsi.com
```

- 正在 Censys 查找 `pepsi.com` 的子域名
- 在 1.4 秒内发现了 42 个 `pepsi.com` 的唯一子域名

接下来，让我们搜索 Cypher：

```
root@OSINT: python censys_subdomain_finder.py cypher.org
```

- 正在 Censys 查找 `cypher.org` 的子域名
- 未找到任何子域名

`Sublist3r` 包含以下选项：

- `dns`: DNS 服务器
- `domain`: 要搜索的域名
- `file`: 输出到文件
- `fierce`: 子域名破解
- `delay`: 之间的等待时间
- `nmap`: 使用 nmap
- `p`: 扫描端口列表
- `range`: 范围
- `threads`: 线程
- `t`: 并线程数
- `v`: 详细模式
- `e`: 指定使用哪些搜索引擎
- `b`: 启用暴力破解模块
- `d`: 要搜索的域名
- `o`: 输出到文件

`Sublist3r` 不需要大量的配置或调优。你只需要使用标准的 `-d` 选项搜索一个域名并让它发挥魔法：

```
root@OSINT: python sublist3r.py -d pepsi.com

[-] 正在枚举 pepsi.com 的子域名

[-] 正在在百度中搜索..

[-] 正在在雅虎中搜索..
```

## 第一部分 网络探索

你对知道哪些风力涡电机具有可访问的 IP 地址感兴趣吗？问 Shodan。想知道哪些 Elasticsearch 或 MongoDB 数据库可以在没有密码的情况下访问？想知道哪些摄像头或家用路由器仍在使用默认密码？Shodan 拥有这些答案。

> 注意：Shodan 提供的免费查询次数有限，如果你想能够进行更多搜索并执行诸如通过 API 批量下载数据列表等酷操作，你需要付费访问。

Shodan 的搜索设计非常出色，并提供了使用高级搜索操作符（dorks）快速搜索特定目标的能力。以下是你在使用 Shodan 时使用的基础过滤器：

- `city`: 查找特定城市的设备
- `country`: 查找特定国家的设备
- `geo`: 使用地理坐标
- `hostname`: 查找匹配特定主机名的设备
- `net`: 根据 IP 或 CIDR 搜索
- `OS`: 根据操作系统进行搜索
- `port`: 查找特定端口
- `before/after`: 查找时间范围内的结果
- `Org`: 搜索特定的组织名称

我们可以这样搜索特定的组织：

```
Org: Company Name
```

要将 Pepsi 作为组织搜索，我们可以使用以下搜索：

```
Org: Pepsi
```

如果使用 org 搜索参数范围太广，我们可以尝试通过查找具有特定主机名的任何结果来缩小搜索（见图 3.8）：

```
Hostname:pepsi.com
```

这为我们提供了 28 个与 `pepsi.com` 相关的结果，这是一个很好的开始。如果你无法在 Shodan 中搜索特定的主机名，或者你只是想做得更彻底一些，可以尝试搜索一个域的 IP。

在 `cyper.org` 的情况下，主机名搜索返回 0 个结果。我们可以使用 `Dig` 快速找到与 `cyper.org` 关联的 IP：

```
root@OSINT: dig cyper.org

>>> DIG 9.10.6 <<< cyper.org
```

```
global options: +cmd

;; Got answer:

;; --HEADER<< opcode: QUERY, status: NOERROR, id: 127771

;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1
```

```
; OPT PSEUDECTION:

; EDNS version: 0, flags; udp: 4096

; QUESTION SECTION:

; cyper.org

		IN		A

;; ANSWER SECTION:

cyper.org		3155		IN		A		162.210.102.59
```

| TOTAL RESULTS |
| :--- |
| 28 |
| TOP COUNTRIES |
| Uzbekistan | 14 |
| Pakistan | 12 |
| Guatemala | 2 |
| TOP SERVICES |
| SMTP | 2 |
| POP3 + SSL | 2 |
| IMAP + SSL | 2 |
| HTTPS | 2 |
| IMAP | 2 |

```
图 3.8
```

现在让我们检查 Shodan 上基于该 IP 的任何命中（也称为反向 DNS 查询）。此输出中没有子域名；相反，我们获得了来自此 IP 的大量元数据，包括其他关联域名。

我们将在本书的第二部分（网站信息收集）中更详细地讨论反向 DNS (`RDNS`) 查询——特别是在查看域名时。顾名思，反向 DNS 查询获取一个 IP 地址并返回与该 IP 关联的所有域名。

## Censys（子域名查找）

`Censys.io` (`www.censys.io`) 是与 Shodan 非常相似的服务，两者都提供了连接到互联网的可见性。像 Shodan 一样，Censys 是一个帮助组织了解他们在互联网上暴露了哪些服务器和设备的工具。`Censys.io` 可用于搜索特定网络上的资产，甚至发现可能被员工创建并忘记的主机。开放基础设施的发现是渗透测试中非常重要的一部分，因为它识别了开放端口或信息泄露源。

在我看来，Shodan 和 `Censys.io` 的主要区别在于 Censys 提供历史数据。这些数据需要付费，因为 Censys 比 Shodan 贵。尽管如此，在我们讨论潜在调查途径时，你会发现历史数据可以是整个调查的基础。

## Censys 子域名查找

`Censys Subdomain finder` (`https://github.com/christophe/censys-subdomain-finder`) 是一个易用的命令行工具，使用 Censys API 返回可用子域名列表。我的结果在 Shodan 和 Censys（或任何其他子域名研究工具）之间经常会有，这是快速查询 Censys 以检查额外命中的绝佳方法。

对于技术背景的读者，该脚本使用证书透明度 (`CT`) 日志查询 Censys 获取可用子域名列表。证书透明度日志非常神奇，可以用于多种类型的归因。我们将在第 10 章更详细地介绍 CT。

通过我们的两个示例，首先对 `pepsi.com` 的搜索显示了 42 个唯一的子域名：

```
root@OSINT: python censys_subdomain_finder.py pepsi.com
```

- 正在 Censys 查找 `pepsi.com` 的子域名
- 在 1.4 秒内发现了 42 个 `pepsi.com` 的唯一子域名

接下来，让我们搜索 Cypher：

```
root@OSINT: python censys_subdomain_finder.py cypher.org
```

- 正在 Censys 查找 `cypher.org` 的子域名
- 未找到任何子域名

# 第 3 章 手动网络探索

`Sublist3r` 包含以下选项：

- `dns`: DNS 服务器
- `domain`: 要搜索的域名
- `file`: 输出到文件
- `fierce`: 子域名破解
- `delay`: 之间的等待时间
- `nmap`: 使用 nmap
- `p`: 扫描端口列表
- `range`: 范围
- `threads`: 线程
- `t`: 并线程数
- `v`: 详细模式
- `e`: 指定使用哪些搜索引擎
- `b`: 启用暴力破解模块
- `d`: 要搜索的域名
- `o`: 输出到文件

`Sublist3r` 不需要大量的配置或调优。你只需要使用标准的 `-d` 选项搜索一个域名并让它发挥魔法：

```
root@OSINT: python sublist3r.py -d pepsi.com

[-] 正在枚举 pepsi.com 的子域名
[-] 正在在百度中搜索..
[-] 正在在雅虎中搜索..
```

# 第3章 手动网络探索 59

```
[-] 正在 Google 中搜索..
[-] 正在 Bing 中搜索..
[-] 正在 Ask 中搜索..
[-] 正在 Netcraft 中搜索..
[-] 正在 DNSstumpter 中搜索..
[-] 正在 Virustotal 中搜索..
[-] 正在 ThreatCrowd 中搜索..
[-] 正在 SSL Certificates 中搜索..
[-] 正在 PassiveDNS 中搜索..
[-] 发现唯一子域名总数：5
```

这个初始查询从 `pepsi.com` 返回了数百个子域名。让我们用我们的第二个目标尝试相同的命令：

```
root@CSINT: python sublist3.py -d cypher.org

www.cypher.org
office.cypher.org
seek.cypher.org
storm.cypher.org
zone.cypher.org
```

[-] 发现唯一子域名总数：5

现在我们已经看到了一些可以使用传统方法获取子域名列表的 GUI 和命令行工具。让我们更进一步，尝试暴力破解。

## Enumall

`Enumall` 是由 Jason Haddix 创建的一个脚本，用于通过单个命令执行详尽的子域名发现。`Enumall` 的设计目的是实现你在本章中使用 `recon-ng` 引擎看到的所有操作：

- 枚举子域名
- 在 Google、Bing、Yahoo 和 Netcraft 中搜索
- 将所有活动地址解析为 IP 地址
- 将所有内容输出为整洁的 CSV 文件

在运行脚本之前，你应该了解这些参数：

- `-a`: 使用 `altdns` 根据种子列表创建单词的排列
- `-p`: 我们想要提供给 `altdns` 的种子列表
- `-w`: 在暴力破解时配合 `recon-ng` 使用的自定义字典列表

> 注意 使用 `altdns` 选项对于你想要执行的测试水平来说可能过度了。这将创建数百万个可能的排列，并花费很长时间才能完成（数小时）。在大多数情况下，使用标准字典 `-w` 可能足够了。如果不是，你也可以尝试不同的字典。让我们针对 `pepsi.com` 运行我们的脚本：

```
root@OSINT: python enumall.py pepsi.com -a ../altdns/words.txt -w /SecLists/sortedcombined-knock-dns-fierce.txt
```

[*] 发现 78 个主机（51 个新的）。16 条记录已添加到 '/opt/recon/domain/pepsi.com.csv'。

```
root@OSINT: python enumall.py cypher.org -a ../altdns/words.txt -w /SecLists/sortedcombined-knock-dns-fierce.txt
```

[*] 发现 5 个主机（5 个新的）。6 条记录已添加到 '/opt/recon/domain/cypher.org.csv'。

## 结果

表 1.1 显示了我们使用的不同工具的结果。

表 1.1: 子域名搜索结果

| 使用的工具 | PEPSI.COM | CYPHER.ORG |
|---|---|---|
| DNSDumpster | 19 | 1 |
| Hacker Target | 31 | 5 |
| Shodan | 28 | 0 |
| Censys | 42 | 0 |
| Fierce | 6 | 4 |
| Sublist3r | 56 | 5 |
| Enumall/Recon-ng | 78 | 5 |

如果你从这一章中学到了什么，那应该是并不是每个工具都是完美的，而且每个工具经常会给你不同的（或不断变化的）结果。你应该始终使用工具箱中的所有工具。`Enumall` 这样的脚本非常棒，因为它们会使用多个工具为你提供尽可能的结果。

## 钓鱼域名和域名抢骗（Typosquatting）

域名抢骗（Typosquatting）是一种注册与原始/合法域名看起来相似的假名称的技术。这其实是“拼写错误的 URL”的一种高级说法。攻击者会利用人们在输入时会犯拼写错误的事实，并以收集凭据、分发恶意软件或进行其他活动为目的注册假域名。攻击者经常在钓鱼邮件中使用错误域名引导人们点击链接。

> 注意 同形字符（Homoglyphs）在钓鱼攻击中也非常流行。这些字符与原始字母中的字符看起来非常相似。例如，查看 `pepsi.com` 和 `pep.com`，你能一眼看出“i”是不同的。

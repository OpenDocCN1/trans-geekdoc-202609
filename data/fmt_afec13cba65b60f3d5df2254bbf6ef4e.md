
| d.root-servers | 192.33.4 | University of California |
| e.root-servers | 192.53.244.100 | Internet Systems |
| f.root-servers | 199.7.27.33 | RIPE NCC |
| g.root-servers | 199.9.83.42 | ICANN |
| h.root-servers | 198.97.190.5 | U.S. Army (Research Lab) |
| i.root-servers | 192.36.148.17 | Netnod |
| j.root-servers | 198.51.100.30 | Verisign, Inc. |
| k.root-servers | 193.0.141.129 | Department of Defense |
| l.root-servers | 199.9.10.130 | Verisiana |
| m.root-servers | 202.12.27.33 | WIDE Project |

F 根服务器不会为你的 ISP 提供请求域名（`duckduckgo.com`）的地址。相反，它指向指向顶级域名的方向——返回负责 `.com` 的名称服务器的 IP 地址。你的 ISP 将查询该名称服务器并收到响应。这不是最终答案——它将是 `duckduckgo.com` 的名称服务器的 IP 地址，恰好是 `ns-175.awdns-21.com`。你的 ISP 向此服务器发送最终查询并收到访问 `duckduckgo.com` 所需的 IP 地址。该地址通过路由器的 DNS 服务器返回给你的计算机。你的 ISP 将缓存所有这些结果以供下次访问 `duckduckgo`，你的路由器和本地机器也是如此。如果你请求 `duckduckgo.com` 的子域名，例如 `news.duckduckgo.com`，你的计算机已经知道了拥有答案的名称服务器地址。这加速了对同一域名的后续查询，并减轻了全球 DNS 的整体压力。

### 权威与区域

名称服务器对域名系统中的特定子部分具有权威性；换句话说，它们为特定空间内的域名查询提供答案，并针对该空间。在上一个例子中，DNS 解析了对 `duckduckgo.com` 的查询。只有一个被称为 `duckduckgo.com` 权威起始（SOA）的名称服务器可以为该查询提供确定性的答复。你的互联网服务提供商（ISP）可能有答案，但前提是它已经进行了检查并缓存了结果。

你家庭路由器的名称服务器——即你日常 DNS 需求所使用的那个——理想情况下不应该是权威名称服务器。它不应该对任何区域拥有权威性，因为它的用途不同。它的工作是代表你在互联网上执行 DNS 查询。它是一个递归名称服务器——它会查询其他名称服务器，直到找到你查询的答案，并在过程中保存获取的所有答案。

`duckduckgo.com` 的 SOA 负责 `duckduckgo.com` 空间内的域名。它无法为 `plus.google` 或任何其他域名查询提供答案，因为它对 `google.com` 空间不具权威性。`.com` 的 SOA 是 `nsl.google.com`。`.com` 名称服务器对 `.com` 空间具有权威性，无法回答对 `.net` 空间的查询。

实际上，像 Google 这样的公司会有多个名称服务器，但这是为了冗余；它们执行相同的工作，因此都被视为 SOA。它们通常命名为 `ns1`、`ns2` 等。如果一个名称服务器离线，下一个服务器将接替它处理查询。DNS 内部的空间或名称空间也被称为权威区域（zones of authority）或简称区域（zones）。

DNS 是分级结构的，顶端是按树形结构组织的根服务器。这些服务器将权威授权给下方的名称服务器，即负责 `.com`、`.org` 等顶级域名（TLD）服务器，而这些服务器又将其传递给更低级。小型组织和个人没有自己的名称服务器，相反他们将此项工作外包给拥有名称服务器的公司，很可能是他们的网络托管公司。图 5.2 显示了 DNS 层级结构如何划分为区域。

### DNS 资源记录

域名系统是一个数据库，尽管它被拆分并存储在全球无数机器上。事实上，从理论上讲，由于其去中心化和分布式特性，没有任何单一实体应该能够控制它。如果 DNS 是一个数据库，那么它的数据在哪里，这些数据又是如何存储的？此外，你——无论是普通用户还是黑客——如何获取其访问权限？

### 域名空间

![](img/46e491ee87887ca9f9393b757b453bb7_120_0.png)

NS RR（“资源记录”）指定了对委托区域具有权威性的名称服务器

- “被委托子区域”
- 资源记录 = 与名称关联

当系统管理员想让另一个管理员管理区域的一部分时，第一个管理员的名称服务器会在稍后将区域的部分委托给另一个名称服务器。

- 由名称服务器管理的权威区域
- 另请参见：RFC 1034 4.2：数据库如何被划分为区域。

**图 5.2:** DNS 区域

来源：维基百科

存储在 DNS 中的数据被称为*资源记录*

- **主机地址 (A 记录)**：主机的 IP 地址；例如，`123.45.67.89`。这通常是你在发送包含主机名的查询（例如 `google.com`）时所请求的信息。
- **主机地址 (AAAA 记录)**：与上述类似，但这是一个 IPv6 地址而非 IPv4 地址。
- **规范名称 (CNAME)**：别名的另一种术语。一个公司可能有两个指向相同位置域，在这种情况下，其中一个就是别名。查询此记录中域名的任何人都将获得 A 记录。
- **邮件交换器 (MX)**：指一个邮件服务器，可以是主机名（如 `mail.google.com`）也可以是 IP 地址。
- **名称服务器 (NS)**：包含区域的名称服务器信息。
- **权威起始 (SOA)**：此记录比其他记录都大，可以在每个区域文件的开头找到。它包含了该区域的主名称服务器和其他一些信息。
- **指针 (PTR)**：指针记录用于 DNS 中的反向查找。这意味着你可以通过提供 IP 地址来查找主机名。当你不知道主机名并使用 IP 地址进行反向查找时，这非常有用。
- **文本 (TXT)**：这仅仅是一个文本记录。它们用于为 DNS 添加额外功能和一些杂项信息。管理员有时使用它们留下人类可读的注释。

很快将解释访问这些记录的方法，但首先查看运行在名称服务器上的软件以及可能配置的内容是有用的。伯利互联网名称域（BIND）是互联网上最广泛使用的 DNS 软件，存在多个版本（`BIND4`、`BIND8` 和 `BIND9`）。由于其广泛的使用和重要性，这（以及其他 DNS 软件）被视为关键代码。20 世纪 90 年代后期（在发现有人黑入名称服务器后），曾投入过很大精力寻找漏洞并修复 BIND 代码。该软件通过新的错误处理代码进行了审计和审查。如果你尝试阅读它，代码可能会让你眼睛流血。

- BIND
- DJBDNS
- PowerDNS
- MaraDNS
- MSDNS
- DNSmasq
- BIND

### BIND

你可能想设置自己的 DNS 服务器。在确定它足够安全之前，建议不要将自己的名称服务器暴露在网上。为什么不下载一个 Ubuntu Server (`ubuntu.com/download/server`) 或 Debian (`debian.org/distrib`) 并将其安装到虚拟机中？一旦运行，你可以从终端以 root 用户身份安装：`apt install bind9` 或任何其他包。本书提供的实验环境（`www.hackerhouse.com/hh-lab-vl-1386.io`）已经运行着一个 BIND 服务器，所以如果你不想这样做，就不需要遵循下面的步骤。

BIND 的 DNS 配置存储在 `/etc/bind/named.conf` 中，这是主配置文件，让我们来看看。注意 `named` 是守护进程，读作 "name dee"。

```bash
cd /etc/bind
named.conf
```

你应该看到此文件简单地指向（或包含）其他文件。其中一个是 `named.conf.local`。你可以打开它编辑并创建一个新区域。

```bash
vim named.conf.local
```

向文件中追加以下内容：

```
zone mydomain.com
{
    type master;
    file "/etc/bind/db.mydomain.com";
};
```

此文件指向一个不存在的文件，因此如下所示创建它：

```
vim db.mydomain.com
```

编辑此文件包含以下内容。注意开头的 SOA 记录和包含 IP 地址的 A 记录。这些是内部 IP 地址，因为此名称服务器实际上不会被公开访问。此文本的其他元素将在稍后解释。

```
$TTL 60400 IN SOA mydomain.com. root.mydomain.com. (
    2 ; Serial
    60400 ; Refresh
    86400 ; Retry
    2419200 ; Expire
    604800 ; Negative TTL
)
 A 10.10.10.10
```

# 第96 页 第5章 域名系统

```
@ IN A 10.10.10.10
@ IN AAAA ::1
@ IN NS ns.mydomain.com.
s IN A 10.10.10.10
```

虽然从上一个例子中并不容易一眼看出，但这样的区域文件只是一个使用空格作为分隔符的记录表。如果我们将当前文件以格式良好的表格形式呈现，它看起来就像表 5.1 所示。

表 5.1: 格式良好的 DNS 区域文件

| 节点 | TTL | 记录类 | 记录类型 | 记录数据 |
|---|---|---|---|---|
| @ | | IN | SOA | mydomain.com (2604800 86400 2419200 640800 ) |
| | | IN | A | 10.10.10.10 |
| @ | | IN | NS | ns.mydomain.com |
| @ | | IN | A | 10.10.10.10 |
| @ | | IN | AAAA | ::1 |
| ns | | IN | A | 10.10.10.10 |

注意 `$64800` 位于表格之前。这设置了文件中所有记录的全局 TTL 值。TTL 设置了资源记录的过期时间（单位为秒），并决定了缓存服务器何时应该丢弃记录并获取新记录。这允许 DNS 更新新的主机名、IP 地址等。

以下是文件和表 5.1 中其他字符和缩写含义的解释：

- `-` 此字符用于注释。
- `@` 此字符用于表示区域源（zone origin）。如果你在文件中使用 `ORIGIN` 指定了区域源，那么 `@` 符号将被替换为该值。由于没有指定 `ORIGIN`，它将取自 `named.conf` 中的区域名称，在我们案例中是 `mydomain.com`。（你在文件中指定了 `named.conf.local`，它被包含在 `named.conf` 中。）
- **名称**：这是映射到记录数据字段中给出的地址的名称。当有空格时，名称将从上一行复制。在本文件中，第二行中的空格（代表 `mydomain.com`）被映射到 `10.10.10.10`。

# 第5章 ■ 域名系统 97

**记录类 (Record Class)** 这通常是 IN，代表 Internet（互联网）。另一个正在使用的类是 CH，它是 CHAOS 的缩写。稍后将进一步讨论 CHAOS 类。

**记录类型 (Record Type)** 这些在本章的上一节中已经过。在上一个例子中，你可以看到 SOA、A、NS 和 AAAA 分别代表权威起始、IPv4 地址、名称服务器和 IPv6 地址。

**记录数据 (Record Data)** 这取决于记录的类型，但它通常是一个 IP 地址或主机名。我们表格中的第一条记录（SOA 记录）包含一些额外信息，以 `root.mydomain.com..` 开始。这实际上是一个电子邮件地址，应该被视为 `root@mydomain.com`。括号内的值分别代表文件的序列号、刷新时间、重试时间、过期时间和负缓存 TTL。

**序列号 (Serial Number)** 每当更新区域文件时，都需要增加此值。使用此作为序列号很常见，但在上一个例子中使用了 2。

你会注意到其中一条记录是 NS 类型。名称服务器的主机名设置为 `ns.mydomain.com`。还有另一个名为 `ns` 的名称，它实际上提供了名称服务器的 IP 地址。此类文件中可能包含的其他名称还包括 `vpn`、`ns1` 和 `ns2`，作为可以被猜测的可预测值的几个例子。

现在你已经对此区域文件进行了更改并对其进行了探索，你应该重启 BIND（更具体说是重启 BIND9）以便你的更改生效。

```
systemctl restart bind9.service
```

此时，你可以使用 Dig（域名信息探路器）来测试你的配置，该工具将在本章中被广泛使用。你应该从服务器本身运行 dig，该服务器不应连接到互联网。这意味着 Dig 将查询你的名称服务器，而不是寻找真实的 `mydomain.com`。

```
dig mydomain.com.
```

你应该看到状态为 `NOERROR`，以及包含你在文件中包含的细节的 `ADDITIONAL SECTION`（附加部分）。你还会注意到查询的服务器是端口 53 的 `127.0.0.1`，即你的本地机器。现在你已经设置好了基础的名称服务器，你可能想扩展它，或者你可能准备好查看一些它可以被攻击的方法。

## DNS 攻击工具包

这里是本章将用于演示 DNS 攻击技术的工具。所有这些工具都是免费获取的。

- Dig: 用于查询工具
- lookup: 用于查询工具
- dnsrecon: 用于侦察的脚本
- dnsenum: 用于枚举的工具
- Host: 用于查询信息的工具
- whois: 用于查询域名的工具
- WHOIS: 用于查询域名和 IP 地址信息的协议
- DNSspoof: 用于伪造 DNS 的工具
- Dsniff: 用于嗅探数据包的工具（此处为意译）
- Hping3: 在许多场景下用于创建和注入数据包的工具
- Scapy: 数据包工具
- Nmap: 扫描器
- Metasploit: 渗透测试框架
- Wireshark: 检查数据包的工具

## 查找主机

在开始攻击之前，你需要知道它在哪里。你会发现名称服务器提供。这种特定的活动是可以执行的。

## WHOIS

WHOIS 是一种用于查询域名和 IP 地址信息的协议。你会发现名称服务器提供关于目标的信息。你会发现名称服务器提供。此工具查询公共资源。尝试查找某些，例如：

```
whois hacker.house
```

你可能会发现一些记录被隐藏了。以下是 `hacker.house` 的片段：

```
Domain Name: hacker.house
Registry Domain: 352bd55d678452ad6625394453af0d
Registrar WHOIS Server: tows.com
Registrar URL: http://www.tucows.com
Updated Date: 2018-08-08T16:19:43Z
Creation Date: 2015-09-02T15:36:01Z
Expiry Date: 2019-09-02T15:36:01Z
Registrar: Tucows Domains Inc.
Registrar IANA ID: 69
Registrar Abuse Contact Email:
Registrar Abuse Contact Phone:
Domain Status: clientTransferhibited
https://icann.org/help#clientTransferhibited
Domain Status: clientUpdatehibited
https://icann.org/help#clientUpdatehibited
Registry Registrant ID: REDACTED FOR PRIVACY
Name Server: ns3.livedns.co.uk
Name Server: ns1.livedns.co.uk
Name Server: ns2.livedns.co.uk
```

最后，你可以发现列出了三个服务器。是的，就如此简单；名称服务器很难与 `hacker.house` 域名关联。

> **提示** 获取信息（如主机名）的一种方法就是直接猜测它们。更好的方法是进行大量的推测。换句话说，你可以通过暴力破解来获取信息。暴力破解这个术语在书中经常出现，通常指猜测密码。无论你是在破解用户名、密码、域名还是主机名，其概念都是相同的。对于主机名来说，这种方法几乎可以产生结果。人们在命名域名和子域名时倾向于使用可预测的规则。你会发现许多具有以下子域示例：
>
> ```
> mail.example.com
> firewall.example.com
> webserver.example.com
> vpn.example.com
> www.example.com
> web.example.com
> webmail.example.com
> ```

## 使用 Recon-ng 对主机进行暴力破解

寻找主机列表（包括名称服务器）的一种方法是对它们进行暴力破解或枚举。在理想情况下，这将揭示出一个主机或子域名的列表，例如 `mail.example.com`、`vpn.example.com` 和 `ns1.example.com`。`ns` 是表示名称服务器的常见方式，而且为了冗余考虑，通常会有多个名称服务器。

Recon-ng 中的 `brute_hosts` 模块提供了一种枚举主机的方法，并且应该针对真实的域名使用它，以最有效地演示其功能。如果想的话，可以使用 `hacker.house` 作为目标。打开上一章中的 Recon-ng，并选择 `brute_hosts` 模块。

```
modules load recon/domains-hosts/brute_hosts
```

记住，你可以按照以下方式查看模块信息：

```
info
```


-   [存在一些特定的网站，攻击者可以从中获取有用信息。例如，`netcraft.com`，如在 [Figure 6.1](#ch06.xhtml#ch06fig01) 中所示，提供关于网站的信息。例如，你可以查找一个站点运行的是什么类型的服务器，在某些情况下还能知道服务器距离最后一次重启的时间。

![Figure 6.1 www.netcraft.com. ¶  ¶ The site report for the website www.chuckeasttom.com is shown. The information for some of the fields mentioned are site, domain, ip address, country, date first screen, organization, last reboot, netblock owner, site rank, DNS admin, Reverse DNS, Nameserver organization, and so on. The hosting history at the second half of the page displays the netblock owner, IP address, OS, web server, and last changed. ¶ ](Images/06fig01.jpg)

**Figure 6.1** `www.netcraft.com`. ¶ 

另一个对攻击者有用的网站是 [`https://archive.org`](https://archive.org)。该网站，如在 [Figure 6.2](#ch06.xhtml#ch06fig02) 中所示，存档了网站的旧版本。服务器会遍历网络，存档站点。存档频率取决于站点的受欢迎程度。

![Figure 6.2 www.archive.org. ¶  ¶ A window for older archive versions are displayed for the website http://www.chuckeasttom.com. The version is displayed in the form of a calendar from January to August. The frequency distribution with which a site is archived is also given for the year 1996 to 2011 in the form of vertical bars. There is no distribution for the years 1996 to 2000, and 2010. ¶ ](Images/06fig02.jpg)

**Figure 6.2** `www.archive.org`. ¶ 

#### 主动扫描技术

前面提到的技术都是被动的，因为攻击者不需要连接到目标系统。由于攻击者实际上并未连接到目标系统，入侵检测系统（IDS）无法检测到扫描。主动扫描更可靠，但可能会被目标系统检测到。有几种主动扫描类型。

##### 端口扫描

*[Port scanning](#glossary.xhtml#gloss63)* 是尝试向目标系统的每个网络端口发送请求并查看哪些端口是打开的过程。通常有 1024 个众所周知的端口，它们与特定服务相关联。例如，`port 161` 与简单网络管理协议（SNMP）相关联。如果攻击者在目标系统上检测到 `port 161` 打开，他可能会尝试进行 SNMP 相关攻击。即使如此，端口扫描还能提供更多信息。例如，`ports 137, 138, and 139` 都与 NetBIOS 相关联，这是一种老旧的 Windows 网络通信方式，已不再在 Windows 中使用。但 NetBIOS 常用于 Windows 机器需要与 Linux 机器通信的环境，因此发现这些端口打开揭示了目标网络的一些信息。

通过简单的 Google 搜索 *port scanner*，可以发现许多知名、广泛使用且通常免费的端口扫描工具。然而，黑客和安全社区中最流行的端口扫描工具是免费工具 Nmap（[https://nmap.org](https://nmap.org)）。它有一个 Windows 版本，名为 Zenmap，如在 [Figure 6.3](#ch06.xhtml#ch06fig03) 所示。

![Figure 6.3 Zenmap GUI. ¶  ¶ A screenshot for Zenmap Graphical User Interface (GUI) is shown. The target address is mentioned as 127.0.0.1. The profile option has a dropdown list that displays intense scan; intense scan plus UDP; intense scan, no ping; ping scan; quick scan; quick scan plus; quick traceroute; regular scan; and slow comprehensive scan. The option "Intense scan" is selected. There are other tabs for hosts, services, and Nmap output. ¶ ](Images/06fig03.jpg)

**Figure 6.3** Zenmap GUI. ¶ 

Nmap 允许你自定义扫描，使其更隐蔽或更精准地针对特定系统。最常见的扫描类型如下：

*   **Ping scan:** 该扫描仅向目标端口发送 ping。许多网络管理员会阻止入站的 ICMP 包，以阻止 ping 扫描。

*   **Connect scan:** 这是最可靠的扫描方式，但也最容易被检测到。使用此类扫描时，会建立完整的连接到目标系统。

*   **SYN scan:** 该扫描非常隐蔽。大多数系统接受 SYN（同步）请求。该扫描类似于 [Chapter 4](#ch04.xhtml#ch04) “[Denial of Service Attacks](#ch04.xhtml#ch04)” 中描述的 SYN flood DoS 攻击。在该类扫描中，你发送 SYN 包但不在系统返回 SYN/ACK 时回复。与 DoS SYN flood 不同，你每个端口仅发送一个包。这也称为 *half-open scan*。

*   **FIN scan:** 该扫描将 FIN（连接结束）标志置位。该标志在系统中并不罕见，因此被视为隐蔽。

这些扫描会在目标机器上产生不同的响应，从而为端口扫描者提供不同的信息：

*   使用 FIN 扫描或 XMAS 扫描时，如果目标端口关闭，系统会返回 RST（重置）标志包；如果端口打开，则没有响应。

*   使用 SYN 扫描时，如果端口关闭，响应是 RST；如果端口打开，响应是 SYN/ACK。

*   ACK 扫描和 NULL 扫描仅在 UNIX 系统上有效。

Nmap 还允许你通过 Nmap 的命令行版本或 Windows 版本设置多个标志来自定义扫描。允许的标志列表如下：

`-O` 检测操作系统

`-sP` 执行 ping 扫描

`-sT` 执行 TCP 连接扫描

`-sS` 执行 SYN 扫描

`-sF` 执行 FIN 扫描

`-sX` 执行 Xmas tree 扫描

`-sN` 执行 NULL 扫描

`-sU` 执行 UDP 扫描

`-sO` 执行协议扫描

`-sA` 执行 ACK 扫描

`-sW` 执行 Windows 扫描

`-sR` 执行 RPC 扫描

`-sL` 执行列表/DNS 扫描

`-sI` 执行空闲扫描

`-Po` 不执行 ping

`-PT` 执行 TCP ping

`-PS` 执行 SYN ping

`-PI` 执行 ICMP ping

`-PB` 执行 TCP 和 ICMP ping

`-PM` 执行 ICMP netmask

`-oN` 正常输出

`-oX` XML 输出

`-oG` 可grep 输出

`-oA` 所有输出

`-T` 调整时间

`-T0` 隐蔽

`-T1` 偷偷

`-T2` 礼貌

`-T3` 正常

`-T4` 积极

`-T5` 疯狂

如你所见，攻击者使用 Nmap 时有许多选项可供选择。花费大量时间仅学习 Nmap 是可以的。当然，还有其他端口扫描工具。我们专注于 Nmap，因为它免费且广泛使用，并且在 EC-Council Certified Ethical Hacker 认证、GPEN（来自 SANS）以及专业渗透测试师认证中具有重要地位。

Nmap 设置大部分是自解释的。也许关于时间（timing）的讨论需要更多阐述。时间涉及如何快速发送扫描包。基本上，发送包越快，扫描被检测到的可能性就越大。

以下是最基础的 Nmap 扫描：

```
nmap 192.168.1.1
```

以下是扫描 IP 地址范围的命令：

```
nmap 192.168.1.1-20
```

下面的命令用于检测操作系统、使用 TCP 扫描并使用隐蔽速度：

```
nmap -O -PT -T1 192.168.1.1
```

##### 漏洞评估

漏洞评估包括检查系统是否易受特定攻击的影响。虽然黑客可以使用漏洞评估工具来评估你的系统，但这些工具是设计用来让你自行评估系统的。这些工具并不特别隐蔽，因此很可能会被入侵检测系统（IDS）检测到。事实上，网络管理员经常使用漏洞评估工具来测试自己的网络。这些工具将在 [Chapter 11](#ch11.xhtml#ch11) “[Network Scanning and Vulnerability Scanning](#ch11.xhtml#ch11)” 中介绍。

##### 列举



向端口 80 (HTTP) 发送包并向端口 443 (HTTPS) 发送 TCP 包。你可以为基础 nmap 扫描添加多个选项来调优你的环境。为了获得最佳结果，你绝对需要使用管理员凭据来执行这些命令。例如，当你使用管理员凭据扫描网络时，会启用地址解析协议（ARP）。ARP 是一种将 IP 地址映射到主机物理地址（称为媒体访问控制或 MAC 地址）的协议。在 ARP 请求期间创建的表称为 ARP 缓存，它将其主机的网络地址与其物理地址匹配。

要在网段上启动扫描，请使用以下命令：

```
>nmap -sn <target addresses>
```

结果将包含所有对 nmap 发出的探测做出响应的主机。`-sn` 选项禁用了端口扫描，同时保持发现阶段不变。图 3.1 显示了 Nmap 如何进行资产扫描，这意味着你只会看到对发送探测做出响应的活跃主机。大多数管理员发现此选项极其有用，可以快速验证网络上哪些资产处于活跃状态。

![](img/e8e965b6c3537819be0d570febb3fc1d_47_0.png)

> 图 3.1: nmap 命令

定期扫描未通知即加入网络的新资产是非常重要的。变更管理程序没有被遵守，或者在初创企业中情况更糟。新机器可能被添加到网络中而不经过漏洞扫描。

我曾遇到过一种情况：系统管理员会在晚上和周末扫描系统漏洞以避开生产时间。在这一周中，他会在扫描中看到一台服务器弹出。当这个管理员在周一回来时，他无法 ping 通这台服务器。它消失了。这种情况持续了几周，直到他终于找到了问题。其中本该在周末工作的网络支持人员在桌子下放了一台游戏服务器。他们一直在进行局域网大战，而不是修补系统。当他们“工作”结束时，服务器从网络上拔掉了。

## 端口扫描

端口扫描是确定网络上哪些端口是开放的、哪些正在监听的方法，并可能显示发送者和接收者之间是否存在防火墙等安全设备。这个过程被称为指纹识别。端口编号从 0 到 65,535，但 0 到 1,023 的低范围由“已知”端口组成。端口扫描会向每个目标端口构建数据包。根据网络拓扑和扫描目标，有一些基本技术供选择。

- **空扫描 (Null scan)**: 这是最基本的扫描，完全连接 65,536 个端口。它很准确但容易被检测。
- **SYN 扫描 (SYN scan)**: 发送 SYN 但不等待响应。它更快，但你仍然知道端口是否开放。
- **闪电扫描 (Strobe scan)**: 选择性地尝试连接少数端口，通常少于 20 个。

渗透测试人员还会使用其他技术，例如隐身扫描（Stealth）、FTP 射出、XMAS 以及为了让发送者不被检测的情况下进行的扫描。可以隐藏发送者的位置，以便攻击者在获取信息而不被追踪。

现在你知道网络上有一台机器在线，是时候确定主机上哪些端口是开放的。从安全角度来看，了解你的网络健康状况至关重要，以便确切知道 65,536 个端口中的哪些可能暴露在外。Nmap 目前识别六种端口状态。

- **Open（开放）**: 应用程序正在监听连接。
- **Closed（关闭）**: 接收到了探测，但没有应用程序在监听。
- **Filter（过滤）**: 不清楚端口是否开放；通常来自防火墙的数据过滤阻止了探测到达端口。有时你会收到错误，有时过滤器会丢弃探测。
- **Unfiltered（未过滤）**: 端口可访问，但 Nmap 不知道它是开放还是关闭。
- **Open/filtered（开放/过滤）**: 端口被过滤或开放，但状态未建立。
- **Closed/filtered（关闭/过滤）**: Nmap 无法确定端口是关闭还是过滤。

最常用的扫描是 `-sS`，即你在图 3.2 中看到的 SYN 扫描。这是一种快速扫描数千端口的隐身扫描，因为它不需要等待确认。要在网段上启动扫描，请使用以下命令：

```
>nmap -sS <target addresses>
```

```
C:\WINDOWS\system>nmap -sS 192.168.1.0
Starting Nmap scan for 192.168.1.1 at 20:16 Daylight
Host is up (0.004s latency). Nmap scan report for 1000 ports
PORT     STATE SERVICE
53/tcp   open domain
80/tcp   open http
139/tcp  open netbios
445/tcp   open microsoft-ds
515/tcp   open printer
8200/tcp open trivnet
MAC Address: 00:45:CE:D2:08 (Asus Computer)

map scan report for 192.168.1.74
Host is up (0.035s latency). Nmap scan for 901 filtered ports
PORT     STATE SERVICE
111/tcp  open rpbind
180/tcp  open http
139/tcp  open netbios
643/tcp  open https
445/tcp  open microsoft-ds
802/tcp  open secure
9000/tcp open nmap
6646/tcp open unknown
MAC Address: B4:18:5E:26:FC:54 (Giga Technology)
```

图 3.2: Nmap SYN 扫描

## 运行的服务

很久以前，我在科罗拉多斯普林的铁马大学教授 CompTIA 课程。我的士兵们会在教室里进行两周的教学和实操。如果有人想和我的士兵交流，他们就会去 4 号教室。他们需要一个特定的人，这样他们就可以去那里交流。例如，假设士兵的名字是 Carla，坐在 23 号位置。那么 Carla 的 socket 就是 23 号教室。socket 是入口或出口点。IP 地址和端口的组合称为端点。socket 是网络上两个程序双向对话的端点之一。socket 绑定端口号，以便知道数据去向哪里。

23 号位置就像向操作系统注册监听那里的程序。如果 Carla 不在怎么办？如果有人坐在 23 号位置呢？监听特定端口的程序可能是常用的监听器。你需要知道 Carla 和 Robert 是否交换了座位。表 3.1 描述了常用端口以及应该运行的服务。

### 表 3.1: 常用端口定义

| 端口编号 | 名称 | 用途 |
|---|---|---|
| 20 | FTP-data | 文件传输协议 | 在客户端和服务器之间移动文件 |
| 21 | FTP-control | 文件传输协议 | 移动文件的控制信息 |
| 22 | SSH | 安全外壳 | 登录和文件传输的安全 |
| 23 | Telnet | Telnet 协议 | 过时的加密通信 |
| 25 | SMTP | 简单邮件传输协议 | 发送/路由电子邮件 |
| 53 | DNS | 域名系统 | 互联网电话簿；将网站名称转换为 IP 地址 |
| 80 | HTTP | 超文本传输协议 | 万维网的基础 |
| 110 | POP3 | 邮局协议 | 通过下载到你的主机接收邮件 |
| 123 | NTP | 网络时间协议 | 同步网络上计算机的时钟 |
| 143 | IMAP | 互联网消息访问协议 | 从任何设备查看邮件；不下载到主机 |
| 161 | SNMP | 简单网络管理协议 | 收集信息并配置不同的网络设备 |
| 443 | HTTPS | 超文本传输安全 | HTTP 的安全版本；浏览器和网站之间的信息已加密 |
| 445 | Microsoft | 目录服务 | IP 之 SMB；Windows 文件共享的首选端口 |
| 465 | SMTPS | 安全 SMTP | SSL 之上的身份验证 SMTP |
| 1433 | MSSQL | Microsoft SQL | SQL 数据库管理系统 |
| 3389 | RDP | 远程桌面协议 | 应用程序共享协议 |

这些通常在那些端口上运行的服务。根据我的经验，网络管理员通常很有主见，他们对企业环境中服务的配置方式有自己的想法，有时这种数据库（中的记录）与现实情况是不符的。如果你正在进行资产盘点或漏洞管理，你希望尽可能准确，并尽可能地了解系统的版本号和补丁水平。

版本检测 `nmap-services-probes` 数据库包含了用于发现服务并将其与响应进行匹配的探测包（Probe Packets）。Nmap 将尝试确定服务、应用程序、版本号、主机名、设备类型和操作系统。

## 操作系统

Nmap 常用于检测机器的操作系统。能够正确识别操作系统对于许多原因至关重要，包括资产盘点、发现漏洞以及特定的利用程序。Nmap 以拥有最稳健、最全面的指纹数据库而闻名。

在识别操作系统时，关键在于操作系统如何响应 Nmap 探测包。Windows XP 和 Windows Server 2003 的表现几乎完全相同，而 Windows Vista 和 Ubuntu Linux 16 在响应方式上则完全不同。在图 3.4 中，你可以看到 `nmap -O` 命令的响应。要启用操作系统检测，请参考以下命令：

```
C:\Users\Admin>nmap -O 192.168.1.97
Starting Nmap 7.70 ( https://nmap.org ) at 2018-09-16 22:08 Mountain Daylight Time
Host is up (0.00052 latency).
Not shown: 991 closed ports
port state
513 open
80/tcp open http
111/tcp open rpbind
139/tcp open netbios-ssn
443/tcp open https
445/tcp open microsoft-ds
548/tcp open afp
631/tcp open ip
6200/tcp open cinet1
5000/tcp open ibm-db2
MAC Address: 00:0C:2E:BC:5C:54 (Netgear)
Device type: storage-linux
Running: Netgear RAIDator
OS: Linux 2.6 (RAIDator:4.2)
OS details: Netgear READNAS device (RAIDator 4.2 - 4.27)
Network Distance: 1 hop
```

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ -nmap done; (1 host) scanned in 7.68 seconds

Figure 3.4: nmap -O

## Zenmap

本章中的所有内容目前都是通过命令行或终端界面完成的。随着 Nmap 的成熟，其界面也是如此。Zenmap 是 Nmap 的图形用户界面（GUI）。它是一个跨平台、免费开源的应用。Zenmap 具有一些旧命令行 Nmap 无法实现的优点，例如构建拓扑结构、创建交互式地图、显示两次扫描之间的比较、保留并跟踪扫描结果，以及使扫描可重复。Zenmap 的目标是让初学者和专家都能轻松免费地进行扫描。你只需要识别你的目标并点击 Scan（扫描）按钮即可，如图 3.5 所示。

![](img/e8e965b6c3537819be0d570febb3fc1d_53_0.png)

**图 3.5：** Zenmap GUI 扫描

如你所见，这正是之前的扫描结果，只是如果你点击中间的标签页，就可以看到所有开放端口的列表、网络拓扑、主机详情以及该资产的扫描历史，如图 3.6 所示。

要将单个扫描保存到文件，选择 Scan 菜单并从下拉菜单中选择 Save（保存）。如果有多个扫描，系统会询问你想要保存哪一个。你可以选择保存为 `.xml` 或 `.txt` 格式。`.xml` 格式只能由 Zenmap 打开和使用。默认情况下，所有扫描都会保存为期 60 天。

## 第 3 章 Nmap——网络映射器

| Nmap 输出 / 端口 / 拓扑 | 主机详情扫描 |
| :--- | :--- |
| 192.168.1.97 | |
| Host State: up | |
| Open ports: 9 | |
| Filtered ports: 0 | |
| Closed ports: 991 | |
| Scanned ports: 1000 | |
| Up time: 22857 | |
| Last boot: Tue Aug 21 11:44 2018 | |
| Address | |
| IPv4: 192.168.1.97 | |
| IPv6: Not available | |
| MAC: 00:0C:2E:BC:5C:54 | |
| Operating System Name: Netgear READNAS device (RAIDator 4.2-4.27) | |
| Accuracy: 100% | |
| Ports used | |
| OS Classes | |
| Type OS Family Generation | |
| storage-linux RAIDator 4.221 - 4.27 | |
| Accuracy: 100% | |
| TCP Sequence | |
| IP ID Sequence | |
| TS Sequence | |
| Comments | |

Figure 3.6: Zenmap details

在安装 Nmap 或 Zenmap 之前，你可能想确认它是否已经安装。有几个操作系统（包括大多数 Linux 系统）还没有安装 Nmap。在命令提示符中输入：

```
nmap --version
```

这将显示已安装的 Nmap 版本。如果收到 `nmap: command not found` 错误，则说明系统中未安装 Nmap。Zenmap 位于安装程序中。最新版本位于 www.nmap.org/download。要下载执行文件，请点击图 3.7 所示的链接。

最新版本：nmap-70-setup.exe

Figure 3.7: Downloading nmap-70-setup.exe

大多数 Windows 系统，文件默认保存在 Downloads 文件夹中。双击执行文件开始安装过程。保持所有默认设置直到点击 Finish（完成）。安装完成后，打开任务栏上的 Start 菜单并输入 Nmap。在菜单顶部，你应该看到 Nmap-Zenmap GUI。点击应用程序，定义目标并点击 Scan 启动。

发布在 www.cisecurity.org 的白皮书《中小企业 CIS 控制实施指南》分为以下阶段：

1. 了解你的环境。
2. 保护你的资产。
3. 准备你的组织。

在阶段 1 中，Nmap 被描述为多功能网络扫描器，而 Zenmap 被描述为 Nmap 的易用图形界面。你必须比攻击者更了解你的环境，并在关键控制中使用攻击者的思维来开发安全程序。

## 第 4 章 漏洞管理

在本章你将学到：

- OpenVAS
- 持续评估
- 修复
- Nexpose

多年的漏洞管理经验。起初我在路易斯安州立大学教学时，它是理论性的。当我担任某私立学校的 IT 主监以及作为承包商为美国国防部（DoD）工作时它变成了一个实践的角色。如果你计划参加任何安全认证考试——无论是 ISACA、ISC2 还是 CompTIA——你需要意识到漏洞生命周期风险的管理是这些考试的关键组成部分。

有些船是泰坦尼克，有些船像皮划艇（可能代表你的家庭网络），而财富50 强公司更像伊丽莎白二世号。两艘船的目标相同：不要沉没。如果你被赋予漏洞管理的任务，你的任务也是：不要沉没。

## 管理漏洞

正如我之前提到的，你必须比攻击者更了解你的环境，并在关键控制中使用攻击者的思维来开发安全程序。现在你已经有了所有用于排查网络的开源工具，并且知道你需要保护哪些资产，你必须能够对资产进行漏洞评估。这是一个循环过程，如图 4.1 所示。

![](img/e8e965b6c3537819be0d570febb3fc1d_57_0.png)

**图 4.1：漏洞管理生命周期**

在发现阶段，你必须弄清楚网络上有什么设备在与其他设备通信。你无法保护你不知道拥有的东西。一旦能够映射网络上的资产、主机、节点和中间设备，你就可以移动下一步。

并不是所有设备都是平等的。域是网络上的一组根据通用规则进行访问和管理的计算机和其他设备。Windows 域控制器（DC）是响应网络内登录身份验证请求的 Microsoft 服务器。在企业环境中，如果 DC 故障，由于用户无法登录域，你的帮助服务台将会被电话淹没。然而，如果你有一个营销部门拥有一个每月备份一次的小文件服务器，如果这台机器故障，可能只需要打一两个电话。在知道网络上存在哪些机器后，你必须确定哪些资产是关键任务的。

## 第 4 章 = 漏洞管理

技术报告通常会下发给资产所有者，并包含该设备上需要修复的内容。

拿到报告后，你现在拥有了你环境中的漏洞列表，以及它们所处的设备。某些具有高级功能的软件将生成有关如何修复这些漏洞的指令。

大多数此类技术报告都会为你提供一个严重程度评分，通常基于通用漏洞评分系统（CVSS），如表 4.1 所示。美国国立标准与技术研究院（NIST）维护着国家漏洞数据库（NVD）。在这些数据库中，你可以通过访问向量、复杂性和身份验证，以及对机（机密性、完整性和可用性的影响，对每个漏洞进行量化分析。基本上，这意味着每个漏洞都将获得一个 0 到 10 分的评分，0 分表示良好，10 分表示极度糟糕。

表 4.1：CVSS v3.0 评分标准

| 严重程度 | 基础评分范围 |
|---|---|
| 无 (None) | 0 |
| 低 (Low) | 0.1–3.9 |
| 中 (Medium) | 4.0–6.9 |
| 高 (High) | 7.0–8.9 |
| 严重 (Critical) | 9.0–10.0 |

来源：美国国立标准与技术研究院

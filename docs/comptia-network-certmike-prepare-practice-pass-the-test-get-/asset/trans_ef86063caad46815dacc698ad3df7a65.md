

# 命令行工具

根据计算机的默认 DNS 服务器，在命令行输入可以返回与该服务器名称关联的 IP 地址。

然而，对于故障排除人员来说，nslookup 最实用的功能之一是：它具有向特定服务器定义名称解析查询的能力。有时，名称解析问题可能是由于 DNS 记录尚未传播到互联网上的所有名称服务器。通过重定向查询，你可以确定特定服务器是否拥有最新信息。

Dig 是一种 Unix/Linux 工具，在功能上与 nslookup 几乎相同，尽管它显示结果的方式有所不同。Dig 没有像 nslookup 那样的交互模式，这也就是为什么某些 Unix/Linux 发行版同时包含了这两个工具。

# Traceroute/Tracert

网络数据包到达目的地所经过的路径称为路由。路由由“跳”（hops）组成，即数据包从一个路由器到另一个路由器的单独旅行。互联网任务的源和目的地之间的路由可能有 20 个或更多跳。

Unix/Linux 上的 traceroute 工具和 Windows 上的 Tracerert 程序会显示通往指定目的地的路由跳数列表。这些工具通过发送一系列 ICMP Echo 请求消息（其 IP 头中的值逐渐增大）来实现的。这会导致消息在每一跳处失败并向源端返回错误消息。错误消息包含每一跳路由器的 IP 地址，Windows trace 命令以如下显示列出：

Tracing to www.finartchool.co.uk [173.146.1] over a maximum of 30 hops:

```
| <10 ms 1 ms <10 ms 98 ms qrvl-6terminal01.cpandl [131.107.24.67.3]
| 105 ms 92 ms 98 ms qrvl.cpandl [131.107.67.1]
| 110 ms 118 ms 98 ms svrcr3-7b.cpandl [131.107.103.125]
| 123 ms 109 ms 118 ms clsm2b2-4.cpandl [131.107.08.26]
| 123 ms 112 ms 114 ms sl-g119-pen-6-1-g73-f.fabrikam.com [157.54.51.165]
| 136 ms 130 ms 133 ms sl-bb20-pen-12-0.fabrikam.com [157.54.5.1]
| 146 ms 129 ms 133 ms sl-daemon-1-0.fabrikam.com [157.54.5.1]
| 147 ms 149 ms 152 ms sl-daemon-1-0.fabrikam.com [157.54.173.10]
| 230 ms 225 ms 226 ms tele-back-1-ge023.router.adatum.co.uk [157.60.173.12]
| 236 ms 220 ms 226 ms tele-core-3fpl1.router.adatum.co.uk [157.60.252.56]
| 236 ms 221 ms 226 ms tele-service-2-165.router.adatum.co.uk [157.60.139.34]
| 1222 ms 224 ms 210 ms www.finartchool.co.uk [206.718.65]
Trace complete.
```

# 第 23 章 • 网络软件工具与命令

Traceroute 在大型企业网络中是一项非常有价值的工具，因为它能为故障排除人员提供数据包通过网络时路由的信息。例如，在示例显示中，请注意当路由将数据包从北美传输到英国的服务器时，往返时间从 100 级跳跃到 200 级。

# Arp

如第 11 章所述，“地址解析协议（ARP）”是一种数据链路协议，系统使用它将 IP 地址解析为媒体访问控制（MAC）地址。然后将该对项保存到 ARP 表中，以节省内存供重复使用。除了协议本身外，Windows 和 Unix/Linux 中还有 arp 实用程序允许用户显示并修改 ARP 表的内容。在命令行运行 `arp -a` 会产生如下的显示：

```
Interface: 192.168.1.2
Internet Address Physical Address Type
192.168.1.1 00-80-e7-e5 dynamic
192.168.1.11 84-b8-d8-69 dynamic
192.168.1.14 20-ef-bd-33 dynamic
192.168.1.16 1c-e3-ae-42 dynamic
192.168.1.23 9e-d3-cf-c3 dynamic
```

# Netstat

Netstat 是 Windows 和 Linux 的命令，可以显示关于系统 TCP 和 UDP 连接的各种网络统计数据。运行 netstat 不带参数会显示当前的打开会话：

| 协议 | 本地地址 | 外部地址 | 状态 |
| :--- | :--- | :--- | :--- |
| TCP | 127.0.0.1:4994 | | ESTABLISHED |
| TCP | 127.0.0.1:5923 | | ESTABLISHED |
| TCP | 192.168.1.21:57617 | | ESTABLISHED |
| TCP | 192.168.1.21:57633 | | TIME_WAIT |
| TCP | 192.168.1.21:57638 | | TIME_WAIT |
| TCP | 192.168.1.21:57662 | | ESTABLISHED |
| TCP | 192.168.1.21:57674 | | ESTABLISHED |
| TCP | 192.168.1.21:57680 | | ESTABLISHED |
| TCP | 192.168.1.21:57681 | | ESTABLISHED |
| TCP | 192.168.1.21:57684 | | ESTABLISHED |
| TCP | fe80::4445 | | ESTABLISHED |
| TCP | fe80::55341 | | ESTABLISHED |
| TCP | fe80::57700 | | TIME_WAIT |

加上命令行参数，netstat 还可以显示系统的监听端口、以太网包计数以及 IPv4 和 IPv6 包计数。

# Hostname

Hostname 是 Windows 和 Unix/Linux 系统上的简单实用程序，返回当前计算机或主机的名称。它没有命令行参数或其他功能。然而，当 IT 技术人员同时处理多个系统时，他们需要快速确认自己正在访问哪一个。

# Route

Route 是 Windows 和 Unix/Linux 的实用程序，用于访问系统的路由表。所有 TCP/IP 主机都有路由表（如第 10 章“路由与带宽管理”所述），无论它们是否作为连接网络的路由器。在 Windows（或 Unix/Linux）中运行 `route print -n` 命令可以显示 IPv4 和 IPv6 系统路由表的内容。除了显示路由表，route 实用程序还可以允许管理员添加、修改和删除路由条目。

# Telnet

Telnet 是一种通信协议，允许用户连接到远程计算机并在那里执行命令。除了协议本身，Telnet 还包含一个允许用户启动连接的简单 CLI。几乎所有的 Unix/Linux 发行版默认安装了 Telnet。Windows 工作站也包含 Telnet 客户端，但用户必须在“Windows 功能”对话框中启用它才能使用。Telnet 可以帮助故障排除人员确定网络上的系统是否运行，但重要的是记住 telnet 通过网络传输的是明文，包括密码。安全 Shell SSH 程序与 telnet 类似，但它以加密格式传输数据。

# Tcpdump

tcpdump 工具仅用于 Unix 和 Linux 平台，它可以捕获特定网络接口上传输和接收的数据包并显示它们。通过命令行参数，用户可以过滤数据包，仅保存与特定应用层协议相关的 IP 地址或端口号的数据包。


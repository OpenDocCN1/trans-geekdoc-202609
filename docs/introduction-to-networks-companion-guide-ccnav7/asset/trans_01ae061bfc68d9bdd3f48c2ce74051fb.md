
用作默认网关的均在本地网络上运行正常。ping 还可用于测试本地主机在互联网之间通信的能力。本地主机可以 ping 远程网络上运行正常的 IPv4 主机。traceroute（tracert）会生成沿途成功到达的跳数列表。该列表提供验证和故障排除信息。如果数据到达目的地，则跟踪会列出主机之间路径中每个路由器的接口。如果数据在途中某个跳点失败，最后响应跟踪的路由器的地址可以指示问题或安全限制发生的位置。往返时间是指数据包到达远程主机所需的时间以及主机响应返回所需的时间。traceroute 利用 IPv4 和 IPv6 第 3 层报头中 TTL 字段和 Hop Limit 字段的功能，以及 ICMP Time Exceeded 消息。

![](img/e71dc48d3ae3db3394e5857ab2acae75_491_0.png)

## Packet Tracer—使用 ICMP 测试和纠正网络连通性 (13.3.1)

在此 Packet Tracer 活动中，您将使用 ICMP 测试网络连通性并定位网络问题。您还将纠正简单的配置问题并恢复网络连通性：

- 使用 ICMP 定位连通性问题。
- 配置网络设备以纠正连通性问题。

![](img/e71dc48d3ae3db3394e5857ab2acae75_491_1.png)

## Lab—使用 Ping 和 Traceroute 测试网络连通性 (13.3.2)

在本实验中，您将完成以下目标：

- 第 1 部分：构建和配置网络
- 第 2 部分：使用 ping 命令进行基本网络测试
- 第 3 部分：使用 tracert 和 traceroute 命令进行基本网络测试
- 第 4 部分：排除拓扑故障

## 练习

以下活动提供了本章介绍主题的练习。实验可在配套的 Introduction to Networks Labs & Study Guide (CCNAv7)（ISBN 9780136634454）中找到。Packet Tracer 活动说明也提供在 Labs & Study Guide 中。PKA 文件可在在线课程中获得。

## 实验

Lab 13.3.2：使用 Ping 和 Traceroute 测试网络连通性

## Packet Tracer 活动

- Packet Tracer 13.2.6：验证 IPv4 和 IPv6 地址
- Packet Tracer 13.2.7：使用 ping 和 traceroute 测试网络连通性
- Packet Tracer 13.3.1：使用 ICMP 测试和纠正网络连通性

## 检查你的理解问题

请完成此处列出的所有复习问题，以测试您对本章主题和概念的理解。附录“‘检查你的理解’问题的答案”列出了答案。

1. 用户来电报告 PC 无法访问互联网。网络技术人员要求用户在命令提示符窗口中执行 ping 127.0.0.1 命令。用户报告结果为四个积极回复。基于此连通性测试，可以得出什么结论？
- a. PC 可以访问网络。问题存在于本地网络之外。
- b. 从 DHCP 服务器获取的 IP 地址是正确的。
- c. PC 可以访问互联网。但是，网页浏览器可能无法工作。
- d. TCP/IP 实现是功能正常的。

2. 哪个命令可用于使用 Echo Request 和 Echo Reply 消息测试两个设备之间的连通性？
- a. netstat
- b. ipconfig
- c. icmp
- d. ping

3. 路由器使用哪个 IPv6 字段来确定数据包已过期？
- a. TTL 字段
- b. CRC 字段
- c. Hop Limit 字段
- d. Time Exceeded 字段

4. 哪个协议提供有关数据包传输错误的反馈，从目标主机到源主机？
- a. ARP
- b. BOOTP
- c. DNS
- d. ICMP

5. 哪个实用程序使用 Internet 控制消息协议 (ICMP)？
- a. RIP
- b. DNS
- c. ping
- d. NTP

6. 网络管理员可以成功 ping www.cisco.com 上的服务器，但无法 ping 位于另一城市 ISP 上的公司 Web 服务器。哪个工具或命令可以帮助识别数据包丢失或延迟的具体路由器？
- a. ipconfig
- b. netstat
- c. telnet
- d. traceroute

7. IPv6 使用哪个协议提供地址解析和动态地址分配信息？
- a. ICMPv4
- b. NDP
- c. ARP
- d. DHCP

8. 主机在开始使用该地址之前可以发送什么消息来检查 IPv6 地址的唯一性？
- a. Neighbor Solicitation
- b. ARP Request
- c. Echo Request
- d. Router Solicitation

9. 技术人员正在排除网络故障，怀疑网络路径中的一个缺陷节点导致数据包被丢弃。技术人员只有端点设备的 IP 地址，没有中间设备的任何详细信息。技术人员可以使用什么 Windows 命令来识别故障节点？
- a. tracert
- b. ping
- c. ipconfig /flushdns
- d. ipconfig /displaydns

10. 一名无法连接到文件服务器的用户联系了帮助台。帮助台技术人员要求用户 ping 工作站上配置的默认网关的 IP 地址。此 ping 命令的目的是什么？
- a. 从服务器获取动态 IP 地址
- b. 请求网关将连接请求转发到文件服务器
- c. 测试主机是否有能力到达其他网络上的主机
- d. 将文件服务器的域名解析为其 IP 地址

11. 当在工作站上使用这些命令时，Windows tracert 命令做了 ping 命令没有做的事情是什么？
- a. tracert 命令更快地到达目的地。
- b. tracert 命令显示路径中路由器的信息。
- c. tracert 命令向路径中的每个跳发送一条 ICMP 消息。
- d. tracert 命令用于测试两个设备之间的连通性。

12. traceroute 实用程序在查找两个端主机之间的路径过程中使用哪个 ICMP 消息？
- a. Redirect
- b. ping
- c. Time Exceeded
- d. Destination Unreachable

13. 使用 **ping** 命令可以确定哪两件事？
（请选择两项。）
- a. 源设备和目标设备之间的路由器数量
- b. 距目标设备最近的路由器的 IP 地址
- c. 数据包到达目的地并响应返回源所需时间的平均值
- d. 通过网络到达目标设备的可达性
- e. 源和目标之间路径中每个路由器响应的平均时间

14. 哪条语句描述了 **traceroute** 实用程序的特征？
- a. 它发送四个 Echo Request 消息。
- b. 它利用 ICMP Source Quench 消息。
- c. 它主要用于测试两个主机之间的连通性。
- d. 它识别从源主机到目标主机的路径中的路由器。

本页特意留空

## 传输层

## 目标

完成本章后，您将能够回答以下问题：

- 传输层在管理端到端通信中数据传输方面的目的是什么？
- TCP 的特征是什么？
- UDP 的特征是什么？
- TCP 和 UDP 如何使用端口号？
- TCP 会话建立和终止过程如何促进可靠通信？
- TCP 协议数据单元如何传输和确认以保证交付？
- 传输层协议在支持端到端通信方面的操作是什么？

## 关键术语

本章使用以下关键术语。您可以在本书末尾的词汇表中找到定义。

传输控制协议 (TCP) 第 462 页
用户数据报协议 (UDP) 第 462 页
段 第 463 页
面向连接的协议 第 471 页
有状态 第 471 页
端口号 第 476 页
套接字 第 477 页
套接字对 第 477 页
三次握手 第 483 页
初始序列号 (ISN) 第 487 页
预期确认 第 488 页
选择性确认 (SACK) 第 489 页
窗口大小 第 490 页

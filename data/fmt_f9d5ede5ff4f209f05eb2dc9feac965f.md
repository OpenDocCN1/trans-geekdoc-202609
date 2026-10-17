
```
root@kali:~# nmap -oO 192.168.2.19
Starting Nmap 7.60 ( https://nmap.org ) at 2018-01-25 17:57 EST
Nmap scan report for 192.168.2.19
Host is up (0.00036s latency).
Not shown: 908 closed ports
PORT STATE SERVICE
135/tcp open ms-rpc
139/tcp open netbios-ssn
445/tcp open microsoft-ds
554/tcp open rtssp
2069/tcp open icslap
5357/tcp open wdsapi
10243/tcp open unknown
49152/tcp open unknown
49153/tcp open unknown
49154/tcp open unknown
49155/tcp open unknown
49156/tcp open unknown
MAC Address: 08:00:27:bd:f4 (Oracle VirtualBox NIC)
Device type: general purpose
Running: Windows 7 [2009R1]
OS CPE: cpe:o:microsoft:windows 7::- cpe:o:microsoft:windows 7:sp1 cpe:o:microsoft:windows_server 2008::-sp1 cpe:o:microsoft:windows_server 2008:2 cpe:o:microsoft:windows 8:cpe cpe:o:microsoft:windows 8.1
OS details: Windows 7 SP0 - SP1, Windows Server 2008 SP1, Windows Server 2008 R2, Windows 8, or Windows 8.1 Update
Network Distance: 1 hop
OS detection performed. Please report any incorrect results at https://nmap.org/submit/.
nmap done: 1 IP address (1 host up) scanned in 7.20 seconds
root@kali:~#
```

## 图 2-2 第二次扫描

- C 是正确的。图 2-1 显示该系统可能是防火墙，这是通过观察图 2-2 中端口被报告为“过滤（filtered）”而非“关闭（closed）”来确定的。A、B 和 D 是错误的，因为动态端口范围（49152 到 65535）没有正在监听的服务。图 2-2 报告这些端口已关闭。D 没有识别出操作系统。

12. 下列哪项不是 Windows 的事件类别？

- A. 应用（Application）
- B. 系统（System）
- C. 安全（Security）
- D. 审计（Audit）
- E. 存储（Storage）

D 是正确的。存储不是实际的事件类别。A、B 和 E 是错误的。应用、系统和审计都是有效的事件类别。

13. 你正在查看 Windows 机器的日志。参考图 2-3，选择产生警告的类别、事件 ID 以及机器名称。

- A. 安全（Security）
- B. 客户端（Client）
- C. 系统（System）
- D. 存储（Storage）
- E. 审计（Audit）

![](img/912de3ecf2d271d89c5f4.png)

图 2-3 事件查看器结果

- D 是正确的。日志显示事件 ID 为 1014。此外，系统名称为 COMPUTER（计算机）。
- A、B 和 C 是错误的。A 和 B 是错误的，因为类别错误。此外，A 是错误的。

14. 分析师启动 `nmap` 扫描一台未知机器。从图 2-4 的端口中，分析师可以假设操作系统是什么？

- A. Linux
- B. Windows
- C. Ubuntu
- D. OpenVMS
- E. Cisco IOS

B 是正确的。扫描到的系统是 Windows。证据是发现了 端口 `135` 和 `139`。

15. 网络安全分析师扫描 TCP 端口 `636` 的网络。分析师预计在这些服务器上还会发现哪个端口是开启？

- A. `22`
- B. `111`
- C. `53`
- D. `389`
- E. `5000`

D 是正确的。端口 `636` 用于 SSL 之 LDAP (`LDAPS`)。任何监听 `636` 端口的服务器都可能在 `389` 端口监听 LDAPS。

A、B、C 和 E 是错误的。A 是错误的，端口 `22` 通常用于 SSH。B 是错误的，端口 `111` 用于 RPC（远程过程调用）。C 是错误的，端口 `53` 用于 DNS。最后，E 是错误的，因为端口 `5000` 可能用于多种服务，但与端口 `636` 无特定关联。

16. 哪种工具为 `nmap` 提供图形用户界面？

- A. Nessus
- B. Zenmap
- C. TShark
- D. Qualys

B 是正确的。`Zenmap` 是 `nmap` 的 GUI 版本。

A、C 和 D 是错误的。A 是错误的，因为 Ness 是漏洞扫描器而不是端口扫描器。C 是错误的，因为 `TShark` 是 Wireshark 的 CLI 版本。最后，D 是错误的，因为 Qualys 是 GUI 漏洞扫描器。

17. 分析师正在查看 ASA 防墙的日志。分析师应该在命令行输入什么来验证是否启用了日志？

- A. `# show running-config logging`
- B. `# log full show`
- C. `# show all`
- D. show run

A 是 ASA 防墙上启动的正确命令。

18. 运行 `tcpdump` 后，分析师查看输出，其中包含以下行：

```
16:35:39.83754 > badguy.org.12889 > target.net.80: FP(DF)
```

“FP”代表什么？

- A. 最终包（Final Packet）
- B. 第一包（First Packet）
- C. Fin Push
- D. 前向包（Forward Packet）

C 是正确的。“F”代表 Fin，“P”代表 Push。A、B 和 D 是错误的。FP 中的“P”不代表“Packet（包）”。

19. 总监决定公司需要 IDS。作为高级安全分析师，你推荐使用 Snort。总监要求你标记任何来自竞争对手网络的 SSH 请求。检查以下规则，选择当流量源自网络 `12.34.56.x/24` 目标为公司服务器（IP 地址 `210.67.79.89`）时触发告的规则。

- A. alert tcp 210.67.78.89 -> 12.34.56.0/24 80
- B. alert tcp 12.34.56.0 24 -> 210.67.79.89 21
- C. alert tcp 210.67.78.80 -> 12.34.56.0/24 any
- D. alert tcp 12.34.56.0 24 -> 210.67.79.89 22

D 是正确的。当 SSH 请求（通过 `22/TCP`）来自 `12.34.56.0/24` 网络并发送到 `210.67.79.89` 的公司服务器时，该 Snort 规则会正确告警。

A、B 和 C 是错误的。A 是错误的，因为源目的地址反了，且监控的是端口 `80` (HTTP)，而题目说是 SSH 请求。B 是错误的，因为 Snort 规则监控的是端口 `21` (FTP)。C 是错误的，因为端口 `53` 用于 DNS。

源地址和目的地址反了，并且正在监控指向所有 TCP 端口的流量，而不只是 `22` 端口。

20. 用户告知安全分析师网络性能很差。安全分析师快速查看数据包捕获以判断是否有明显的异常。根据图 2-5，安全分析师的第一印象应该是什么？

- A. ARP 风暴
- B. DDoS
- C. DoS
- D. 广播风暴

| No. | Time | Source | Destination | Info | Protocol |
|---|---|---|---|---|---|
| 1 | 0.000000 | Cisco251_af:f | Broadcast | Who has 24.166.173.159? Tell 24.166.172.121 | ARP |
| 2 | 0.089594 | Cisco251_af:f | Broadcast | Who has 24.166.172.141? Tell 24.166.172.121 | ARP |
| 3 | 0.110617 | Cisco251_af:f | Broadcast | Who has 24.166.173.161? Tell 24.166.172.121 | ARP |
| 4 | 0.221791 | Cisco251_af:f | Broadcast | Who has 65.28.78.76? Tell 65.28.78.1 | ARP |
| 5 | 0.216744 | Cisco251_af:f | Broadcast | Who has 24.166.173.163? Tell 24.166.172.121 | ARP |
| 6 | 0.307990 | Cisco251_af:f | Broadcast | Who has 24.166.175.123? Tell 24.166.172.121 | ARP |
| 7 | 0.330433 | Cisco251_af:f | Broadcast | Who has 24.166.173.165? Tell 24.166.172.121 | ARP |
| 8 | 0.408556 | Cisco251_af:f | Broadcast | Who has 24.166.175.82? Tell 24.166.172.121 | ARP |
| 9 | 0.455184 | Cisco251_af:f | Broadcast | Who has 69.76.220.137? Tell 69.76.216.211 | ARP |
| 10 | 0.486666 | Cisco251_af:f | Broadcast | Who has 24.166.173.168? Tell 24.166.172.121 | ARP |
| 11 | 0.506494 | Cisco251_af:f | Broadcast | Who has 69.76.223.116? Tell 69.76.216.211 | ARP |
| 12 | 0.510684 | Cisco251_af:f | Broadcast | Who has 24.166.174.184? Tell 24.166.172.121 | ARP |
| 13 | 0.540738 | Cisco251_af:f | Broadcast | Who has 24.166.173.169? Tell 24.166.172.121 | ARP |
| 14 | 0.587388 | Cisco251_af:f | Broadcast | Who has 24.166.174.181? Tell 24.166.172.121 | ARP |
| 15 | 0.662937 | Cisco251_af:f | Broadcast | Who has 69.76.223.217? Tell 69.76.216.211 | ARP |

## 图 2-5 Wireshark 数据包列表窗

- A. 显示的数据包列表显示了大量的 ARP 数据包。ARP 协议将硬件地址或 MAC 地址解析为 IP 地址。ARP 风暴可能由恶意意或配置错误的网络连接（例如网桥环路）引起。
- B、C 和 D 是错误的。B 和 C 是正确的，因为没有足够的证据认为许多 ARP 数据包具有恶意意。此外，比 ARP 风暴有更有效的方法可以中断服务。D 是错误的，虽然 ARP 是一个限制在广播域内的协议，但更准确的答案是 ARP 风暴。

21. 分析网络带宽消耗的适当工具是什么？

- A. Wireshark
- B. TShark
- C. NetFlow
- D. IDS

C 是正确的。`NetFlow Analyzer` 显示了网络带宽消耗，以及有关网络利用率和健康状况的其他指标。A、B 和 D 都是错误的。A 和 B 是数据包分析器，可以详细说明数据包的数量，但不会提供带宽消耗的深入见解。D 是错误的，因为入侵检测系统关于拒绝服务（DoS）攻击的信息非常少。

22. 以下哪些是分析无线网络的主要挑战？（选择所有适用项）

- A. MAC 地址的高信度
- B. 识别设备
- C. WAPs 的清单
- D. 确定网络是自形成模式还是基础设施模式

A 和 B 是正确的。A 是错误的，因为 MAC 地址很容易修改。B 是正确的，因为连接设备的数量不断变化——特别是在自带设备（BYOD）环境中。C 和 D 是错误的。拥有接入点（WAPs）清单比拥有所有连接设备列表要简单得多。D 是错误的，取决于网络设置。

# 响应网络威胁

本章节包括：

- 网络和主机加固
- 欺骗技术
- 常见的访问控制
- 威胁检测和终端保护

如果目标是使网络安全，分析师将持续致力于安全网络。在编写策略、配置和审查日志后，分析师仍然必须对威胁做出响应。安全并不是一个终点，而是一个持续的过程。分析师的目标是确保网络具有机密性、完整性和可用性。威胁随时间变化。为了管理这些风险和威胁，分析师可以使用从硬件到软件的各种控制措施。本章节涵盖了考试中的重要部分。

## 题目

1. 目前公司服务器位于内部网络之外。Web 服务器需要供公众访问，但外部暴露会带来巨大风险。镜像已包含运行的服务和安装的应用程序，以使任务尽可能简单。作为安全分析师，对管理员的最好建议是什么？

- A. 使用尽可能少的服务应用程序重新构建服务器镜像。
- B. 重新构建服务器镜像，安装所有程序但不运行。
- C. 根据子网创建多个镜像。
- D. 对已部署的服务器运行漏洞扫描器。

2. 以下哪些是网络划分的好处？（选择所有适用项）

- A. 改进网络流量
- B. 缓解攻击者的风险
- C. 更简单的拓扑
- D. 防止敏感数据泄露
- E. 简化应用程序和服务访问

3. 有时，管理员不在公司。当他们需要访问内部网络的服务器时，你的建议是什么？

- A. 实现一个只有管理员知道的端口防火墙。
- B. 仅当使用移动设备时允许管理员绕过防火墙。
- C. 在 DMZ 中作为跳板服务器配置服务器。
- D. 在防火墙内部安装并配置独立的跳板机。

4. “强制门户”（captive portal）是以下哪者的示例？

- A. DAC
- B. 带内 NAC
- C. 带外 NAC
- D. 基于角色的 NAC

5. NAC 解决方案根据哪些授予访问？（选择所有适用项）

- A. 角色
- B. 规则
- C. 速率
- D. 位置
- E. 系统补丁级别
- F. 时间

6. 为了更多地了解威胁，安全分析师可以安装一个看起来像典型服务器但仅作为攻击者诱饵的系统。这种系统称为什么？

- A. 跳板服务器
- B. 入侵检测系统
- C. 蜜罐（Honeypot）
- D. RBAC 盒
- E. 微隔离服务器

7. 使用 ACL 的直接影响？（选择两个）

- A. 控制访问
- B. 限制恶意软件传播
- C. 过滤特定流量
- D. 启用直接网络路由

8. 以下文本是什么的示例？

```
deny icmp 172.16.0.0 0.15.255.255 192.168.50.0 0.0.0.255
```

- A. 垃圾邮件过滤器
- B. 访问控制列表
- C. VPN 隧道设置
- D. IGMP 设置

9. 在以下 ACL 中，“10.235.235.235”代表什么？

```
permit tcp 10.15.0.0 0.255.255.255 10.235.235.235 0.255.255.255
```

- A. 子掩码
- B. 源地址
- C. 目的地址
- D. 被过滤端口

10. 添加新服务器时，公司管理员从安装预构建的服务器镜像开始。镜像包含运行的服务和安装的应用程序，以使任务尽可能简单。作为安全分析师，对管理员的最好建议是什么？

- A. 使用尽可能少的服务应用程序重新构建服务器镜像。
- B. 重新构建服务器镜像，安装所有程序但不运行。
- C. 根据子网创建多个镜像。
- D. 对已部署的服务器运行漏洞扫描器。

11. 以下哪些是 DNS 汇洞（DNS sinkhole）的方法和目的？（选择两个。）

- A. 将 DNS 查询重定向到已知的恶意服务器
- B. 不提供 DNS 解析响应
- C. 记录 DNS 解析请求以确定受感染的主机
- D. 记录 DNS 重定向以确定受感染的域名

12. 一家公司在网络入侵检测系统上投入了大量，这些系统能够以极快的速度和合理的有效性检查流量。然而，最近的一个事件显示，员工可以使用点对点加密来掩盖数据外泄。对于该公司来说，最好的建议是什么？

- A. 将 IDS 升级为 IPS。
- B. 采用终端安全控制措施。
- C. 禁止所有加密的使用。
- D. 替换涉嫌的员工。

13. 图 3-1 展示的是哪种类型的网络访问控制？

- A. 基于角色的
- B. 基于规则的
- C. 按时间的
- D. 基于位置的

## 设备访问限制列表

| 设备名称 | MAC 地址 | 允许日期 | 允许时间 | 编辑 |
| --- | --- | --- | --- | --- |
| OfficePrinter | 98:e7:f4:48:13:79 | 周一、二、三、四、周五 | 上午 9:00 到 下午 7:00 | 删除 |
| Bills-iPhone | 40:33:1a:00:79:18 | 周一、三、周五 | 上午 8:00 到 下午 5:00 | 删除 |

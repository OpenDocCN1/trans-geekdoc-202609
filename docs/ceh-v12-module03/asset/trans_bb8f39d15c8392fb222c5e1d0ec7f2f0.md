
攻击者可以使用各种工具对目标机器执行操作系统发现，包括 Wireshark、Nmap、Unicornscan 和 Nmap 脚本引擎。攻击者还可采用 IPv6 指纹识别方法获取目标操作系统的详细信息。

## 使用 Wireshark 进行操作系统发现

来源: https://www.wireshark.org

为了识别目标操作系统，使用 Wireshark 等数据包嗅探工具嗅探/捕获目标机器发往请求源机器的响应，并观察第一个捕获到的 TCP 数据包中的 TTL 和 TCP 窗口大小字段。通过将这些值与上表中值进行比较，可以确定生成响应的目标操作系统。

![](img/198108450322f24970ade227cbf24f47_80_0.png)

图 3.76：Wireshark 屏幕截图显示 TTL 值（可能的系统为 Windows）

![](img/198108450322f24970ade227cbf24f47_81_0.png)

## 可能的操作系统为 Linux

图 3.77：Wireshark 屏幕截图显示 TTL 值（可能的系统为 Linux）

![](img/198108450322f24970ade227cbf24f47_82_0.png)

## 使用 Nmap 和 Unicornscan 进行操作系统发现

## 使用 Nmap 进行操作系统发现

来源: https://nmap.org

为了利用目标，识别目标机器上运行的操作系统至关重要。攻击者可以使用各种工具获取目标的操作系统详细信息。Nmap 是执行操作系统发现活动的有效工具之一。在 Zenmap 中，使用 -O 选项执行操作系统发现，可显示目标机器的操作系统详细信息。

![](img/198108450322f24970ade227cbf24f47_83_0.png)

```
nmap -O 10.10.1.11
```

MAC 地址: 00:15:5D:01:80:00 (Microsoft)
设备类型: general purpose
运行中: Microsoft Windows 10
OS CPE: cpe:/o:microsoft:windows_10:1703
操作系统详细信息: Microsoft Windows 10 1703

图 3.78：使用 Zenmap 进行操作系统发现

## 使用 Unicornscan 进行操作系统发现

来源: https://sourceforge.net

在 Unicornscan 中，可以通过观察获取的扫描结果中的 TTL 值来识别目标机器的操作系统。执行 Unicornscan 时使用的语法为 `#unicornscan <目标 IP 地址>`。如屏幕截图所示，扫描后获取的 `ttl` 值为 128；因此操作系统可能是 Microsoft Windows。

![](img/198108450322f24970ade227cbf24f47_84_0.png)

图 3.79：使用 Unicornscan 进行操作系统发现

## 使用 Nmap 脚本引擎进行操作系统发现

- Nmap 脚本引擎 (NSE) 可通过允许用户编写和共享脚本来自动化各种网络任务
- 攻击者使用 Nmap 脚本引擎中的各种脚本对目标机器执行操作系统发现
- 例如，在 Nmap 中，smb-os-discovery 是一个内置脚本，可通过 SMB 协议收集目标机器的操作系统信息
- 在 Zenmap 中，使用 -sC 选项或 --script 选项激活 NSE 脚本

![](img/198108450322f24970ade227cbf24f47_85_0.png)

## 使用 Nmap 脚本引擎进行操作系统发现

来源: https://nmap.org

Nmap 中的 Nmap 脚本引擎 (NSE) 可通过允许用户编写和共享脚本来自动化各种网络任务。这些脚本可以与 Nmap 相同效率和速度并行执行。攻击者还可使用 Nmap 脚本引擎中的各种脚本执行目标机器的操作系统发现。例如，在 Nmap 中，smb-os-discovery 是一个内置脚本，用于通过 SMB 协议收集目标机器的操作系统信息。

在 Zenmap 中，通常使用 -sC 选项激活 NSE。如果要指定自定义脚本，则攻击者可以使用 --script 选项。NSE 结果将与 Nmap 的常规和 XML 输出一起显示。

```
[root@parrot] /home/attacker
# nmap --script smb-os-discovery.nse 10.10.1.22
Starting Nmap 7.92 ( https://nmap.org ) at 2022-03-25 00:36 EDT
Nmap scan report for 10.10.1.22
Host is up (0.0094s latency).
Not shown: 983 filtered tcp ports (no-response)
PORT      STATE SERVICE
53/tcp    open  domain
80/tcp    open  http
88/tcp    open  kerberos-sec
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
389/tcp   open  ldap
445/tcp   open  microsoft-ds
464/tcp   open  kpasswd5
593/tcp   open  http-rpc-epmap
636/tcp   open  ldaps
1801/tcp  open  msmq
2103/tcp  open  zephyr-clt
2105/tcp  open  eklogin
2107/tcp  open  msmq-mgmt
3268/tcp  open  globalcatLDAP
3269/tcp  open  globalcatLDAPssl
3389/tcp  open  ms-wbt-server
MAC Address: 00:15:5D:01:80:02 (Microsoft)

Host script results:
| smb-os-discovery:
|   OS: Windows Server 2022 Standard 20348 (Windows Server 2022 Standard 6.3)
|   Computer name: Server2022
```

图 3.80：使用 Nmap 脚本引擎进行操作系统发现

## 使用 IPv6 指纹识别进行操作系统发现

IPv6 指纹识别可用于识别目标机器上运行的操作系统

IPv6 指纹识别的功能与 IPv4 相同

IPv6 与 IPv4 指纹识别之间的区别在于，IPv6 使用多个针对 IPv6 的额外高级探测，以及专门用于 IPv6 的独立操作系统检测引擎

在 Zenmap 中，使用 -6 选项和 -O 选项通过 IPv6 指纹识别方法执行操作系统发现

```
Syntax: # nmap -6 -O <target>
```

## 使用 IPv6 指纹识别进行操作系统发现

来源: https://nmap.org

IPv6 指纹识别是识别目标机器上运行的操作系统的另一种技术。它具有与 IPv4 相同的功能，例如发送探测、等待并收集响应，并将其与指纹数据库进行匹配。IPv6 与 IPv4 指纹识别之间的区别在于，IPv6 使用多个针对 IPv6 的额外高级探测，以及专门用于 IPv6 的独立操作系统检测引擎。Nmap 发送近 18 个探测，按以下顺序使用 IPv6 指纹识别方法识别目标操作系统。

- 序列生成 (S1–S6)
- ICMPv6 回显 (IE1)
- ICMPv6 回显 (IE2)
- 节点信息查询 (NI)
- 邻居请求 (NS)
- UDP (U1)
- TCP 显式拥塞通知 (TECN)
- TCP (T2–T7)

在 Zenmap 中，使用 -6 选项和 -O 选项通过 IPv6 指纹识别方法执行操作系统发现。

```
Syntax: # nmap -6 -O <target>
```

## LO#06：演示绕过 IDS 和防火墙的各种扫描技术

![](img/198108450322f24970ade227cbf24f47_88_0.png)

## 绕过 IDS 和防火墙的扫描

入侵检测系统 (IDS) 和防火墙是旨在防止攻击者访问网络的安全机制。然而，即使是 IDS 和防火墙也存在一些安全限制。攻击者试图发动攻击来利用这些限制。本节介绍各种 IDS/防火墙规避技术，例如数据包分片、源路由、IP地址欺骗等。

## IDS/防火墙规避技术

尽管防火墙和 IDS 可以防止恶意流量（数据包）进入网络，但攻击者可以通过以下技术规避 IDS 或防火墙，从而将预期数据包发送到目标：

- 1. 数据包分片
- 2. 源路由
- 3. 源端口操作
- 4. IP 地址诱饵
- 5. IP 地址欺骗
- 6. MAC 地址欺骗
- 7. 创建自定义数据包
- 8. 随机化主机顺序并发送错误校验和
- 9. 代理服务器
- 10. 匿名器

## IDS/防火墙规避技术

尽管防火墙和 IDS 可以防止恶意流量（数据包）进入网络，但攻击者可以通过实施以下技术发送能够规避 IDS/防火墙的预期数据包到目标：

- 数据包分片
- 源路由
- 源端口操作
- IP 地址诱饵
- IP 地址欺骗
- MAC 地址欺骗
- 创建自定义数据包
- 随机化主机顺序
- 发送错误校验和
- 代理服务器
- 匿名器

## 数据包分片

- 数据包分片是指在向网络发送时将探测数据包 **拆分为多个较小的包**（片段）
- 它不是一种新的扫描方法，而是之前技术的 **修改**
- **TCP 头部** 被拆分为多个数据包，以便数据包过滤器无法检测数据包的意图

## 使用 IP 片段进行 SYN/FIN 扫描

![](img/198108450322f24970ade227cbf24f47_90_0.png)

![](img/198108450322f24970ade227cbf24f47_90_1.png)

## 数据包分片

数据包分片是指在向网络发送时将探测数据包拆分为多个较小的包（片段）。当这些数据包到达主机时，主机后面的 IDS 和防火墙通常会将它们全部排队并逐一处理。然而，由于这种处理方法涉及更大的 CPU 和网络资源消耗，大多数 IDS 的配置会导致它们在端口扫描期间跳过分片数据包。

因此，攻击者使用 Nmap 和 fragroute 等数据包分片工具将探测数据包拆分为较小的包，以规避 IDS 采用的端口扫描技术。一旦这些片段到达目标主机，它们将被重新组装成单个数据包。

## 使用 IP 片段进行 SYN/FIN 扫描

使用 IP 片段进行 SYN/FIN 扫描不是一种新的扫描方法，而是之前技术的修改。这种扫描过程是为了避免由于目标系统上的数据包过滤设备而产生的其他扫描产生的误报。TCP 头部被拆分为多个数据包以规避数据包过滤器。对于任何传输，每个 TCP 头部必须具有初始数据包的源端口和目标端口（8 字节，64 位）。下一数据包中初始化的标志允许远程主机通过 Internet 协议模块在接收时重新组装数据包，该模块使用源、目标、协议和标识的字段等值检测分片数据包。


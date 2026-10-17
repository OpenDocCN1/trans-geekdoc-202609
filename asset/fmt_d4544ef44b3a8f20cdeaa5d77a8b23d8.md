
```
C:\Users\PC-A> ipconfig
Windows IP Configuration
(Output omitted)
Wireless LAN adapter Wi-Fi:
    Connection-specific DNS Suffix  . :
    Link-local IPv6 Address . . . . . : fe80::a4aa:2dd1:ae2d:a75e%16
    IPv4 Address . . . . . . . . . . : 192.168.10.10
    Subnet Mask . . . . . . . . . . . : 255.255.255.0
    Default Gateway . . . . . . . . . : 192.168.10.1
(Output omitted)
```

### 默认网关问题 (17.7.4)

终端设备的默认网关是可以将流量转发到其他网络的最接近的网络设备。如果设备的默认网关地址不正确或不存在，则无法与远程网络中的设备通信。由于默认网关是通往远程网络的路径，其地址必须属于与终端设备相同的网络。

默认网关的地址可以手动设置或从 DHCP 服务器获取。与 IPv4 地址问题类似，默认网关问题可能与配置错误（手动分配的情况）或 DHCP 问题（自动分配使用时）有关。

为了解决默认网关配置错误问题，请确保设备已配置正确的默认网关。如果默认地址是手动设置但不正确，您只需将其替换为正确的地址即可。如果默认网关地址是自动设置的，则需要确保设备能够与 DHCP 服务器通信。还必须验证路由器的接口上是否已正确配置 IPv4 地址和子网掩码，并且接口处于活动状态。

要验证基于 Windows 的计算机上的默认网关，请使用 `ipconfig` 命令，如示例 17-34 所示。

### 示例 17-34 使用 ipconfig 验证 Windows 主机上的默认网关

```
C:\Users\PC-A> ipconfig
Windows IP Configuration
(Output omitted)
Wireless LAN adapter Wi-Fi:
    Connection-specific DNS Suffix . . :
    Link-local IPv6 Address . . . . . : fe80::a4aa:2dd1:ae2d:a75e%16
    IPv4 Address. . . . . . . . . . : 192.168.10.10
    Subnet Mask . . . . . . . . . . : 255.255.255.0
    Default Gateway . . . . . . . . : 192.168.10.1
(Output omitted)
```

在路由器上，使用 `show ip route` 命令列出路由表并验证默认网关，也称为默认路由，是否已设置。当数据包的目的地址与路由表中的任何其他路由都不匹配时，就会使用此路由。

示例 17-35 中的输出验证了 R1 已配置默认网关，即最后的网关，并且它指向 IP 地址 209.165.200.226。

在示例 17-35 中，第一条高亮行基本上说明，通往任何地址，即 0.0.0.0 的网关应发送到 IP 地址 209.165.200.226。第二条高亮行显示了 R1 如何获知默认网关。在此情况下，R1 从另一台启用了 OSPF 的路由器接收了该信息。

### 示例 17-35 使用 show ip route 验证路由器上的默认网关

```
R1# show ip route | begin Gateway
Gateway of last resort is 209.165.200.226 to network 0.0.0.0
O*E2  0.0.0.0/0 [110/1] via 209.165.200.226, 02:19:50, GigabitEthernet0/0/0
         10.0.0.0/24 is subnetted, 1 subnets
O         10.1.1.0/24 [110/3] via 209.165.200.226, 02:05:42, GigabitEthernet0/0/0
         192.168.10.0/24 is variably subnetted, 2 subnets, 2 masks
C         192.168.10.0/24 is directly connected, GigabitEthernet0/0/1
L         192.168.10.1/32 is directly connected, GigabitEthernet0/0/1
         209.165.200.0/24 is variably subnetted, 3 subnets, 2 masks
C         209.165.200.224/30 is directly connected, GigabitEthernet0/0/0
L         209.165.200.225/32 is directly connected, GigabitEthernet0/0/0
O         209.165.200.228/30
                [110/2] via 209.165.200.226, 02:07:19, GigabitEthernet0/0/0
R1#
```

## 故障排除 DNS 问题 (17.7.5)

域名系统 DNS 是一种自动服务，可将网站名称，例如 www.cisco.com，与 IP 地址匹配。虽然 DNS 解析对设备通信并非至关重要，但对终端用户非常重要。

用户常常错误地将互联网链路的运行与 DNS 的可用性联系起来。用户投诉，例如“网络已断开”或“互联网已断开”，通常是由无法访问的 DNS 服务器引起的。虽然数据包路由和其他所有网络服务仍在运行，但 DNS 故障常常导致用户得出错误的结论。如果用户在 Web 浏览器中输入域名，例如 www.cisco.com，而 DNS 服务器无法访问，则名称将无法转换为 IP 地址，网站将无法显示。

DNS 服务器地址可以手动或自动分配。网络管理员通常负责在服务器和其他设备上手动分配 DNS 服务器地址，而 DHCP 则用于自动为客户端分配 DNS 服务器地址。

尽管公司和组织管理自己的 DNS 服务器很常见，但任何可访问的 DNS 服务器都可用于解析名称。小办公和家庭办公 SOHO 用户通常依赖其 ISP 维护的 DNS 服务器进行名称解析。ISP 维护的 DNS 服务器通过 DHCP 分配给 SOHO 客户。此外，Google 维护着一个公共 DNS 服务器，可供任何人使用；它非常适合测试。Google 公共 DNS 服务器的 IPv4 地址是 8.8.8.8，其 IPv6 DNS 地址是 2001:4860:4860::8888。

Cisco 提供 OpenDNS，通过过滤钓鱼网站和某些恶意软件网站提供安全的 DNS 服务。您可以在首选 DNS 服务器和备用 DNS 服务器字段中将 DNS 地址更改为 208.67.222.222 和 208.67.220.220。家庭和企业可使用诸如 Web 内容过滤和安全等高级功能。

使用 `ipconfig /all` 命令，如示例 17-36 所示，以验证 Windows 计算机正在使用哪个 DNS 服务器。

### 示例 17-36 使用 ipconfig /all 验证 Windows 主机上使用的 DNS 服务器

```
C:\Users\PC-A> ipconfig /all
(Output omitted)
Wireless LAN adapter Wi-Fi:
    Connection-specific DNS Suffix  . . : 
    Description . . . . . . . . . . . : Intel(R) Dual Band Wireless-AC 8265
    Physical Address. . . . . . . . . : F8-94-C2-E4-C5-0A
    DHCP Enabled. . . . . . . . . . . : Yes
    Autoconfiguration Enabled . . . . : Yes
    Link-local IPv6 Address . . . . . : fe80::a4aa:2dd1:ae2d:a75e%16(Preferred)
    IPv4 Address. . . . . . . . . . . : 192.168.10.10(Preferred)
    Subnet Mask . . . . . . . . . . . : 255.255.255.0
    Lease Obtained. . . . . . . . . . : August 17, 2019 1:20:17 PM
    Lease Expires . . . . . . . . . . : August 18, 2019 1:20:18 PM
    Default Gateway . . . . . . . . . : 192.168.10.1
    DHCP Server . . . . . . . . . . . : 192.168.10.1
    DHCPv6 IAID . . . . . . . . . . . : 100177090
    DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-21-F3-76-75-54-E1-AD-DE-DA-9A
    DNS Servers . . . . . . . . . . . : 208.67.222.222
    NetBIOS over Tcpip. . . . . . . . : Enabled
(Output omitted)
```

`nslookup` 命令是 PC 上另一个有用的 DNS 故障排除工具。通过 `nslookup`，用户可以手动发出 DNS 查询并分析 DNS 响应。示例 17-37 中的 `nslookup` 命令显示了对 www.cisco.com 的查询输出。请注意，您也可以直接输入 IP 地址，`nslookup` 将解析其名称。

### 注意

由于各种原因，并非总能输入 IP 地址到 `nslookup` 中并获得域名。其中最常见的原因之一是大多数网站运行在支持多个站点的服务器上。

## 示例 17-37 在 Windows 主机上使用 nslookup 验证 DNS 信息

```
C:\Users\PC-A> nslookup
Default Server:  Home-Net
Address:  192.168.1.1
> cisco.com
Server:  Home-Net
Address:  192.168.1.1
Non-authoritative answer:
Name:    cisco.com
Addresses:  2001:420:1101:1::185
          72.163.4.185
> 8.8.8.8
Server:  Home-Net
Address:  192.168.1.1
Name:    dns.google
Address:  8.8.8.8
>
> 208.67.222.222
Server:  Home-Net
Address:  192.168.1.1
Name:    resolver1.opendns.com
Address:  208.67.222.222
>
```

![](img/e71dc48d3ae3db3394e5857ab2acae75_659_0.png)

## 实验——排查连接问题 (17.7.6)

在本实验中，您将完成以下目标：

- 识别问题
- 实施网络更改
- 验证完整功能
- 记录发现和配置更改

![](img/e71dc48d3ae3db3394e5857ab2acae75_659_1.png)

## Packet Tracer——排查连接问题 (17.7.7)

本 Packet Tracer 活动的目标是排查并解决连接问题，如果可能的话。否则，问题应清楚地记录下来以便升级。

## 摘要 (17.8)

以下是本章主题及其对应在线模块的摘要。

### 小型网络中的设备

小型网络通常具有由 DSL、电缆或以太网连接提供的单个 WAN 连接。小型网络由本地 IT 技术人员或外聘专业人员管理。选择小型网络设备时需要考虑的因素包括成本、速度、端口/接口类型、可扩展性以及操作系统功能和服务。在实施网络时，创建 IP 地址方案并将其用于终端设备、服务器和外围设备以及中间设备。冗余可以通过安装重复设备来实现，但也可以通过为关键区域提供重复的网络链路来实现。小型网络中的路由器和交换机应配置为以相对于其他数据流量的适当方式支持实时流量，例如语音和视频。事实上，一个良好的网络设计会实施服务质量 QoS 以根据优先级仔细分类流量。

### 小型网络应用程序和协议

网络应用程序和应用层服务这两种形式的软件程序或进程提供对网络的访问。一些终端用户应用程序实现应用层协议，能够直接与协议栈的下层通信。电子邮件客户端和网页浏览器是这种类型应用程序的示例。其他程序可能需要应用层服务的帮助才能使用网络资源，例如文件传输或网络打印池。这些程序与网络接口并准备数据以进行传输。两种最常见的远程访问解决方案是 Telnet 和安全外壳 SSH。SSH 是 Telnet 的安全替代方案。网络管理员还必须支持常见的网络服务器及其所需的关联网络协议，例如 Web 服务器、电子邮件服务器、FTP 服务器、DHCP 服务器和 DNS 服务器。如今，企业越来越多地使用 IP 电话和流媒体与客户和业务合作伙伴进行通信。这些是实时应用程序。因此，网络基础设施必须支持 VoIP、IP 电话和其他实时应用程序。

### 扩展到更大网络

要扩展网络，需要以下几个要素：网络文档、设备清单、预算和流量分析。了解跨越网络的流量类型以及当前流量流向非常重要。在高峰利用时段捕获流量，以获得不同流量类型的良好代表，并在不同的网络段和设备上进行捕获，因为某些流量将本地化于特定段。网络管理员必须了解网络使用情况的变化。员工计算机的使用详情可以用 Windows 任务管理器、事件查看器和数据使用情况等工具进行“快照”捕获。

### 验证连接

使用 `ping` 命令是快速测试源 IP 地址与目标 IP 地址之间第三层连接的最有效方法。该命令还显示各种往返时间统计信息。Cisco IOS 提供 `ping` 命令的“扩展”模式，使用户可以通过调整与命令操作相关的参数来创建特殊类型的 ping。扩展 ping 在特权 EXEC 模式下通过键入不带目标 IP 地址的 `ping` 进入。`traceroute` 可帮助定位网络中第三层问题区域。跟踪返回数据包在网络中路由时经过的跳数列表。它用于识别路径中出现问题的点。在 Windows 中，命令为 `tracert`，而在 Cisco IOS 中等效命令为 `traceroute`。还有扩展 `traceroute` 命令。它允许管理员调整与命令操作相关的参数。网络命令的输出为网络基线提供数据。建立基线的一种方法是复制并粘贴执行 `ping`、`traceroute` 或其他相关命令的结果到文本文件中。这些文本文件可以用日期时间戳，并保存到存档中以便以后检索和比较。

### 主机和 IOS 命令

网络管理员通过发出 `ipconfig` 命令在 Windows 主机上查看 IP 地址信息（地址、掩码、路由器和 DNS）。其他必要命令是 `ipconfig /all`、`ipconfig /release` 和 `ipconfig /renew`，以及 `ipconfig /displaydns`。在 Linux 机器上使用 GUI 验证 IP 设置因 Linux 发行版（distro）和桌面界面而异。必要命令是 `ifconfig` 和 `ip address`。在 Mac 主机的 GUI 中，打开网络偏好设置 > 高级以获取 IP 地址信息。Mac 的其他 IP 地址命令是 `ifconfig`、`networksetup -listallnetworkservices` 和 `networksetup -getinfo <network service>`。从 Windows、Linux 或 Mac 命令提示符执行的 `arp` 命令列出主机 ARP 缓存中当前的所有设备，并包括每个设备的 IPv4 地址、物理地址和寻址类型（静态/动态）。`arp -a` 命令显示已知的 IP 地址和 MAC 地址绑定。常见的 show 命令有 `show running-config`、`show interfaces`、`show ip address`、`show arp`、`show ip route`、`show protocols` 和 `show version`。`show cdp neighbor` 命令提供有关每个 CDP 邻居设备的以下信息：标识符、地址列表、端口标识符、功能列表和平台。`show cdp neighbors detail` 命令有助于确定 CDP 邻居之一是否存在 IP 配置错误。`show ip interface brief` 命令输出显示路由器上的所有接口、分配给每个接口的 IP 地址（如果有）以及接口的运行状态。

### 故障排除方法

- **步骤 1.** 识别问题。
- **步骤 2.** 建立可能原因的理论。
- **步骤 3.** 测试理论以确定原因。
- **步骤 4.** 建立行动计划并实施解决方案。
- **步骤 5.** 验证解决方案并实施预防措施。
- **步骤 6.** 记录发现、操作和结果。

当问题需要经理的决定、某些特定专业知识或故障排除技术人员无法获得的网络访问级别时，应升级问题。操作系统进程、协议、机制和事件会生成消息以传达其状态。IOS `debug` 命令允许管理员实时显示这些消息以供分析。要在终端（虚拟控制台）上显示日志消息，请使用 `terminal monitor` 特权 EXEC 命令。

### 故障排除场景

存在两种双工通信模式：半双工和全双工。如果两个连接设备中的一个以全双工运行而另一个以半双工运行，则会发生双工不匹配。虽然可以通过存在双工不匹配的链路进行数据通信，但链路性能非常差。

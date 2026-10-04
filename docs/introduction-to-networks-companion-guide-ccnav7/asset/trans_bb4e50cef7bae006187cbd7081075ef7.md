
## 终端设备上的 IP 地址问题 (17.7.3)

在基于 Windows 的机器上，当设备无法联系到 DHCP 服务器时，Windows 会自动分配一个属于 169.254.0.0/16 范围的地址。这种自动寻址称为自动专用 IP 地址分配 (APIPA)，旨在促进本地网络内的通信。可以将其理解为 Windows 在说：“我将使用来自 169.254.0.0/16 范围的此地址，因为我无法获取其他地址。”

通常，具有 APIPA 地址的计算机无法与其他网络设备通信，因为这些设备很可能不属于 169.254.0.0/16 网络。这种情况表明存在应予修复的自动 IPv4 地址分配问题。

### 注意

其他操作系统，例如 Linux 和 macOS，如果与 DHCP 服务器的通信失败，则不会为网络接口分配 IPv4 地址。

大多数终端设备配置为依赖 DHCP 服务器进行自动 IPv4 地址分配。如果设备无法与 DHCP 服务器通信，服务器就无法为特定网络分配 IPv4 地址，并且设备无法通信。

要验证分配给基于 Windows 的计算机的 IP 地址，请使用 ipconfig 命令，如示例 17-33 所示。

### 示例 17-33 使用 ipconfig 验证 Windows 主机上的 IPv4 地址

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

## 默认网关问题 (17.7.4)

终端设备的默认网关是可以将流量转发到其他网络的最接近的网络设备。如果设备的默认网关地址不正确或不存在，则无法与远程网络中的设备通信。由于默认网关是通往远程网络的路径，其地址必须属于与终端设备相同的网络。

默认网关的地址可以手动设置或从 DHCP 服务器获取。与 IPv4 地址问题类似，默认网关问题可能与配置错误（手动分配的情况）或 DHCP 问题（自动分配使用时）有关。

为了解决默认网关配置错误问题，请确保设备已配置正确的默认网关。如果默认地址是手动设置但不正确，您只需将其替换为正确的地址即可。如果默认网关地址是自动设置的，则需要确保设备能够与 DHCP 服务器通信。还必须验证路由器的接口上是否已正确配置 IPv4 地址和子网掩码，并且接口处于活动状态。

要验证基于 Windows 的计算机上的默认网关，请使用 ipconfig 命令，如示例 17-34 所示。

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

在路由器上，使用 show ip route 命令列出路由表并验证默认网关，也称为默认路由，是否已设置。当数据包的目的地址与路由表中的任何其他路由都不匹配时，就会使用此路由。

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

使用 ipconfig /all 命令，如示例 17-36 所示，以验证 Windows 计算机正在使用哪个 DNS 服务器。

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

nslookup 命令是 PC 上另一个有用的 DNS 故障排除工具。通过 nslookup，用户可以手动发出 DNS 查询并分析 DNS 响应。示例 17-37 中的 nslookup 命令显示了对 www.cisco.com 的查询输出。请注意，您也可以直接输入 IP 地址，nslookup 将解析其名称。

### 注意

由于各种原因，并非总能输入 IP 地址到 nslookup 中并获得域名。其中最常见的原因之一是大多数网站运行在支持多个站点的服务器上。

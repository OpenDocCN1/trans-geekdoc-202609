
```
R1# show ip interface
GigabitEthernet0/0/0 is up, line protocol is up
  Internet address is 209.165.200.225/30
  Broadcast address is 255.255.255.255
  Address determined by setup command
  MTU is 1500 bytes
  Helper address is not set
  Directed broadcast forwarding is disabled
  Multicast reserved groups joined: 224.0.0.5 224.0.0.6
  Outgoing Common access list is not set
  Outgoing access list is not set
  Inbound Common access list is not set
  Inbound access list is not set
  Proxy ARP is enabled
  Local Proxy ARP is disabled
  Security level is default
  Split horizon is enabled
  ICMP redirects are always sent
  ICMP unreachables are always sent
  ICMP mask replies are never sent
IP fast switching is enabled
IP Flow switching is disabled
IP CEF switching is enabled
IP CEF switching turbo vector
IP Null turbo vector
Associated unicast routing topologies:
    Topology "base", operation state is UP
IP multicast fast switching is enabled
IP multicast distributed fast switching is disabled
IP route-cache flags are Fast, CEF
Router Discovery is disabled
IP output packet accounting is disabled
IP access violation accounting is disabled
TCP/IP header compression is disabled
RTP/IP header compression is disabled
Probe proxy name replies are disabled
Policy routing is disabled
Network address translation is disabled
BGP Policy Mapping is disabled
Input features: MCI Check
IPv4 WCCP Redirect outbound is disabled
IPv4 WCCP Redirect inbound is disabled
IPv4 WCCP Redirect exclude is disabled
GigabitEthernet0/0/1 is up, line protocol is up

(Output omitted)
```

如示例 17-22 所示，`show arp` 命令用于验证本地以太网 LAN 上已知主机的列表。

## 示例 17-22 show arp 命令

`R1# show arp`

| 协议 | 地址 | 年龄（分钟） | 硬件地址 | 类型 | 接口 |
|---|---|---|---|---|---|
| Internet | 192.168.10.1 | - | a0e0.af0d.e141 | ARPA | GigabitEthernet0/0/1 |
| Internet | 192.168.10.10 | 95 | c07b.bcc4.a9c0 | ARPA | GigabitEthernet0/0/1 |
| Internet | 209.165.200.225 | - | a0e0.af0d.e140 | ARPA | GigabitEthernet0/0/0 |
| Internet | 209.165.200.226 | 138 | a03d.6fe1.9d90 | ARPA | GigabitEthernet0/0/0 |

`R1#`

如示例 17-23 所示，`show ip route` 命令用于验证第 3 层路由信息。

## 示例 17-23 show ip route 命令

```
R1# show ip route
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
    D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
    N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
    E1 - OSPF external type 1, E2 - OSPF external type 2
    i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
    ia - IS-IS inter area, * - candidate default, U - per-user static route
    o - ODR, P - periodic downloaded static route, H - NHRP, l - LISP
    a - application route
    + - replicated route, & - next hop override, p - overrides from PfR
Gateway of last resort is 209.165.200.226 to network 0.0.0.0
O*E2  0.0.0.0/0 [110/1] via 209.165.200.226, 02:19:50, GigabitEthernet0/0/0
        10.0.0.0/24 is subnetted, 1 subnets
O       10.1.1.0 [110/3] via 209.165.200.226, 02:05:42, GigabitEthernet0/0/0
        192.168.10.0/24 is variably subnetted, 2 subnets, 2 masks
C           192.168.10.0/24 is directly connected, GigabitEthernet0/0/1
L           192.168.10.1/32 is directly connected, GigabitEthernet0/0/1
        209.165.200.0/24 is variably subnetted, 3 subnets, 2 masks
C           209.165.200.224/30 is directly connected, GigabitEthernet0/0/0
L           209.165.200.225/32 is directly connected, GigabitEthernet0/0/0
O           209.165.200.228/30
                [110/2] via 209.165.200.226, 02:07:19, GigabitEthernet0/0/0
R1#
```

如示例 17-24 所示，`show protocols` 命令用于验证哪些协议处于运行状态。

## 示例 17-24 show protocols 命令

```
R1# show protocols
Global values:
    Internet Protocol routing is enabled
GigabitEthernet0/0/0 is up, line protocol is up
    Internet address is 209.165.200.225/30
GigabitEthernet0/0/1 is up, line protocol is up
    Internet address is 192.168.10.1/24
Serial0/1/0 is down, line protocol is down
Serial0/1/1 is down, line protocol is down
GigabitEthernet0 is administratively down, line protocol is down
R1#
```

如示例 17-25 所示，`show version` 命令用于验证设备的内存、接口和许可证。

## 示例 17-25 show version 命令

```
R1# show version
Cisco IOS XE Software, Version 03.16.08.S - Extended Support Release
Cisco IOS Software, ISR Software (X86_64-LINUX-IOSD-UNIVERSALK9-M), Version 15.5(3)S8, RELEASE SOFTWARE (fc2)
Technical Support: http://www.cisco.com/techsupport
Copyright (c) 1986-2018 by Cisco Systems, Inc.
Compiled Wed 08-Aug-18 10:48 by mcpre

(Output omitted)

ROM: IOS-XE ROMMON
R1 uptime is 2 hours, 25 minutes
Uptime for this control processor is 2 hours, 27 minutes
System returned to ROM by reload
System image file is "bootflash:/isr4300-universalk9.03.16.08.S.155-3.S8-ext.SPA.bin"
Last reload reason: LocalSoft

(Output omitted)

Technology Package License Information:
```

| 技术 | 技术包 | 当前类型 | 下次重启 |
|---|---|---|---|
| appxk9 | appxk9 | RightToUse | appxk9 |
| uck9 | None | None | None |
| securityk9 | securityk9 | Permanent | securityk9 |
| ipbase | ipbasek9 | Permanent | ipbasek9 |

cisco ISR4321/K9 (1RU) processor with 1647778K/6147K bytes of memory.

Processor board ID FLM2044W0LT

2 Gigabit Ethernet interfaces

2 Serial interfaces

32768K bytes of non-volatile configuration memory.

4194304K bytes of physical memory.

3207167K bytes of flash memory at bootflash:.

978928K bytes of USB flash at usb0:.

Configuration register is 0x2102

R1#

## show cdp neighbors 命令 (17.5.6)

除了本章迄今为止讨论的命令之外，还有其他一些有用的 IOS 命令。Cisco Discovery Protocol（CDP）是一种在数据链路层运行的思科专有协议。由于 CDP 在数据链路层运行，因此两个或多个思科网络设备，例如支持不同网络层协议的路由器，即使第 3 层连接尚未建立也可以相互了解。

当思科设备启动时，CDP 默认启动。CDP 会自动发现运行 CDP 的邻近思科设备，而不管运行哪些第 3 层协议或套件。CDP 与直接连接的 CDP 邻居交换硬件和软件设备信息。

CDP 提供有关每个 CDP 邻居设备的以下信息：

- `设备标识符：` 交换机、路由器或其他设备的配置主机名
- `地址列表：` 每个受支持协议的一个网络层地址
- `端口标识符：` 本地和远程端口的名称，以 ASCII 字符字符串的形式表示，例如 FastEthernet 0/0
- `功能列表：` 功能，例如特定设备是第 2 层交换机还是第 3 层交换机
- `平台：` 设备的硬件平台（例如思科 1841 系列路由器）

请参阅图 17-21 中的拓扑以及示例 17-26 中的 `show cdp neighbors` 命令输出。

![](img/e71dc48d3ae3db3394e5857ab2acae75_645_0.png)

图 17-21 CDP 邻居示例拓扑

## 示例 17-26 show cdp neighbors 命令

`R3# show cdp neighbors`

Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge

                S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone,

                D - Remote, C - CVTA, M - Two-port Mac Relay

| 设备 ID | 本地接口 | 保持时间 | 功能 | 平台 | 端口 ID |
|---|---|---|---|---|---|
| S3 | Gig 0/0/1 | 122 | S I | WS-C2960+ | Fas 0/5 |

Total cdp entries displayed : 1

`R3#`

示例 17-26 中的输出显示，R3 的 GigabitEthernet 0/0/1 接口连接到 S3 的 FastEthernet 0/5 接口，而 S3 是一台 Cisco Catalyst 2960+ 交换机。请注意，R3 并未收集到关于 S4 的信息。这是因为 CDP 只能发现直接连接的 Cisco 设备。S4 并未直接连接到 R3，因此未列在输出中。

`show cdp neighbors detail` 命令会显示邻居设备的 IP 地址。无论是否可以 ping 该邻居，此命令都会显示邻居的 IP 地址。当两台 Cisco 路由器无法通过其共享的数据链路路由时，此命令非常有帮助。`show cdp neighbors detail` 命令有助于确定 CDP 邻居中是否有一台存在 IP 配置错误。

CDP 虽然很有帮助，但也可能构成安全风险，因为它可以向威胁行为者提供有用的网络基础设施信息。例如，默认情况下，许多 IOS 版本会通过所有已启用的端口发送 CDP 广告。然而，最佳实践建议仅在连接到其他基础设施 Cisco 设备的接口上启用 CDP。应在面向用户的端口上禁用 CDP 广告。

由于某些 IOS 版本默认会发送 CDP 广告，因此了解如何禁用 CDP 很重要。要全局禁用 CDP，请使用全局配置命令 `no cdp run`。要在接口上禁用 CDP，请使用接口命令 `no cdp enable`。

## show ip interface brief 命令 (17.5.7)

最常用的命令之一是 `show ip interface brief` 命令。此命令比 `show ip interface` 命令提供的输出更简略。它为路由器上的所有网络接口提供关键信息的摘要。

在示例 17-27 中，`show ip interface brief` 输出显示路由器上的所有接口、分配给每个接口的 IP 地址（如有）以及接口的运行状态。

### 示例 17-27 路由器上的 show ip interface brief 命令

```
R1# show ip interface brief
Interface              IP-Address      OK? Method Status                Protocol
GigabitEthernet0/0/0   209.165.200.225 YES manual    up                    up
GigabitEthernet0/0/1   192.168.10.1    YES manual    up                    up
Serial0/1/0            unassigned      NO  unset     down                  down
Serial0/1/1            unassigned      NO  unset     down                  down
GigabitEthernet0       unassigned      YES unset     administratively down down
R1#
```

## 验证交换机接口

`show ip interface brief` 命令可用于验证交换机接口的状态，如示例 17-28 所示。

### 示例 17-28 交换机上的 show ip interface brief 命令



# MAC 地址示例

注意，我们选择的示例是示例地址。媒体访问控制（MAC）地址是一个全局唯一的标识符，表示为一个长十六进制数字字符串，通常用连字符分隔成部分。这些地址通常由电气电子工程师学会（IEEE）以池的形式分配给供应商。

## IPv4：地址解析协议

这就是地址解析协议（ARP）登场来展现全貌的地方。ARP 是一种以太网广播。从技术上讲，所有的以太网数据包都会在子网中广播，但大多数数据包带有目的地址，并在被其他以太网卡接收时被丢弃。以太网广播数据包旨在被任何以太网卡接收。

ARP 数据包包含请求者的源 MAC 地址及其正在查找的 IP 地址。该网段上的每个以太网卡都会接收此请求，并将其转发到其 IP 层。该层将检查自己是否拥有被请求的 IP 地址。拥有该 IP 地址的接口将向请求地址的所有者做出肯定响应。

请求者接收此响应并将 ARP 表地址与以太网地址关联。你可以在任何 Windows 中使用多种不同的方法查看此 ARP 表。最容易记忆的可能是命令 `-a`，它显示分配给网卡的地址，如图 20.2 所示。

图 20.2
显示 ARP 表

```
C:\Users\john>arp -a
Interface 192.168.0.1
Address            Physical Address      Type
192.168.0.1         00-0c-29-bd-38-fd     dynamic
192.168.0.1         00-00-5e-00-01-ed     static
192.168.0.255       ff-ff-ff-ff-ff-ff     static
192.168.0.2         00-00-5e-00-01-00     static
192.168.0.3         00-00-5e-00-01-03     static
192.168.0.4         00-00-5e-00-01-0fd     static
255.255.255.255     ff-ff-ff-ff-ff-ff     static
```

与大多数网络设施一样，你也可以使用 `netstat` 命令查看此表，即 `netstat interface ipv4`，如图 20.3 所示。

在此示例中，A 处的 IP 计算机将创建一个数据包，发送：“我是 192.168.0.1，我想知道 IP 为 192.168.0.3 的接口的 MAC 地址。”计算机 A 随后会“大喊”，网段内的大多数机器会停止手头工作，检查自己的 IP 地址看自己是否是 192.168.0.3，并且只有一个（C）会向 A 发送响应，说：“我是来自 IP 192.168.0.3 机器的 ARP 响应数据包，我的 MAC 地址是 00:01:CA:FE:D5:03。”

有时你必须清除 ARP 表中的条目以执行此操作，请使用 `arp -d inet_addr_`（其中 `_addr_` 是你想删除的 IP 地址）来重新发送广播。你可以使用帮助开关 `arp -` 探索更多的 ARP 选项。

## 图 20.3
使用 netsh 显示邻居表

IP 数据包的生命 1029

```
C:\Users\john>netsh interface ipv4 show neighbors
Interface 1: Loopback Pseudo-Interface 1
```

| Internet Address | Physical Address | Type |
| --- | --- | --- |
| 224.0.0.12 | | Permanent |
| 224.0.0.252 | | Permanent |
| 224.0.0.250 | | Permanent |
| 255.255.255.255 | | Permanent |

Interface 12: Wi-Fi

| Internet Address | Physical Address | Type |
| --- | --- | --- |
| 192.168.1.1 | cc-5d-d4-e6-f7-f8 | Reachable |
| 192.168.1.2 | 18-a7-05-9d-bb-a4 | Reachable |
| 192.168.1.3 | fe-b3-44-83-8b-8b | Reachable |
| 192.168.1.4 | ff-00-00-00-00-00 | Reachable |
| 192.168.1.255 | ff-ff-ff-ff-ff-ff | Permanent |
| 224.0.0.1 | 01-00-5e-00-00-01 | Permanent |
| 224.0.0.252 | 01-00-5e-00-00-f2 | Permanent |
| 224.0.0.250 | 01-00-5e-00-00-f6 | Permanent |
| 255.255.255.250 | 01-00-5e-00-00-f4 | Permanent |
| 255.255.255.255 | ff-ff-ff-ff-ff-ff | Permanent |

Interface 13: Bluetooth Connection

| Internet Address | Physical Address | Type |
| --- | --- | --- |
| 224.0.0.1 | 01-00-5e-00-00-01 | Permanent |
| 224.0.0.252 | 01-00-5e-00-00-f2 | Permanent |
| 224.0.0.250 | 01-00-5e-00-00-f6 | Permanent |
C:\Users\john>

## IPv6 邻居发现

在 IPv4 中，子网上的每个计算机的 IP 层都需要知道该如何处理入站请求。你知道让每个人都停止工作会有多么烦人，但如果你不小心，仍然会遇到糟糕的广播风。IPv6 取代了基于广播的 ARP，改为基于组播的邻居发现（ND），它向目的地址 `ff02::` 发送邻居请求消息。因为最后 24 位有超过 1600 万种可能性，几乎可以确定此消息只会中断请求该 IP 地址的网卡，防止重复发送相同的邻居请求消息。要显示 IPv6 的邻居，你可以使用 ARP 命令吗？不，获取 IPv6 层的邻居表的唯一方法是运行 `netsh` 命令，特别是 `netsh interface ipv6 show neighbors`；局域连接的示例见图 20.4。

## 图 20.4. 显示 IPv6 邻居表

| Internet Address | Physical Address | Type |
| --- | --- | --- |
| fe80::15fe:a69:254:150:14 | 00-00-56-d2:a6:96 | Unreachable |
| fe80::15fe:a69:254:224 | 00-00-56-d2:a6:e0 | Unreachable |
| fe80::15fe:a69:254:364 | 00-00-56-d2:a6:f4 | Unreachable |
| fe80::15fe:a69:254:464 | 00-00-56-d2:a6:93:28 | Unreachable |
| fe80::15fe:a69:254:564 | 00-00-56-d2:a6:93:5c | Unreachable |
| fe80::15fe:a69:254:664 | 00-00-56-d2:a6:93:8b | Unreachable |
| fe80::15fe:a69:254:764 | 00-00-56-d2:a6:93:ca | Unreachable |
| fe80::15fe:a69:254:864 | 33-23-f8-01-00-02 | Permanent |
| fe80::15fe:a69:254:964 | 33-23-f8-01-01-05 | Permanent |
| fe80::15fe:a69:254:a64 | 33-23-f8-01-01-38 | Permanent |
| fe80::15fe:a69:254:b64 | 33-23-f8-01-01-45 | Permanent |
| fe80::15fe:a69:254:c64 | 33-23-f8-01-01-69 | Permanent |
| fe80::15fe:a69:254:d64 | 33-23-f8-01-01-70 | Permanent |
| fe80::15fe:a69:254:e64 | 33-23-f8-01-01-7d | Permanent |
| fe80::15fe:a69:254:f64 | 33-23-f8-01-01-bd | Permanent |

## 终于，你可以发送数据包了！

现在你已经知道是谁在尝试通信了，接口 A 处的计算机可以通过构建以太网数据包来发送数据，其负载是 IP 数据包（IP 头部和负载），其头部包含源地址和目的地址、长度以及协议类型（在此情况下为 IP）。

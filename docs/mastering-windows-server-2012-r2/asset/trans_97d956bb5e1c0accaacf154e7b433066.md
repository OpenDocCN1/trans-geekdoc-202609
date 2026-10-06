

# IP 数据包的生周期

IPv4 路由和 IPv6 路由列表。如果你运行 IPv4 路由查询，可以运行 `route -4 print`；对于 IPv6 路由，可以运行 `route -6 print`。

netsh `netsh` 命令旨在处理所有与网络相关的配置设置，以及未来可能出现的显示项。显示路由表的命令是 `netsh interface ipv4 route` 或 `netsh interface ipv6 route`。

每个命令显示的是相同的路由表，但信息和呈现方式有所不同。`route` 命令显示的是更基于分类的路由表，对许多人来说很熟悉。在本章结束时，你应该能够熟悉如图 20.5 所示的输出，它显示了 IPv4 路由表的示例。

## 图 20.5

使用 print 显示 IPv4 路由表

![](img/41a83208e6906a3732620203b836cea7_1066_0.png)

那两个 `interface ipv6 routes` 路由稍微紧凑一些——如果你不需要接口索引表，这种格式可能正是你需要的。

在两个网络输出中，网络目的都是无分类域间路由（CIDR）格式，我们将在后文中详细描述。图 20.6 显示了 IPv4 路由表，图 20.7 显示了 IPv6 路由表。它们在格式和大小上几乎没有区别。

## 图 20.6

使用 route 查看 IPv4 路由表

![](img/41a83208e6906a3732620203b836cea7_1066_1.png)

## 图 20.7

使用 route
查看
IPv6
路由表

| 类型 | 名称 | 前缀 | 索引 | 网关/接口名称 |
|---|---|---|---|---|
| 系统 | | ::/128 | 1 | Loopback Pendo-Interface |
| 系统 | | 2001::/32 | 15 | Tunnel Pendo-Interface |
| 接口 | | 2001:db85:7f48:304f:c3a6:83c4/64 | 15 | Tunnel Pendo-Interface |
| 接口 | | 2001:db86/64 | 28 | fe80::f18:d662:32c:31e6:236 |
| 接口 | | 2001:db87/64 | 28 | fe80::f18:d662:32c:31e6:236 |
| 接口 | | 2001:db88/64 | 28 | fe80::f18:d662:32c:31e6:236 |
| 接口 | | 2001:db89/64 | 28 | IPHTPS-Interface |
| 接口 | | 2001:db8a/64 | 28 | IPHTPS-Interface |
| 接口 | | 2001:db8b/64 | 28 | IPHTPS-Interface |
| 接口 | | 2001:db8c/64 | 28 | IPHTPS-Interface |
| 接口 | | 2001:db8d:0000:0000/64 | 28 | IPHTPS-Interface |
| 接口 | | 2001:db8e:4000:606f:ce25/128 | 28 | |
| 接口 | | fe80::fada:dad2::40 | 28 | IPHTPS-Interface |
| 接口 | | fe80::fada:dad3::v6 | 28 | Bluetooth Connect |
| 接口 | | fe80::fe64/64 | 12 | Wi-Fi |
| 接口 | | fe80::fe65/64 | 15 | Tunnel Pendo-Interface |
| 接口 | | fe80::fe66/64 | 28 | IPHTPS-Interface |
| 接口 | | 192.168.1.1/32 | 28 | Tunnel Pendo-Interface |
| 接口 | | fe80::304f:c3a6:83c4/64 | 15 | Tunnel Pendo-Interface |
| 接口 | | fe80::253a:11b8:6c/64 | 28 | IPHTPS-Interface |
| 接口 | | fe80::15c5:ff77:d80 | 12 | Wi-Fi |
| 系统 | | ff00::8 | 16 | Tunnel Pendo-Interface |
| 系统 | | ff00::8 | 16 | Bluetooth Connect |
| 系统 | | ff00::8 | 12 | Wi-Fi |

```
> C:\Users\John>
```

如你所见，理解这些有很多困惑。让我们从中选一个输出进行分析。因为这对我们是新的，让我们选择 netsh 的输出。这个输出有六列——发布（Publish）、类型（Type）、跃（Met）、前缀（Prefix）、索引（Idx）和网关/接口名称（Gateway/Interface Name）。以下是每一列的含义：**发布**、**类型**、**跃**、**前缀**、**索引**以及**网关/接口名称**。


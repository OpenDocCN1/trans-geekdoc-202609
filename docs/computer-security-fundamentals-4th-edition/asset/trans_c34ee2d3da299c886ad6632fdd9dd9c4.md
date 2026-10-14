
-   [如图 2.2 所示](#ch02.xhtml#ch02fig02)，下面列出了用于查询计算机配置详细信息的多种选项。最常用的方法可能是 `IPConfig /all`，如 [图 2.3](#ch02.xhtml#ch02fig03) 所示。你可以看到，该选项提供了更多信息。例如，`IPConfig /all` 会显示你的计算机名称、IP 地址获取时间以及更多内容。

![Figure 2.3 IPConfig /all. ¶  ¶ The several options of ipconfig/all command are displayed in a command prompt window. The following are the options: windows ip configuration like host name, node type, Ip routing enabled, primary dns suffix and description, physical address, ip address, autoconfiguration enabled, subnet mask, default gateway, DHCP server of the local area connection. ¶ ](Images/02fig03.jpg)

**Figure 2.3** `IPConfig /all`. ¶ 

#### `Ping`

另一个常用的命令是 `ping`。`ping` 用于向机器发送测试数据包（回显包），以判断机器是否可达以及数据包到达所需时间。这种有用的诊断工具可用于基础黑客技术。在 [图 2.4](#ch02.xhtml#ch02fig04) 中，你可以看到在 [www.yahoo.com](http://www.yahoo.com) 上执行的 `ping` 命令。

![Figure 2.4 Ping.](Images/02fig04.jpg)

**Figure 2.4** `Ping`.

该图表明，向目标发送了 32 字节的回显数据包并收到响应。TTL（Time to Live）项显示数据包在放弃之前应经过的中继跳数。请记住，互联网是由众多相互连接的网络组成的庞大集合。你的数据包很可能不会直接到达目的地，而是经过多个跳跃才能到达。与 `IPConfig` 类似，你可以输入 `ping -?` 查看如何优化 `ping`。

#### `Tracert`

下一个命令是 `tracert`。该命令基本上是 `ping` 的高级版本。`tracert` 不仅告诉你数据包是否到达目的地以及耗时，还会显示它经过的所有中继跳跃。该实用工具在本书后期将非常有用。[图 2.5](#ch02.xhtml#ch02fig05) 展示了向 [www.yahoo.com](http://www.yahoo.com) 的 `tracert`。 (在 Linux 或 UNIX 系统中，该命令称为 `traceroute` 而非 `tracert`。)

![Figure 2.5 Tracert.](Images/02fig05.jpg)

**Figure 2.5** `Tracert`.

使用 `tracert`，你可以以毫秒为单位看到每个中继跳跃的 IP 地址以及到达该步骤所需的时间。知道到达目标所需的步骤很重要，后文将进一步说明。

当然，还有其他网络通信工具可以帮助你。但我们刚刚考察的三个核心工具——`IPConfig`、`ping` 和 `tracert`——是网络管理员的基础，也是必备知识，务必牢记于心。

#### `Netstat`

`Netstat` 是另一个有趣的命令，全称 *network status*。它基本上显示你电脑当前的网络连接。如果看到多个连接，并不意味着黑客已入侵你的电脑。你会看到许多私有 IP 地址，这说明本地网络内部存在通信。如 [图 2.6](#ch02.xhtml#ch02fig06) 所示。

![Figure 2.6 Netstat.](Images/02fig06.jpg)

**Figure 2.6** `Netstat`.

#### `NSLookup`

`nslookup`（全称 *name server lookup*）用于与你的网络 DNS 服务器进行交互。它常用于验证 DNS 服务器是否正常运行，也可用于执行命令。请回顾 [第 1 章](#ch01.xhtml#ch01) “[Introduction to Computer Security](#ch01.xhtml#ch01)”，我们讨论了 DNS 劫持。DNS 劫持的第一步是查看目标 DNS 服务器是否会执行区域传输（zone transfer），且除非是经过认证的另一 DNS 服务器，否则不应这样做。可以使用 `nslookup` 实现，如下所示：

[Click here to view code image](Images/ch02_images.xhtml#p53pro01)

```
run: nslookup
type: ls -d domain_name <enter>
```

你可以在 [图 2.7](#ch02.xhtml#ch02fig07) 中看到基本的 `nslookup` 命令。

![Figure 2.7 nslookup.](Images/02fig07.jpg)

**Figure 2.7** `nslookup`.

#### ARP

地址解析协议（ARP）用于将 IP 地址映射到 MAC 地址。`arp` 命令显示你当前知道的 IP 到 MAC 的映射。[图 2.8](#ch02.xhtml#ch02fig08) 展示了 `arp -a` 命令的使用。

![Figure 2.8 arp –a.](Images/02fig08.jpg)

**Figure 2.8** `arp –a.`

与其他命令一样，ARP 也有多种参数。以下是常见的几种：

*   `-a` 显示当前的 ARP 缓存表。

*   `/g` 的作用同 `/a`。

*   `/d` 从 ARP 缓存表中删除特定条目。

*   `/s` 向 ARP 缓存表中添加静态条目。

#### `Route`

`route` 命令用于查看 IP 路由表。[图 2.9](#ch02.xhtml#ch02fig09) 展示了 `route – print 4` 命令的样本输出。

![Figure 2.9 route print -4.](Images/02fig09.jpg)

**Figure 2.9** `route print -4`.

与大多数命令一样，`route` 也有多种参数。以下是常用参数的总结：

*   `print` 打印特定路由；例如，`print -4` 显示 IPv4 路由表。

*   `add` 添加路由。

*   `delete` 删除路由。

*   `change` 修改路由。

*   `destination` 向特定主机发送命令。

### 其他网络设备

在 [第 1 章](#ch01.xhtml#ch01) 中简要提到的网络设备中，还有许多其他设备用于保护你的电脑免受外部威胁。下面我们将对其中两种进行更详细的介绍：防火墙（firewall）和代理服务器（proxy server）。

*防火墙* 本质上是你的网络与互联网其余部分之间的屏障。个人电脑（PC）可以充当防火墙；在许多情况下，专用路由器也可以充当防火墙。防火墙使用多种技术保护网络，但最常用的策略是包过滤。在包过滤防火墙中，每个入站数据包都会被检查，只有符合你设定的条件的数据包才会被允许通过（通常仅允许特定类型的协议）。

第二种常见的防御设备是 *代理服务器*。代理服务器几乎总是一个独立的计算机。你可能会看到同一台机器同时充当代理服务器和防火墙。代理服务器的作用很简单：它将你的整个网络隐藏在外部世界之外。外部试图探查你的网络时，只能看到代理服务器，看不到实际的机器。当数据包离开你的网络时，它们的头部会被修改，使返回地址显示为代理服务器。相反，你只能通过代理服务器访问外部世界。代理服务器和防火墙提供基本的网络安全，若没有这两者，运行网络将是一大疏忽。我们将在 [第 9 章](#ch09.xhtml#ch09) “[Computer Security Technology](#ch09.xhtml#ch09)” 中更详细地探讨防火墙。

### 高级网络通信主题

本节讨论的主题并非理解本书的必要条件，但能够让你更全面地认识网络。如果你有志于在专业层面深入网络安全，则这部分知识是必备的，并且还需要更多内容。


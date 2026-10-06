

# IPv6 隧道命令

在您的 ISP 不支持原生 IPv6 的情况下，您可能通过使用 IPv6 隧道服务（例如 Hurricane Electric 的服务）来测试 IPv6 访问访问。我们按照以下方式执行并设置隧道（通过 IPv4 传输 IPv6 隧道）：

```
netsh interface ipv6 add v4tunnel IPv6Tunnel myIPv4Address 72.52.104.74
netsh interface ipv6 add address IPv6Tunnel 2001:db8:1234:567:2
netsh interface ipv6 add route ::/ 2001:db8:1234:567:1 publish=yes
netsh interface ipv6 set interface IPv6Tunnel forwarding=enable
netsh interface ipv6 add route 2001:db8:fed:cba9::64 "Local Area Connection"
netsh interface ipv6 set interface "Local Area Connection" forwarding=enable
```

第一条命令从此服务器到 72.52.104.74 创建了隧道本身，运行此命令的服务器现在能够通过此隧道进行 IPv6 通信。第二条命令创建了一个地址并将其分配给隧道，而第三条命令创建了一个路由，如果没有其他更具体的定义，则将流量转发到 IPv6 隧道——/0 是路由中默认网关的 IPv6 占位符。

第四条命令启用 IPv6 隧道的转发功能，以便任何通过隧道进入我们网络其他机器的流量都将转发给它们。第五条命令添加了从此机器到本地网络中其他机器的路由，第六条命令启用了本地网络的转发和广告流量，以便我们能够转发在该网络接收的数据包，并且该网络上的计算机知道我们愿意转发它们的流量。

`proxyport` 的另一个用途是让仅支持 IPv6 流量的应用程序“可用”。同样，选择 HTTP 作为协议，如果您有一个仅支持 IPv4 的新闻阅读器和一个仅支持 IPv6 的新闻服务器，可以使用如下 `proxyport` 命令将两者连接：

```
netsh interface proxyport add v4tov6 119 news6server.com 119
```

然后将您的新闻阅读器设置为 `localhost:119`，它将通过代理连接到 IPv6 新闻服务器！

# 测试与故障排除

您永远不需要这一节，因为我们在本章中提供的信息将帮助您理解 Windows Server 2012 R2 服务器环境下的路由。噢，也许这有点夸张——一些基础的故障排除可以帮助您确定哪台不受您控制的机器在您不知情的情况下被，并且这就是您正在遇到的问题。

# 使用应用程序本身

可以使用许多工具来调试网络状态。使用哪种工具以及何时使用，取决于您尝试修复的问题。始终一样，第一个工具应该是您实际计划使用的工具。假设您正尝试建立 FTP 连接——首先，读取 FTP 客户端给出的错误信息。

如果客户端显示“连接被拒绝”（Connection refused），则客户端从您尝试访问的 IP 地址收到了表面上的 TCP RST。这可能是您和服务器之间存在防火墙的信号，或者服务器应用程序本身可能没有运行。

如果客户端显示“超时”（Timed out），则客户端在多次请求后没有收到任何响应。这意味着在客户端和服务器之间存在“隐身”防火墙，或者服务器计算机目前无法访问，可能是因为没有它的网络路由，或者计算机当前没有运行。

# 避免隐身防火墙

尽管安全支持者建议使用隐身防火墙，但我们并不这样做。隐身防火墙会对意外的入站请求做出响应，但倾向于保持沉默。“走开，不要跟我说话”的适当 TCP 表达式是 TCP RST；传统上沉默意味着“稍后再试”。RST 不仅会限制意外连接重试，还会防止他人使用 IP 欺骗来伪装服务器。如果正在进行 IP 欺骗会话，通用服务器将收到 SYN，而响应的 RST 将导致客户端中止连接。如果没有 RST，客户端将继续连接伪造的服务器，这是一种安全风险。

# 使用 ping 探测远程计算机

`ping` 是我们许多人已经使用了几十年的经典工具。它的设计没有太大变化，但基本原理向远程机器发送一个数据包，远程机器应该回复，并等待回复以指示是否成功。Windows Server 2012 R2 仍然使用“经典”方法向远程机器发送 ICMP echo 回显（带有额外数据 "abcdefghijklmnopqruvabcdefgh"）并等待 ICMP echo 回传。

因此，记住这一点很重要：`ping` 只测试 ICMP echo 连通性；它并不测试到服务器端口的 TCP 连接。只有到服务器端口的 TCP 连接才有效（我们之前建议您的调试工具就是您自己），所以，正如您可以通过先 ping 来证明的那样，许多防火墙阻止了 ICMP echo 服务器，因此您可以通过网络浏览器连接 microsoft.com 来证明，`ping` 失败并不意味着结果失败。

成功的 `ping` 表示某些消息正在响应您的查询。您还可以使用 `ping` 命令的输出来确保您正在将名称解析为 IP 地址。`nsLookup` 工具允许您查询名称。`ping` 有以下参数数组，最有用的是：

- -t: 持续 ping 直到停止为止。
- -4: 强制使用 IPv4。
- -6: 强制使用 IPv6。

# 使用 traceroute 探测远程计算机

`traceroute` 的工作方式与 `ping` 类似，它会发送 ICMP echo 请求并等待 ICMP 回复。不同之处在于 `traceroute` 在发出的请求上设置了 TTL（跳数）。路由器在通过它们时会减少跳数，`traceroute` 报告第一个路由器的地址。同样，第二个数据包显示第二个路由器的位置，依此类推。某些路由器未配置为响应此类信息，或者回复会被视为“超时”。当您看到连续多个超时时，通常表示超时开始之前的最后一个路由器无法向您的目标转发数据包。

正如您从图 20.24 的 `ping` 输出所示，在世界上该地区 www.microsoft.com 的主机是 `lbl.ms.akdns.net`。如果您重现此测试，可能会有所不同。我们已经通过尝试 ping 此主机获知，它不回答 ICMP 请求，并且由于某种原因，跳数为 14 或更多的数据包不会收到回显或错误回复。

# 图 20.24
通往微软网站的路由

```
C:\Users>tracerert www.microsoft.com
tracing the route to lbl.ms.akdns.net [64.4.11.42]
over a maximum of 30 hops:
  1  ms      ms      ms  192.168.1.1
  2  36ms     35ms     35ms 10.0.0.1
  3  37ms     40ms     46ms 1.1.1.1
  4  36ms     37ms     39ms lbl.ms.akdns.net (89.127.179.106)
  5  *           Request timed out.
  6  *           Request timed out.
  7  *           Request timed out.
  8  *           Request timed out.
  9  *           Request timed out.
 10 *           Request timed out.
 11 *           Request timed out.
 12 *           Request timed out.
 13 *           Request timed out.
 14 *           Request timed out.
 15 *           Request timed out.
 16 *           Request timed out.
C:\Users>_
```


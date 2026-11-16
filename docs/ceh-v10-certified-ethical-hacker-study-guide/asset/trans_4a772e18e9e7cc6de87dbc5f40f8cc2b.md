

## Ettercap DNS Spoof Log (continued)

```
SEND L3 ERROR: 83 byte packet (0800:06) destined to 192.168.86.26 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Network is unreachable))
)
SEND L3 ERROR: 52 byte packet (0800:06) destined to 192.168.86.26 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Network is unreachable))
)
SEND L3 ERROR: 52 byte packet (0800:06) destined to 192.168.86.26 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Network is unreachable))
)
SEND L3 ERROR: 48 byte packet (0800:11) destined to 192.168.86.26 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Network is unreachable))
)
SEND L3 ERROR: 48 byte packet (0800:11) destined to 192.168.86.26 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Network is unreachable))
)
SEND L3 ERROR: 48 byte packet (0800:11) destined to 192.168.86.26 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Network is unreachable))
)
SEND L3 ERROR: 52 byte packet (0800:06) destined to 192.168.86.26 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Network is unreachable))
)
SEND L3 ERROR: 245 byte packet (0800:06) destined to 192.168.86.26 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Network is unreachable))
)
DHCP: [192.168.86.1] ACK : 192.168.86.43 255.255.255.0 GW 192.168.86.1 DNS
192.168.86.1 "lan"
dns_spoof: A [browser.pipe.aria.microsoft.com] spoofed to [107.170.40.56]
```

即使 DNS 请求确实发送到了合法的 DNS 服务器并得到了响应，这种方法之所以有效，是因为 DNS 使用 UDP，因此无需建立连接。基于 UDP 的请求会发送出去，基于 UDP 的响应会返回。一个系统可能会发送多个请求，因为它们是 UDP，且无法保证请求会到达 DNS 服务器。请求系统接收到的第一个响应将被使用。由于 Ettercap 系统在本地网络上，而 DNS 服务器很可能不在本地网络上，因此来自 Ettercap 系统的 DNS 响应应该是第一个返回的。对请求系统的任何后续响应都将被忽略。到那时，etter.dns 中配置的地址已发送回请求系统并填充了该系统上的 DNS 缓存。

## sslstrip

在捕获流量方面，加密消息是一个问题。加密旨在实现端到端传输，这意味着无法在中间插入。任何试图在中间插入的机制都会违背大多数加密方案所期望的端到端特性。

话虽如此，作为道德黑客，试图违反规则和破坏事物是我们的本性。有办法尝试破解加密协议。当然，在使用 SSL 时代，这要容易得多。SSL 在 TLS 出现之前的不同版本中存在多个漏洞。即使 TLS 被引入以取代 SSL（因为 SSL 的漏洞），早期的 TLS 版本也有漏洞，使得加密可能被破解。

sslstrip 程序被开发出来用于捕获 SSL 消息并剥离其中的加密。该程序由 Moxie Marlinspike 开发，配合他在 2009 年 Black Hat 上所做的演示。那时候 SSL 仍然普遍使用，所以成功的机会很大。今天，成功的可能性较小了，因为理想情况下，技术过硬的系统管理员已经移除了 SSL 和 TLS 1.0、1.1 等旧加密机制。如果服务器仅支持 TLS 1.2 及以上版本，SSL strip 将无法工作，因为使其能够工作的漏洞已经得到解决。

你可以将 sslstrip 作为独立程序使用。本质上，sslstrip 充当透明代理，位于服务器和客户端之间。这样做时，在某些情况下它可以将链接从 HTTPS 改为 HTTP。它还使用其他技术，使连接看起来是加密的，但实际上并非如此。作为独立程序，sslstrip 使用了我们之前介绍过的 arpspoof。但是，也可以将 sslstrip 作为 Ettercap 的插件运行。

与我们进行 DNS 欺骗时一样，sslstrip 要求我们已部署 ARP 欺骗。我们可以像之前一样使用 Ettercap 来完成此操作。我们需要像之前一样欺骗互联网网关。在设置 ARP 欺骗攻击时，我们还需要嗅探远程连接。sslstrip 是 Ettercap 的插件，因此可以像启用 DNS 欺骗插件一样启用它。这确实需要在启用插件之前对 Ettercap 进行配置更改。sslstrip 需要知道正在使用什么防火墙命令，以便在防火墙中设置重定向。/etc/ettercap/etter.conf 文件中的以下行被注释掉了。如果你使用 iptables（比 ipchains 更常见，ipchains 是另一个选项），则需要取消注释。

### /etc/ettercap/etter.conf

```
# if you use iptables:
redir_command_on = "iptables -t nat -A PREROUTING -i %iface -p tcp --dport %port
-j REDIRECT --to-port %rport"
redir_command_off = "iptables -t nat -D PREROUTING -i %iface -p tcp --dport %port
-j REDIRECT --to-port %rport"
```

完成后，即可启用 sslstrip 插件。它将运行 iptables 命令来启动重定向，以便插件可以接收消息。以下是显示在 Ettercap 内部启动 sslstrip 的日志。

## 在 Ettercap 中运行 sslstrip

```
Host 192.168.86.1 added to TARGET1
ARP poisoning victims:
GROUP 1 : 192.168.86.1 18:D6:C7:7D:F4:8A
GROUP 2 : ANY (all the hosts in the list)
Activating sslstrip plugin...
SSLStrip plugin: bind 443 on 59273
SSLStrip Plugin version 1.1 is still under experimental mode. Please reports any issues to the development team.
DHCP: [192.168.86.1] ACK : 0.0.0.0 255.255.255.0 GW 192.168.86.1 DNS 192.168.86.1 "lan"
```

一旦 iptables 规则生效，sslstrip 应该会捕获任何 HTTPS 流量。不过，这同样假设 HTTPS 连接使用的是易受剥离攻击的 SSL 或 TLS 版本。如果不是，你将无法获取任何流量。

## 摘要

嗅探可能是一项重要技能，因为许多策略都依赖于从嗅探中收集的信息。嗅探是捕获数据包的另一种说法，即收集通过网络接口的所有消息，在数据链路层捕获它们，并将所有消息传递给能够显示所捕获消息的应用程序。虽然它被称为数据包捕获，但实际上捕获的是帧，因为数据在数据链路层捕获，并且第 2 层头部完好无损。第 2 层的协议数据单元（PDU）是帧。第 3 层的 PDU 是数据包。如果数据包捕获软件丢弃了第 2 层信息，那么它实际上就是数据包捕获。

有许多软件可用于在各种平台上捕获数据包。tcpdump 程序自 20 世纪 80 年代末就已存在，并在 20 世纪 90 年代末得到标准化。它通常在多种操作系统上都可用，尤其是类 Unix 操作系统。在 Windows 上，你可以获得名为 windump 的 tcpdump 移植版。其行为相同，但源代码不同，以考虑到 Windows 与其网络硬件交互的方式。如果你在寻找可以在多个平台上使用相同名称的程序，可以使用 tshark。这是一个随 Wireshark 包提供的命令行程序。它还有一个优势，即可以只打印你指定的字段。Wireshark 是一个基于 GUI 的程序，不仅可以执行数据包捕获，还可以执行数据包分析。

可能还有其他程序和实用程序可用于分析数据包捕获，但 Wireshark 可能是你能获得的最好的选择，尤其是考虑到它是免费的。它可免费获得且功能丰富。Wireshark 了解数十种甚至数百种


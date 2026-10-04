
![](img/e71dc48d3ae3db3394e5857ab2acae75_623_0.png)

### 图 17-11 PC B 响应 PC A

如示例 17-1 中的命令输出所示，PC A 已收到来自 PC B 的 Echo Reply 消息，验证了第 3 层网络连接。此输出验证了 PC A 与 PC B 之间的第 3 层连通性。

### 示例 17-1 PC A 上的 ping 输出

```
C:\Users\PC-A> ping 10.1.1.10
Pinging 10.1.1.10 with 32 bytes of data:
Reply from 10.1.1.10: bytes=32 time=47ms TTL=51
Reply from 10.1.1.10: bytes=32 time=60ms TTL=51
Reply from 10.1.1.10: bytes=32 time=53ms TTL=51
Reply from 10.1.1.10: bytes=32 time=50ms TTL=51
Ping statistics for 10.1.1.10:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 47ms, Maximum = 60ms, Average = 52ms
C:\Users\PC-A>
```

Cisco IOS 中的 ping 命令输出与 Windows 主机上的 ping 命令输出不同。例如，如示例 17-2 所示，IOS ping 发送五个 ICMP Echo 消息。

### 示例 17-2 R1 上的 ping 输出

```
R1# ping 10.1.1.10
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.1.1.10, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
R1#
```

请注意 !!!! 输出字符。IOS ping 命令为每个收到的 ICMP Echo Reply 消息显示一个 ! 输出字符。表 17-2 列出了 ping 命令最常见的输出字符。

### 表 17-2 IOS ping 指示符

| 元素 | 描述 |
|---|---|
| ! | - 感叹号表示成功收到 Echo Reply 消息。<br>- 它验证了源与目标之间的第 3 层连接。 |
| . | - 一个句点表示在等待 Echo Reply 消息时超时。<br>- 这表明路径中的某个位置发生了连通性问题。 |
| U | - 大写字母 U 表示路径中的路由器以 ICMP 类型 3“目标不可达”错误消息进行响应。<br>- 可能的原因包括路由器不知道通往目标网络的方向或无法在目标网络上找到主机。 |

注意
其他可能的 ping 回复包括 Q、M、? 和 &。但是，这些回复超出了本章的范围。

## 扩展 Ping（17.4.2）

标准 ping 使用距离目标网络最近的接口的 IP 地址作为 ping 的源。R1 上 ping 10.1.1.10 命令的源 IP 地址将是 G0/0/0 接口的地址（即 209.165.200.225），如图 17-12 所示。

![](img/e71dc48d3ae3db3394e5857ab2acae75_624_0.png)

### 图 17-12 R1 使用出接口作为源 IPv4 地址 Ping PC B

Cisco IOS 提供了 ping 命令的“扩展”模式。此模式使用户能够通过调整与命令操作相关的参数来创建特殊类型的 ping。

您在特权 EXEC 模式下通过输入不带目标 IP 地址的 ping 来进入扩展 ping。然后会提供多个提示以自定义扩展 ping。

注意
按 Enter 接受指示的默认值。

例如，假设您想测试从 R1 LAN（即 192.168.10.0/24）到 10.1.1.0 LAN 的连通性。这可以从 PC A 验证。但是，可以在 R1 上配置扩展 ping 以指定不同的源地址。

如图 17-13 所示，R1 上扩展 ping 命令的源 IP 地址可以配置为使用 G0/0/1 接口 IP 地址（即 192.168.10.1）。

![](img/e71dc48d3ae3db3394e5857ab2acae75_625_0.png)

| 源 IP | 目标 IP | ICMP |
|---|---|---|
| 192.168.10.1 | 10.1.1.10 | Echo |

### 图 17-13 R1 使用扩展 ping Ping PC B

示例 17-3 显示了 R1 上扩展 ping 的配置，其中源 IP 地址为 G0/0/1 接口（即 192.168.10.1）。

### 示例 17-3 R1 上的扩展 ping

```
R1# ping
Protocol [ip]:
Target IP address: 10.1.1.10
Repeat count [5]:
Datagram size [100]:
Timeout in seconds [2]:
Extended commands [n]: y
Ingress ping [n]:
Source address or interface: 192.168.10.1
DSCP Value [0]:
Type of service [0]:
Set DF bit in IP header? [no]:
Validate reply data? [no]:
Data pattern [0x0000ABCD]:
Loose, Strict, Record, Timestamp, Verbose [none]:
Sweep range of sizes [n]:
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.1.1.10, timeout is 2 seconds:
Packet sent with a source address of 192.168.10.1
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/1 ms
R1#
```

注意
使用 **ping ipv6** 命令进行 IPv6 扩展 **pings**。

## 使用 Traceroute 验证连通性（17.4.3）

**ping** 命令对于快速确定是否存在第 3 层连通性问题很有用。但是，它无法识别问题沿路径的位置。

**traceroute** 可以帮助定位网络中的第 3 层问题区域。它返回数据包在网络中路由时经过的跳数列表。它可用于识别路径中可以找到问题的位置。

**traceroute** 命令的语法在不同操作系统之间有所不同，如图 17-14 所示。

![](img/e71dc48d3ae3db3394e5857ab2acae75_626_0.png)

### 图 17-14 Windows 和 Cisco IOS 跟踪命令

示例 17-4 显示了 Windows 10 主机上 **tracert** 命令的输出。

### 示例 17-4 PC A 上的 **tracert** 命令

```
C:\Users\PC-A> tracert 10.1.1.10
Tracing route to 10.1.1.10 over a maximum of 30 hops:
1    2 ms    2 ms    2 ms  192.168.10.1
2    *       *       *    Request timed out.
3    *       *       *    Request timed out.
4    *       *       *    Request timed out.
^C
C:\Users\PC-A>
```

注意
在 Windows 中使用 Ctrl+C 中断 tracert。

示例 17-4 中唯一的成功响应来自 R1 上的网关。下一跳的跟踪请求超时，如星号 (*) 所示，意味着下一跳路由器未响应。超时的请求表明局域网之外的互联网存在故障，或者这些路由器已配置为不对跟踪中使用的 Echo Request 消息做出响应。在此示例中，R1 与 R2 之间似乎存在问题。

Cisco IOS traceroute 命令的输出与 Windows tracert 命令的输出不同。图 17-15 中的拓扑提供了一个示例。

![](img/e71dc48d3ae3db3394e5857ab2acae75_627_0.png)

### 图 17-15 Cisco IOS traceroute 命令

示例 17-5 显示了 R1 上 traceroute 命令的示例输出。在此示例中，输出验证了 traceroute 命令可以成功到达 PC B。

### 示例 17-5 R1 上的 traceroute 命令

```
R1# traceroute 10.1.1.10
Type escape sequence to abort.
Tracing the route to 10.1.1.10
VRF info: (vrf in name/id, vrf out name/id)
 1 209.165.200.226 1 msec 0 msec 1 msec
 2 209.165.200.230 1 msec 0 msec 1 msec
 3 10.1.1.10 1 msec 0 msec
R1#
```

超时表示潜在问题。例如，如果 10.1.1.10 主机不可用，traceroute 命令将显示示例 17-6 所示的输出。

### 示例 17-6 R1 上 **traceroute** 命令的主机不可达输出

```
R1# traceroute 10.1.1.10
Type escape sequence to abort.
Tracing the route to 10.1.1.10
VRF info: (vrf in name/id, vrf out name/id)
 1 209.165.200.226 1 msec 0 msec 1 msec
 2 209.165.200.230 1 msec 0 msec 1 msec
 3 * * *
 4 * * *
 5 *
```

在 Cisco IOS 中使用 Ctrl+Shift+6 中断 **traceroute** 命令。

注意
Windows 实现的 **traceroute**（tracert）发送 ICMP Echo Request 消息。Cisco IOS 和 Linux 使用无效端口号的 UDP。最终目标返回 ICMP 端口不可达消息。

## 扩展 Traceroute（17.4.4）

与扩展 **ping** 命令类似，还有扩展 **traceroute** 命令。扩展 **traceroute** 命令允许管理员调整与命令操作相关的参数。这有助于在排除路由环路故障、确定下一跳路由器或确定数据包被路由器或防火墙丢弃或拒绝的位置时定位问题。

Windows **tracert** 命令允许通过命令行选项输入多个参数。但是，这种额外输入没有指导，就像扩展 **traceroute** IOS 命令一样。示例 17-7 显示了 Windows **tracert** 命令的可用选项。

Cisco IOS 扩展 **traceroute** 选项使用户能够通过调整与命令操作相关的参数来创建特殊类型的跟踪。扩展 **traceroute** 在特权 EXEC 模式下通过输入不带目标 IP 地址的 **traceroute** 进入。IOS 通过呈现与所有不同参数设置相关的多个提示来指导您完成命令选项。

注意
按 Enter 接受指示的默认值。

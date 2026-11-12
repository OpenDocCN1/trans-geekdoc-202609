
以下是一些帮助你判断是否需要特定服务或程序的实用方法：

- 访问你的 Linux 发行版的主页并搜索该程序。
- 使用 Yahoo! 或 Google 等搜索引擎搜索“man program/service”。手册（man）页面通常会揭示关于程序/服务及其用途的大量信息。

## 使用防火墙进行防护

虽然 Linux 有许多第三方安全产品可用，包括防火墙，但操作系统本身也内置了一些实用功能。如果你的 Linux 系统位于其他防火墙之外，那么在系统上安装防火墙至关重要。例如，如果没有设置安全局域网的资源，而你搭建的 Linux 服务器连接到 Internet，则需要安装本地防火墙。即使你使用的是安全的局域网配置，额外的本地防火墙也能增加一道防线，以防入侵者攻陷你现有的路由器之一。

## Ipchains

Ipchains 是一种历史悠久的防火墙机制，适用于大多数使用内核版本 2.2.x 的 Linux 发行版。要开始使用，你需要启用 ipchains。如果你的系统使用内部 IP 地址 10.50.4.55，子网掩码为 255.255.255.0，则需要以 root 权限运行以下命令：

```
echo 1 > /proc/sys/net/ipv4/ip_forward
ipchains -A forward -j MASQ -s 10.50.4.0/24 -d 0.0.0.0/0
```

第一个命令启用 ip_forwarding，第二个命令配置服务器允许哪个网络访问 Internet。如果你希望在启动时加载 ipchains 服务，则需要将上述两个命令放入 /etc/rc.d/rc.local 文件中。防火墙运行后，可以使用 ipchains -L 命令查看已配置的 IP 过滤规则。初始情况下，显示内容不多。该命令的输出类似于图 1-4。

```
ipchains -A input -p icmp -i eth0 -j REJECT
```

下面逐一介绍此示例中的各个组件：

- `ipchains -A input` 部分表示你要向 ipchains `input` 链追加（A）一条新规则。除了 -A，还可以使用 -L 查看当前的 ipchains 规则，使用 -D 从链中删除一条规则。
- 选项 -p 指定你要为某个协议设置规则。
- icmp 是类型（与 -p 选项一起使用），在此示例中，它表示所有 ICMP 流量。
- eth0 是要应用规则的网络接口。
- -j REJECT 选项指定在接口处拒绝 ICMP 流量。结果是，eth0 接口上的任何入站 ICMP 流量都会被直接拒绝。

有关简化 ipchains 和其他防火墙配置的产品信息，请参见图书 I 第 3 章。本章仅简要介绍 ipchains 工具的功能。如果你想了解更多关于 ipchains 的信息，请访问 `www.rt.com/man/ipchains.8.html` 或在 Linux 服务器上输入 "man ipchains" 以查看几乎数不胜数的 ipchains 运行时选项。

![](img/3f967ab8a8fddc723173059f56621648_46_0.png)

图 1-4：ipchains 规则配置示例。

## Iptables

在 Linux 系统上实现防火墙的另一种选择是使用 iptables。两者在功能上相似（都控制网络访问）；不过，iptables 相对于 ipchains 有几个优势。这些优势足够值得注意，因此如果你使用的是 2.4.x 或更新版本的内核（例如比 Red Hat 7.1 更新的任何版本），应该使用 iptables。以下是 iptables 与 ipchains 的一些不同之处。

- 与 ipchains 不同，iptables 使用单个链来处理过滤的数据包。因此，iptables 让你能更精细地控制所选的过滤选项。例如，由 ipchains 主机转发的数据包必须经过 input、forward 和 output 链才能到达目的地。而使用 iptables 的主机只需将数据包与 output 过滤器进行检查。如果主机使用 iptables，input 链上的冲突规则不会阻止数据包的转发。
- iptables 主机仅使用入站规则处理入站数据包，仅使用出站规则处理出站数据包。如果要为特定规则指定要使用的网络接口，必须在配置中使用相应的选项。`-i` 选项必须与入站或 forward 链一起使用，`-o` 选项必须与出站链一起使用。请记住，入站接口不会使用出站规则，出站接口不会使用入站规则。如果混用选项，规则将无法产生预期效果。
- 与 ipchains 不同，在 iptables 中，你必须在协议声明（ICMP、TCP 或 UDP）之后指定源端口或目标端口。在 ipchains 中顺序并不十分重要，但在 iptables 中，如果不使用正确的顺序，规则将无法按预期工作。

如你所料，配置文件（通常位于 /etc/sysconfig/iptables）也发生了相当大的变化。整体布局更清晰一些，如果使用注释，理解配置内容也相当简单。在图 1-5 中，配置首先设置一条规则，允许本地主机（运行 iptables）与 *本地主机* 之间传递任何流量。下一条目允许 ICMP 类型 3 流量通过。当转发数据到另一台主机的系统找不到目标主机时，会使用类型 3“目标不可达”消息。接下来，允许挂载和 NFS 连接。如果你需要通过网络连接到系统以发送数据（例如上传网页内容），这些可能是必不可少的；但如果你在本机上本地工作，则可以删除这些条目。本示例中的 mount 条目只有在转到 NFS 配置文件 /etc/rc.d/init.d/nfs 并将挂载服务分配给单个端口（本例中为 33333）时才有效。默认情况下，端口在系统启动时选择，范围在 32000 到 42000 之间。最后，配置文件允许端口 80 上的 http 流量通过。如果还需要使用 https，可以复制此最后条目，并将目标端口（dport）和源端口（sport）值更改为 443。

注意，图 1-4 中默认存在三条链。

我强烈建议你在将 ipchains 或 iptables 用于生产环境之前，先熟悉它们的语法和用法。很容易遗漏某些东西，导致系统暴露在风险之中。为需要允许进入和离开服务器的流量类型，以及需要阻止的服务和端口制定计划。有了清晰的计划，你的效果会好得多。要了解有关 ipchains 配置的更多信息，请查看 www.linux.org/docs/ldp/howto/IPCHAINS-HOWTO.html。如果你将使用 iptables，www.jollycom.ca/iptables-tutorial/iptables-tutorial.html 是一个非常好的常规信息和配置示例来源。

```
*mangle
COMMIT

*nat
COMMIT
# DEFAULT ALL CHAINS TO DROP ON FALLTHROUGH
#:INPUT DROP [0:0]
#:FORWARD DROP [0:0]
#:OUTPUT DROP [0:0]
# PASS ALL FROM LOCALHOST
[0:0] -A INPUT -i lo -j ACCEPT
[0:0] -A OUTPUT -o lo -j ACCEPT
# PASS ICMP TYPE 3 PACKETS, INPUT AND OUTPUT
[0:0] -A INPUT -p icmp --icmp-type 3 -j ACCEPT
[0:0] -A OUTPUT -p icmp --icmp-type 3 -j ACCEPT
# PASS NFS: 2049, INPUT AND OUTPUT, TCP AND UDP
[0:0] -A INPUT -p tcp -m tcp --dport 2049 -j ACCEPT
[0:0] -A INPUT -p udp -m udp --dport 2049 -j ACCEPT
[0:0] -A OUTPUT -p tcp -m tcp --sport 2049 -j ACCEPT
[0:0] -A OUTPUT -p udp -m udp --sport 2049 -j ACCEPT
# PASS MOUNTD AT 33333, INPUT AND OUTPUT, TCP AND UDP
[0:0] -A INPUT -p tcp -m tcp --dport 33333 -j ACCEPT
[0:0] -A INPUT -p udp -m udp --dport 33333 -j ACCEPT
[0:0] -A OUTPUT -p tcp -m tcp --sport 33333 -j ACCEPT
[0:0] -A OUTPUT -p udp -m udp --sport 33333 -j ACCEPT
# PASS HTTP AT 80, INPUT AND OUTPUT, TCP AND UDP
[0:0] -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
[0:0] -A INPUT -p tcp -m tcp --sport 80 -j ACCEPT
[0:0] -A OUTPUT -p tcp -m tcp --dport 80 -j ACCEPT
[0:0] -A OUTPUT -p tcp -m tcp --sport 80 -j ACCEPT
COMMIT
```

图 1-5：iptables 配置示例。

## 玩转游戏：IP 伪装

网络地址转换（NAT）用于将一组主机地址隐藏在单个公共地址后面。通常，NAT 用于允许多个私有主机使用单个公共 IP 地址访问 Internet。私有网络中共享该单个公共 IP 的每个人都会被有效地“掩盖”——因此得名 Masquerade——从 Internet 上看不见。单个主机可以使用私有 IP 地址（例如 192.168.1.22），并使用 NAT 通过一个在 Internet 上可路由的不同 IP 地址访问公共网络。这种配置的优势在于，拥有许多内部主机的组织只需为其所有资源使用一个公开知晓的 IP 地址。

要使用 IP 伪装，你需要一个已支持它的构建版本，或者可能需要重新编译内核才能使用 IP 伪装。大多数当前的 Linux 发行版都支持 IP 伪装。要检查你的系统，可以运行此命令：

```
uname -a
```

结果会显示你系统使用的内核版本。要使用 IP 伪装，你需要内核版本 2.0.x 或更高版本。在 Red Hat 发行版中，/etc/rc.d/rc.local 脚本内有一个条目，用于加载

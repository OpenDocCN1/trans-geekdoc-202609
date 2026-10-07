

# 64 第一部分 | 网络探索

| 同形异字 | ppsi.com |
| :--- | :--- |
| 同形异字 | peps.com |
| 同形异字 | p6psi.com |
| 同形异字 | p8xi.com |
| 同形异字 | p8psi.com |
| 同形异字 | pepsi.com |
| 同形异字 | pepsi.com |
| 同形异字 | pepsgi.com |
| 同形异字 | p8psi.com |
| 同形异字 | pepxi.com |
| 同形异字 | pepsl.com |
| 同形异字 | p3si.com |
| 同形异字 | p3psi.com |
| 同形异字 | pepsi.com |
| 同形异字 | pepsl.com |
| 同形异字 | p6psi.com |
| 同形异字 | pepsf.com |
| 插入 | pe1psi.com |
| 插入 | pewpsi.com |
| 插入 | p4epsi.com |
| 插入 | pepsai.com |
| 插入 | psepsi.com |
| 插入 | pewswi.com |
| 插入 | pepasi.com |
| 插入 | pepdsi.com |
| 插入 | p4epsi.com |
| 插入 | pe8psi.com |
| 插入 | pepsi.com |
| 插入 | pzpsi.com |
| 插入 | pe3psi.com |
| 插入 | pzpsi.com |
| 插入 | pepsyi.com |
| 插入 | pexxi.com |
| 插入 | pempsi.com |
| 插入 | pewpsi.com |

# 总结

本章在网络和子域名发现与探索领域涵盖了大量内容。我们查看了 Sublist3r、fierce 和 Enummer 等工具，这些工具对于任何数字调查员或渗透测试人员都是至关重要的，因为它们能够在目标域名内嗅探子域名。

本章还触及了 Shodan 和 Censys.io 等服务，这些是可发现服务器信息的大型仓库，也可以用于识别目标组织的服务器或设备。

最后，本章通过观察在测试不同规模的组织网站时所提供的结果类型，比较了这些不同工具和服务的搜索性能。

**冒着听起来有些冗余的风险，你永远不要依赖单一工具来获取所有结果。**

下一章将以这些结果为基础，通过查看我们新发现的子域名并寻找网络活动，最终发现跨组织基础设施的信息泄露。

# 寻找网络活动
（高级 NMAP 技术）

本章侧重于使用高级的 NMAP 扫描技术识别活跃的主机和端口。对于几乎每一次渗透任务，NMAP 都是寻找活跃主机的“首选哪个工具”问题中的圣杯。

由于 NMAP 是每个黑客工具箱中不可或缺的工具，我觉得它在许多其他书中已经被讨论得足够透彻了。本章将不再重复执行 NMAP 扫描的基础知识，而是将重点关注我曾用于发现主机活动的若干种高级用例和技术，即使是面对最具挑战性的防火墙也能做到。

# 入门

通过执行 NMAP 扫描可以获得大量的关键数据，这确实可以为你后续的渗透任务奠定调。在我们开始之前，本书假设你对 NMAP 有基本的了解，即它是什么、如何工作以及如何使用它。如果你是 NMAP 新手，你可能想查看一些免费的在线教程；或者像我一样，直接玩玩看。

# 准备活跃主机列表

这通常是运行的第一次扫描。它设计用于扫描所有的本地 IP 空间并返回一个格式良好的活跃主机列表。我将此用于内部渗透测试，但也可以轻松调整到外部地址在线的情况。

我使用以下命令获取内部网络上所有活跃主机的列表：

```
root@OSINT: nmap -n -sn 10.0.0.0/8 172.16.0.0/12 192.16.0.0/16 -oG - | awk '/Up$/print $2' > outputfile.txt
```

该命令执行了以下操作：

- -sn 执行 ping 扫描（如果禁用了 ping 则使用 -ss）
- 扫描所有内部 IP 空间
- -oG - 输出为可搜索格式 (greppable format)
- 将输出发送到 AWK，仅显示标记为 Up 的 IP
- 将输出发送到 outputfile.txt

输出将是一个非常干净的活跃 IP 地址列表，你可以将其用于下一个任务。列表看起来如下：

```
192.168.0.1
192.168.0.2
192.168.0.3
... 依此类推。
```

# 使用不同扫描类型进行全扫描

我很少在某一种扫描类型上获得好运。这通常取决于运气，我总是发现多次运行完整的 NMAP 扫描是一种良好的做法，以确保我没有漏掉任何东西。我也扫描每个端口。总是如此。

对于更复杂的网络，采用典型的 SYN 扫描是有效的，因为如果端口开启，目标机器将响应 SYN/ACK；如果端口关闭，则响应 RST（重置）。

但实际上，使用 SYN 或 FIN 的标准 TCP 扫描通常会被拦截，特别是当你正在处理任何类型的 IDS/IPS 时。一个很好的起点是 Xmas 扫描 (-sX)，但如果你没有得到结果，你应该尝试 --scanflags。这是我们配置扫描的方式：-p- 扫描所有端口，而不仅仅是默认端口。这将为你的扫描增加一些时间，NMAP 将扫描端口 1-6535。

# 第 4 章 寻找网络活动（高级 NMAP 技术）

大多数扫描关注 TCP 端口。许多服务和端口 经常被遗漏。之前的扫描 (-sX 等）无法发现 UDP。要发现这些端口，我们需要包含 -sU 以告诉 Nmap 使用哪些类型。在运行扫描时，你必须定义某些类型，包括 null 扫描。--scanflags 允许你设置多种类型。值得尝试的是 PSH、FIN 和 SYN。PSH 会尝试通过操作 TCP 头部获取响应，FIN 将尝试相同的策略，SYN 将尝试使用 SYN/ACK 方法获取响应。让我们对 pepsi.com 进行全扫描：

```
root@OSINT: nmap -v -pU pepsi.com --scanflags PSH
```

此扫描的结果并不理想。所有部分返回为过滤 (filtered)：

```
Nmap 7.0 ( https://nmap.org ) at 2018-12-11 01:03
Initiating Ping at 01:03
Scanning pepsi.com (182.214.229.99) [4 hosts]
Completed Ping at 01:03, 0.06s elapsed (1 hosts)
Initiating DNS resolution of 1 host. at 01:03
Completed DNS resolution of 1 host. at 01:03, 0.0s elapsed
Initiating Xmas Scan at 01:03
Scanning pepsi.com (182.214.229.99) [65535 ports]
Xmas Scan Timing: About 18.4m done; ETC: 01:06 (02:17 remaining)
Stats: 00:39 elapsed, 0 hosts (1), undergoing Xmas Scan
Xmas Scan Timing: About 25.85m done; ETC: 01:06 (01:52 remaining)
Xmas Scan Timing: About 53.74m done; ETC: 01:06 (00:59 remaining)
Completed Xmas Scan at 01:05, 117.00s elapsed (65535 ports)
Initiating UDP Scan at 01:05
Scanning pepsi.com (182.214.229.99) [65535 ports]
Stats: 02:17 elapsed; 0 hosts (1), undergoing UDP Scan
UDP Scan Timing: About 11.73m done; ETC: 01:08 (02:30 remaining)
UDP Scan Timing: About 35.76m done; ETC: 01:08 (01:31 remaining)
UDP Scan Timing: About 57.06m done; ETC: 01:07 (00:40 remaining)
Completed UDP Scan at 01:07, 108.80s elapsed (65535 ports)
Nmap scan report for pepsi.com (182.214.229.99)
Host is up (0.058s latency).
rdNS record for 182.214.229.99: ec2-184-214-229.99.compute-1.amazonaws.com
All 13170 ports on pepsi.com (182.214.229.99) are open|filtered
```

# TCP 窗口扫描

nmap 的 -sW 扫描将执行“窗口扫描”。TCP 窗口扫描类似于 ACK 扫描，但旨在区分开启和关闭端口，而不是显示它们为未过滤 (unfiltered)。

```
root@OSINT: nmap -v -p-- pepsi.com -sW
```

Starting Nmap 7.0 ( https://nmap.org ) at 2018-12-11 01:15 CST
Initiating Ping at 01:15
Scanning pepsi.com (182.214.229.99) [4 hosts]
Completed Ping at 01:15, 0.05s elapsed (1 total)
Initiating Parallel DNS resolution of 1 host. at 01:15
Completed DNS resolution of 1 host. at 01:15, 0.0s elapsed
Initiating Window Scan at 01:15
Scanning pepsi.com (182.214.229.99) [65535 ports]
Window Scan: About 13.6% done; ETC: 01:19 (00:03 remaining)
Window Scan: About 26.85% done; ETC: 01:19 (00:02 remaining)
Window Scan: About 41.15% done; ETC: 01:19 (00:02 remaining)
Window Scan: About 54.0% done; ETC: 01:19 (00:01 remaining)
Window Scan: About 68.1% done; ETC: 01:19 (00:01 remaining)
Window Scan: About 81.9% done; ETC: 01:19 (00:01 remaining)
Window Scan: About 95.8% done; ETC: 01:19 (00:00 remaining)
Stats: 00:37 elapsed; 0 hosts completed (1), 1 undergoing scan
Completed Window Scan at 01:19, 244.8ms elapsed (65535 total ports)

# 工作中的防火墙和 IDS

任何现代防火墙或入侵检测系统都带有大量的预配置阻止规则，旨在阻止或最小化你扫描其基础设施的能力。如果流量没有被防火墙直接拦截，那么它可能被 IDS 监控。本节提供了绕过这些系统检测的有用指南。


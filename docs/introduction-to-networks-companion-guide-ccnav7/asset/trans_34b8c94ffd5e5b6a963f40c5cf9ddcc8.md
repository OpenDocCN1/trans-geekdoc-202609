
所有 **调试** 命令均在特权 EXEC 模式下输入。Cisco IOS 允许将 **调试** 输出范围缩小为仅包含相关的功能或子功能。这很重要，因为调试输出在 CPU 进程中被赋予高优先级，并且可能导致系统无法使用。因此，仅在排除特定问题时使用 **调试** 命令。

例如，要监视 Cisco 路由器中 ICMP 消息的状态，请使用 **调试 ip icmp**，如示例 17-29 所示。

### 示例 17-29 使用 **调试** 命令监视 ICMP

```
R1# debug ip icmp
ICMP packet debugging is on
R1#
R1# ping 10.1.1.1
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.1.1.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
R1#
*Aug 20 14:18:59.605: ICMP: echo reply rcvd, src 10.1.1.1, dst 209.165.200.225, topology BASE, dscp 0 topoid 0
*Aug 20 14:18:59.606: ICMP: echo reply rcvd, src 10.1.1.1, dst 209.165.200.225, topology BASE, dscp 0 topoid 0
*Aug 20 14:18:59.608: ICMP: echo reply rcvd, src 10.1.1.1, dst 209.165.200.225, topology BASE, dscp 0 topoid 0
*Aug 20 14:18:59.609: ICMP: echo reply rcvd, src 10.1.1.1, dst 209.165.200.225, topology BASE, dscp 0 topoid 0
*Aug 20 14:18:59.611: ICMP: echo reply rcvd, src 10.1.1.1, dst 209.165.200.225, topology BASE, dscp 0 topoid 0
R1#
```

列出所有调试命令选项的简要说明，请在命令行中使用特权 EXEC 模式下的 **调试 ?** 命令。

关闭特定调试功能时，在 **调试** 命令前添加 **no** 关键字：

```
Router# no debug ip icmp
```

或者，您可以在特权 EXEC 模式下输入该命令的 **取消调试** 形式：

```
Router# undebug ip icmp
```

要一次性关闭所有活动的 **调试** 命令，请使用 **取消调试 all** 命令：

```
Router# undebug all
```

使用某些 **调试** 命令时请谨慎。诸如 **调试 all** 和 **调试 ip packet** 之类的命令会产生大量输出并占用大量系统资源。路由器可能因显示 **调试** 消息而变得过于繁忙，以至于没有足够的处理能力来执行其网络功能，甚至无法接收关闭调试的命令。因此，不建议使用这些命令选项，应避免使用。

## 终端监视 命令 (17.6.4)

访问 IOS 命令行界面的连接可以通过两种方式建立：

- **本地：** 本地连接（即控制台连接）需要使用翻转电缆物理访问路由器或交换机的控制台端口。
- **远程：** 远程连接需要使用 Telnet 或 SSH 建立到已配置 IP 的设备的连接。

某些 IOS 消息会自动显示在控制台连接上，但不会显示在远程连接上。例如，**调试** 输出默认显示在控制台连接上。然而，**调试** 输出不会自动显示在远程连接上。这是因为 **调试** 消息是日志消息，被阻止显示在 vty 线路上。

例如在示例 17-30 中，用户使用 Telnet 从 R2 建立到 R1 的远程连接。然后用户发出 **调试 ip icmp** 命令。然而，该命令未能显示 **调试** 输出。

### 示例 17-30 演示 **调试** 命令无终端输出

```
R2# telnet 209.165.200.225
Trying 209.165.200.225 ... Open
Authorized access only!
User Access Verification
Password:
R1> enable
Password:
R1# debug ip icmp
ICMP packet debugging is on
R1# ping 10.1.1.1
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.1.1.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
R1#
```

要在终端（虚拟控制台）上显示日志消息，请使用特权 EXEC 命令 **终端监视**。要停止在终端上记录消息，请使用特权 EXEC 命令 **终端 no monitor**。

例如在示例 17-31 中，注意已输入 **终端监视** 命令，并且 **ping** 命令显示了 **调试** 输出。

### 示例 17-31 启用并验证终端监视

```
R1# terminal monitor
R1# ping 10.1.1.1
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.1.1.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
R1#
*Aug 20 16:03:49.735: ICMP: echo reply rcvd, src 10.1.1.1, dst 209.165.200.225, topology BASE, dscp 0 topoid 0
*Aug 20 16:03:49.737: ICMP: echo reply rcvd, src 10.1.1.1, dst 209.165.200.225, topology BASE, dscp 0 topoid 0
*Aug 20 16:03:49.738: ICMP: echo reply rcvd, src 10.1.1.1, dst 209.165.200.225, topology BASE, dscp 0 topoid 0
*Aug 20 16:03:49.740: ICMP: echo reply rcvd, src 10.1.1.1, dst 209.165.200.225, topology BASE, dscp 0 topoid 0
*Aug 20 16:03:49.741: ICMP: echo reply rcvd, src 10.1.1.1, dst 209.165.200.225, topology BASE, dscp 0 topoid 0
R1# no debug ip icmp
ICMP packet debugging is off
R1#
```

### 注意

**调试** 命令的目的是在短时间内（即几秒钟到一分钟左右）捕获实时输出。始终在不需要时禁用 **调试**。

## 检查理解—故障排除方法 (17.6.5)

请参考在线课程完成此活动。

![](img/e71dc48d3ae3db3394e5857ab2acae75_652_0.png)

## 故障排除场景 (17.7)

本节重点介绍各种故障排除场景。

### 双工操作和不匹配问题 (17.7.1)

许多常见的网络问题可以用很少的努力识别和解决。现在您已掌握工具并了解网络故障排除流程，本节回顾了一些您作为网络管理员很可能遇到的常见网络问题。

在数据通信中，双工是指两个设备之间数据传输的方向。存在两种双工通信模式：

- **半双工：** 通信仅限于一次一个方向的数据交换。
- **全双工：** 通信允许同时发送和接收。

图 17-22 说明了每种双工方法的工作方式。

![](img/e71dc48d3ae3db3394e5857ab2acae75_653_0.png)

图 17-22 双工操作

互连的以太网接口必须以相同的双工模式运行，以获得最佳通信性能并避免链路上的低效率和延迟。

以太网自动协商功能有助于配置、最大程度地减少问题并最大化两个互连以太网链路之间的链路性能。连接的设备首先宣布其支持的功能，然后选择两端都支持的最高性能模式。例如，图 17-23 中的交换机和路由器已成功自动协商全双工模式。

如果两个连接设备中的一个以全双工运行而另一个以半双工运行，则会发生双工不匹配。虽然可以通过双工不匹配的链路进行数据通信，但链路性能非常差。

双工不匹配通常是由配置错误的接口或在极少数情况下由自动协商失败引起的。由于设备之间仍会进行通信，双工不匹配可能难以排除故障。

![](img/e71dc48d3ae3db3394e5857ab2acae75_654_0.png)

图 17-23 双工自动协商

### IOS 设备上的 IP 地址问题 (17.7.2)

与 IP 地址相关的问题可能会阻止远程网络设备通信。由于 IP 地址是分层的，因此分配给网络设备的任何 IP 地址都必须符合该网络中地址的范围。错误分配的 IP 地址会产生各种问题，包括 IP 地址冲突和路由问题。

不正确的 IPv4 分配的两个常见原因是手动分配错误和与 DHCP 相关的问题。

网络管理员通常必须手动为服务器和路由器等设备分配 IP 地址。如果分配过程中出现错误，很可能会出现与该设备的通信问题。

在 IOS 设备上，使用 show ip interface 命令或 show ip interface brief 命令来验证分配给网络接口的 IPv4 地址。例如，如示例 17-32 所示发出 show ip interface brief 命令将验证 R1 上的接口状态。

### 示例 17-32 使用 show ip interface brief 验证 Cisco 设备上的 IPv4 地址

```
R1# show ip interface brief
```

| 接口 | IP 地址 | 正常? | 方法 | 状态 | 协议 |
|---|---|---|---|---|---|
| GigabitEthernet0/0/0 | 209.165.200.225 | YES | manual | up | up |
| GigabitEthernet0/0/1 | 192.168.10.1 | YES | manual | up | up |
| Serial0/1/0 | unassigned | NO | unset | down | down |
| Serial0/1/1 | unassigned | NO | unset | down | down |
| GigabitEthernet0 | unassigned | YES | unset | administratively down | down |

```
R1#
```

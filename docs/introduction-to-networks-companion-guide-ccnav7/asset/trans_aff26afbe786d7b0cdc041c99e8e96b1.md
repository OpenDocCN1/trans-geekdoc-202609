
12. ICMPv6 Neighbor Solicitation 消息的目的 MAC 地址是什么？
- a. 多播
- b. 单播
- c. 广播
- d. 任播

13. 当接收到的帧的目的 MAC 地址不在 MAC 表中时，二层交换机做什么？
- a. 它发起 ARP 请求。
- b. 它将帧广播到交换机上的所有端口。
- c. 它通知发送主机帧无法交付。
- d. 它将帧转发到除接收帧的端口外的所有端口。

14. 在以太网 MAC 地址解析过程中使用了哪两种 ICMPv6 消息？（选择两项。）
- a. 路由器请求
- b. 路由器通告
- c. 邻居请求
- d. 邻居通告
- e. 回显请求

## 目标

本章完成后，你将能够回答以下问题：
- 如何在 Cisco IOS 路由器上配置初始设置？
- 如何在 Cisco IOS 路由器上配置两个活动接口？
- 如何配置设备使用默认网关？

## 引言 (10.0)

你是否参加过接力赛？第一个人跑完比赛的第一棒并将接力棒交给下一位跑者，后者继续在第二棒前进并将接力棒交给第三位跑者，以此类推。如果第一个跑者不知道在哪里找到第二个跑者，或者第一个跑者在交接前掉落了接力棒，那么该接力队肯定会输掉比赛。

分组路由类似于接力。正如你所知，路由表由路由器创建并用于将数据包从本地网络转发到其他网络。但路由器在配置之前无法创建路由表或转发任何数据包。如果你计划成为网络管理员，你肯定必须知道如何做到这一点。好消息？很容易！本章包含 Syntax Checker 活动，以便你可以练习配置命令并查看输出。还有一些 Packet Tracer 活动供你入门。让我们开始吧！

## 配置初始路由器设置 (10.1)

本节介绍所有 IOS 路由器所需的基本配置。

## 基本路由器配置步骤 (10.1.1)

应完成以下任务以配置路由器的初始设置：

![](img/e71dc48d3ae3db3394e5857ab2acae75_356_0.png)

**步骤 1.** 配置设备名称：
```
Router(config)# hostname hostname
```
**步骤 2.** 保护特权 EXEC 模式：
```
Router(config)# enable secret password
```
**步骤 3.** 保护用户 EXEC 模式：
```
Router(config)# line console 0
Router(config-line)# password password
Router(config-line)# login
```
**步骤 4.** 保护远程 Telnet/SSH 访问：
```
Router(config)# line vty 0 4
Router(config-line)# password password
Router(config-line)# login
Router(config-line)# transport input {ssh | telnet}
```
**步骤 5.** 在配置文件中保护所有密码：
```
Router(config-line)# exit
Router(config)# service password-encryption
```

Step 6. 提供合法的通知横幅：
```
Router(config)# banner motd delimiter message delimiter
```

Step 7. 保存配置：
```
Router(config)# end
Router# copy running-config startup-config
```

## 基本路由器配置示例 (10.1.2)

本节提供一个示例，使用图 10-1 中的拓扑。在此示例中，你将看到如何为路由器 R1 配置初始设置。

![](img/e71dc48d3ae3db3394e5857ab2acae75_357_0.png)

图 10-1 基本路由器配置参考拓扑

要为 R1 配置设备名称，请使用示例 10-1 中的命令。

## 示例 10-1 配置设备名称
```
Router> enable
Router# configure terminal
Enter configuration commands, one per line.
End with CNTL/Z.
Router(config)# hostname R1
R1(config)#
```

## 注意

请注意，在示例 10-1 中，路由器提示符现在显示主机名。

所有路由器访问都应得到保护。特权 EXEC 模式为用户提供对设备及其配置的完全访问权限。因此，这是最重要的需要保护的模式。

示例 10-2 中的命令可保护特权 EXEC 模式和用户 EXEC 模式，启用 Telnet 和 SSH 远程访问，并加密所有明文（即用户 EXEC 和 vty 线路）密码。

## 示例 10-2 保护对路由器的访问
```
R1(config)# enable secret class
R1(config)#

R1(config)# line console 0
R1(config-line)# password cisco
R1(config-line)# login
R1(config-line)# exit
R1(config)#

R1(config)# line vty 0 4
R1(config-line)# password cisco
R1(config-line)# login
R1(config-line)# transport input ssh telnet
R1(config-line)# exit
R1(config)#

R1(config)# service password-encryption
R1(config)#
```

提供合法通知以警告用户只有允许的用户才能访问设备是个好主意。合法通知的配置如示例 10-3 所示。

## 示例 10-3 配置横幅警告
```
R1(config)# banner motd #
Enter TEXT message. End with a new line and the #
**************************************************
WARNING: Unauthorized access is prohibited!
**************************************************
#
R1(config)#
```

如果到目前为止显示的命令全部输入到意外断电的路由器上，所有这些配置都将丢失。因此，在实施更改时保存配置非常重要。示例 10-4 中显示的命令将配置保存到 NVRAM。

## 示例 10-4 保存运行配置
```
R1# copy running-config startup-config
Destination filename [startup-config]?
Building configuration...
[OK]
R1#
```

## Syntax Checker—配置初始路由器设置 (10.1.3)

使用此 Syntax Checker 活动练习在路由器上配置初始设置：
- 配置设备名称。
- 保护特权 EXEC 模式。
- 保护并启用远程 SSH 和 Telnet 访问。
- 保护所有明文密码。
- 提供合法通知。

请参考在线课程完成此活动。

## Packet Tracer—配置初始路由器设置 (10.1.4)

在此活动中，你将执行基本的路由器配置。你将使用加密和明文密码保护对 CLI 和控制台端口的访问。你还将为登录路由器的用户配置消息。这些横幅还警告未经授权的用户禁止访问。最后，你将验证并保存运行配置。

## 配置接口 (10.2)

本节介绍基本路由器接口配置。

## 配置路由器接口 (10.2.1)

当你的路由器具有基本配置后，下一步是配置其接口。这是因为在配置接口之前，终端设备无法访问路由器。Cisco 路由器上有许多不同类型的接口。例如，Cisco ISR 4321 路由器配备了两个千兆以太网接口：
- GigabitEthernet 0/0/0 (G0/0/0)
- GigabitEthernet 0/0/1 (G0/0/1)

配置路由器接口类似于在交换机上配置管理 SVI。具体来说，它涉及发出以下命令：
```
Router(config)# interface type-and-number
Router(config-if)# description description-text
Router(config-if)# ip address ipv4-address subnet-mask
Router(config-if)# ipv6 address ipv6-address/prefix-length
Router(config-if)# no shutdown
```

![](img/e71dc48d3ae3db3394e5857ab2acae75_359_0.png)

![](img/e71dc48d3ae3db3394e5857ab2acae75_359_1.png)

> **注意**
当路由器接口启用时，应显示信息消息以确认已启用的链路。

虽然 **description** 命令不是启用接口所必需的，但使用它是一个良好的做法。此命令在生产网络的故障排除中可能很有帮助，因为它使你能够提供有关所连接网络类型的信息。例如，对于连接到 ISP 或服务提供商的接口，你可以使用 **description** 命令输入第三方连接和联系信息。

> **注意**
*description-text* 限制为 240 个字符。

使用 **no shutdown** 命令激活接口，类似于为接口供电。接口还必须连接到另一台设备，例如交换机或路由器，以便物理层处于活动状态。

> **注意**
在没有以太网交换机的路由器间连接中，两个互连接口都必须配置并启用。

## 配置路由器接口示例 (10.2.2)

示例 10-5 显示了如何启用图 10-1 中 R1 的直接连接接口。

## 示例 10-5 使用双栈寻址配置路由器接口
```
R1> enable
R1# configure terminal
Enter configuration commands, one per line.
End with CNTL/Z.
R1(config)# interface gigabitEthernet 0/0/0
R1(config-if)# description Link to LAN
R1(config-if)# ip address 192.168.10.1 255.255.255.0
R1(config-if)# ipv6 address 2001:db8:acad:10::1/64
R1(config-if)# no shutdown
R1(config-if)# exit
R1(config)#
```

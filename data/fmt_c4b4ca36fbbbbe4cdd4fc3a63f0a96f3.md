
以下活动提供了本章介绍主题的练习。实验可在配套的 *Introduction to Networks Labs & Study Guide* (*CCNAv7*)（ISBN 9780136634454）中找到。Packet Tracer 活动说明也提供在 *Labs & Study Guide* 中。PKA 文件可在在线课程中获得。

![](img/e71dc48d3ae3db3394e5857ab2acae75_603_0.png)

## 实验

- Lab 16.2.6：研究网络安全威胁
- Lab 16.4.7：使用 SSH 配置网络设备
- Lab 16.5.2：保护网络设备

![](img/e71dc48d3ae3db3394e5857ab2acae75_603_1.png)

## Packet Tracer 活动

- Packet Tracer 16.4.6：配置安全密码和 SSH
- Packet Tracer 16.5.1：保护网络设备

## 检查你的理解问题

完成此处列出的所有复习问题，以测试你对本章主题和概念的理解。附录“‘检查你的理解’问题的答案”列出了答案。

+   1. 哪个组件旨在防止对计算机的未经授权的通信？
   a. security center
   b. port scanner
   c. antimalware
   d. antivirus
   e. firewall

2. 如果在 10 秒内有 2 次登录失败，哪个命令会阻止对 RouterA 的登录尝试 30 秒？
   a. `RouterA(config)# login block-for 10 attempts 2 within 30`
   b. `RouterA(config)# login block-for 30 attempts 2 within 10`
   c. `RouterA(config)# login block-for 2 attempts 30 within 10`
   d. `RouterA(config)# login block-for 30 attempts 10 within 2`

3. 网络安全记账功能的目的何在？
   a. to require users to prove who they are
   b. to determine which resources a user can access
   c. to keep track of the actions of users
   d. to provide challenge-and-response questions

4. 可能涉及使用 `nslookup` 和 `fping` 等工具的攻击类型是什么？
   a. access attack
   b. reconnaissance attack
   c. denial-of-service attack
   d. worm attack

5. SSH 相对于 Telnet 在远程管理路由器时提供什么好处？
   a. encryption
   b. TCP usage
   c. authorization
   d. connections via multiple vty lines

6. 保护用户免受外部威胁的最有效安全工具之一是什么？
   a. firewall
   b. router that run AAA services
   c. path server
   d. password encryption

7. 哪种类型的网络威胁旨在阻止授权用户访问资源？
   a. DoS attack
   b. access attack
   c. reconnaissance attack
   d. trust exploitation

8. AAA 框架提供了哪三项服务？（选择三项。）
   +   a. accounting
   b. automation
   c. authorization
   d. authentication
   e. availability
   f. autoconfiguration

9. 哪种恶意代码攻击是自包含的并试图利用系统中的特定漏洞？
   +   a. virus
   b. worm
   c. Trojan horse
   d. maintenance

10. 空调单元故障后，配线间中的一些路由器和交换机出现故障。这种情况描述了哪种类型的威胁？
    +   a. configuration
    b. environmental
    c. electrical
    d. maintenance

11. 术语“漏洞”是什么意思？
    +   a. a weakness that makes a target susceptible to an attack
    b. a computer that contains sensitive information
    c. a method of attack to exploit a target
    d. a known target or victim machine
    e. a potential threat a hacker creates

12. 实现对路由器的 SSH 访问必须执行哪三个配置步骤？（选择三项。）
    +   a. a password on the console line
    b. an IP domain name
    c. a user account
    d. an enable mode password
    e. a unique hostname
    f. an encrypted password

13. 网络侦察攻击的目标是什么？
    +   - a. discover and map systems
    - b. manipulate data without authorization to do so
    - c. disable network systems or services
    - d. deny access to resources by legitimate users

14. 出于安全原因，网络管理员需要确保本地计算机不能相互 ping。哪些设置可以完成此任务？
    +   - a. smartcard settings
    - b. firewall settings
    - c. MAC address settings
    - d. file system settings

15. 网络管理员通过 SSH 建立到交换机的连接。什么特征唯一描述了 SSH 连接？
    +   - a. out-of-band access to a switch through the use of a virtual terminal with password authentication
    - b. remote access to the switch through the use of a telephone dialup connection
    - c. on-site access to a switch through the use of a directly connected PC and a console cable
    - d. remote access to a switch where data is encrypted during the session
    - e. direct access to the switch through the use of a terminal emulation program

## 目标

完成本章后，你将能够回答以下问题：

- 在小型网络中使用哪些设备？
- 在小型网络中使用哪些协议和应用程序？
- 小型网络如何作为大型网络的基础？
- 如何使用 `ping` 和 `tracert` 命令的输出来验证连接并建立相对网络性能？
- 如何使用主机和 IOS 命令获取有关网络中设备的的信息？
- 常见的网络故障排除方法有哪些？
- 如何排除网络中设备的故障？

## 关键术语

本章使用了以下关键术语。你可以在本书末尾的词汇表中找到定义。

*冗余* 第 576 页

*协议分析器* 第 583 页

*服务质量 (QoS)* 第 577 页

## 引言 (17.0)

Hooray! 你已经来到本书的最后一章。你现在已经掌握了设置自己的网络所需的大部分基础知识。接下来去哪里？当然是构建网络。一旦你构建了网络，你需要验证它是否正常工作，并且可能还需要排除一些常见的网络问题。本章包含实验和 Packet Tracer 活动，帮助你练习作为网络管理员的新技能。让我们开始吧！

## 小型网络中的设备 (17.1)

小型网络中的网络设备数量和类型通常与大型网络不同，但各种规模的网络都必须能够提供许多相同的服务。

### 小型网络拓扑 (17.1.1)

大多数企业规模较小；因此，大多数企业网络也规模较小，这并不令人惊讶。

小型网络设计通常很简单。与大型网络相比，小型网络的设备数量和类型明显较少。例如，请参阅图 17-1 所示的示例小型企业网络。

![](img/e71dc48d3ae3db3394e5857ab2acae75_608_0.png)

图 17-1 小型企业网络拓扑

此小型网络需要路由器、交换机和无线接入点来连接有线和无线用户、IP 电话、打印机和服务器。小型网络通常具有单个 WAN 连接，由 DSL、电缆或以太网连接提供。

大型网络需要 IT 部门来维护、保护和排除网络设备的故障并保护组织数据。管理小型网络需要与管理大型网络所需的许多相同技能。小型网络由本地 IT 技术人员或合同专业人员管理。

### 小型网络的设备选择 (17.1.2)

与大型网络一样，小型网络也需要规划和设计以满足用户需求。规划确保所有需求、成本因素和部署选项都得到充分考虑。

第一个设计考虑因素之一是用于支持网络的中介设备类型。以下各节描述了在选择网络设备时必须考虑的因素。

#### 成本

交换机或路由器的成本由其容量和功能决定，例如可用端口的数量和类型以及背板速度。影响成本的其他因素包括网络管理能力、嵌入式安全技术和可选的高级交换技术。连接网络上每个设备所需的布线费用也必须考虑。影响成本考虑的另一个关键因素是要纳入网络中的冗余量。

#### 速度和端口/接口类型

选择路由器或交换机上的端口数量和类型是一个关键决策。较新的计算机具有内置 1 Gbps NIC。一些服务器甚至可能具有 10 Gbps 端口。虽然成本更高，但选择能够适应更高速度的第 2 层设备可以使网络演进，而无需更换核心设备。

#### 可扩展性

网络设备有固定和模块化物理配置。固定配置设备具有特定数量和类型的端口或接口，不能扩展。模块化设备具有扩展槽，可在需求演变时添加新模块。交换机可提供额外的端口用于 high-speed uplinks. Routers can be used to connect different types of networks. Care must be taken to select the appropriate modules and interfaces for the specific media.

#### 操作系统功能和服务

网络设备必须具有能够支持组织需求的操作系统，例如以下内容：

- 三层交换
- 网络地址转换 (NAT)
- 动态主机配置协议 (DHCP)
- 安全
- 服务质量 (QoS)
- 语音 over IP (VoIP)

### 小型网络的 IP 地址分配 (17.1.3)

在实施网络时，创建 IP 地址方案并使用它非常重要。互联网中每个主机或设备必须具有唯一的地址。

影响 IP 地址方案的设备包括以下内容：

- 终端用户设备，包括设备数量和连接类型（即有线、无线、远程访问）
- 服务器和外围设备（例如打印机和安全摄像头）
- 中间设备，包括交换机和接入点

建议您根据设备类型规划、记录和维护 IP 地址方案。使用计划好的 IP 地址方案可以更轻松地识别设备类型并排除故障，例如在使用协议分析器排查网络流量问题时。

例如，请考虑图 17-2 中小型至中型组织的拓扑结构。

该组织需要三个用户局域网（即 `192.168.1.0/24`、`192.168.2.0/24`、`192.168.3.0/24`）。该组织决定为每个 `192.168.x.0/24` 局域网实施一致的 IP 地址方案，采用表 17-1 所示的计划。

![](img/e71dc48d3ae3db3394e5857ab2acae75_611_0.png)

图 17-2 小型至中型组织拓扑

#### 表 17-1 一致的 IPv4 地址方案示例

| 设备类型 | 可分配 IP 地址范围 | 汇总为 |
|---|---|---|
| 默认网关（路由器） | `192.168.x.1–192.168.x.2` | `192.168.x.0/30` |
| 交换机（最多 2 台） | `192.168.x.5–192.168.x.6` | `192.168.x.4/30` |
| 接入点（最多 6 个） | `192.168.x.9–192.168.x.14` | `192.168.x.8/29` |
| 服务器（最多 6 台） | `192.168.x.17–192.168.x.22` | `192.168.x.16/29` |
| 打印机（最多 6 台） | `192.168.x.25–192.168.x.30` | `192.168.x.24/29` |
| IP 电话（最多 6 部） | `192.168.x.33–192.168.x.38` | `192.168.x.32/29` |
| 有线设备（最多 62 台） | `192.168.x.65–192.168.x.126` | `192.168.x.64/26` |
| 无线设备（最多 62 台） | `192.168.x.193–192.168.x.254` | `192.168.x.192/26` |

图 17-3 显示了使用预定义 IP 地址方案分配了 IP 地址的 `192.168.2.0/24` 网络设备的示例。

![](img/e71dc48d3ae3db3394e5857ab2acae75_612_0.png)

图 17-3 已分配地址的小型企业拓扑

例如，默认网关 IP 地址为 `192.168.2.1/24`，交换机 IP 地址为 `192.168.2.5/24`，服务器 IP 地址为 `192.168.2.17/24`，依此类推。

请注意，可分配的 IP 地址范围是有意在子网边界上分配的，以简化组类型的汇总。例如，假设另一台 IP 地址为 `192.168.2.6` 的交换机被添加到网络中。为了在网络策略中识别所有交换机，管理员可以指定汇总的网络地址 `192.168.x.4/30`。

### 小型网络中的冗余 (17.1.4)

网络设计的重要组成部分是可靠性。即使是小型企业也经常严重依赖其网络进行业务运营。网络故障可能代价高昂。

为了保持高度的可靠性，网络设计中需要冗余。冗余有助于消除单点故障。实现网络冗余的方法有很多。冗余可以通过安装重复设备来实现，也可以通过为关键区域提供重复的网络链路来实现，如图 17-4 所示。

![](img/e71dc48d3ae3db3394e5857ab2acae75_613_0.png)

冗余服务器可在服务器故障时使用。

冗余链路存在以在链路故障时提供替代路径。

冗余交换机存在以在交换机故障时使用。

冗余路由器可在路由器或路由故障时使用。

图 17-4 具有冗余设备和链路的小型网络

小型网络通常通过一个或多个默认网关向互联网提供单一出口点。如果路由器故障，整个网络将失去对互联网的连接。因此，对于小型企业来说，支付第二服务提供商作为备份可能是明智的。

### 流量管理 (17.1.5)

即使在小型网络中，良好网络设计的目标也是提高员工的生产力并最大限度地减少网络停机时间。网络管理员应考虑网络设计中各种类型的流量及其处理方式。

小型网络中的路由器和交换机应配置为以相对于其他数据流量适当的方式支持实时流量，例如语音和视频。事实上，良好的网络设计实施服务质量（QoS），在拥塞时根据优先级仔细分类流量，如图 17-5 所示。

![](img/e71dc48d3ae3db3394e5857ab2acae75_614_0.png)

图 17-5 QoS 优先级队列

交互式图形

### 检查您的理解——小型网络中的设备 (17.1.6)

请参考在线课程完成此活动。

## 小型网络应用程序和协议 (17.2)

除了考虑小型网络中的网络设备外，检查其必须支持的应用程序和服务也很重要。

### 常见应用程序 (17.2.1)

上一节讨论了小型网络的组件以及一些设计考虑因素。在刚设置网络时需要这些考虑因素。设置好后，网络仍需要某些类型的应用程序和协议才能正常工作。

网络的实用性仅取决于其上的应用程序。提供网络访问的软件程序或进程有两种形式：网络应用程序和应用层服务。

#### 网络应用程序

应用程序是用于通过网络通信的软件程序。一些终端用户应用程序具有网络感知能力，这意味着它们实现了应用层协议并且能够直接与协议栈的下层通信。电子邮件客户端和网络浏览器是此类应用程序的示例。

#### 应用层服务

其他程序可能需要应用层服务的帮助来使用网络资源，例如文件传输或网络打印 spooling。虽然它们对员工来说是透明的，但这些服务是与网络接口并为传输准备数据的程序。不同类型的数据——无论是文本、图形还是视频——都需要不同的网络服务，以确保它们能被 OSI 模型下层功能正确处理而做好准备。

每个应用程序或网络服务都使用协议，协议定义了要使用的标准和数据格式。如果没有协议，数据网络将没有通用的格式化和定向数据的方式。为了理解各种网络服务的功能，有必要熟悉控制其操作的底层协议。

在 Windows PC 上，您使用任务管理器查看当前正在运行的应用程序、进程和服务，如图 17-6 所示。

![](img/e71dc48d3ae3db3394e5857ab2acae75_615_0.png)

图 17-6 Windows 任务管理器

### 常见协议 (17.2.2)

无论是小型网络还是大型网络，技术人员的大部分工作都或多或少涉及网络协议。网络协议支持小型网络中员工使用的应用程序和服务。

网络管理员通常需要访问网络设备和服务器。

两种最常见的远程访问解决方案是 Telnet 和安全外壳 (SSH)。

SSH 是 Telnet 的安全替代方案。连接后，管理员可以像本地登录一样访问 SSH 服务器设备。

SSH 用于在 SSH 客户端与其他启用 SSH 的设备之间建立安全远程访问连接：


## 图 4-4 虚拟威胁防御设备的接口选项卡

取决于你运行的威胁防御平台，你可能会遇到不同类型的接口和特定模型的选项。例如，威胁防御模型 1010 带有带有内置交换机端口的以太网接口，如图 4-5 所示。为了在路由模式下配置此模型，你需要禁用接入模式`交换机端口`。

![图 4-5 威胁防御模型 1010 接口卡显示交换端口模式](img/04fig05.jpg)

**图 4-5** 威胁防御模型 1010 接口卡显示交换端口模式

### 步骤 3
在接口选项卡上，点击 `GigabitEthernet0/0` 和 `GigabitEthernet0/1` 旁边的铅笔图标，分别为内部网络和外部网络配置这些接口。使用表 4-2 所示的设置配置这两个接口。

**表 4-2** 入站和出站接口设置

| | `GigabitEthernet0/0` | `GigabitEthernet0/1` |
| --- | --- | --- |
| 接口名称 | `INSIDE_INTERFACE` | `OUTSIDE_INTERFACE` |
| 安全区域（可选） | `INSIDE_ZONE` | `OUTSIDE_ZONE` |
| IP 地址 | `192.168.1.1/24` | `172.16.1.1/24` |

要启用接口，必须为它指定一个名称；这是强制要求。然而，配置安全区域是一个可选步骤。在这里，在编辑物理接口窗口中，你可以动态创建一个安全区域并将其与接口关联。在将来，你可以使用 `Objects > Object Management > Interface` 页面来管理安全区域。

图 4-6 显示了 `GigabitEthernet0/0` 的常规设置；例如，它的名称为 `INSIDE_INTERFACE`。确保使用 `Enabled` 复选框启用接口。

![图 4-6 内部接口的常规配置](img/04fig06.jpg)

**图 4-6** 内部接口的常规配置

图 4-7 显示了向 `GigabitEthernet0/0` 接口手动分配静态 IP 地址。

![图 4-7 内部接口 GigabitEthernet0/0 上的静态 IP 地址](img/04fig07.jpg)

**图 4-7** 内部接口 GigabitEthernet0/0 上的静态 IP 地址

### 步骤 4
对 `GigabitEthernet0/1` 重复上述步骤以为外部网络启用它。完成后，点击 `Save` 按钮保存更改。

图 4-8 显示了入站和出站路由接口的配置。

![图 4-8 内部和外部接口配置](img/04fig08.jpg)

**图 4-8** 内部和外部接口配置

### 步骤 5
保存配置后，导航到 `Deploy > Deployment`。选择你想要应用更改的威胁防御，并点击 `Deploy` 按钮应用配置（参见图 4-9）。

![图 4-9 威胁防御配置部署](img/04fig09.jpg)

**图 4-9** 威胁防御配置部署

## 使用自动 IP 地址配置接口

![](img/key_topic_icon.jpg)

威胁防御既可以作为 DHCP 客户端，也可以作为 DHCP 服务器。例如，如果你在外部接口和互联网服务提供商（ISP）之间部署威胁防御，设备可以从 ISP 路由器为其外部接口动态获取 IP 地址。同时，威胁防御可以作为 DHCP 服务器，通过内部接口为其检查的主机动态提供 IPv4 地址。将威胁防御配置为 DHCP 服务器是一个可选选择；它不会影响深度包检测能力。

图 4-10 说明了两种场景：内部网络从运行在威胁防御上的 DHCP 服务获取 IP 地址，而威胁防御的外部接口从服务提供商获取 IP 地址。

![图 4-10 作为 DHCP 服务器和 DHCP 客户端的威胁防御](img/04fig10.jpg)

**图 4-10** 作为 DHCP 服务器和 DHCP 客户端的威胁防御

启用接口从 DHCP 服务器获取 IP 地址是一个简单的过程。例如，在配置外部接口期间，当你为接口分配静态 IP 地址时，只需从列表中选择 `Use DHCP`。当配置部署后，外部接口将从服务提供商获取 IP 地址。参见图 4-11 中的 `Use DHCP` 选项来启用接口以从 DHCP 服务器获取 IP 地址。

![图 4-11 作为 DHCP 客户端的威胁防御的接口配置](img/04fig11.jpg)

**图 4-11** 作为 DHCP 客户端的威胁防御的接口配置

然而，如果你想让威胁防御为其连接的主机提供 IP 地址，你需要在其上启用 DHCP 服务。以下步骤描述了如何为威胁防御配置 DHCP 服务：

### 步骤 1
转到 `Devices > Management` 并点击铅笔图标编辑威胁防御。

### 步骤 2
在威胁防御上分配静态 IP 地址 `192.168.1.1`。

### 步骤 3
在设备编辑器页面上，转到 DHCP 选项卡。默认情况下会出现 Server 页面。

### 步骤 4
点击 Server 选项卡上的 `Add` 按钮。

### 步骤 5
在 Server 下拉列表中选择内部接口。

### 步骤 6
为 DHCP 服务器创建地址池。记住池中的地址必须与接口处于同一子网。例如，如果你为内部接口分配 `192.168.1.1/24`，地址池应在 `192.168.1.2` 到 `192.168.1.254` 之间。

图 4-12 显示威胁防御的内部接口上启用了 DHCP 服务器，地址池为 `192.168.1.2` 到 `192.168.1.10`。

![图 4-12 威胁防御上的 DHCP 服务器配置](img/04fig12.jpg)

**图 4-12** 威胁防御上的 DHCP 服务器配置

### 步骤 7
勾选 `Enable DHCP Server` 复选框以启用该服务并点击 `OK`。你返回设备编辑器页面。

### 步骤 8
可选地，通过 DHCP 服务，威胁防御可以向你的 DHCP 传输任何 DNS 信息。Server 允许你手动输入域名和 DNS 地址。或者，你可以选择 `Auto-Configuration` 复选框，让威胁防御从连接到预定义接口的 DHCP 自动获取任何 DNS 信息。

### 步骤 9
点击 `Save` 按钮保存配置。

## 接口配置验证

配置部署到威胁防御后，内部网络和外部网络之间的主机应该成功通信。要测试连接性，你可以简单地在内外部主机之间运行 ICMP ping 测试。如果主机运行任何服务（如 Web 或 Secure Shell），你也可以使用它们来验证连通性。

在全新的部署中，管理中心不会显示`连接事件`。如果您想使用管理中心来验证通过威胁防御系统的任何连接尝试，您则需要在访问控制策略中启用日志记录。默认情况下，新的访问控制策略不包含任何可自定义的访问控制规则。由于我们将在随后的章节中详细描述访问控制规则的操作，目前，您可以添加一条简单的访问控制规则来允许流量，并在该规则中启用日志记录（参见图 4-13）。或者，在没有任何没有任何规则的访问控制策略中，您可以简单地在默认操作中启用日志（参见图 4-14），这也可以触发连接事件。

![图 4-13 在访问控制规则内启用日志](img/04fig13.jpg)

**图 4-13** 在访问控制规则内启用日志

![图 4-14 在访问控制策略中作为默认操作启用日志](img/04fig14.jpg)

**图 4-14** 在访问控制策略中作为默认操作启用日志

如果您部署了启用了日志功能的访问控制策略，现在您可以通过导航到管理中心的**分析 > 连接 > 事件**来查看任何关联连接的事件。

图 4-15 显示了内部主机（IP: 192.168.1.2）通过 ICMP、SSH 和 HTTPS 协议到外部主机（IP: 172.168.1.2）的连接尝试。

![图 4-15 内部与外部之间的连接事件表](img/04fig15.jpg)

**图 4-15** 内部与外部之间的连接事件表

当您运行 ICMP 流量时，可以使用 `debug` 命令查看系统处理 ICMP 包的详细信息。示例 4-6 显示了位于内部网络和外部网络的两台计算机之间的 ICMP 请求和响应。

### 示例 4-6 在威胁防御系统上调试 ICMP 流量

点击此处查看代码

```
debug icmp trace
debug icmp trace enabled at level 1
ICMP echo from INSIDE_INTERFACE:192.168.1.2 to OUTSIDE_INTERFACE:172.168.1.100
ID=4101 seq=56
ICMP reply from OUTSIDE_INTERFACE:172.168.1.100 to INSIDE_INTERFACE:192.168.1.2
ID=4101 seq=56
ICMP echo request from INSIDE_INTERFACE:192.168.1.2 to OUTSIDE_INTERFACE:172.168.1.100
ID=4101 seq=56
ICMP echo reply from OUTSIDE_INTERFACE:172.168.1.100 to INSIDE_INTERFACE:192.168.1.2
ID=4101 seq=56
```

如果 `ping` 测试失败，您需要确定接口的状态。您可以在威胁防御系统上运行以下命令，以确定接口状态并验证从管理中心应用到威胁防御系统的配置。命令输出略微取决于配置（静态与动态）。

`show ip`

`show interface brief`

`show interface interface_ID`

`show running-config`

示例 4-7 显示了 `show ip` 命令的输出。您可以在此输出中查看接口、逻辑名称和 IP 地址之间的映射。不过，请查看输出中的当前状态。

### 示例 4-7 show ip 命令输出

点击此处查看代码

```
show ip
System Addresses:
Interface            Name                IP address    Subnet mask    Method
GigabitEthernet0/0   INSIDE_INTERFACE    192.168.1.1   255.255.255.0  CONFIG
GigabitEthernet0/1   OUTSIDE_INTERFACE   172.168.1.1    255.255.255.0  CONFIG
Current IP Addresses:
Interface            Name                IP address    Subnet mask    Method
GigabitEthernet0/0   INSIDE_INTERFACE    192.168.1.1   255.255.255.0  CONFIG
GigabitEthernet0/1   OUTSIDE_INTERFACE   172.168.1.1    255.255.255.0  CONFIG
```

示例 4-7 显示了 GigabitEthernet0/0 和 GigabitEthernet0/1 接口、逻辑名称和 IP 地址之间的映射（注：此处原文“however”此处可能有误）。

```
show ip
System Addresses:
Interface            Name                IP address    Subnet mask    Method
GigabitEthernet0/0   INSIDE_INTERFACE    192.168.1.1   255.255.255.0  CONFIG
GigabitEthernet0/1   OUTSIDE_INTERFACE   172.168.1.1    255.255.255.0  CONFIG
Current IP Addresses:
Interface            Name                IP address    Subnet mask    Method
GigabitEthernet0/0   INSIDE_INTERFACE    192.168.1.1   255.255.255.0  CONFIG
GigabitEthernet0/1   OUTSIDE_INTERFACE   172.168.1.1    255.255.255.0  CONFIG
```

示例 4-8 确认了 GigabitEthernet0/0 和 GigabitEthernet0/1 接口已启用（使用静态）。`show interface brief` 命令提供了接口状态的概述。

### 示例 4-8 接口状态

点击此处查看代码

```
show interface brief
Interface              IP-Address      Status Protocol
GigabitEthernet0/0     192.168.1.1     up      up
GigabitEthernet0/1     172.168.1.1    up      up
```

示例 4-9 显示了 GigabitEthernet0/0 接口的详细信息。通过 `show interface interface_ID` 命令，您可以查看接口上发生的任何错误或丢包。

### 示例 4-9 接口详细统计

点击此处查看代码

```
> show interface GigabitEthernet 0/0
Interface GigabitEthernet0/0 "INSIDE_INTERFACE", is up, line protocol is up
  Hardware is netvmx3, BW 10000 Mbps, DLY usec
        Auto-Duplex(Full-duplex), Auto-Speed(10000 Mbps)
        Input flow control is unsupported, output flow control is unsupported
        MAC address 000a.000b.abcd, MTU 1500
        IP address 192.168.1.1, subnet mask 255.255.255.0
        277 packets input, 57079 bytes, 0 no buffer
        Received 0 broadcasts, 0 runts, 0 giants
        0 input errors, 0 CRC, 0 frame, 0 overrun, 0 ignored, 0 abort
        0 pause input, 0 resume input
        0 L2 decode drops
        215 packets output, 74336 bytes, 0 underruns
        0 pause output, 0 resume output
        0 output errors, 0 collisions, 0 interface resets
        0 late collisions, 0 deferred
        0 input reset drops, 0 output reset drops
        input queue (blocks free curr/low): (0/0)
        output queue (blocks free curr/low): (0/0)
  Traffic Statistics for "INSIDE_INTERFACE":
        277 packets input, 57099 bytes
        215 packets output, 74336 bytes
        7 packets dropped
      1 minute input rate 0 pkts/sec, 0 bytes/sec
      1 minute output rate 0 pkts/sec, 0 bytes/sec
      1 minute drop rate, 0 pkts/sec
      5 minute input rate 0 pkts/sec, 0 bytes/sec
      5 minute output rate 0 pkts/sec, 0 bytes/sec
      5 minute drop rate, 0 pkts/sec
>
```

```
> show running-config interface
!
interface GigabitEthernet0/0
 nameif INSIDE_INTERFACE
 cts manual
  propagate sgt preserve-untag
  policy static sgt disabled trusted
 security-level 0
 ip address 192.168.1.1 255.255.255.0
!
interface GigabitEthernet0/1
 nameif OUTSIDE_INTERFACE
 cts manual
  propagate sgt preserve-untag
  policy static sgt disabled trusted
 security-level 0
 ip address 172.16.1.1 255.255.255.0
!
interface GigabitEthernet0/2
 shutdown
 no nameif
 no security-level
 no ip address
.
.
<Output Omitted for Brevity>
.
.
>
```

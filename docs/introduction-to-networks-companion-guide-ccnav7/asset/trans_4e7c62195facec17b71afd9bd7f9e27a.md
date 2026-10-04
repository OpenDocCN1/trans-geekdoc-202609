
Autonegotiation is an optional function on most Ethernet switches and NICs. It enables two devices to automatically negotiate the best speed and duplex capabilities. Full-duplex is chosen if both devices have the capability, along with their highest common bandwidth.

In Figure 7-22, the Ethernet NIC for PC-A can operate in full-duplex or half-duplex and at 10 Mbps or 100 Mbps. PC-A is connected to switch S1 on port 1, which can operate in full-duplex or half-duplex and at 10 Mbps, 100 Mbps, or 1000 Mbps (1 Gbps). If both devices are using autonegotiation, the operating mode is full-duplex, at 100 Mbps.

![](img/e71dc48d3ae3db3394e5857ab2acae75_294_0.png)

![](img/e71dc48d3ae3db3394e5857ab2acae75_294_1.png)

图 7-22 双工和速率设置

## 注

Most Cisco switches and Ethernet NICs default to autonegotiation for speed and duplexing. Gigabit Ethernet ports operate only in full-duplex.

大多数 Cisco 交换机和以太网 NIC 默认对速率和双工使用自动协商。千兆以太网端口仅在全双工模式下运行。

Duplex mismatch is one of the most common causes of performance issues on 10/100 Mbps Ethernet links. It occurs when one port on the link operates at half-duplex while the other port operates at full-duplex, as shown in Figure 7-23. In this scenario, S2 will continually experience collisions because S1 keeps sending frames any time it has something to send.

双工不匹配是 10/100 Mbps 以太网链路性能问题最常见的原因之一。它发生在链路上的一个端口以半双工运行而另一个端口以全双工运行时，如图 7-23 所示。在这种情况下，S2 将不断发生冲突，因为 S1 在有帧要发送时就会持续发送帧。

![](img/e71dc48d3ae3db3394e5857ab2acae75_295_0.png)

## 图 7-23 双工不匹配

Duplex mismatch occurs when one or both ports on a link are reset, and the autonegotiation process does not result in the two link partners having the same configuration. It also can occur when users reconfigure one side of a link and forget to reconfigure the other. Both sides of a link should have autonegotiation on, or both sides should have it off. Best practice is to configure both Ethernet switch ports as full-duplex.

双工不匹配发生在链路上的一个或两个端口被重置，并且自动协商过程未能使两个链路伙伴具有相同配置时。它也可能发生在用户重新配置链路的一侧而忘记重新配置另一侧时。链路的两侧应都启用自动协商，或两侧都关闭。最佳做法是将两个以太网交换机端口都配置为全双工。

## Auto-MDIX (7.4.5)

At one time, connections between devices required the use of either a crossover cable or a straight-through cable. The type of cable required depended on the type of interconnecting devices. For example, Figure 7-24 identifies the correct cable types required to interconnect a switch to a switch, a switch to a router, a switch to a host, or a router to a host. A crossover cable is used for connecting like devices, and a straight-through cable is used for connecting unlike devices.

过去，设备之间的连接需要使用交叉电缆或直通电缆。所需电缆类型取决于互连设备的类型。例如，图 7-24 标识了将交换机连接到交换机、交换机连接到路由器、交换机连接到主机或路由器连接到主机所需的正确电缆类型。交叉电缆用于连接同类设备，直通电缆用于连接不同类设备。

> 注

A direct connection between a router and a host requires a crossover connection.

直接将路由器和主机连接起来需要交叉连接。

Most switch devices now support the automatic medium-dependent interface crossover (auto-MDIX) feature. When this feature is enabled, the switch automatically detects the type of cable attached to the port and configures the interfaces accordingly. Therefore, you can use either a crossover cable or a straight-through cable for connections to a copper 10/100/1000 port on a switch, regardless of the type of device on the other end of the connection.

现在大多数交换机设备都支持自动介质相关接口交叉（auto-MDIX）功能。当启用此功能时，交换机会自动检测连接到端口的电缆类型并相应地配置接口。因此，无论连接另一端是什么类型的设备，您都可以使用交叉电缆或直通电缆连接到交换机上的铜制 10/100/1000 端口。

The auto-MDIX feature is enabled by default on switches running Cisco IOS Release 12.2(18)SE or later. However, the feature can be disabled. For this reason, you should always use the correct cable type and should not rely on the auto-MDIX feature. Auto-MDIX can be re-enabled using the mdix auto interface configuration command.

在运行 Cisco IOS 版本 12.2(18)SE 或更高版本的交换机上，auto-MDIX 功能默认启用。但是，该功能可以被禁用。因此，您应始终使用正确的电缆类型，而不应依赖 auto-MDIX 功能。可以使用 mdix auto 接口配置命令重新启用 Auto-MDIX。

![](img/e71dc48d3ae3db3394e5857ab2acae75_296_0.png)

图 7-24 电缆类型

交互式图形

## 检查你的理解——交换机速率和转发方法 (7.4.6)

Refer to the online course to complete this activity.

请参考在线课程完成此活动。

## 摘要 (7.5)

The following is a summary of the topics in the chapter and their corresponding online modules.

以下是本章主题及其对应在线模块的摘要。

### 以太网帧

Ethernet operates at the data link layer and the physical layer. Ethernet standards define both the Layer 2 protocols and the Layer 1 technologies. Ethernet operates at the LLC and MAC sublayers of the data link layer. Data encapsulation includes the following: Ethernet frame, Ethernet addressing, and Ethernet error detection. Ethernet LANs use switches that operate in full-duplex. The Ethernet frame fields are Preamble and Start Frame Delimiter, Destination MAC Address, Source MAC Address, EtherType, Data, and FCS.

以太网工作在数据链路层和物理层。以太网标准定义了第 2 层协议和第 1 层技术。以太网工作在数据链路层的 LLC 和 MAC 子层。数据封装包括以下内容：以太网帧、以太网寻址和以太网差错检测。以太网局域网使用工作在全双工模式的交换机。以太网帧字段为前导码和帧起始定界符、目的 MAC 地址、源 MAC 地址、EtherType、数据和 FCS。

### 以太网 MAC 地址

The binary number system uses the digits 0 and 1. Decimal uses 0 through 9. Hexadecimal uses 0 through 9 and the letters A through F. The MAC address is used to identify the physical source and destination devices (NICs) on the local network segment. MAC addressing provides a method for device identification at the data link layer of the OSI model. An Ethernet MAC address is a 48-bit address expressed using 12 hexadecimal digits, or 6 bytes. An Ethernet MAC address consists of a 6-digit hexadecimal vendor OUI code followed by a 6-digit hexadecimal vendor-assigned value. When a device is forwarding a message to an Ethernet network, the Ethernet header includes the source and destination MAC addresses. In Ethernet, different MAC addresses are used for Layer 2 unicast, broadcast, and multicast communications.

二进制数制使用数字 0 和 1。十进制使用 0 到 9。十六进制使用 0 到 9 和字母 A 到 F。MAC 地址用于标识本地网络段上的物理源和目的设备（NIC）。MAC 地址提供了一种在 OSI 模型数据链路层进行设备识别的方法。以太网 MAC 地址是 48 位地址，使用 12 位十六进制数字或 6 字节表示。以太网 MAC 地址由 6 位十六进制厂商 OUI 代码后跟 6 位十六进制厂商分配值组成。当设备向以太网转发消息时，以太网报头包含源 MAC 地址和目的 MAC 地址。在以太网中，不同的 MAC 地址用于第 2 层单播、广播和多播通信。

### MAC 地址表

A Layer 2 Ethernet switch makes forwarding decisions based solely on Layer 2 Ethernet MAC addresses. The switch dynamically builds its MAC address table by examining the source MAC addresses of the frames received on a port. The switch forwards frames by searching for a match between the destination MAC address in the frame and an entry in the MAC address table. As a switch receives frames from different devices, it is able to populate its MAC address table by examining the source MAC address of each frame. When the MAC address table of the switch contains the destination MAC address, the switch is able to filter the frame and forward it out a single port.

第 2 层以太网交换机仅基于第 2 层以太网 MAC 地址做出转发决策。交换机通过检查端口上接收到的帧的源 MAC 地址动态构建其 MAC 地址表。交换机通过在帧中的目的 MAC 地址与 MAC 地址表中的条目之间查找匹配项来转发帧。随着交换机从不同设备接收帧，它能够通过检查每个帧的源 MAC 地址来填充其 MAC 地址表。当交换机的 MAC 地址表包含目的 MAC 地址时，交换机能够过滤帧并将其转发到单个端口。

### 交换机速率和转发方法

Switches use one of two forwarding methods for switching data between network ports: store-and-forward switching or cut-through switching. Two variants of cut-through switching are fast-forward and fragment-free switching. Two methods of memory buffering are port-based memory buffering and shared memory buffering. Two types of duplex settings are used for communications on an Ethernet network: full-duplex and half-duplex. Autonegotiation is an optional function on most Ethernet switches and NICs. It enables two devices to automatically negotiate the best speed and duplex capabilities. Full-duplex is chosen if both devices have the capability, and their highest common bandwidth is chosen. Most switch devices now support the automatic medium-dependent interface crossover (auto-MDIX) feature. When this feature is enabled, the switch automatically detects the type of cable attached to the port and configures the interfaces accordingly.

交换机使用两种转发方法之一在网络端口之间切换数据：存储转发切换或直通切换。直通切换的两种变体是快速转发和无碎片切换。内存缓冲的两种方法是基于端口的内存缓冲和共享内存缓冲。以太网通信中使用两种双工设置：全双工和半双工。自动协商是大多数以太网交换机和 NIC 上的可选功能。它使两个设备能够自动协商最佳速率和双工能力。如果两个设备都具备该能力，则选择全双工，并选择它们共同的最高带宽。现在大多数交换机设备都支持自动介质相关接口交叉（auto-MDIX）功能。当启用此功能时，交换机会自动检测连接到端口的电缆类型并相应地配置接口。

## 练习

The following activities provide practice with the topics introduced in this chapter. The lab is available in the companion *Introduction to Networks Labs & Study Guide (CCNAv7)* (ISBN 9780136634454). The Packet Tracer activity instructions are also provided in the *Labs & Study Guide*. The PKA files are available in the online course.

以下活动提供了本章介绍主题的练习。实验室可在配套的 *网络基础实验室与学习指南 (CCNAv7)*（ISBN 9780136634454）中找到。Packet Tracer 活动说明也提供在 *实验室与学习指南* 中。PKA 文件可在在线课程中找到。

![](img/e71dc48d3ae3db3394e5857ab2acae75_298_0.png)

## 实验

- Lab 7.1.6: Use Wireshark to Examine Ethernet Frames
- Lab 7.1.6: 使用 Wireshark 检查以太网帧
- Lab 7.2.7: View Network Device MAC Addresses
- Lab 7.2.7: 查看网络设备 MAC 地址
- Lab 7.3.7: View the Switch MAC Address Table
- Lab 7.3.7: 查看交换机 MAC 地址表

## 检查你的理解问题

Complete all the review questions listed here to test your understanding of the topics and concepts in this chapter. The appendix “Answers to ‘Check Your Understanding’ Questions” lists the answers.

请完成此处列出的所有复习问题，以测试您对本章主题和概念的理解。附录“‘检查你的理解’问题的答案”列出了答案。

1. Which network device makes forwarding decisions based only on the destination MAC address that is contained in a frame?
1. 哪个网络设备仅基于帧中包含的目的 MAC 地址做出转发决策？
- a. repeater
- a. 中继器
- b. hub
- b. 集线器
- c. Layer 2 switch
- c. 第 2 层交换机
- d. router
- d. 路由器

2. For which network device is the primary function to send data to a specific destination based on the information found in the MAC address table?
2. 对于哪个网络设备，其主要功能是根据 MAC 地址表中找到的信息将数据发送到特定目的地？
- a. hub
- a. 集线器
- b. router
- b. 路由器
- c. Layer 2 switch
- c. 第 2 层交换机
- d. modem
- d. 调制解调器

3. What does the LLC sublayer do?
3. LLC 子层做什么？
- a. It performs data encapsulation.
- a. 它执行数据封装。
- b. It communicates with upper protocol layers.
- b. 它与上层协议层通信。
- c. It is responsible for media access control.
- c. 它负责媒体访问控制。
- d. It adds a header and trailer to a packet to form an OSI Layer 2 PDU.
- d. 它向数据包添加报头和尾部以形成 OSI 第 2 层 PDU。

4. Which statement is true about MAC addresses?
4. 关于 MAC 地址，哪个说法是正确的？
- a. MAC addresses are implemented by software.
- a. MAC 地址由软件实现。
- b. A NIC needs a MAC address only if it is connected to a WAN.
- b. 只有当 NIC 连接到广域网时才需要 MAC 地址。
- c. The first 3 bytes are used by the vendor-assigned OUI.
- c. 前 3 个字节由厂商分配的 OUI 使用。
- d. The ISO is responsible for MAC address regulations.
- d. ISO 负责 MAC 地址规范。

5. What happens to a runt frame received by a Cisco Ethernet switch?
5. Cisco 以太网交换机接收到的残帧会发生什么？
- a. The frame is dropped.
- a. 帧被丢弃。
- b. The frame is returned to the originating network device.
- b. 帧被返回给源网络设备。
- c. The frame is broadcast to all other devices on the same network.
- c. 帧被广播到同一网络上的所有其他设备。
- d. The frame is sent to the default gateway.
- d. 帧被发送到默认网关。

6. What are the minimum and maximum sizes of an Ethernet frame? (Choose two.)
6. 以太网帧的最小和最大尺寸是多少？（选择两个。）
- a. 56 bytes
- a. 56 字节
- b. 64 bytes
- b. 64 字节
- c. 128 bytes
- c. 128 字节
- d. 1024 bytes
- d. 1024 字节
- e. 1518 bytes
- e. 1518 字节

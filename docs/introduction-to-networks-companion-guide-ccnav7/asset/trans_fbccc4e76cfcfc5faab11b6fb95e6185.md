

![](img/e71dc48d3ae3db3394e5857ab2acae75_323_0.png)

Figure 8-15 Example Topology of Directly Connected and Remote Networks

图 8-15 直接连接和远程网络的示例拓扑

A router can learn about remote networks in one of two ways:

路由器可以以两种方式之一了解远程网络：

- **Manually:** Remote networks are manually entered into the route table using static routes.
- **Dynamically:** Remote routes are automatically learned using a dynamic routing protocol.

- **手动：** 远程网络使用静态路由手动输入到路由表中。
- **动态：** 远程路由使用动态路由协议自动学习。

## Static Routing (8.5.3)

## 静态路由（8.5.3）

*Static routes* are route entries that are manually configured. Figure 8-16 shows an example of a static route that was manually configured on router R1. A static route includes the remote network address and the IP address of the next hop router.

*静态路由* 是手动配置的路由条目。图 8-16 显示了在路由器 R1 上手动配置的静态路由示例。静态路由包括远程网络地址和下一跳路由器的 IP 地址。

![](img/e71dc48d3ae3db3394e5857ab2acae75_323_1.png)

```
R1(config)# ip route 10.1.1.0 255.255.255.0 209.165.200.226
```

Figure 8-16 Static Routing Example

图 8-16 静态路由示例

If there is a change in the network topology, a static route is not automatically updated and must be manually reconfigured. For example, in Figure 8-17, R1 has a static route to reach the 10.1.1.0/24 network via R2. If that path becomes unavailable, R1 needs to be reconfigured with a new static route to the 10.1.1.0/24 network via R3. Router R3 therefore needs to have a route entry in its routing table to send packets destined for 10.1.1.0/24 to R2.

如果网络拓扑发生变化，静态路由不会自动更新，必须手动重新配置。例如，在图 8-17 中，R1 具有经由 R2 到达 10.1.1.0/24 网络的静态路由。如果该路径变得不可用，则需要重新配置 R1，使其具有经由 R3 到达 10.1.1.0/24 网络的新静态路由。因此，路由器 R3 需要在其路由表中具有路由条目，以便将目标为 10.1.1.0/24 的数据包发送到 R2。

![](img/e71dc48d3ae3db3394e5857ab2acae75_324_0.png)

Figure 8-17 Static Routing Does Not Automatically Update to Topology Changes

图 8-17 静态路由不会自动更新以适应拓扑变化

Static routing has the following characteristics:

静态路由具有以下特征：

- A static route must be configured manually.
- The administrator needs to reconfigure a static route if there is a change in the topology and the static route is no longer viable.
- A static route is appropriate for a small network and when there are few or no redundant links.
- A static route is commonly used with a dynamic routing protocol for configuring a default route.

- 静态路由必须手动配置。
- 如果拓扑发生变化且静态路由不再可行，管理员需要重新配置静态路由。
- 静态路由适用于小型网络以及冗余链路很少或没有的情况。
- 静态路由通常与动态路由协议一起用于配置默认路由。

## Dynamic Routing (8.5.4)

## 动态路由（8.5.4）

A *dynamic routing protocol* allows the routers to automatically learn about remote networks, including a default route, from other routers. Routers that use dynamic routing protocols automatically share routing information with other routers and compensate for any topology changes without involving the network administrator. If there is a change in the network topology, routers share this information using the dynamic routing protocol and automatically update their routing tables.

*动态路由协议* 允许路由器从其他路由器自动了解远程网络，包括默认路由。使用动态路由协议的路由器会自动与其他路由器共享路由信息，并在不涉及网络管理员的情况下补偿任何拓扑变化。如果网络拓扑发生变化，路由器会使用动态路由协议共享此信息并自动更新其路由表。

Dynamic routing protocols include OSPF and Enhanced Interior Gateway Routing Protocol (EIGRP). Figure 8-18 shows an example of routers R1 and R2 automatically sharing network information using the routing protocol OSPF.

动态路由协议包括 OSPF 和增强型内部网关路由协议（EIGRP）。图 8-18 显示了路由器 R1 和 R2 使用路由协议 OSPF 自动共享网络信息的示例。

![](img/e71dc48d3ae3db3394e5857ab2acae75_325_0.png)

Figure 8-18 Dynamic Routing Example

图 8-18 动态路由示例

Basic dynamic routing configuration only requires the network administrator to enable the directly connected networks within the dynamic routing protocol. The dynamic routing protocol automatically does the following:

基本的动态路由配置仅要求网络管理员在动态路由协议中启用直接连接的网络。动态路由协议会自动执行以下操作：

- Discovers remote networks
- Maintains up-to-date routing information
- Chooses the best paths to destination networks
- Attempts to find a new best path if the current path is no longer available

- 发现远程网络
- 维护最新的路由信息
- 选择到目标网络的最佳路径
- 如果当前路径不再可用，则尝试找到新的最佳路径

When a router is manually configured with a static route or learns about a remote network dynamically using a dynamic routing protocol, the remote network address and next hop address are entered into the IP routing table. As shown in Figure 8-19, if there is a change in the network topology, the routers automatically adjust and attempt to find a new best path.

当路由器手动配置静态路由或使用动态路由协议动态了解远程网络时，远程网络地址和下一跳地址会输入到 IP 路由表中。如图 8-19 所示，如果网络拓扑发生变化，路由器会自动调整并尝试找到新的最佳路径。

![](img/e71dc48d3ae3db3394e5857ab2acae75_325_1.png)

Figure 8-19 Dynamic Routing Automatically Updates to Topology Changes

图 8-19 动态路由自动更新以适应拓扑变化

## Note

## 注意

It is common for some routers to use a combination of both static routes and a dynamic routing protocol.

一些路由器同时使用静态路由和动态路由协议的组合是很常见的。

## Video—IPv4 Router Routing Tables (8.5.5)

## 视频—IPv4 路由器路由表（8.5.5）

Refer to the online course to view this video.

请参考在线课程观看此视频。

## Introduction to an IPv4 Routing Table (8.5.6)

## IPv4 路由表简介（8.5.6）

Notice in Figure 8-20 that R2 is connected to the internet. Therefore, the administrator configured R1 with a default static route sending packets to R2 when there is no specific entry in the routing table that matches the destination IP address. R1 and R2 are also using OSPF routing to advertise directly connected networks.

请注意图 8-20 中 R2 已连接到互联网。因此，管理员为 R1 配置了默认静态路由，当路由表中没有与目标 IP 地址匹配的特定条目时，将数据包发送到 R2。R1 和 R2 也使用 OSPF 路由来通告直接连接的网络。

![](img/e71dc48d3ae3db3394e5857ab2acae75_326_0.png)

Figure 8-20 Sample Topology for IPv4 Routing Table

图 8-20 IPv4 路由表的示例拓扑

The show ip route privileged EXEC mode command is used to view the IPv4 routing table on a Cisco IOS router. Example 8-2 shows the IPv4 routing table of router R1.

show ip route 特权 EXEC 模式命令用于查看 Cisco IOS 路由器上的 IPv4 路由表。示例 8-2 显示了路由器 R1 的 IPv4 路由表。

### Example 8-2 R1 IPv4 Routing Table

### 示例 8-2 R1 IPv4 路由表

```
R1# show ip route
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
      D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
      N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
      E1 - OSPF external type 1, E2 - OSPF external type 2
      i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
      ia - IS-IS inter area, * - candidate default, U - per-user static route
      o - ODR, P - periodic downloaded static route, H - NHRP, l - LISP
      a - application route
      + - replicated route, % - next hop override, p - overrides from PFR
Gateway of last resort is 209.165.200.226 to network 0.0.0.0
S*   0.0.0.0/0 [1/0] via 209.165.200.226, GigabitEthernet0/0/1
10.0.0.0/24 is subnetted, 1 subnets
O       10.1.1.0 [110/2] via 209.165.200.226, 00:02:45, GigabitEthernet0/0/1
192.168.10.0/24 is variably subnetted, 2 subnets, 2 masks
C       192.168.10.0/24 is directly connected, GigabitEthernet0/0/0
L       192.168.10.1/32 is directly connected, GigabitEthernet0/0/0
209.165.200.0/24 is variably subnetted, 2 subnets, 2 masks
C       209.165.200.224/30 is directly connected, GigabitEthernet0/0/1
L       209.165.200.225/32 is directly connected, GigabitEthernet0/0/1
R1#
```

At the beginning of each routing table entry is a code that is used to identify the type of route or how the route was learned. Common route sources (codes) include these:

每个路由表条目的开头都有一个代码，用于标识路由的类型或路由的学习方式。常见的路由来源（代码）包括以下内容：

- L: Directly connected local interface IP address
- C: Directly connected network
- S: Static route manually configured by an administrator
- O: OSPF
- D: EIGRP

- L：直接连接的本地接口 IP 地址
- C：直接连接的网络
- S：管理员手动配置的静态路由
- O：OSPF
- D：EIGRP

The routing table displays all of the known IPv4 destination routes for R1.

路由表显示了 R1 的所有已知 IPv4 目标路由。

A directly connected route is automatically created when a router interface is configured with IP address information and is activated. The router adds two route entries with the codes C (that is, the connected network) and L (that is, the local interface IP address of the connected network). The route entries also identify the exit interface to use to reach the network. The two directly connected networks in this example are 192.168.10.0/24 and 209.165.200.224/30.

当路由器接口配置了 IP 地址信息并被激活时，会自动创建直接连接路由。路由器添加两个路由条目，代码为 C（即连接的网络）和 L（即连接网络的本地接口 IP 地址）。路由条目还标识用于到达网络的出接口。此示例中的两个直接连接网络为 192.168.10.0/24 和 209.165.200.224/30。

Routers R1 and R2 are also using the OSPF dynamic routing protocol to exchange router information. In the sample routing table, R1 has a route entry for the 10.1.1.0/24 network that it learned dynamically from router R2 thanks to the OSPF routing protocol.

路由器 R1 和 R2 也使用 OSPF 动态路由协议交换路由器信息。在示例路由表中，R1 具有 10.1.1.0/24 网络的路由条目，这是它通过 OSPF 路由协议从路由器 R2 动态学习到的。

A default route has a network address of all zeros. For example, say that the IPv4 network address is 0.0.0.0. A static route entry in the routing table begins with the code S*, as highlighted in Example 8-2.

默认路由的网络地址为全零。例如，假设 IPv4 网络地址为 0.0.0.0。路由表中的静态路由条目以代码 S* 开头，如示例 8-2 中突出显示的那样。

![](img/e71dc48d3ae3db3394e5857ab2acae75_327_0.png)

## Check Your Understanding—Introduction to Routing (8.5.7)

## 检查你的理解—路由简介（8.5.7）

Refer to the online course to complete this activity.

请参考在线课程完成此活动。

## Summary (8.6)

## 摘要（8.6）

The following is a summary of the topics in the chapter and their corresponding online modules.

以下是本章主题及其对应在线模块的摘要。

## Network Layer Characteristics

## 网络层特性

The network layer (OSI Layer 3) provides services to allow end devices to exchange data across networks. IPv4 and IPv6 are the principal network layer communication protocols. The network layer also includes the routing protocol OSPF and messaging protocols such as ICMP. Network layer protocols perform four basic operations: addressing end devices, encapsulation, routing, and de-encapsulation. IPv4 and IPv6 specify the packet structure and processing used to carry the data from one host to another host. IP encapsulates the transport layer segment by adding an IP header, which is used to deliver the packet to the destination host. The IP header is examined by Layer 3 devices (that is, routers) as it travels across a network to its destination. IP is connectionless, meaning that it creates no dedicated end-to-end connection before data is sent. In addition, IP is best effort, meaning that it does not guarantee that all packets that are sent are, in fact, received. Finally, IP is media independent, meaning that it operates independently of the media that carry the data at lower layers of the protocol stack.

网络层（OSI 第 3 层）提供服务以允许终端设备在网络间交换数据。IPv4 和 IPv6 是主要的网络层通信协议。网络层还包括路由协议 OSPF 和消息协议如 ICMP。网络层协议执行四个基本操作：寻址终端设备、封装、路由和解封装。IPv4 和 IPv6 指定用于将数据从一个主机携带到另一个主机的分组结构和处理。IP 通过添加 IP 头封装传输层段，该头用于将分组传递到目标主机。IP 头在穿越网络到达其目的地时会被第 3 层设备（即路由器）检查。IP 是无连接的，这意味着在发送数据之前它不会创建专用端到端连接。此外，IP 是尽力而为的，这意味着它不能保证发送的所有分组实际上都被接收。最后，IP 是媒体独立的，这意味着它独立于协议栈下层承载数据的媒体而运行。

## IPv4 Packet

## IPv4 分组

An IPv4 packet header consists of fields containing information about the packet. These fields contain binary numbers that are examined by the Layer 3 process. The binary values of the fields identify various settings of the IP packet. Significant fields in the IPv4 header include Version, DS, Header Checksum, TTL, Protocol, Source IPv4 Address, and Destination IPv4 Address.

IPv4 分组头由包含有关分组信息的字段组成。这些字段包含由第 3 层进程检查的二进制数字。字段的二进制值标识 IP 分组的各种设置。IPv4 头中的重要字段包括 Version、DS、Header Checksum、TTL、Protocol、Source IPv4 Address 和 Destination IPv4 Address。

## IPv6 Packet

## IPv6 分组

IPv6 is designed to overcome the limitations of IPv4, including IPv4 address depletion, lack of end-to-end connectivity, and increased network complexity. IPv6 increases the available address space, improves packet handling, and eliminates the need for NAT. The fields in the IPv6 packet header include Version, Traffic Class, Flow Label, Payload Length, Next Header, Hop Limit, Source IPv6 Address, and Destination IPv6 Address.

IPv6 设计用于克服 IPv4 的限制，包括 IPv4 地址耗尽、缺乏端到端连接性和网络复杂性增加。IPv6 增加了可用地址空间，改进了分组处理，并消除了对 NAT 的需求。IPv6 分组头中的字段包括 Version、Traffic Class、Flow Label、Payload Length、Next Header、Hop Limit、Source IPv6 Address 和 Destination IPv6 Address。


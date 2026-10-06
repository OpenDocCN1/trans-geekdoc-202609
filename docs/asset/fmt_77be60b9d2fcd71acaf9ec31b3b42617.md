
第 2 层以太网交换机使用第 2 层 MAC 地址进行转发决策。它完全不知道帧数据部分中携带的数据（协议），例如 IPv4 数据包、ARP 消息或 IPv6 ND 数据包。交换机的转发决策完全基于第 2 层以太网 MAC 地址。

以太网交换机检查其 `MAC 地址表` 为每个帧做出转发决策。相比之下，传统的以太网集线器将位重复到除入端口外的所有端口。在图 7-14 中，四端口交换机刚刚加电。表格显示了 `MAC 地址表`，该表尚未学习四个连接 PC 的 MAC 地址。

## 注意

本节中的 MAC 地址已缩短以用于演示目的。

![](img/e71dc48d3ae3db3394e5857ab2acae75_285_0.png)

交换机 `MAC 地址表` 为空。

## 图 7-14  交换机启动时 MAC 地址表为空

## 注意

`MAC 地址表` 有时被称为内容可寻址内存 (`CAM`) 表。虽然 `CAM` 表这一术语相当常见，但就本课程而言，我们将其称为 `MAC 地址表`。

### 交换机学习和转发 (7.3.2)

交换机通过检查端口上接收到的帧的源 MAC 地址动态构建其 `MAC 地址表`。交换机通过在帧中的目的 MAC 地址与 `MAC 地址表` 中的条目之间搜索匹配来转发帧。

#### 检查源 MAC 地址

进入交换机的每个帧都会被检查以学习新信息。它通过检查帧的源 MAC 地址和帧进入交换机的端口号来实现。如果源 MAC 地址不存在，则将其连同入端口号一起添加到表中。如果源 MAC 地址已存在，则交换机会更新该条目的刷新计时器。默认情况下，大多数以太网交换机在表中保留条目 5 分钟。

例如，在图 7-15 中，`PC-A` 正在向 `PC-D` 发送以太网帧。表格显示交换机将 `PC-A` 的 MAC 地址添加到 `MAC 地址表`。

注意

如果源 MAC 地址存在于表中但位于不同的端口，交换机将其视为新条目。条目将被替换，使用相同的 MAC 地址但使用更新的端口号。

#### 查找目的 MAC 地址

如果目的 MAC 地址是单播地址，交换机会在帧的目的 MAC 地址与其 `MAC 地址表` 中的条目之间查找匹配项。如果目的 MAC 地址在表中，则交换机将帧转发到指定的端口。如果目的 MAC 地址不在表中，则交换机将帧转发到除入端口外的所有端口。这称为 *未知单播*。

如图所示 7-16 所示，交换机在表中没有 `PC-D` 的目的 MAC 地址，因此它将帧发送到除端口 1 之外的所有端口。

注意

如果目的 MAC 地址是广播或多播地址，则帧会泛洪到除入端口外的所有端口。

| 端口 | MAC 地址 |
|------|-------------|
| 1 | 00-0A |

![](img/e71dc48d3ae3db3394e5857ab2acae75_287_0.png)

1. `PC-A` 发送以太网帧。
2. 交换机将 `PC-A` 的端口号和 MAC 地址添加到 `MAC 地址表`。

## 图 7-15 交换机学习 PC-A 的 MAC 地址

| 端口 | MAC 地址 |
|------|-------------|
| 1 | 00-0A |

![](img/e71dc48d3ae3db3394e5857ab2acae75_287_1.png)

1. 目的 MAC 地址不在表中。
2. 交换机将帧转发到所有其他端口。

## 图 7-16 交换机将帧转发到所有其他端口

### 过滤帧 (7.3.3)

随着交换机从不同设备接收帧，它能够通过检查每个帧的源 MAC 地址来填充其 `MAC 地址表`。当交换机的 `MAC 地址表` 包含目的 MAC 地址时，交换机能够过滤帧并转发到单个端口。

在图 7-17 中，`PC-D` 正在回复 `PC-A`。交换机在端口 4 的入站帧中看到 `PC-D` 的 MAC 地址。然后交换机将 `PC-D` 的 MAC 地址放入与端口 4 关联的 `MAC 地址表` 中。

**`MAC 地址表`**

| 端口 | MAC 地址 |
|------|-------------|
| 1 | 00-0A |
| 4 | 00-0D |

![](img/e71dc48d3ae3db3394e5857ab2acae75_288_0.png)

交换机将 `PC-D` 的端口号和 MAC 地址添加到其 `MAC 地址表`。

## 图 7-17  交换机学习 PC-D 的 MAC 地址

接下来，由于交换机在 `MAC 地址表` 中具有 `PC-A` 的目的 MAC 地址，因此它仅将帧发送到端口 1，如图 7-18 所示。

接下来，`PC-A` 如图 7-19 所示向 `PC-D` 发送另一个帧。`MAC 地址表` 已包含 `PC-A` 的 MAC 地址；因此，该条目的 5 分钟刷新计时器被重置。接下来，由于交换机表包含 `PC-D` 的目的 MAC 地址，因此它仅将帧发送到端口 4。

![](img/e71dc48d3ae3db3394e5857ab2acae75_288_1.png)

### 视频——连接交换机上的 MAC 地址表 (7.3.4)

交换机可以有一个端口关联多个 MAC 地址。当交换机连接到另一台交换机时很常见。交换机将为每个具有不同源 MAC 地址的接收帧拥有单独的 `MAC 地址表` 条目。

请参考在线课程观看此视频。

**`MAC 地址表`**

| 端口 | MAC 地址 |
|------|-------------|
| 1 | 00-0A |
| 4 | 00-0D |

![](img/e71dc48d3ae3db3394e5857ab2acae75_289_0.png)

![](img/e71dc48d3ae3db3394e5857ab2acae75_289_1.png)

- 1. 交换机为目标地址有一个 `MAC 地址` 条目。
- 2. 交换机过滤帧，仅通过端口 1 发送出去。

## 图 7-18 交换机将帧转发到属于 PC-A 的端口

**`MAC 地址表`**

| 端口 | MAC 地址 |
|------|-------------|
| 1 | 00-0A |
| 4 | 00-0D |

![](img/e71dc48d3ae3db3394e5857ab2acae75_289_2.png)

![](img/e71dc48d3ae3db3394e5857ab2acae75_289_3.png)

- 1. 交换机接收来自 `PC-A` 的另一帧并刷新端口 1 的 `MAC 地址` 条目的计时器。
- 2. 交换机具有目标 `MAC 地址` 的最新条目并过滤帧，仅通过端口 4 转发。

## 图 7-19 交换机将帧转发到属于 PC-D 的端口

## 视频—向默认网关发送帧 (7.3.5)

当设备的 IP 地址位于远程网络上时，以太网帧不能直接发送到目标设备。相反，以太网帧发送到默认网关的 MAC 地址，即路由器。

请参考在线课程观看此视频。

## 活动—Switch It! (7.3.6)

使用此活动检查您对交换机如何学习和转发帧的理解。

请参考在线课程完成此活动。

## 实验—查看交换机 MAC 地址表 (7.3.7)

在本实验中，您将完成以下目标：

- Part 1: 构建和配置网络
- Part 2: 检查交换机 `MAC 地址表`

## 交换机速率和转发方法 (7.4)

交换机可能具有实现各种转发方法以提高网络性能的能力。

### Cisco 交换机上的帧转发方法 (7.4.1)

正如您在上一节中所学，交换机使用其 `MAC 地址表` 来确定用于转发帧的端口。对于 Cisco 交换机，实际上有两种帧转发方法，并且根据情况，使用其中一种而不是另一种是有充分理由的。

交换机使用以下其中一种转发方法在网络端口之间切换数据：

- *存储转发切换*: 采用这种帧转发方法，交换机接收整个帧并计算 CRC。交换机使用基于帧中位数（1）数的数学公式来确定接收到的帧是否有错误。如果 CRC 有效，交换机将查找目的地址，从而确定出站接口。然后帧被转发到正确的端口。
- **直通切换:** 采用这种帧转发方法，交换机在帧完全接收之前就转发帧。至少必须在帧转发之前读取帧的目的地址。

存储转发切换的一个很大的优势是交换机在传播帧之前确定帧是否有错误。当在帧中检测到错误时，交换机丢弃该帧。丢弃有错误的帧可以减少损坏数据消耗的带宽量。存储转发切换对于需要帧分类以进行流量优先级的汇聚网络上的服务质量（QoS）分析是必需的。例如，语音 over IP（VoIP）数据流需要优先于网页浏览流量。

图 7-20 显示了存储转发过程。

![](img/e71dc48d3ae3db3394e5857ab2acae75_291_0.png)

> 存储转发交换机接收整个帧并计算 CRC。如果 CRC 有效，交换机将查找目的地址，从而确定出站接口。然后帧被转发到正确的端口。

图 7-20 存储转发切换

### 直通切换 (7.4.2)

在直通切换中，交换机在传输未完成时就对数据进行操作。交换机仅缓冲足够多的帧以读取目的 MAC 地址，以便确定用于转发数据的端口。目的 MAC 地址位于帧的前缀之后的最初 6 个字节中。交换机在交换表中查找目的 MAC 地址，确定出站接口端口，并通过指定的交换机端口将帧转发到其目的地。交换机不对帧执行任何错误检查。

图 7-21 显示了直通切换过程。

![](img/e71dc48d3ae3db3394e5857ab2acae75_292_0.png)

直通交换机在帧完全接收之前就转发帧。至少必须在帧转发之前读取帧的目的地址。

图 7-21 直通切换

直通切换有两种变体：

- *快速转发切换*: 快速转发切换提供最低的延迟级别。采用快速转发切换，交换机在读取目的地址后立即转发数据包。由于快速转发切换在整个数据包接收完成之前就开始转发，因此有时会转发带有错误的包。这种情况很少发生，目的网卡在接收时会丢弃有故障的数据包。在快速转发模式下，延迟从接收到的第一个位到传输的第一个位进行测量。快速转发切换是典型的直通切换方法。
- *无碎片切换*: 在无碎片切换中，交换机在转发前存储帧的前 64 个字节。无碎片切换可以被视为存储转发切换和快速转发切换之间的折中。交换机仅存储帧的前 64 个字节的原因是大多数网络错误和冲突发生在前 64 个字节中。无碎片切换试图通过在转发帧之前对帧的前 64 个字节执行少量错误检查来增强快速转发切换，以确保未发生冲突。无碎片切换是在存储转发切换的高延迟和高完整性与快速转发切换的低延迟和降低的完整性之间的一种折中。

一些交换机配置为按端口执行直通切换，直到达到用户定义的错误阈值，然后自动更改为存储转发。当错误率低于阈值时，端口会自动更改回直通切换。

### 交换机上的内存缓冲 (7.4.3)

以太网交换机可能会使用缓冲技术在转发它们之前存储帧。当目标端口由于拥塞而繁忙时，也可以使用缓冲。交换机在可以传输之前存储帧。

如表 7-2 所示，有两种内存缓冲方法。

表 7-2 内存缓冲方法

| 方法 | 描述 |
|---|---|
| 基于端口的内存缓冲 | 帧存储在与特定入站和出站端口链接的队列中。 |
|  | 只有当队列中前面的所有帧都已成功传输时，帧才会被传输到出站端口。 |
|  | 由于目标端口繁忙，单个帧可能会延迟内存中所有帧的传输。即使其他帧可以传输到空闲的目标端口，也会发生这种延迟。 |
| 共享内存缓冲 | 所有帧都存放在所有交换机端口共享的公共内存缓冲区中，并且端口所需的缓冲内存量是动态分配的。 |
|  | 缓冲区中的帧动态链接到目标端口，使数据包能够在一个端口上接收然后在另一个端口上传输，而无需将其移动到不同的队列。 |

共享内存缓冲导致能够存储更大的帧，并且可能丢弃更少的帧。这在非对称交换中很重要，非对称交换允许在不同端口上具有不同的数据速率，例如将服务器连接到 10 Gbps 交换机端口而将 PC 连接到 1 Gbps 端口。

### 双工和速率设置 (7.4.4)

交换机上最基本的两个设置是每个单独交换机端口的带宽（有时称为速率）和双工设置。交换机端口与连接的设备（如计算机或其他交换机）之间的双工和带宽设置必须匹配。

在以太网网络上通信中使用两种类型的双工设置：

- 全双工：连接的两端可以同时发送和接收。
- 半双工：连接的一端一次只能发送。

`Autonegotiation` is an optional function on most Ethernet switches and NICs. It enables two devices to automatically negotiate the best speed and duplex capabilities. Full-duplex is chosen if both devices have the capability, along with their highest common bandwidth.

In Figure 7-22, the Ethernet NIC for `PC-A` can operate in full-duplex or half-duplex and at 10 Mbps or 100 Mbps. `PC-A` is connected to switch `S1` on port 1, which can operate in full-duplex or half-duplex and at 10 Mbps, 100 Mbps, or 1000 Mbps (1 Gbps). If both devices are using autonegotiation, the operating mode is full-duplex, at 100 Mbps.

![](img/e71dc48d3ae3db3394e5857ab2acae75_294_0.png)

![](img/e71dc48d3ae3db3394e5857ab2acae75_294_1.png)

图 7-22 双工和速率设置

#### 注

Most Cisco switches and Ethernet NICs default to autonegotiation for speed and duplexing. Gigabit Ethernet ports operate only in full-duplex.

大多数 Cisco 交换机和以太网 NIC 默认对速率和双工使用自动协商。千兆以太网端口仅在全双工模式下运行。

Duplex mismatch is one of the most common causes of performance issues on 10/100 Mbps Ethernet links. It occurs when one port on the link operates at half-duplex while the other port operates at full-duplex, as shown in Figure 7-23. In this scenario, `S2` will continually experience collisions because `S1` keeps sending frames any time it has something to send.

双工不匹配是 10/100 Mbps 以太网链路性能问题最常见的原因之一。它发生在链路上的一个端口以半双工运行而另一个端口以全双工运行时，如图 7-23 所示。在这种情况下，`S2` 将不断发生冲突，因为 `S1` 在有帧要发送时就会持续发送帧。

![](img/e71dc48d3ae3db3394e5857ab2acae75_295_0.png)

## 图 7-23 双工不匹配

Duplex mismatch occurs when one or both ports on a link are reset, and the autonegotiation process does not result in the two link partners having the same configuration. It also can occur when users reconfigure one side of a link and forget to reconfigure the other. Both sides of a link should have autonegotiation on, or both sides should have it off. Best practice is to configure both Ethernet switch ports as full-duplex.

双工不匹配发生在链路上的一个或两个端口被重置，并且自动协商过程未能使两个链路伙伴具有相同配置时。它也可能发生在用户重新配置链路的一侧而忘记重新配置另一侧时。链路的两侧应都启用自动协商，或两侧都关闭。最佳做法是将两个以太网交换机端口都配置为全双工。

## Auto-MDIX (7.4.5)

At one time, connections between devices required the use of either a crossover cable or a straight-through cable. The type of cable required depended on the type of interconnecting devices. For example, Figure 7-24 identifies the correct cable types required to interconnect a switch to a switch, a switch to a router, a switch to a host, or a router to a host. A crossover cable is used for connecting like devices, and a straight-through cable is used for connecting unlike devices.

过去，设备之间的连接需要使用交叉电缆或直通电缆。所需电缆类型取决于互连设备的类型。例如，图 7-24 标识了将交换机连接到交换机、交换机连接到路由器、交换机连接到主机或路由器连接到主机所需的正确电缆类型。交叉电缆用于连接同类设备，直通电缆用于连接不同类设备。

> 注

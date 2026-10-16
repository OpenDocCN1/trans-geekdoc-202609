
-   [UTP 和 STP 的导线由细小的铜线对扭转而成。线对的扭转可保护免受外部射频和电磁、磁性干扰，并减少线对之间的串扰。当电流产生的电磁场使一组线上的传输数据被另一组线“ pickup”时，就会发生串扰。每根线对在电缆中以不同的扭转速率（即每英寸扭转次数）扭转；因此，同一电缆内一对线上的信号无法跨越到另一对线上（至少在同一电缆内）。

-   UTP 布线有多种类别。不同类别是通过加强线对的扭转、提高导体质量以及提高外部屏蔽质量来实现的。[Table 11.9](#c11.xhtml#table11-9) 显示了原始 UTP 类别。

[**TABLE 11.9**](#c11.xhtml#tableanchor11-9) **UTP categories**

| UTP category || Throughput || Notes |
| --- | --- | --- |
| Cat 1 || Voice only || Not suitable for networks but usable by modems |
| --- | --- | --- |
| Cat 2 || 4 Mbps || Not suitable for most networks; often employed for host-to-terminal connections on mainframes |
| Cat 3 || 10 Mbps || Primarily used in 10BaseT Ethernet networks (offers only 4 Mbps when used on Token Ring networks) and as telephone cables |
| Cat 4 || 16 Mbps || Primarily used in Token Ring networks |
| Cat 5 || 100 Mbps || Used in 100BaseTX, FDDI, and ATM networks |
| Cat 6 || 1,000 Mbps || Used in high-speed networks |
| Cat 7 || 10 Gbps || Used on 10 gigabit-speed networks |

-   扭绞对布线最常见的问题包括：

*   为高吞吐量网络使用了错误类别的扭绞对电缆
*   部署的扭绞对电缆长度超过了其建议的最大长度（即 100 米）
*   在存在显著干扰的环境中使用 UTP

#### Conductors

-   导体网络布线的长度限制源于用作导体的金属的电阻。铜是最常用的导体，也是一种在室温下性能优异且成本低廉的导体。然而，它仍然会阻碍电子的流动。这种电阻导致信号随电缆长度的衰减和质量下降。

-   每种电缆类型所规定的最大长度表明，在此长度之后信号退化可能会影响数据高效传输。这种信号退化称为衰减。虽然可以使用比电缆额定长度更长的线路段，但该段会出现更多错误和重传，最终导致网络性能下降。随着传输速度的提高，衰减更为明显。建议在传输速度提高时使用更短的线路长度。

-   通过使用集线器（repeaters）或集中器（concentrators）可以延长长线路。集线器是一种信号放大设备，类似于车载或家庭音响的放大器。它增强 incoming data stream 的信号强度，并通过第二个端口广播。集中器功能相同，但拥有多个端口。不过，连续使用超过四个集线器（或集线器）是不建议的（参见侧边栏“5-4-3 规则”）。

### Network Topologies

-   计算机和网络设备的物理布局和组织方式称为网络拓扑。逻辑拓扑是将网络系统分组为受信任集合的方式。物理拓扑不一定与逻辑拓扑相同。网络物理布局的四种基本拓扑为环形、总线、星形和网状。

**Ring Topology** 环形拓扑将每个系统作为圆周上的点连接（参见 [Figure 11.9](#c11.xhtml#figure11-9)）。连接介质作为单向传输循环。同一时间只能有一个系统传输数据。流量由令牌（token）管理。令牌是一个数字通行证，环绕环形直到某个系统抓取它。拥有令牌的系统可以传输数据。数据和令牌会传送到特定目的地。随着数据沿环流动，每个系统检查该数据是否为其自身。如果不是，则转递令牌；如果是，则读取数据。数据接收完毕后，令牌释放并继续在环中循环，直至另一个系统抓取它。如果环形的任何一段断裂，环形上的所有通信都会停止。某些环形拓扑的实现采用双环机制（双向相反方向运行的环），以防止单点故障。

![FIGURE 11.9 A ring topology ](images/c11f009.jpg)

[**FIGURE 11.9**](#c11.xhtml#figureanchor11-9) A ring topology 

**Bus Topology** 总线拓扑将每个系统连接到主干线或后骨线上。总线上的所有系统可以同时传输数据，这可能导致碰撞。碰撞发生在两个系统同时传输数据时，信号相互干扰。为避免碰撞，系统使用碰撞避免机制，基本上“监听”当前是否有其他流量。如果听到流量，系统稍后再尝试。如果没有听到，系统即传输数据。总线拓扑下传输的数据所有网络系统都能接收；如果数据未针对特定系统，则该系统忽略。总线拓扑的优点是，若单个段失败，其他段仍可继续通信。但主干线仍是单点故障。

总线拓扑有两种类型：线性和树形。线性总线拓扑使用单条主干线，所有系统直接连接到它上。树形总线拓扑使用单条主干线，并设有可支持多个系统的分支。[Figure 11.10](#c11.xhtml#figure11-10) 展示了两种类型。今天几乎不再使用总线，因为它必须在两端终止，且任何断开都会导致整个网络瘫痪。

![FIGURE 11.10 A linear bus topology and a tree bus topology ](images/c11f010.jpg)

[**FIGURE 11.10**](#c11.xhtml#figureanchor11-10) A linear bus topology and a tree bus topology 

**Star Topology** 星形拓扑采用集中连接设备。该设备可以是简单的集线器或交换机。每个系统通过专用段连接到中心集线器（参见 [Figure 11.11](#c11.xhtml#figure11-11)）。若任一段失败，其他段仍可继续工作。但中心集线器是单点故障。通常星形拓扑的布线比其他拓扑少，且更易于定位损坏的线缆。

逻辑总线和逻辑环可以作为物理星形实现。以太网是基于总线的技术。它可以作为物理星形部署，但集线器或交换机实际上是逻辑总线连接设备。同样，令牌环是基于环形的技术。它可以通过多站接入单元（MAU）作为物理星形部署，内部则实现逻辑环连接。

![FIGURE 11.11 A star topology ](images/c11f011.jpg)

[**FIGURE 11.11**](#c11.xhtml#figureanchor11-11) A star topology 

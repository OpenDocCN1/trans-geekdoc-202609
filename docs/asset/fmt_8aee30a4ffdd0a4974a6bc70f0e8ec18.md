
防止控制平面计算的路由出现环路的一种方法是简单地不向会将流量转发回我的（发送节点）的邻居通告路由。这称为水平分割；它导致网络中流量的流动像瀑布或溪流床中的水一样，沿着阻力最小的路径流向目的地，如 Figure 12-5 所示。

![Image](img/12fig05.jpg)

**Figure 12-5** *Traffic Flow from a Metric-based Packet Divide* **图 12-5** *基于度量的数据包分区的流量流向*

在 Figure 12-5 中，如果流量在 C 处进入网络（在源 2）并且目的地在 E 之外，它将沿环的右侧向下流动。然而，如果流量在 A 处进入网络并且目的地在 E 之外，它将沿环的左侧向下流动。为了防止目的地在 E 之外的流量在此环上循环，控制平面可以做的一件简单的事情是，要么不允许 A 向 C 通告目的地，要么不允许 C 向 A 通告目的地。阻止这两个路由器中的一个向另一个通告称为水平分割，因为它阻止路由在地平线上传播，或者说阻止在任何特定设备知道沿特定链路传递的流量会被循环的点之外传播。

水平分割是通过只允许设备通过其未用于到达相关目的地的接口通告可达性来实现的。在本例中：

• D 使用 E 到达目的地，因此它不会向 E 通告可达性

• C 使用 D 到达目的地，因此它不会向 D 通告可达性

• B 使用 E 到达目的地，因此它不会向 E 通告可达性

• A 使用 B 到达目的地，因此它不会向 B 通告可达性

因此，A 阻止 B 知道它通过 C 到达目的地的替代路径，而 C 阻止 D 知道它通过 A 到达目的地的替代路径。无环备选路径将跨越网络中的此水平分割点。在 Figure 12-5 中，A 可以计算出 C 的路径成本小于 A 的路径成本，因此 A 向 C 转发到目的地的任何流量都将沿着 A 所知的路径以外的某条路径转发。在 LFA 术语中，C 是 A 的下游邻居。

因此，另一种看待 LFA 计算的方法是找到环中的水平分割点，并确定分割点两侧的设备是否会通过数据包分水岭转发流量。

### P/Q Space

描述 LFA 如何工作的另一种模型是 *P/Q Space；* Figure 12-6 说明了这一点。

![Image](img/12fig06.jpg)

**Figure 12-6** *P Space and Q Space* **图 12-6** *P 空间和 Q 空间*

最容易从两个空间的定义开始。假设 `[E,D]` 链路需要从故障中保护：

• 从 E 计算一棵反向最短路径树（E 在计算此树时使用通往自身的路径成本，而不是远离自身的成本，因为流量沿此路径流向 D）。

• 删除 `[E,D]` 链路，以及只能通过该链路到达的任何节点。

• E 仍可到达的剩余节点为 Q 空间。

• 从 D 计算一棵最短路径树。

• 删除 `[E,D]` 链路，以及只能通过该链路到达的任何节点。

• D 仍可到达的剩余节点在 P 空间中。

如果 D 能在 `[E,D]` 链路故障时找到 Q 空间中的一个路由器来转发流量，这就是一个 LFA。

### Remote Loop-Free Alternates 远程无环备选路径

如果没有 LFA 怎么办？有时可以找到远程无环备选路径 rLFA，它也可以承载流量到目的地。rLFA 并未直接连接到计算路由器，而是距离一个或多个跳；这意味着流量必须通过计算路由器和远程下一跳之间的路由器承载；这通常是通过隧道传输流量来实现的。

这些模型可以在不查看计算所需的数学的情况下解释 rLFA。了解环将在何处“分割”为 P 和 Q，或分割为水平分割划分的两半，有助于你快速了解即使没有 LFA 存在时 rLFA 也可用于规避故障的位置。回到 Figure 12-6，例如，如果 `[E,D]` 链路故障，D 必须简单地等待网络收敛后再开始向目的地转发流量。E 的最佳路径已因故障而从 D 的树中移除，而 E 没有可转发流量的 LFA。

回到本节开始时对无环路径的受限定义——任何设备可以转发流量而不被返回的邻居。设备在本地链路故障情况下发送数据包的邻居没有特别的理由必须是本地连接的。Chapter 9，“Network Virtualization，” 描述了创建可承载网络中任意两个节点之间流量的隧道或覆盖拓扑的能力。

鉴于能够通过 C 隧道传输流量，以便 C 不基于实际目的地转发流量，而是基于隧道头，D 可以直接将流量转发给 A，从而绕过环路。因此，当 `[E,D]` 链路故障时，D 可以执行以下操作：

1. 计算网络中可隧道传输流量且不会返回到 C 本身的最接近点。
2. 形成到该路由器的隧道。
3. 将流量封装到隧道头中。
4. 转发流量。

**Note**

在实际实现中，rLFA 隧道会在故障发生时之前预先计算，而不是在故障时计算。这些 rLFA 隧道也不一定需要对正常转发过程可见。本文档是为了清晰地说明此过程的*如何*工作而安排的，而不是关注其通常的实现方式。

D 将流量转发到隧道目的地，而不是原始目的地；这绕过了 C 的本地转发表中针对原始目的地的条目，该条目会将流量循环回 C。关于此类交点计算的讨论将在 第 13 章 中关于 Dijkstra 最短路径优先算法的部分进行。

### Bellman-Ford 无环路径计算

Bellman-Ford 是较易理解的协议之一，因为它通常通过将关于某个目的地的最新学习信息与关于同一目的地的现有信息进行比较来实现。如果新发现的路由比当前已知的路由更好，则路径列表中较高的成本路由会简单地被替换——正如用于在网络中寻找无环路径的最短路径规则所规定。按这种方式迭代整个拓扑，可以找到到每个目的地的最短路径集。 图 12-7 用于说明该过程。

![Image](img/12fig07.jpg)

**Figure 12-7** *A Sample Network to Run Bellman-Ford*

**Note**

虽然 Bellman-Ford 因其在 *Routing Information Protocol (RIP)* 等广泛部署的协议中实现的分布式变体而广为人知，但它最初是作为在描述节点和边拓扑的单个结构上执行的搜索算法设计的。本文将 Bellman-Ford 讨论为 *algorithm*。与 Bellman-Ford 相似的分布式算法将在下一节中讨论。

#### Bellman-Ford as an Algorithm

尽管该算法最早由 Alfonso Shimbel 于 1955 年提出，^(1) 并于 1957 年由 Edward F. Moore 再次提出，^(2) 但该算法以 Richard Bellman 的名字命名，他于 1958 年发表了它，^(3) 以及 Lester Ford, Jr.，他于 1956 年发表了它。^(4)

Bellman-Ford 将在最坏情况下以 O(`V`*`E`) 计算到每个可达目的地的最短路径树，其中 *V* 是网络中节点的数量（顶点），*E* 是链路（边）的数量。从本质上讲，这意味着 Bellman-Ford 在拓扑上运行并计算最短路径树所需的时间与设备和链路的数量成线性关系；将其中任一数量加倍将使运行时间加倍。同时将两者加倍将使运行时间增加 4 倍。

因此，当在最坏情况下对较大拓扑使用时，Bellman-Ford 是一种相对较慢的算法，此时拓扑表中的节点从离根最远到离根最近排序。如果拓扑表从离根最近到离根最远排序，Bellman-Ford 可以在 O(`E`) 中终止，这要快得多；在现实世界中，很难确保任一排序，因此构建最短路径树实际所需的时间通常介于 O(`V`*`E`) 和 O(`E`) 之间。

Bellman-Ford 是一种贪心算法，通过假设网络中除本地节点外的每个节点只能通过无限成本到达来运行，并在遍历拓扑时用实际成本替换这些无限成本。假设所有节点都是无限远的称为放松计算，因为它对网络中所有未知目的地的距离使用近似值，一旦计算出实际成本就将其替换为实际成本。

**Note**

用于计算最短路径树的任何算法的实际运行时间通常会被将拓扑变化信息通过网络所需的时间所掩盖；有关此主题的更多信息，请参阅 第 14 章， “Reacting to Topology Changes”。所有这些协议的实现，特别是在其分布式形式中，都包含许多优化措施，以将它们的运行时间降低到远低于最坏情况，因此虽然最坏情况作为参考点给出，但在实际部署的网络中，它通常对每个算法的性能影响很小（或没有）。

要在此拓扑上运行 Bellman-Ford，它必须首先转换为一组向量和距离，并存储在数据结构中，如 表 12-1 所示。

**Table 12-1** *Topology, or Edges, Represented as a Table for Bellman-Ford*

| **Row** || **Source (s)** || **Destination (d)** || **Distance (cost)** |

| --- | --- | --- | --- |

| 1 || F (6) || G (7) || 1 |

| 2 || E (5) || H (8) || 1 |

| 3 || D (4) || H (8) || 2 |

| 4 || D (4) || E (5) || 1 |

| 5 || B (2) || F (6) || 1 |

| 6 || B (2) || E (5) || 2 |

| 7 || C (3) || D (4) || 1 |

| 8 || A (1) || B (2) || 2 |

| 9 || A (1) || C (3) || 1 |

该表中共有九个条目，因为网络中有九条链路（边）。最短路径算法计算单向树（沿图的一个方向）。在 图 12-7 中的网络中，SPT 显示起源于节点 1，计算显示从节点 1 向外移动，节点 1 将是计算进行的点。算法的伪代码如下：

**Note**

此示例中的数据结构是 1 引用（或基于），这意味着第一行是 1 而不是 0，以便使编号更清晰。

```
 // create a set to hold the response, with one entry for each node  
 // the first slot in the resulting structure will represent node 1,  
 // the second node 2 etc.  
 define route[nodes] {  
   predecessor // as a node  
   cost // as an integer  
 }  
 // set the source (me) to 0 cost  
 // position 1 in the array is the origination point’s entry  
 route[1].predecessor = NULL  
 route[1].cost = 0  
 // table 1, above, is held in an array called topo  
 // walk the topo (edges) table once for each entry in the route  
 // (results) table, replacing longer entries with shorter ones  
 i = nodes  
 while i > 0 {  
   j = 1  
   while j <= nodes { // iterates over every row in the topology table  
     source_router = topo[j].s  
     destination_router = topo[j].d  
     link_cost = topo[j].cost  
     if route[source_router].cost == NULL {  
       source_router_cost = INFINITY  
     } else {  
       source_router_cost = route[source_router].cost  
     }  
     if route[destination_router].cost == NULL {  
       destination_router_cost = INFINITY  
     } else {  
       destination_router_cost = route[destination_router].cost  
     }  
     if source_router_cost + link_cost <= destination_router_cost {  
       route[destination_router].cost = source_router_cost + link_cost  
       route[destination_router].predecessor = source_router  
     }  
     j = j + 1 //or j++ depending on what pseudocode this is representing  
   }  
   i = i - 1  
 }
```

这段代码看起来比实际更复杂。关键行是比较 `if route[topo[j].s].cost + topo[j].cost < route[topo[j].d].cost;` 通过一个示例聚焦于这一行是有用的。在外层循环的第一次运行中（该循环对结果表中的每个条目运行一次，这里称为 `route`）：

• 对于 `topo` 表的第一行：

• `j` 为 1，因此 `topo[j].s` 为节点 6 (F)，边表中向量的源

• `j` 为 1，因此 `topo[j].d` 为节点 7 (G)，边表中向量的目标

• `route[6].cost =` 无穷大，`topo[1].cost` = 1，且 `route[7].cost` = 无穷大

• 无穷大 + 1 == 无穷大，因此条件失败且没有其他操作发生

• 任何源成本为无穷大的 `topo` 表条目都会产生相同的结果，因为无穷大 + 任何值始终等于无穷大；其余包含源成本为无穷大的行将被跳过。

• 对于 `topo` 表的第八行（第八条边）：

• `j` 为 8，因此 `topo[j].s` 为节点 1 (A)，边表中向量的源

• `j` is 8, so `topo[j].d` is node 2 (B), the destination of the vector in the edge table

• `route[1].cost` = 0, `topo[8].cost` = 2, and `route[2].cost` = infinity

• 0 + 2 <= infinity, so the condition succeeds

• `route[2].predecessor` is set to 1, and `route[2].cost` is set to 2

• For the ninth line of the topo table (the ninth edge):

• `j` is 9, so `topo[j].s` is node 1 (A), the source of the vector in the edge table

• `j` is 9, so `topo[j].d` is node 3 (C), the destination of the vector in the edge table

• `route[1].cost` = 0, `topo[9].cost` = 1, and `route[3].cost` = infinity

• 0 + 1 <= infinity, so the condition succeeds

• `route[3].predecessor` is set to 1, and `route[3].cost` is set to 1

In the second run of the outer loop:

• For the fifth line of the topo table (the fifth edge):

• `j` is 5, so `topo[j].s` is node 2 (B), the source of the vector in the edge table

• `j` is 5, so `topo[j].d` is node 6 (F), the destination of the vector in the edge table

• `route[2].cost` = 2, `topo[5].cost` = 1, and `route[6].cost` = infinity

• 2 + 1 <= infinity, so the condition succeeds

• `route[6].predecessor` is set to 2, and `route[6].cost` is set to 3

• For the sixth line of the topo table (the sixth edge):

• `j` is 6, so `topo[j].s` is 2 (B), the source of the vector in the edge table

• `j` is 6, so `topo[j].d` is 5 (E), the destination of the vector in the edge table

• `route[2].cost` = 2, `topo[6].cost` = 2, and `route[5].cost` = infinity

• 2 + 2 <= infinity, so the condition succeeds

• `route[5].predecessor` is set to 2, and `route[5].cost` is set to 4

• The remainder of this run is shown in 表 12-2.

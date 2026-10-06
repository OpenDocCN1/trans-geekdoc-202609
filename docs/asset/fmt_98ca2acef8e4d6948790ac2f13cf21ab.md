
1974 年，J. W. Suurballe 发表了一篇论文，描述了如何使用多次运行 `Dijkstra` 的 `SPF` 算法在网络中找到多个不相交拓扑。^2 该算法本质上是计算一次 `SPF`，移除 `SPT` 上使用的部分链路，然后在剩余链路上计算第二次 `SPF`。由于 Suurballe 算法依赖于通过 `SPT` 计算的链路的方向性，因此用示例说明比解释更容易；Figure 13-14 至 Figure 13-18 被用作示例。

![Image](img/13fig14.jpg)

**Figure 13-14** *Using Suurballe’s Algorithm for Finding Disjoint Paths, Step 1*

![Image](img/13fig15.jpg)

**Figure 13-15** *Using Suurballe’s Algorithm for Finding Disjoint Paths, Step 2*

![Image](img/13fig16.jpg)

**Figure 13-16** *Using Suurballe’s Algorithm for Finding Disjoint Paths, Step 3*

![Image](img/13fig17.jpg)

**Figure 13-17** *Using Suurballe’s Algorithm for Finding Disjoint Paths, Step 4*

![Image](img/13fig18.jpg)

**Figure 13-18** *A Depth First Search Tree Example*

Figure 13-14 显示了第一次 `SPF` 运行完成后且初始 `SPT` 计算完毕后的操作状态。请注意链路上的方向箭头；通常不会将 `SPT` 视为有方向的，但实际上它是这样，链路都指向远离源或树的根。当 `F` 向 `X` 计算一棵树时，它也会产生一棵方向相反的树，箭头指向相反方向。

`SPT` 上的边（或链路）称为树边，而不在生成的 `SPT` 上的边（或链路）称为非树边。在 Figure 13-14 中，树边以实心黑色并带方向箭头标记，非树边为浅灰色虚线。

第二步显示在 Figure 13-15 中。

Figure 13-15 显示了每个链接的修改后成本；每个属于原始 SPT 的链接（每个树边，以实线显示）具有两个成本，一个在每个方向，而不原本属于 SPT 的链接（非树边，以虚线显示）保持其原始成本。注意显示每个情况下成本方向的箭头；这在计算的下一步中将很重要。计算每个树边的两个方向链接的成本：

1. 将链接的一端称为 `u`，另一端称为 `v`；注意方程在两个方向上运行。

2. 从源到 `v` 的成本从从 `u` 到 `v` 的链接成本中减去。

3. 加上从源到 `u` 的成本。

如果源是 `s`：

`dsp = d(u,v) − d(s,v) + d(s,u)`

这本质上将树边的成本设置为 0，正如通过对 `[B,E]` 链接进行数学运算所能看到的那样：

- `B` 是 `u`，`E` 是 `v`，`A` 是 `s`

- `d(u,v) = 2`，`d(s,v) = 3`，`d(s,u) = 1`

- `2 − 3 + 1 = 0`

然而，所有非树边将被设置为某个（通常更大）非零成本。对于 Figure 13-15 中的网络：

- 对于 `[B,A]` 链接（注意 `[A,B]` 不是正在计算的方向树中的链接）：

`B` 是 `u`，`A` 是 `v`，`A` 是 `s`

`d(u,v) = 0`，`d(s,v) = 0`，`d(s,u) = 1`

`0 − 0 + 1 = 1`

- 对于 `[E,B]` 链接：

`E` 是 `u`，`B` 是 `v`，`A` 是 `s`

`d(u,v) = 2`，`d(s,v) = 1`，`d(s,u) = 3`

`2 − 1 + 3 = 4`

- 对于 `[C,A]` 链接：

`C` 是 `u`，`A` 是 `v`，`A` 是 `s`

`d(u,v) = 2`，`d(s,v) = 0`，`d(s,u) = 2`

`2 − 0 + 2 = 4`

- 对于 `[F,D]` 链接：

`F` 是 `u`，`D` 是 `v`，`A` 是 `s`

`d(u,v) = 1`，`d(s,v) = 4`，`d(s,u) = 5`

`1 − 4 + 5 = 2`

- 对于 `[D,B]` 链接：

`D` 是 `u`，`B` 是 `v`，`A` 是 `s`

`d(u,v) = 1`，`d(s,v) = 1`，`d(s,u) = 2`

`1 − 1 + 2 = 2`

下一步，如 Figure 13-16 所示，是删除所有指向源的方向边，该源沿原始 SPT 指向特定目的地（本例中为 Z），反转沿同一路径的零成本边（链接）的方向，然后再次运行 Dijkstra 的 SPF，创建同一拓扑上的第二个 SPT。

回到原始 SPT，从 X 到 Z 的路径沿路径 `[A,B,D,F]`。因此，指向源 A 的四个非零成本边（虚线）沿此路径已被删除。沿同一路径 `[A,B,D,F]`，每条边的方向已被反转；例如，`[A,B]` 原本从 A 指向 B，现在从 B 指向 A。下一步是运行此图上的 SPF，记住 *流量不能逆着链接的方向流动*。 resulting tree 显示在 Figure 13-17 中。

Figure 13-17 显示了原始树和新计算的树叠加在原始拓扑上作为两条不同的虚线。两个拓扑仍然共享 `[B,D]` 链接，因此它们尚未真正分离。此时，从 X 到 Z 有两条最短路径：

- `[A,B,D,F]`

- `[A,C,D,B,E,F]`

这两个图合并形成一组边，任何在两个图中但方向相反的链接都被丢弃；合并后的集合如下所示：

`[A->B, B->E, E->F, A->C, C->D, D->F]`

再次注意每个链接的方向性——对于剔除重叠链接至关重要，该链接将被同时列为 `[B->D]` 和 `[D->B]`。有了图上这部分可能的边，就可以看到正确的最短路径集是 `[A,B,E,F]` 和 `[A,C,D,F]`。

Suurballe 算法很复杂，但展示了计算不相交树的原理要点——包括它们计算起来有多困难。

### 最大冗余树

计算不相交树的 Suurballe 算法的更简单替代方案是计算最大冗余树（MRT）。理解 MRT 的最佳起点是谦逊的深度优先搜索（DFS），特别是编号 DFS。 Figure 13-18 用作说明。

在 Figure 13-18 中，左侧代表一个简单的拓扑；右侧是使用 DFS 编号的同一拓扑。假设用于“遍历”树的 DFS 算法总是选择左侧节点而不是右侧，过程将如下所示：

Click here to view code image

```
01 main {  
02   dfs_number = 1  
03   root.number = dfs_number  
04   recurse_dfs(root)  
05 }  
06 recurse_dfs(current) {  
07   for each neighbor of current {  
08     child = left most neighbor (not visited)  
09     if child.number == 0 {  
10       dfs_number++  
11       child.number = dfs_number  
12       if child.children > 0 {  
13         recurse_dfs(child)  
14       }  
15     }  
16   }  
17 }
```

理解这段代码的最佳方法是遍历递归几次以了解其工作原理。使用 Figure 13-18：

- 第一次调用 `recurse_dfs` 时，A 或 `root` 被设为当前节点。

- 进入 `recurse_dfs` 后，A 的最左侧节点被选中，即 B。

- 进入循环时 B 没有 `number`，因此第 09 行的 `if` 语句为真。

- B 被分配下一个 DFS 编号（第 11 行）。

- B 有子节点（第 12 行），因此 `recurse_dfs` 再次被调用，当前节点为 B。

- 进入（第二层的）`recurse_dfs` 后，B 的最左侧邻居被选中，即 E。

- E 没有 DFS 编号，因此第 09 行的 `if` 语句为真。

- E 被分配下一个 DFS 编号（3）。

- E 没有子节点，因此处理回退到循环顶部。

- F 现在是 B 的尚未访问的最左侧邻居，因此被分配给 `child`。

- F 没有编号，因此第 09 行的 `if` 语句为真。

- F 被分配下一个 DFS 编号（4）。

- B 没有更多子节点，因此第 07 行的 `for` 循环失败，`recurse_dfs` 退出。

- 然而，`recurse_dfs` 并未真正退出——它只是“回退”到之前的递归级别，即第 14 行；该递归级别仍在处理 A 的邻居。

- C 是 A 的下一个尚未触及的邻居，因此 `child` 被设为 C。

- 等等。

检查 Figure 13-18 右侧节点编号会得出以下有趣观察：

- 如果 A 总是遵循递增编号到达 D，它将遵循路径 `[A,C,G,D]`。

- 如果 D 总是遵循递减 DFS 编号到达 A，它将遵循路径 `[D,A]`。

- 这两条路径实际上是不相交的。

此属性适用于通过 DFS 搜索分配编号的所有拓扑：始终遵循递增编号的路径将始终与始终遵循递减编号的路径不相交。这正是 MRT 构建不相交路径所依赖的属性。然而，DFS 编号的问题在于在接近实时中执行它很困难。必须有某种选举的 `root`，流量在局部水平上是次优的（就像最小生成树 MST 可能一样），并且拓扑的任何更改都需要重建整个 DFS 编号方案。

为了解决这些问题，MRT 使用相同原理但以不同方式构建不相交拓扑。 Figure 13-19 用于解释。

![Image](img/13fig19.jpg)

**Figure 13-19** *Sample Network for Building an MRT*

构建 MRT 的第一步是找到从根通过拓扑的短环（通常这些环是使用 Dijkstra 的 SPF 算法找到的）。在这种情况下，A 将被选为根，环将为 `[A,B,C,D]`。这个第一个环将用作两个拓扑中的第一个，称为 *red* 拓扑。将环反转为 `[A,D,C,B]` 生成一个不相交的拓扑，称为 *blue* 拓扑。通过这个短环的这对拓扑称为 *ear*。

为了扩展 MRT 的范围，在第一个 `ear` 上添加第二个 `ear`。为此，发现了第二个环路，这次是通过 `[A,D,F,E,B]`，而不相交的拓扑是 `[A,B,E,F,D]`。问题是：这两个拓扑扩展中哪一个应添加到 `red` 拓扑，哪一个应添加到 `blue`？这就是 DFS 编号发挥作用的地方。

网络中的每个设备必须已经分配了标识符，要么由管理员分配，要么通过其他机制分配。这些标识符必须在每个设备中唯一。在 DFS 编号方案中，还有 `low point` 的概念，它指示该节点在特定树上的连接位置，以及哪些节点通过该节点连接到树。

给定这些唯一标识符以及计算 `low point` 的能力，网络中的每个节点都可以像通过 DFS 编号过程赋予数字一样进行 `ordered`。关键是要知道排序如何对应于现有的 `red` 和 `blue` 拓扑。假设 `B` 的 low point 高于 `C` 的，如果 `[A,B,C,D]` 拓扑是 `red` 拓扑的一部分。对于拓扑中经过 `B` 和 `C` 的任何其他 `ear` 或环路，`B` 小于 `C` 的 `ear` 方向应放置在 `red` 拓扑上。相反方向的环路应放置在 `blue` 拓扑上。

这个解释相当简略，但它确实让你感受到 MRT 如何形成不相交拓扑。有关 MRT 及其构造的更多信息，请参阅本章末尾的“Further Reading”部分。

### Two-Way Connectivity

本章和前一章描述了通过网络计算无环路径或一组不相交路径的多种不同方法。在每种情况下，计算出的路径都是单向的——从树的根到边缘，或可达的目的地。事实上，`no return path to exist` 是可能的。换句话说，源可能能够沿无环路径到达目的地，但从目的地到源可能没有返回路径。这在某些链路类型中可能是一种不常见的故障模式，是由于过滤可达性信息，或网络中的其他多种情况造成的。

`Note`

并非总是希望具有双向连通性；例如，考虑一艘潜艇的情况，它需要接收有关当前任务的信息，但不能传输任何信息而不暴露其当前位置。即使没有双向连通性，也能够向位于潜艇上的设备发送数据包，这将是可取的。控制平面必须修改或专门设计以处理这种不常见的案例，因为常见情况是需要双向连通性才能使网络正常运行。

`One other problem control planes must contend with in the area of computing paths is ensuring end-to-end two-way connectivity exists`。

控制平面可以通过多种方式解决这个问题：

• 一些控制平面只是忽略这个问题，这意味着它们假设其他协议，例如传输协议，会检测到这种状况。

• 控制平面可以在路由计算期间检查这个问题。例如，在使用 Dijkstra 算法计算路由时，可以在计算无环路径时执行回链检查。在计算的每一步执行此回链检查可以确保存在双向连通性。

• 控制平面可以假设邻居之间的双向连通性确保端到端双向连通性。执行基于每个邻居的显式双向连通性检查的控制平面通常可以安全地假设通过这些邻居的任何路径也能够进行双向通信。

### Final Thoughts

这两章涵盖了很多内容，从最短路径规则及其在计算网络中无环路径过程中的重要性开始。接下来讨论了 Bellman-Ford 的原始形式，然后是 Garcia 的 DUAL。基于这两种协议构建的路由协议被认为是 `distance-vector` 协议，你将在后续章节中遇到该术语。接下来考虑了 Dijkstra 的 SPF；基于该算法构建的协议被认为是 `link state`。然后讨论了路径向量解决方案，最后是 disjoint paths。

大多数这些算法可以由分布式控制平面或集中式控制平面使用。主要要点是了解如何解决无环路径问题，以便你能够以其多种形式识别它并理解它是如何被解决的，无论你查看的是什么协议或控制器。

### Further Reading

Chandra, Ravi, and John Scudder. *Capabilities Advertisement with BGP-4*. Request for Comments 5492. RFC Editor, 2009. doi:10.17487/rfc5492.

Chen, Enke, Tony J. Bates, and Ravi Chandra. *BGP Route Reflection: An Alternative to Full Mesh Internal BGP (IBGP)*. Request for Comments 4456. RFC Editor, 2006. doi:10.17487/rfc4456.

Chen, Enke, John Scudder, Alvaro Retana, and Daniel Walton. *Advertisement of Multiple Paths in BGP*. Request for Comments 7911. RFC Editor, 2016. doi:10.17487/rfc7911.

Chen, Enke, and Quaizar Vohra. *BGP Support for Four-Octet AS Number Space*. Request for Comments 4893. RFC Editor, 2007. doi:10.17487/rfc4893.

Chunduri, Uma, Wenhu Lu, Albert Tian, and Naiming Shen. *IS-IS Extended Sequence Number TLV*. Request for Comments 7602. RFC Editor, 2015. doi:10.17487/rfc7602.

Dijkstra, E. W. “A Note on Two Problems in Connexion with Graphs.” *Numerische Mathematik* 1, no. 1 (1959): 269–71. doi:10.1007/BF01386390.

Doyle, Jeff, and Jennifer DeHaven Carroll. *Routing TCP/IP, Volume 1*. 2nd edition. New Delhi, India: Cisco Press, 2005.

Ferguson, Dennis, Acee Lindem, and John Moy. *OSPF for IPv6*. Request for Comments 5340. RFC Editor, 2008. doi:10.17487/rfc5340.

Ginsberg, Les, Stephane Litkowski, and Stefano Previdi. *IS-IS Route Preference for Extended IP and IPv6 Reachability*. Request for Comments 7775. RFC Editor, 2016. doi:10.17487/rfc7775.

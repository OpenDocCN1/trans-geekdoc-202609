

# 本章首先展示图的真实世界示例。随后描述如何对这些图进行编码，以及如何为图构建监督学习问题。文中讨论了处理图的算法要求，这自然引出了`图卷积网络`，这是一种特定类型的图神经网络。

## 13.1 什么是图？

图是一种非常通用的结构，由一组`节点`或`顶点`组成，成对的节点通过`边`或`链接`相连。图通常是稀疏的；可能存在的边中只有一小部分实际存在。

现实世界中的某些对象天然呈现为图的形式。例如，路网可以视为图，其中节点代表物理位置，边代表它们之间的道路（图 13.1a）。化学分子是小型图，节点代表原子，边代表化学键（图 13.1b）。电路是图，节点代表元件和接点，边代表电气连接（图 13.1c）。

![Figure 13.1 Real-world graphs. Some objects, such as a) road networks, b) molecules, and c) electrical circuits, are naturally structured as graphs.](images/c13-fig-0001.jpg)

图 13.1 真实世界的图。某些对象，如 a) 路网、b) 分子和 c) 电路，天然地以图的形式构建。

此外，许多数据集也可以用图来表示，即使这不是它们显而易见的表面形式。例如：

*   社交网络是图，节点是人，边代表他们之间的友谊。
*   科学文献可视为图，节点是论文，边代表引用关系。
*   维基百科可视为图，节点是条目，边代表条目间的超链接。
*   计算机程序可表示为图，节点是语法标记（程序流中不同位置的变量），边代表涉及这些变量的计算。
*   几何点云可表示为图。此处，每个点是一个节点，边连接到其他附近的点。
*   细胞中的蛋白质相互作用可表示为图，节点是蛋白质，如果两个蛋白质相互作用，它们之间就有一条边。

此外，集合（无序列表）可视为一种图，其中每个成员都是一个节点并连接到其他所有成员。图像可视为具有规则拓扑的图，其中每个像素是一个节点，边连接到相邻像素。

### 13.1.1 图的类型

图可通过多种方式分类。图 13.2a 中的社交网络包含`无向边`；有连接的每对个体已达成共识成为朋友，因此这种关系没有方向性之分。相反，图 13.2b 中的引用网络包含`有向边`。每篇论文引用其他论文，这种关系天然是单向的。

![Figure 13.2 Types of graphs. a) A social network is an undirected graph; the connections between people are symmetric. b) A citation network is a directed graph; one publication cites another, so the relationship is asymmetric. c) A knowledge graph is a directed heterogeneous multigraph. The nodes are heterogeneous in that they represent different object types (people, places, companies) and multiple edges may represent different relations between each node. d) A point set can be converted to a graph by forming edges between nearby points. Each node has an associated position in 3D space, and this is termed a geometric graph (adapted from Hu et al., 2022). e) The scene on the left can be represented by a hierarchical graph. The topology of the room, table, and light are all represented by graphs. These graphs form nodes in a larger graph representing object adjacency (adapted from Fernández-Madrigal & González, 2002).](images/c13-fig-0002.jpg)

图 13.2 图的类型。a) 社交网络是无向图；人与人之间的连接是对称的。b) 引用网络是有向图；一篇出版物引用另一篇，因此关系是不对称的。c) 知识图谱是有向异构多重图。节点是异构的，因为它们代表不同的对象类型（人、地点、公司），且节点之间可能存在多条边代表不同的关系。d) 点集可通过在附近点之间形成边转换为图。每个节点在 3D 空间中都有关联位置，这称为几何图（改编自 Hu 等人，2022）。e) 左侧场景可用层次图表示。房间、桌子和灯的拓扑结构均由图表示。这些图本身构成了一个更大图中的节点，代表对象邻接关系（改编自 Fernández-Madrigal & González, 2002）。

图 13.2c 描绘了一个`知识图谱`，它通过定义对象间的关系来编码一组关于对象的事实。从技术上讲，这是一个`有向异构多重图`。它是异构的，因为节点可以代表不同类型的实体（如人、国家、公司）。它是多重图，因为任意两个节点之间可以存在不同类型的多条边。

图 13.2d 中代表飞机的点集，可通过将每个点连接到其`K`个最近邻来转换为图。结果是一个`几何图`，其中每个点关联一个 3D 空间位置。图 13.2e 代表一个`层次图`。桌子、灯和房间各自由图描述，表示其各自组件的邻接关系。这三个图本身又是另一个图中的节点，代表更大模型中对象的拓扑结构。

所有类型的图均可使用深度学习进行处理。然而，本章重点关注如图 13.2a 所示社交网络这样的无向图。

## 13.2 图表示

除了图结构本身，通常还会有信息与每个节点相关联。例如，在社交网络中，每个个体可能由一个代表其兴趣的定长向量来表征。有时，边也附带信息。例如，在路网示例中，每条边可能由其长度、车道数、事故频率和限速来表征。节点处的信息存储在`节点嵌入`中，边处的信息存储在`边嵌入`中。

更正式地说，图由一组`N`个节点和一组`E`条边连接而成。图可由三个矩阵 `A`、`X` 和 `E` 编码，分别代表图结构、节点嵌入和边嵌入（图 13.3）。

![Figure 13.3 Graph representation. a) Example graph with six nodes and seven edges. Each node has an associated embedding of length five (brown vectors). Each edge has an associated embedding of length four (blue vectors). This graph can be represented by three matrices. b) The adjacency matrix is a binary matrix where element (m, n) is set to one if node m connects to node n. c) The node data matrix X contains the concatenated node embeddings. d) The edge data matrix E contains the edge embeddings.](images/c13-fig-0003.jpg)


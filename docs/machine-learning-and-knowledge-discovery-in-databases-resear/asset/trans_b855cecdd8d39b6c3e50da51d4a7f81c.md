

重新计算节点度以确定局部密度：

```
\(\bar{d} = \frac{1}{n} \sum_{v \in \mathcal{V}} |\mathcal{N}'(v)|,\)
(2)
```

```
Algorithm 1. Hierarchical Mesh Coarsening with Constrained Delaunay Triangulation

Require: Mesh M, Positions P, Levels L, Coarsening Ratios U, Neighbor Counts K
Ensure: Coarsened Meshes {M_l}_{l=1}^L, Positions {P_l}_{l=1}^L, Sampling Indices {I_l}_{l=1}^L, Neighbor Indices {N_l}_{l=1}^L Initialize coarse mesh parameters;
1: while not converged do
2:   Sample nodes from mesh M based on ratio U;
3:   for each level l = 1, ..., L do
4:     Generate sampling indices I_l;
5:     Update positions P_l;
6:     Construct coarse mesh M_l via Constrained Delaunay triangulation;
7:     Compute neighbor indices N_l using fixed-size K;
8:   end for
9:   Update coarse mesh and parameters;
10: end while
```

其中 \(n = |\mathcal{V}|\) 表示网格中的节点数，\(\mathcal{N}'(v)\) 表示节点 \(v\) 的邻居集合。若 \(d'(v) > \bar{d}\)，则节点被分类为 \(\mathcal{V}_\text{d}\)，否则分类为 \(\mathcal{V}_\text{s}\)。

给定粗化比率 \(U\)（例如，\(U = 0.5\) 表示 50% 下采样）以及用于密集区域的采样比例 \(m\)，我们定义密集区域和稀疏区域的采样节点数量如下：

```
\(k_d = \lfloor U \cdot m \cdot n \rfloor,\quad k_s = \lfloor U \cdot (1 - m) \cdot n \rfloor,\)
(3)
```

其中 \(k_d\) 和 \(k_s\) 分别表示从密集区域和稀疏区域采样的节点数量。合并后的采样节点集合定义如下：

```
\(\left\{\begin{array}{l l}
V_d = \{v_i \mid v_i \sim \mathcal{U}(\mathcal{V}_\text{d})\}, & |V_d| = k_d, \\
V_s = \{v_i \mid v_i = \text{FPS}(\mathcal{V}_\text{s})\}, & |V_s| = k_s,
\end{array}\right.\)
(3)
```

在此，\(\mathcal{U}(\mathcal{V}_\text{d})\) 表示对密集区域进行随机采样，而 FPS(\(\mathcal{V}_\text{s}\)) 表示基于欧氏距离的最远点采样。最终，完整的采样集合为 \(S_i = V_d \cup V_s\)。如图 3 所示，我们的分层采样策略能够有效区分需要详细局部表示的区域与反映全局网格结构的区域，保留关键几何细节并避免粗化过程中的错误。

![](img/f56761e6196132d5b74909d98468408f_76_0.png)

图 3. 针对管道湍流的基于密度的分层采样策略示意。

### 3.3 邻域定义

为降低计算开销并增强局部特征聚合，我们定义了固定大小的邻域结构。在传统的 GNN（如 GCN [31]）中，堆叠 $K$ 层消息传递会导致每个节点聚合越来越大感受野中的信息，潜在涉及 $O(d^K)$ 个节点，其中 $d$ 为节点度。虽然每层复杂度与边数成线性关系，但这种累积增长会增加每节点开销，并可能导致过平滑。

受 GraphSAGE [21] 启发，我们改为在每个节点的 1-hop 或 2-hop 距离内采样固定数量 $S$ 的邻居。这将每节点开销限制在 $O(K \cdot S)$，总模型复杂度限制在 $O(K \cdot S \cdot n)$，其中 $n$ 为节点数量。固定大小邻域提高了可扩展性，并确保在不同图密度下计算一致。

### 3.4 约束德劳内重建

在基于图的网格处理中，较粗尺度上的准确边重建对于保持几何和拓扑完整性至关重要。传统方法依赖于空间邻近性 [17–19] 或保留采样节点的边 [12]，但常常在边界间生成错误边，破坏连通性。

为解决这些问题，我们提出了一种自适应约束德劳内重建方法，专门用于多尺度边重建，该方法受到经典计算几何技术的启发，能够鲁棒地处理非凸域和带洞区域 [32]。具体而言，我们利用先前的网格信息定义多边形边界 $\mathcal{B}$，对原始网格的几何和拓扑进行编码。给定采样节点集合 $(V')$，我们使用标准德劳内三角剖分 $T(V')$ 构建边，并针对每个候选边 $e = (u, v)$ 验证约束：

$$E' = \{e \mid e \subseteq \mathcal{B}, e \in T(V')\}. \quad (4).$$

仅保留完全包含在受约束多边形区域内的边。这确保了鲁棒的边重建，防止无效连接并保持网格质量。

## 4 基于点的多尺度 GNN(MPG)

在本节中，我们将介绍 MPGNN，这是一个分层 GNN，其多级结构由输入网格和第 3 节中的预处理确定。

### 4.1 问题

传统 GNN 和多尺度 GNN 在很大程度上依赖堆叠的消息传递（MP）层来聚合节点和边特征：

```
h_v^{(k)} = \text{AGGREGATE} \left( \{h_u^{(k-1)}, e_{uv}^{(k-1)} \mid u \in \mathcal{N}(v)\} \right), \quad (5)
```

其中 \( h_v^{(k)} \) 是节点 \( v \) 在第 \( k \) 层的嵌入，\( e_{uv}^{(k-1)} \) 是节点 \( u \) 和 \( v \) 之间的边嵌入。然而，堆叠 MP 层会显著增加计算复杂度和冗余度，尤其是对于大规模非均匀网格。此外，固定高维嵌入（例如，128 维）进一步加剧了计算开销。

受 PointMLP [22] 启发，该方法无需复杂局部操作即可在点云上实现高效特征提取，我们重新审视网格特征学习。非均匀网格在结构上类似点云；因此，对 MP 层的严重依赖可能不是必需的。我们旨在用轻量级残差 MLP 模块替代堆叠的 MP 层，以高效提取节点特征并提高可扩展性。

### 4.2 编码器

输入是多级网格结构 \(\{\mathcal{M}_l = (\mathcal{V}_l, \mathcal{E}_l)\}_{l=1}^L\)。对于每个网格级别，编码操作可表述为：

```
g_i = \Phi_{\text{pos}} (\mathcal{A} (\Phi_{\text{pre}} (\mathcal{V}_i, \mathcal{V}_{ij}))) , \quad (6)
```

其中 \(\Phi_{\text{pre}}(\cdot)\) 和 \(\Phi_{\text{pos}}(\cdot)\) 表示从 PointMLP [22] 改编的残差 MLP 模块。具体而言，\(\Phi_{\text{pre}}(\cdot)\) 在局部感受野内学习初始节点嵌入，捕获初步几何模式。对于邻域聚合 \(\mathcal{A}\)，我们采用受 CNN 感受野启发的可学习加权机制：

```
\mathcal{A}(f_i) = \sum_{j \in \mathcal{N}(i)} (W_{i,j} \cdot w_{ij}) \cdot f_j, \quad w_{ij} = \frac{\exp(-\|\mathbf{x}_i - \mathbf{x}_j\|_2)}{\sum_{k \in \mathcal{N}(i)} \exp(-\|\mathbf{x}_i - \mathbf{x}_k\|_2)} . \quad (7)
```

其中 \( f_j \) 表示邻居特征，\( W \) 表示可学习参数，\( w_{ij} \) 根据空间关系动态调整邻居重要性。

最后，聚合特征由另一个残差 MLP 块 $\Phi_{pos}(\cdot)$ 进行优化。正式地，残差 MLP 块可表示为：

```
$\Phi(x) = act(W_2 \cdot act((W_1 \cdot x))) + x, \quad (8)$
```

其中 $W_1$ 和 $W_2$ 为可学习参数，$act$ 表示非线性激活函数（例如，PReLU）。

通过明确采用基于轻量级残差 MLP 的特征提取，编码器有效降低了计算开销并提高了维度可扩展性。这种设计避免了深层消息传递堆叠，显著提高了在各种非均匀网格上的效率和泛化能力。

### 4.3 解码器

对于解码器模块，我们采用 k 近邻（KNN）插值来高效恢复细层节点特征 [27,28]。对于细层 $X_f$ 中的每个节点 $x_i$，我们根据欧氏距离从粗层 $X_c$ 中识别其 $k$ 个最近节点。插值特征 $x_i$ 通过距离加权平均计算：

```
$x_i = \sum_{j \in N_k(i)} \frac{w_{ij} h_j}{\sum_{j \in N_k(i)} w_{ij}}, \quad w_{ij} = \frac{1}{d(P_f^i, P_c^j)}, \quad (9)$
```

其中 $h_j$ 表示邻居节点 $j$ 的粗层特征，$d(P_f^i, P_c^j)$ 表示细层节点 $i$ 与粗层节点 $j$ 之间的欧氏距离。

此外，我们在相应的编码器和解码器层之间加入跳跃连接，以促进高效的空间信息传递。进一步采用残差 MLP $\Phi(x)$ 来优化插值特征，提高重建精度，并确保不同网格分辨率下的结构一致性。这种编码器-解码器架构专门用于静态多尺度特征重建，为物理模拟中的时态动态预测提供了高效基础。

## 5 实验

### 5.1 实验设置

**数据集。** 我们在五个涵盖不同物理领域的数据集上评估 MPG 模型：圆柱绕流 [14] 模拟圆柱周围不可压缩流体流动。管道湍流 [33] 在复杂管道内动态表示湍流。热化学反应 [34] 涉及多物理场复杂模型，用于模拟热化学蓄能反应器内的流体流动、热传递、质量传递和化学反应。盖驱动腔流2d [35] 关注不同粘度和边界条件下的不可压缩盖驱动腔流。NSM2d [35] 处理具有复杂边界条件和初始状态的不可压缩流体动力学。



更平滑的轨迹更易预测，因此也更易生成。接下来，我们展示几个 RWTs 的示例。

### 示例 1（Erdos-Renyi 图）

假设 $\mathcal{G}$ 包含连接概率为 $p$ 的 Erdos-Renyi 随机图。换句话说，第 \(j^{th}\) 个图有 \(n^{(j)}\) 个节点，每对节点以概率 \(p\) 相连。为简化起见，我们忽略平滑 \((\alpha=0)\)。那么，如果 \(n^{(j)}\) 足够大，第 \(j^{th}\) 图中所有节点的度数约为 \(\approx n^{(j)}p\)。因此，对于平滑的 \(f(\cdot)\)，该图起始向量的每个条目约为 \(\approx 1\)。换句话说，无论大小如何，所有 Erdos-Renyi 图的 RWTs 都从接近全一向量 \(\mathbf{1}\) 的位置开始。而且，我们可以证明对于此类图的归一化邻接矩阵 \(L^{(j)}\)，有 \(L^{(j)}\mathbf{1} \approx \mathbf{1}\)。因此，随机图的 RWTs 从 \(\mathbf{1}\) 附近开始，围绕该点波动，并最终收敛。

### 示例 2（随机块模型（SBM））

假设 $\mathcal{G}$ 包含从具有以下参数的 SBM 中采样的图。有两个社区，大小比例为 \(\beta:1-\beta\)。如果两个节点来自同一社区，则它们之间存在边的概率为 \(p\)，否则为 $q$。假设对于所有 \(x$ 我们选择 \(f(x)=1$。那么，所有图的起始向量 \(\boldsymbol{v}^{(j)}$ 均等于 \(\mathbf{1}$。我们可以证明，对于足够大的 \(k$，随机走向量 \((L^{(j)})^k\boldsymbol{v}^{(j)}$ 收敛到一个具有聚类条目的向量 \(\boldsymbol{w}$。具体来说，设

\(\kappa_1:=\beta p+(1-\beta)q,\qquad \kappa_2:=p+q-\kappa_1,\qquad \nu:=\frac{\beta\sqrt{\kappa_1}+(1-\beta)\sqrt{\kappa_2}}{\beta\kappa_1+(1-\beta)\kappa_2}.\)

那么，如果节点 \(i$ 属于第一个社区，\(\boldsymbol{w}_i=\sqrt{\kappa_1}/\nu$；否则为 \(\sqrt{\kappa_2}/\nu$（通过稍后证明的定理 1）。因此，RWT 从 \(\mathbf{1}$ 演变为具有聚类条目的向量 \(\boldsymbol{w}$，与图的大小无关。

### 示例 3（优先附着）

假设 $\mathcal{G}$ 包含根据 Barabasi-Albert 模型 [1] 创建的图。那么，对于任何图，节点度的分布服从指数为 3 的幂律分布。如同 SBM 示例中那样，对于所有 \(x$ 取 \(f(x)=1$，因此起始向量等于 \(\mathbf{1}$。随机走的结束向量与度的平方根成正比（稍后证明的定理 1）。这些服从指数为 5 的幂律分布。

### 示例 4（期望度随机图）

假设 $\mathcal{G}$ 包含期望度与 SBM 匹配的随机图。那么，起始向量和结束向量将与示例 2 相同，但中间向量将不同。

以上示例表明，不同家族的图具有不同的 RWT 特征签名。在所有情况下，RWTs 都从全一向量开始。但是，它们追踪的轨迹具有不同的结束向量。对于 \(f(\cdot)$ 的其他选择，RWTs 可以探索（例如）高度节点及其邻域。GRAPH-WEAVE 自动利用这些模式来从同一家族生成新图。

**核心思想：** GRAPHWEAVE 包含三个步骤。首先，我们从 $\mathcal{G}$ 中的图构建 RWTs。基于此，我们学习反转 RWTs。换句话说，给定 RWT 中的一个向量，GRAPHWEAVE 学习预测前一个向量。其次，我们使用这个反向预测器来生成新的 RWTs。为此，我们需要一个“结束”向量。所有生成的 RWTs 共享相同的结束向量，但追踪不同的轨迹。我们展示如何构建一个现实的结束向量，以及为什么可以认为生成的 RWTs 来自同一图。第三，从生成的 RWTs 中，GRAPHWEAVE 推断底层图。关键的是，我们共同推断该图的所有边。我们可以通过从不同结束向量重复第二和第三步来生成多个图。接下来，我们详细介绍 GRAPHWEAVE 的三个部分。

## 2.1 学习反转 RWTs

给定图集 $\mathcal{G} = \{A_i\}$ 和函数集 $\mathcal{F} = \{f_\ell(\cdot)\}$，我们构建所有 RWTs 的集合 $\mathcal{R} := \{RWT(A, f, \alpha, k)\}_{A \in \mathcal{G}, f \in \mathcal{F}}$。回顾，每个 RWT 是一个向量序列 $\boldsymbol{v}_1, \boldsymbol{v}_2, \dots, \boldsymbol{v}_k$，其中一对 $(\boldsymbol{v}_j, \boldsymbol{v}_{j+1})$ 表示在 $\mathcal{G}$ 中某个图上的随机走的一步。

接下来，我们学习反转 RWTs，即在给定 $\boldsymbol{v}_{j+1}$ 和 $f(\cdot)$ 的情况下预测 $\boldsymbol{v}_j$。预测器必须知道 $f(\cdot)$，因为两个不同的 RWTs 可能通过不同路径到达相同的 $\boldsymbol{v}_{j+1}$。每条路径由其起始向量决定，而该向量依赖于 $f(\cdot)$。要构建预测模型，我们面临两个挑战。

- **任意长度的输入/输出：** 向量 $\boldsymbol{v}_j$ 和 $\boldsymbol{v}_{j+1}$ 的长度是图中的节点数。由于 $\mathcal{G}$ 中的图可能具有不同的大小，$\mathcal{R}$ 中向量的长度可能不同。

- **排列不变性：** 模型必须对 $\boldsymbol{v}_j$ 和 $\boldsymbol{v}_{j+1}$ 的组分排列不变，因为排列只是节点的重新排序。这种重新排序不应影响模型的预测。

我们的解决方案简单而优雅：我们使用一个 Transformer。Transformer 可以适应任意上下文长度的输入。在我们的情况中，输入向量是 $\boldsymbol{v}_{j+1} \in \mathbb{R}^n$，其中图大小 $n$ 在 $\mathcal{G}$ 中的图之间变化。对于 Transformer，这意味着长度为 $n$ 的上下文，其中上下文中的每个项目都是一维的。给出这样的输入，Transformer 的输出也是长度 $n$，与所需的输出向量 $\boldsymbol{v}_j$ 相同。因此，同一个 Transformer 可以用于所有大小的输入/输出向量对。此外，没有位置嵌入或因果掩码的 Transformer 在排列下是不变的。因此，原生 Transformer 符合我们的期望。

然而，我们可以使用嵌入显著改进这个 Transformer。正式地说，我们构造一个分桶函数 $B : \mathbb{R}_+ \to [K]$ 和一个嵌入 $\mathcal{E} : [K] \to \mathbb{R}^m$。对于向量，我们逐元素应用这些函数。也就是说，$B(\boldsymbol{v})$ 是通过对 $\boldsymbol{v}$ 的每个元素应用 $B(\cdot)$ 形成的向量；$\mathcal{E}(\boldsymbol{v})$ 的定义类似。用户选择分桶数量 $K$ 和嵌入维度 $m$。$K$ 和 $m$ 的更高值会使 Transformer 具有更大的灵活性。

现在，我们预处理数据以使用这些嵌入。具体来说，在 RWTs 中，我们将每个向量 $\boldsymbol{v}$ 替换为 $\boldsymbol{v} \otimes \mathcal{E}(B(\boldsymbol{v}))$。我们还通过嵌入进一步增强每个

![](img/f56761e6196132d5b74909d98468408f_263_0.png)

图 2. 训练反向预测器：对于 RWT 中路径 \(i$ 的每一对连续向量 \((v_j, v_{j+1})$，我们将 \(v_j$ 与从 \(v_{j+1}$ 获得的预测向量 \(\hat{v}_j$ 进行比较。要创建 \(\hat{v}_j$，首先将 \(v_{j+1}$ 的元素转换为嵌入序列。然后，添加反映用于路径 \(i$ 起始向量的函数 \(f$ 以及路径 \(i$ 中步骤 \(j+1$ 的嵌入。最后，我们转换这些嵌入并将其投影以生成 \(\hat{v}_j$。

输入向量与一个编码 \(f(\cdot)$ 选择和 RWT 中当前步骤的嵌入相结合。具体来说，我们定义一个嵌入 \(\mathcal{E}'$，使得对于所有函数 \(f \in \mathcal{F}$ 和步骤 \(j \in [k]$，\(\mathcal{E}'(f, j) \in \mathbb{R}^m$。给定函数 \(f(\cdot)$ 在步骤 \(j+1$ 时的输入向量 \(v_{j+1}$，我们定义

\(T_\Phi(v_{j+1}, f, j+1) := \text{Transformer}_\Phi(v_{j+1} \otimes \mathcal{E}(B(v_{j+1})) + 1 \otimes \mathcal{E}'(f, j+1)),\)

其中 \(\Phi$ 表示 Transformer 的参数。Transformer 的输入现在是一个长度为 \(n$ 的 \(m$ 维嵌入序列，输出也是如此。最后，我们添加一个线性投影层将输出转换回 \(\mathbb{R}^n$：

\(P_{\Phi, \Psi}(v_{j+1}, f, j+1) := \text{Project}_\Psi(T_\Phi(v_{j+1}, f, j+1)) \text{ to } \mathbb{R}^n,\)

其中 \(\Psi$ 是投影参数。给定输入 \(v_{j+1}$，这个投影输出就是我们对 \(v_j$ 的预测。我们训练 Transformer 以最小化预测值和 \(v_j$ 实际值之间的均方误差。

\(\Phi, \Psi, \mathcal{E}, \mathcal{E}' = \arg \min \sum_{(v_j, v_{j+1})} (P_{\Phi, \Psi}(v_{j+1}, f, j+1) - v_j)^2.\)

图 2 说明了此过程。训练后，我们得到一个反向预测器 \(P_{\Phi, \Psi}$（以下简称 \(P$），使得

\(P(v_{j+1}, f, j+1) \approx v_j \text{ for all } v_j \to v_{j+1} \text{ in the RWTs of } \mathcal{G}. \quad (2)\)

## 2.2 生成 RWTs

假设我们已经学习了一个准确的反向预测器。那么，给定“结束”向量 \(\bar{v}_k$ 和 \(f(\cdot)$ 的选择，我们可以通过反复预测来向后推导



![](img/c73db5a1f734ebb7c0655f19e5bc9daa_81_0.png)

图 9.4: 对4节点 MRF 应用图割的示意图。虚线是对切分代价有贡献的边（对于双向边，我们只计算其中一个代价）。这里最小割的代价为 6。引自 [KF09] 中的图 13.5。特感谢 Daphne Koller 允许使用。

分区不同侧节点之间的边：

cost(X_s, X_t) = \sum_{x_u \in X_s, x_v \in X_t} cost(x_u, x_v) (9.20)

在图 9.4 中，我们看到最小割的代价为 6。在此图中最小化代价等价于在 MRF 中最小化能量。因此，分配给 s 的节点最优状态为 0，分配给 t 的节点最优状态为 1。在图 9.4 中，我们看到最优 MAP 估计为 (1, 1, 1, 0)。因此，我们已将 MAP 估计问题转化为存在高效求解器的标准图论问题（参见例如 [CLR90]）。

### 9.1.4.2 具有次模势的二元 MRF 的图割

我们现在讨论如何将图割结构扩展到具有更一般势函数的二元 MRF。特别是，假设每个成对能量满足以下条件：

\mathcal{E}_{uv}(1, 1) + \mathcal{E}_{uv}(0, 0) \le \mathcal{E}_{uv}(1, 0) + \mathcal{E}_{uv}(0, 1) (9.21)

换句话说，对角能量之和小于非对角能量之和。在这种情况下，我们说这些能量是次模的（？？）。次模能量的一个例子是 \lambda_{uv} > 0 的 Ising 模型。这也称为吸引型 MRF 或关联型 MRF，因为模型“希望”相邻状态相同。

可以修改此设置下的图构建过程，然后应用图割，使得得到的估计是全局最优 [GPS89]。

### 9.1.4.3 非二元度量 MRF 的图割

我们现在讨论如何在每个节点可以具有多个状态的 MRF 中使用图割进行近似 MAP 估计 [BVZ01]。

一种方法是使用 α 扩展。每一步，它从可用标签或状态中选择一个并将其称为 \alpha；然后它求解一个二元子问题，其中每个变量可以选择保持当前状态，或变为状态 \alpha（参见图 9.5(d) 了解示例）。

另一种方法是使用 α-β 交换。每一步，选择两个标签，称它们为 \alpha 和 \beta。如果这样做可以降低能量，当前标记为 \alpha 的所有节点可以改为 \beta（反之亦然）（参见图 9.5(c) 了解示例）。

为了最优地求解这些二元子问题，我们需要确保这些子问题的势是次模的。如果成对能量形成一个度量，则会发生这种情况。我们称这样的模型为度量 MRF。

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_82_0.png)

_图 9.5: (a) 具有 3 个标签的图像。(b) 标准局部移动（例如，通过迭代条件模式）只是翻转一个像素的标签。(c) α − β 交换允许当前标记为 α 的所有节点重新标记为 β，如果这会降低能量。(d) α 扩展允许当前未标记为 α 的所有节点重新标记为 α，如果这会降低能量。引自 [BVZ01] 中的图 2。特感谢 Ramin Zabih 允许使用。_

例如，假设状态具有自然顺序，这通常发生在它们是底层连续空间的离散化时。在这种情况下，我们可以定义形式为 $E(x_s, x_t) = \min(\delta, \|x_s - x_t\|)$ 的度量，或形式为 $E(x_s, x_t) = \min(\delta, (x_s - x_t)^2)$ 的半度量，其中 $\delta > 0$ 为某个常数。这种能量鼓励邻域具有相似标签，但绝不会“惩罚”它们超过 $\delta$。（这个 $\delta$ 项防止过度平滑，我们将在图 9.3 中说明。）

### 9.1.4.4 应用于立体深度估计

图割常被应用于低级计算机视觉问题，如立体深度估计，我们已在第 9.1.3.3 节中讨论过。图 9.6 将图割（交换版本和扩展版本）与另外两个算法（模拟退火和基于归一化互相关的补丁匹配方法）在著名的 Tsukuba 测试图像上进行了比较。图割方法在此示例以及其他示例中效果最佳 [Sze+08; TF03]。它还倾向于在立体问题上超越信念传播（结果未显示），在速度和准确性方面 [Sze+08; TF03]，以及其他问题如 LIDAR 点云数据的 CRF 标注 [LMW17]。

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_83_0.png)

图 9.6: 在成对离散 MRF 中使用 MAP 估计进行立体深度估计的示例。(a) 左图像，大小为 384 × 288 像素，来自筑波大学。（对应的右图像类似，但未显示。）(b) 量化为 15 个电平的地面真实深度图。(c-f): 使用不同方法的 MAP 估计：(c) α − β 交换，(d) α 扩展，(e) 归一化互相关，(f) 模拟退火。引自 [BVZ01] 中的图 10。特感谢 Ramin Zabih 允许使用。

## 第 10 章

## 变分推断

### 10.1 PGM 的精确推断与近似推断

在本节中，我们将从变分角度讨论离散 PGM 的精确推断与近似推断，遵循 [WJ08]。

类似于第 9.1 节，我们将假设形式为

$$
p_\theta(\mathbf{z}|\mathbf{x}) = \frac{1}{Z} \exp \left\{ \sum_{s \in \mathcal{V}} \theta_s(z_s) + \sum_{(s,t) \in \mathcal{E}} \theta_{st}(z_s, z_t) \right\} \quad (10.1)
$$

的成对 MRF。

我们可以将其写为指数族模型，\(p(\mathbf{z}|\mathbf{x}) = \tilde{p}(\mathbf{z})/Z\)，其中 \(Z = \log p(\mathbf{x})\)，\(\tilde{p}(\mathbf{z}) = \mathcal{T}(\mathbf{z})^\top \boldsymbol{\theta}\)，\(\boldsymbol{\theta} = (\{\theta_{s,j}\}, \{\theta_{s,t,j,k}\})\) 是所有节点和边参数（规范参数），\(\mathcal{T}(\mathbf{z}) = (\{\mathbb{I}(z_s = j)\}, \{\mathbb{I}(z_s = j, z_t = k)\})\) 是所有节点和边指示函数（充分统计量）。注意：我们使用 \(s, t \in \mathcal{V}\) 索引节点，\(j, k \in \mathcal{X}\) 索引状态。

### 10.1.1 作为 VI 的精确推断

我们知道 ELBO 是 log 边缘似然的下界：

$$
\mathcal{L}(q) = \mathbb{E}_{q(\mathbf{z})} [\log \tilde{p}(\mathbf{z})] + \mathbb{H}(q) \le \log Z \quad (10.2)
$$

设 \(\boldsymbol{\mu} = \mathbb{E}_q [\mathcal{T}(\mathbf{z})]\) 为变分分布的均值参数。那么我们可以将其改写为

$$
\mathcal{L}(\boldsymbol{\mu}) = \boldsymbol{\theta}^T \boldsymbol{\mu} + \mathbb{H}(\boldsymbol{\mu}) \le \log Z \quad (10.3)
$$

所有有效（无限制）均值参数 \(\boldsymbol{\mu}\) 的集合是与图相对应的 **边缘多极体**，\(\mathbb{M}(G)\)，如第 9.1.2 节所述。对该集合进行优化可恢复 \(q = p\)，因此

$$
\max_{\boldsymbol{\mu} \in \mathbb{M}(G)} \boldsymbol{\theta}^T \boldsymbol{\mu} + \mathbb{H}(\boldsymbol{\mu}) = \log Z \quad (10.4)
$$

方程 (10.4) 看起来易于优化：目标函数是凹的，因为它是线性函数和凹函数的和（参见图 **??** 了解熵为何是凹的）；此外，我们是在凸集 \(\mathbb{M}(G)\) 上最大化它。因此存在唯一的全局最优解。We。然而，熵通常难以计算，因为它需要对所有状态求和。我们将在下面讨论近似方法。有关我们讨论的方法的高层摘要，请参见表 10.1。

| 方法 | 定义 | 目标函数 | 优化域 | 节 |
| :--- | :--- | :--- | :--- | :--- |
| 精确 | $\max_{\boldsymbol{\mu} \in \mathbb{M}(G)} \boldsymbol{\theta}^{*T} \boldsymbol{\mu} + \mathbb{H}(\boldsymbol{\mu}) = \log Z$ | 凹 | 边缘多极体，凸 | 第 10.1.1 节 |
| 平均场 | $\max_{\boldsymbol{\mu} \in \mathbb{M}_F(G)} \boldsymbol{\theta}^T \boldsymbol{\mu} + \mathbb{H}_{MF}(\boldsymbol{\mu}) \le \log Z$ | 凹 | 非凸内近似 | 第 10.1.2 节 |
| 有环信念传播 | $\max_{\boldsymbol{\tau} \in \mathbb{L}(G)} \boldsymbol{\theta}^T \boldsymbol{\tau} + \mathbb{H}_{Bethe}(\boldsymbol{\tau}) \approx \log Z$ | 非凹 | 凸外近似 | 第 10.1.3 节 |
| TRBP | $\max_{\boldsymbol{\tau} \in \mathbb{L}(G)} \boldsymbol{\theta}^T \boldsymbol{\tau} + \mathbb{H}_{TRBP}(\boldsymbol{\tau}) \ge \log Z$ | 凹 | 凸外近似 | 第 10.1.5 节 |

表 10.1: 图模型某些变分推断方法的摘要。TRBP 是树重加权信念传播。

### 10.1.2 平均场 VI

熵的平均场近似简单为

$$\mathbb{H}_{MF}(\boldsymbol{\mu}) = \sum_s \mathbb{H}(\boldsymbol{\mu}_s)$$ (10.5)

这源于分解假设。因此平均场目标为

$$\mathcal{L}_{MF}(\boldsymbol{\mu}) = \boldsymbol{\theta}^T \boldsymbol{\mu} + \mathbb{H}_{MF}(\boldsymbol{\mu}) \le \log Z$$ (10.6)

这是对 $\log Z$ 的凹下界。我们将在更简单但非凸的内近似 \(\mathbb{M}(G)\) 上最大化它，正如我们现在所示。

首先，令 $F$ 为原始图 $G$ 的边子图，令 $\mathcal{I}(F) \subseteq \mathcal{I}$ 为与 $F$ 的团相关的充分统计量子集。令 $\Omega$ 为完整模型的规范参数集，并按如下定义子模型的规范参数空间：

$$\Omega(F) \triangleq \{ \boldsymbol{\theta} \in \Omega : \boldsymbol{\theta}_\alpha = 0 \, \forall \alpha \in \mathcal{I} \setminus \mathcal{I}(F) \}$$ (10.7)

换句话说，我们要求与我们所选类之外的充分统计量 $\alpha$ 相关的自然参数为零。例如，在完全分解近似 $F_0$ 的情况下，我们从图中删除所有边，给出

$$\Omega(F_0) \triangleq \{ \boldsymbol{\theta} \in \Omega : \boldsymbol{\theta}_{st} = 0 \, \forall (s,t) \in E \}$$ (10.8)

在结构化平均场（第 ?? 节）的情况下，我们将不在我们可处理子图中的边的 $\theta_{st} = 0$ 设置为零。

接下来，我们按如下定义受限模型的均值参数空间：

$$\mathbb{M}_F(G) \triangleq \{ \boldsymbol{\mu} \in \mathbb{R}^d : \boldsymbol{\mu} = \mathbb{E}_\boldsymbol{\theta} [\mathcal{T}(\boldsymbol{z})] \text{ for some } \boldsymbol{\theta} \in \Omega(F) \}$$ (10.9)

这被称为边缘多极体的 **内近似**，因为 \(\mathbb{M}_F(G) \subseteq \mathbb{M}(G)\)。参见图 9.1(b) 草图。注意 \(\mathbb{M}_F(G)\) 是非凸多极体，这会导致多个局部最优。

因此平均场问题变为

$$\max_{\boldsymbol{\mu} \in \mathbb{M}_F(G)} \boldsymbol{\theta}^T \boldsymbol{\mu} + \mathbb{H}_{MF}(\boldsymbol{\mu})$$ (10.10)

这要求在非凸集上最大化凹目标函数。通常使用坐标上升进行优化，因为在每个节点的边缘分布上优化标量凹函数很容易。

### 10.1.3 作为 VI 的有环信念传播

回顾第 10.1.1 节，精确推断可以表述为求解以下优化问题：$\max_{\boldsymbol{\mu} \in \mathbb{M}(G)} \boldsymbol{\theta}^T \boldsymbol{\mu} + \mathbb{H}(\boldsymbol{\mu})$，其中 \(\mathbb{M}(G)\) 是与图相对应的边缘多极体（详情见第 9.1.2 节）。由于该集合具有指数级多的面，在其上优化是不可处理的。

在第 10.1.2 节中，我们讨论了平均场近似，它使用非凸内近似 \(\mathbb{M}_F(G)\)，通过从图形模型中删除某些边获得，从而强制后验分解。我们还通过使用每个边缘的熵来近似熵。


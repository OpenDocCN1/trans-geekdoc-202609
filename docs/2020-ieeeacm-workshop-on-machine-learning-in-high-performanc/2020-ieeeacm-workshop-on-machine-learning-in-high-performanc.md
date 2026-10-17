
# 2020 IEEE/ACM 高性能计算环境机器学习研讨会 (MLHPC) 与科学应用的人工智能与机器学习研讨会 (AI4S) (美国佐治亚州)

**摘要**—我们处理了利用相关性聚类解决图像分割的图划分问题，并将其视为一个整数线性规划（ILP）。我们重新表述了 CC 中的优化问题，以便通过 Benders 分解（运筹学中的一种经典技术）进行高效优化。我们的分解方法处理了权重，并强制执行与图中边对应的不等式，每个不等式对应 CC 实例中的一个节点。我们生成了强制-王（Mandatory-Wong）Benders 规则来加速优化。分解允许我们加速 CC 中的优化，并包含之前的平面约束，在理论上允许大规模并行。关键词：相关性聚类，最小代价划分。

现有方法难以扩展到大型 CC 问题实例，且不易于并行化。本文的目标是为 CC 实现一种高效的优化机制，在该机制中可以使用大规模并行计算。

在本文中，我们将运筹学中的相关性聚类应用于计算机视觉中的 CC。Benders 分解通常用于运筹，以解决具有公共块结构的混合整数规划（MILP）。Benders 分解分别处理变量，如果 MILP 的约束矩阵包含来自多个子问题的变量，则不需要任何更改。CC 中的优化通过在其变量上求解一个主问题来分解。子问题的解可以并行求解，并根据它们对主问题解的条件提供原始/对偶割平面。子问题的对偶解将持续存在，直到主问题不再添加更多约束。

使用运筹学技术强制-王 Benders 规则（MWR）加速 Benders 分解。MWR 通过求解具有替代目标（随机顺序）的子问题生成，减少了关于子问题原始目标（可能在某个因子内）的优性硬性约束。

我们的贡献是使用带有 MWR 的 Benders 分解来处理 CC 中的优化。这允许大规模并行，与像 CC 在... 中这样的方法形成对比。

# I. 引言

许多计算机视觉任务涉及将一组观测值划分（聚类）为唯一的实体。对于此类任务，的一种强效表述是（相关性聚类）CC，它定义在具有实值边的图上，其中节点与观测值相关，边表示节点对之间的亲和力。

例如，在图像分割（基于超像素）中，节点对应于超像素，边表示它们之间的相邻关系。超像素之间边的权重指的是由分类器定义的、两个超像素属于同一地面真实实体的概率。如果边的幅度小于 1，我们定义其为一个割切（cut）。边的幅度是分类器决策的函数。

CC 代价函数是划分问题中连通分量（称为实体）边的权重之和。CC 中的优化将图划分为边，以最小化 CC 代价。它非常有吸引力，因为实体的数量作为边权重的函数自然产生，而不需要对描述聚类数量的模型进行额外搜索 ([37])。

对于一般图，CC 的优化是 NP 难的 [5]。之前对 CC 问题优化的方法如 [2], [3] 和 [2] 中描述的基于线性规划 Benders 分解的方法，是一种精确的 MILP 求解技术，但可以直观地作为坐标程序使用，学习主问题和子问题。子问题不共享变量，而且以主问题变量上超平面的形式学习一个下界。该下界是主问题的当前解。

Benders 分解使用运筹学技术强制-王 Benders 规则（MWR）[23] 加速 Benders 分解。MWR 通过求解具有替代目标（随机顺序）的子问题生成，减少了关于子问题原始目标（可能在某个因子内）的优性硬性约束。

我们的贡献是使用带有 MWR 的 Benders 分解来处理 CC 中的优化。这允许大规模并行，与像 CC 在在... 中这样的方法形成对比。

# II. 相关工作

相关性聚类已成功应用于计算机视觉中的多个问题，包括图像分割、多目标跟踪、分割和姿态估计。CC 的经典工作，节点对应于超像素 [20]；使用整数线性规划（ILP）表述-分支定界策略的 CC 排除了并行性 [21]；CC 包含节点集上的高阶代价项，使用类似于 [2] 的方法进行求解。[26] 提出了一种用于无权图聚类的划分方案。该方法依赖于随机采样并提供最优下界。

[37] 研究了聚类中常见的平面图结构中的 CC。他们引入了聚类生成方法 [16]，其中定价问题对应于寻找图的最低代价 2-色划分，通过 [13], [22], [29] 实现。这种方法已扩展到图像分割和分割 [30]，以及非平面图的特定情况 [34], [39]。

大型 CC 问题定义为 [19], [20]，且通常通过可行启发式算法处理 [8], [18], [20], [30]。当最优解无法达到时，这些方法非常相关，但它们没有提供对解质量的保证。

[31] 使用一个与 CC 为相似的框架进行多目标跟踪，其中对象和边的聚类与 CC 关联。我们的工作源于 [17]。

# III. 问题表述

本章节，我们关注的是等式 (CC$_1$) 中 CC 的刻画，而不是针对 [2] 中的特定求解器。

给定解 $x^*_{vij}$，每个 Benders 问题的优化记为 $x_{vij}$，并定义如下。

# IV. 用于相关性聚类的 BENDERS 分解

在本节中，我们引入了一种使用 Benders 分解进行 CC 的新方法（称为 BDCC）。我们的分解方法由一个主问题（master problem） $\mathcal{E}^m$ 定义，其中成员 $s \in \mathcal{E}^m$ 与一个 Benders 问题相关，而 $v_i$ 被称为子问题的根。在 Benders 分解中，使得每个 $(v_i, v_j) \in \mathcal{E}$ 要么与 $v_i$ 的子问题相关，要么与 $v_j$ 的子问题相关。这里 $\mathcal{E}^s$ 是 $\mathcal{E}$ 中与子问题 $s$ 相关的子集。Benders 分解强制执行 $\mathcal{E}^s$ 中的循环约束，$\mathcal{E}^s$ 是 $\mathcal{E}$ 中相邻于 $s$ 的子集。

在 A 节中，我们补充了 $[x^*_{vij}]_{\mathcal{S}}$ 的代价相对于等式 (CC2) 的目标大于 $Q(\hat{o}, s, x)$，且存在等式 (CC2) 的最优解 $x^*$，使得对于所有 $s \in \mathcal{S}$，$Q(\hat{o}, s, x) = 0$。

在本节中，我们假设已提供 $S$，它可以通过贪心算法产生或使用 LP 求解器产生。

在我们用辅助函数 $Q(\hat{o}, s, x)$ 重写等式 (CC1) 之前，该函数通过增加/减少 $x_{vij}$ 提供使 $x$ 满足所有 CC 不等式的代价，其中对于 $(v_i, v_j) \in \mathcal{E}_s$。我们描述主问题边标记 $x$ 的变化，其中 $x^* = \{x_{vij} \in [0,1]\}$，且 $|s|$ 是每个 Benders 子问题的成员数量。

由此得出，等式 (2) 中图中节点的任何最优解 $x^*$ 都是 2-可色的。这是因为任何划分都可以修改，而不会合并相邻的连通分量（不包括根节点 $v_i$）。因此，任何此类分量的对都不会增加代价，因为这些分量不是通过负权重边连接的，除非结果是一个划分。

(CC1) $\to$ (CC2):

基于这一观察，我们使用 $Q(\hat{o}, s, x)$（也称为线性最小切）重写优化等式 (CC2)，公式如下：

$$\min_{x \in \{0,1\}} \sum_{(v_i,v_j) \in \mathcal{E}_s} -x_{vij} + \sum_{(v_i,v_j) \in \mathcal{E}_s} x_{vij} + Q(\hat{o}, s, x) \quad (2)$$

$Q(\hat{o}, s, x)$ 定义为：

我们用 1 表示节点 $v \in \mathcal{V}$ 不是根子问题 $s$ 的关联分量且 $m=s$；否则为 0。因此，没有额外的 $m_i$ 被替换为 0。

$$\min_{x \in \{0,1\}^s} \sum_{(v_i,v_j) \in \mathcal{E}_s} Q_{vij}(1-x_{vij}) + \sum_{(v_i,v_j) \in \mathcal{E}_s} x_{vij}Q_{vij} \text{s.t. } x_{vij} \ge 1-x^*_{vij} \forall (v_i,v_j) \in \mathcal{E}^* \quad \forall c \in C$$

我们构造一个解 $x^* = \{x^*_{vij}\}_{_{(v_i,v_j) \in \mathcal{S}}$，使得等式 (CC2) 最小且所有约束均满足。给定解 $x = \{x_{vij}\}_{_{(v_i,v_j) \in \mathcal{S}\}}$，我们按照如下方式进行：

$$x^*_{vij} = \min_{x \in \{0,1\}} Q_{vij}(x) \quad \forall (v_i,v_j) \in \mathcal{E}_s, s \in \mathcal{S} \quad (3)$$

$$x^*_{vij} = \max_{x \in \{0,1\}} Q_{vij}(x) \quad \forall (v_i,v_j) \in \mathcal{E}^* \quad (4)$$

由于等式 (2) 中的流约束，等式 (4) 的右侧无法达到 1。因此我们将 $Q(\hat{o}, s, x)$ 写为原始对偶 LP，其原始部分由对偶变量 $\lambda$ 满足，$\lambda$ 在原始问题中。由于 $m$ 是非负的，为了确保原始问题存在，我们将 $Q(\hat{o}, s, x)$ 给出：

$$Q(\hat{o}, s, x) = \begin{cases} \sum_{(v_i,v_j) \in \mathcal{E}_s} \phi_{i,j} & (v_i,v_j) \in \mathcal{E}^+ \\ \sum_{(v_i,v_j) \in \mathcal{E}_s} \phi_{i,j} & (v_i,v_j) \in \mathcal{E}^- \end{cases} \quad (7)$$

这得到了对偶问题：

$$\max_{\lambda \ge 0} \sum_{(v_i,v_j) \in \mathcal{E}_s} \lambda_{ij} \quad (8)$$

## 算法 1 用于 CC 的 Benders 分解法 (BDCC)

```
Algorithm 1
  Z = {0}
  done_LP = False
  repeat
    x = Solve Eq. (CC) over Z enforcing integrity if and only if done_LP=True
      add_did = False
      for s ∈ S do
        if (vᵢ, vⱼ) ∈ s. d(vᵢ, vⱼ) < xᵢ,ⱼ then
          z₁ = Get Benders Row via (8)
          z₂ = Get MWR Sec. S.
          Z = Z ∪ {z₁, z₂}
          add_did = True
      end
    if add_did
      done_LP = True
    end
  until done_did=False AND 0 ∈ {V(vᵢ, vⱼ) ∈ S}
  return x
```

我们遵循了运筹学文献的传统，使用一个负随机向量（具有单位范数）来代替目标函数。求解了该随机向量子问题。我们尝试过使用目标函数 -.001*v，这可以鼓励切割具有正权重的边，但也作为负目标。.0001 是一个正数。它防止了目标函数中的项……

在下面，我们需要 Benders 行处于激活状态；这通过要求当前解允许目标函数存在 ε (0,1) 的容差来实现。我们在等式 (8) 中解决了它。

```
$$\tau(\phi, s, X) = \sum_{(v_i,v_j) \in s} (\lambda_{v_i} + \lambda_{v_j})x_{i,j} - \sum_{(v_i,v_j) \in s} (\mu_{v_i} + \mu_{v_j})x_{i,j} = (9)$$
```

在这里，τ=1 要求等式 (8) 中的目标，而 τ=0 则忽略了最优性。在我们的实验中，我们发现 τ=2 提供了强大的性能。

# V. 强制-王 BENDERS 规则 (MWR)

# VI. 实验：图像分割

在本节中，我们展示了 BDCC 在基准伯克利数据集 (BSDS) 图像分割问题上的价值。我们的实验证明了以下三点：

1) BDCC 成功地利用了并行化；(2) BDCC 成功地利用了图像分割；(3) MWR 的使用极大加速了优化。

为了评估性能，我们使用了 BSDS 的 OPENGM 数据提供的成本项。这使得我们将我们的结果与 [2] 中的结果进行了直接比较。我们在生成 MWR 时使用了位于单位负随机向量。我们使用 CPLEX 来求解优化过程中考虑的所有线性和整数规划问题。对于每个问题实例（无论如何），我们使用的最大 CPU 时间为 600 秒。



我们将 S 的选择形成一个最小顶点覆盖，其中每条边 `(vᵢ, vⱼ) ∈ s`，至少有一个 MWR 顶点覆盖覆盖了 S 中的每条边作为 S 中的选中节点。给定一个 ILP，我们发现对于我们的数据，求解最小顶点覆盖消耗的 CPU 忽略不计。我们将其归功于我们问题的性质，因为最小顶点覆盖是一个 NP-hard 问题。这个问题求解最小顶点覆盖正好是精确求解、近似求解或贪心求解。

在图 1 中，我们展示了 BDCC 在各种不同问题上的效果。我们发现 τ 的实际值并不会显著影响优化效果。我们展示了依赖和不依赖并行的性能。我们的处理时间显示了我们为每个子问题使用的时间。对于应用中的每个实例，子问题在数千个以内，每个都很容易求解。并行和非并行时间仅共享求解主问题的时间。我们观察到对于所有 τ 的设置，并行化都有巨大的收益。当不使用 MWR 时，我们观察到改进减少，因为主问题包含了大部分的 CPU 时间。

在图 1 中，我们展示了主问题带来的速度提升。对于大多数实例，使用 MWR 时所需的时间比不使用 MWR 时短。在表 1 中，我们考虑了由于 MWR 使用引起的改进，由于主问题包含了更大比例的 CPU 时间。在我们的实验中，我们发现由于主问题包含了更大比例的 CPU 时间，改进有所减少。我们的方法展示了……

# VII. 结论

我们展示了一种用于聚类的方法。在我们的实验中，我们证明了我们的方法 BDCC 在多种问题上的有效性……(img/6f5b0c0d4f5)

**图 1.** 我们展示了 BDCC 在各种不同问题上的效果。我们发现 τ 的实际值并不会显著影响优化效果。我们展示了依赖和不依赖并行的性能。我们的处理时间显示了我们为每个子问题使用的时间。对于应用中的每个实例，子问题在数千个以内，每个都很容易求解。并行和非并行时间仅共享求解主问题的时间。我们观察到对于所有 τ 的设置，并行化都有巨大的收益。当不使用 MWR 时，我们观察到改进减少，因为主问题包含了大部分的 CPU 时间。

在图 1 中，我们展示了主问题带来的速度提升。对于大多数实例，使用 MWR 时所需的时间比不使用 MWR 时短。在表 1 中，我们考虑了由于 MWR 使用引起的改进，由于主问题包含了更大比例的 CPU 时间。

表 1: 在不同 τ 设置下求解问题的数量（使用和不使用并行化）

| | 10 | 50 | 100 | 300 |
|---|---|---|---|---|
| ε=0 | 0.5 | 0.147 | 0.585 | 0.944 |
| | 0 | 0.0116 | 0.0745 | 0.106 |
| | 0.5 | 0.266 | 0.774 | 0.868 |
| | 0 | 0.0628 | 0.181 | 0.417 |
| ε=1 | 0.5 | 0.149 | 0.394 | 0.606 |
| | 0 | 0.0168 | 0.037 | 0.904 |
| | 0.5 | 0.319 | 0.818 | 0.947 |
| | 0 | 0.0532 | 0.0752 | 0.117 |
| ε=10 | 0.5 | 0.292 | 0.426 | 0.628 |
| | 0 | 0.0532 | 0.0957 | 0.128 |
| | 0.5 | 0.447 | 0.936 | 0.985 |
| | 0 | 0.0638 | 0.128 | 0.223 |

M. E. Fisher. The dimer solution of fulerene models. Journal of Mathematical Physics, 7(10):1776–1781, 1966.

L. R. Ford and D. R. Fulkerson. Maximum flow through a network. Canadian Journal of Mathematics, 8(1956):39–46.

A. S. Johnson and G. W. Graham. Multiobjective system design by design computers. Management science, 25(3):822–844, 1977.

K. Rinnooy and R. Gilmore. A linear programming approach to cutting-stock problem. Operations research (volume 9), 1961.

E. Ineustanço, L. Pritischal, A. Mendez, M. Andrikius, and B. Schiele. Deep learning for human pose and multipose pose estimation. In European Conference on Computer Vision, pages 34–50.

A. Karodoust and M. Kuiper. Solving minimum multicut problems by node aggregation. In Proceedings of the 2018 15th Asian Conference on Computer Science, North Perth, Australia, 2018.

N. Kuyper, B. Andres, and T. Box. Motion trajectory segmentation via minimum cost cut. In ICCV, 2017.

M. Morozov, V. Smirnov, G. Lavov, L. Trov, and B. Andres. Efficient decomposition of images and meshes by guided methods. In IEEE Transactions...

S. Kim, Nowozicki, P. Kobli, and C. D. Yu. Higher-order clustering for image estimation. In Advances in Neural Information Processing Systems, pages 2550–2558, 2011.

V. Kolmogorov. A new implementation of a minimum cost perfect matching algorithm. Mathematical Programming, 10(1):1–79, 1969.

T. L. Magnani and R. T. Wong. Accelerating decomposition: Image segmentation and model selection criteria. Operations research, 29(4):464–484, 1981.

D. Martin, C. Fowkes, and T. Jalabi. A database of human images and applications to segmentation algorithms and measuring statistical statistics. In Proceedings of the International Conference on Computer Vision (ICCV-01), pages 16–23,2001.

S. Nowozicki and G. Solin. Solution library for linear partitioning and unsupervised learning. In Proceedings of the 26th Annual International Conference on Machine Learning, pages 769–776. ACM, 2009.

X. Park, J. Simposos, O. Symak, B. Reich, K. Ramchandander, and M. Jordan. Parallel clustering on graphs. In Proceedings of the 28th Annual Conference on Neural Information Processing Systems (Volume 21):NIPS, pages 82–90, Cambridge, MA, USA, 2015.

T. Pritischal, E. Ineustanço, S. B, B. Andrikius, and V. Gehler, and B. Schiele. Joint subset partitioning and labeling for multipose pose estimation. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pages 4982–4997, 2017.

R. Cother, V. Kolmogorov, V. Lempitsky, and M. Zaumer. Optimizing speed and quality. In Computer Vision and Pattern Recognition, 2007. CVPR ’07. IEEE Conference on, pages 1–8, 2007.

W. Shi, S. Wu, and Y. Kuo. Optimizing maximum cut and minimum cost of a planar graph. IEEE Transactions on Computers, 39(5):694–697, 2000.

S. Pswodes and B. Andres. A passing algorithm for the minimum cost multicut problem. In CVPR, 2017.

M. Wang, M. Andrikius, and B. Schiele. Subgraph decomposition for multi-tracking tasks. In CVPR, 2015.

S. Wang, J. Keering, and J. Yorky. Exploring dynamic programming based decomposition with application to multipose pose estimation. In Proceedings of the European Conference on Computer Vision (ECCV), pages 655–666, 2016.

S. Wang, J. Keering, and J. Yorky. Exploring dynamic programming based decomposition with application to multipose pose estimation. In Proceedings of the European Conference on Computer Vision (ECCV), pages 655–666, 2016.

S. Wang, J. Keering, and J. Yorky. Exploring dynamic programming based decomposition with application to multipose pose estimation. In Proceedings of the European Conference on Computer Vision (ECCV), pages 655–666, 2016.

# 附录 A

在本节中，我们证明存在一个使 $C_2$ 最小的 $x^*$ 使得 $Q(\phi, s, x^*) = 0$。另一个解 $\{x^*_{v_1}, x^*_{v_2}, ..., x^*_{v_n}\}$ 是整数，且满足 $Q(\phi, s, x^*) = 0$，且 $C_2$ 没有增加。我们根据 $x^*$ 保持等式：

$x^*_{v_1} + x^*_{v_2} + ... + x^*_{v_n} + y(v_i, v_j) \in S$ (10)

$x^*_{v_1} + x^*_{v_2} + ... + x^*_{v_n} - 1 \leq y(v_i, v_j) \in E, S$

$0 \leq y(v_i, v_j) \in \mathcal{E}^+$

$x^*_{v_1} + x^*_{v_2} + ... + x^*_{v_n} - 1 \geq y(v_i, v_j) \in E, S$ (1)

方程 (10) 和 (11) 等价于 $f^*$ 的以下方程。这里，$f^*$ 对应于给定 $x^*$ 的解：

$x^*_{v_i} = f^*_{v_i} + \max f(v_i, y), y(v_i, v_j) \in S$ (12)

$x^*_{v_i} = f^*_{v_i} - \min f(v_i, y), y(v_i, v_j) \in E, S$

$0 \geq \max f(v_i, y), y(v_i, v_j) \in S$

$x^* = \min Q(C, s, x), x \in S$ (13)

$x^*_{v_i} = f^*_{v_i}$ (11)。

我们注意到 (10) 和 (11) 是 $C^*$ 中原始线性规划的对偶。同样注意到，对于所有 $s \in \mathcal{S}$，$Q(\phi, s, x^*) = 0$。我们随后考虑由 $x^*$ 导出的 $C_2$ 为整数的情况。如果目标函数的增加是非正，则主问题的总减少值为 $-\phi_{v_i} \max f(v_i, y) + \phi_{v_i} \min f(v_i, y)$。这表明 $C_2$ 的目标是非负的。我们提供了以下算法求解主问题：

- 行 1：使用 $x^*$ 初始化 Benders 割集。
- 行 1：表示我们尚未求解线性松弛并生成 Benders 割集，以获得可行解。
- 行 1：求解主问题提供一个解 $x$，该解可能不满足所有不等式。如果是整数，则我们已经解决了线性松弛，完成并返回。
- 行 2：表示我们向 $x^*$ 添加了某些 Benders 割。
- 行 3：通过迭代子问题并添加 $\mathcal{E}^*$ 的 Benders 割来添加 Benders 规则。
- 行 1：检查是否存在违反 $\mathcal{E}^*$ 的割不等式。通过遍历 $v_i$ 并检查从 $v_i$ 到 $v_j$ 的最短路径是否小于图中等于 $k$ 的边上的 $x_{ij}$。
- 行 4：如果在此迭代中添加了 Benders 规则，我们强制 $x$ 整数性。在算法剩余部分求解主问题时：
- 行 1：返回 $x^*$。

在考虑优化之前，提供可行整数解的需求是有价值的。当整数解与松弛之间的差距很小时，这可以结束优化。在本节中，我们考虑给定当前松弛解的可行整数解问题。我们通过将此过程视为舍入来处理不等式。

舍入是一种基于图 $\mathcal{G}$ 及其边权重 $k$ 的约束下降方法。我们确定这样的 $x^*$：

$x^*_{v_i} = f^*_{v_i} + \max f(v_i, y), y(v_i, v_j) \in S$ (12)

$x^*_{v_i} = f^*_{v_i} - \min f(v_i, y), y(v_i, v_j) \in E, S$

$0 \geq \max f(v_i, y), y(v_i, v_j) \in S$

$x^* = \min Q(C, s, x), x \in S$ (13)

方程 (13) 的过程无论 $x^*$ 是整数还是可行均可用。如果它接近整数且可行，则可以使用 (13) 产生可行解。我们通过迭代 $s$ 构建 $x^*$ 的划分，正如算法 2 所示。

## 算法 2 给定非整数输入 $x^*$ 的初始化和可行解

```
x^* = 0; Q(\phi, s, x) \in S

对于 s \in \mathcal{S}:
    x^*_{v_i} = \max f(v_i, y), y \in \mathcal{E}^+
    x^*_{v_i} = \min f(v_i, y), y \in \mathcal{E}^-

结束:
返回 x^*
```

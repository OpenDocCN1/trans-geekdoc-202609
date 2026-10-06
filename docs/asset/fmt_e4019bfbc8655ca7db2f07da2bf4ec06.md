
在这项研究中，我们使用一种名为 `MultiDiscriminant` 的深度学习方法解决了一对一相互依赖网络的拆解问题。该方法提出了一种基于类的嵌入框架和基于 `DQN` 的分类器。我们证明了 `MultiDiscriminant` 优于现有的先进算法。与其他拆解策略相比，`MultiDiscriminant` 作为免疫策略在防止疾病传播方面表现出很高的相似性。我们在各种网络拓扑结构和成本分布中证明了这一点，这可以轻松应用于实际场景。我们的工作强调了将图神经网络与强化学习相结合处理复杂网络任务的潜力，并为未来研究增强此类方法的可扩展性和适应性开辟了途径。`MultiDiscriminant` 在保护网络免受针对性攻击和随机故障方面的表现。随后，我们通过移除 1% 的剩余节点（随机）或由 `MultiDiscriminant` 识别的节点来评估网络。

## 问题公式

我们考虑一个由两个交互层组成的网络。两层中的节点是单相互依赖的。为了简单起见且不失通用性，我们不对其中一层和另一层进行区分，因为如果它们都属于同一节点集合，我们会处理它们。我们将网络表示为 $G = (V, E^1, E^2)$，其中 $|V|$ 表示节点总数，$E^l$ 表示第 $l$ 层的边，$l = 1$。第 $l$ 层的邻接矩阵的通用元素为 $A^l_{ij} = 1$，如果 $(i, j) \in E^l$，否则为 $A^l_{ij} = 0$。

大规模网络连通性通过属于 LMMC 的节点比例来量化。令 $P(S) = \frac{|S|}{|V|}$，其中 $|S|$ 是 LMMC 中的节点数，$|V|$ 是节点数。当所有节点存在于网络中时，$P(S) = 1$。如果移除子集 $S \subset V$，若 $S = \emptyset$，则 $P(S) = 0$。网络拆解（通常被称为拆解问题）可以作为一个约束优化问题：

$$S^*(C) = \arg \min_{S} P(S)$$

施加在移除集合 $S$ 元素的成本 $C$ 之上的约束。本文考虑了三种成本类型：1) 单位成本、（2) 度、（3) 随机成本。在单位成本版本中，与集合 $S$ 相关的函数是大小，因此 $C(S) = |S|$。度版本定义为 $C(S) = \sum_{v \in S} d_v$，其中 $d_v$ 是图 $G$ 中节点 $v$ 的度。我们用 $d_v^{(l)}$ 表示第 $l$ 层中节点 $v$ 的度，集合 $S$ 中的节点仅计算一次。在随机成本版本中，每个节点 $i$ 相关的成本由 $F(i) = X_i$ 给出，其中 $X_i$ 取自均值为 0.5、方差为 0.1 的分布，或均值为 1 的泊松分布。

优化问题描述的一个重要方面是识别导致 LMMC 消失的最小成本节点集。此类定义：

$$S^*(C) = \arg \min_{S: C(S) \leq C} P(S)$$

本质上，只有将 $P$ 降低到阈值以下的 $S$ 才被视为解决方案：近似多层网络拆解。本文考虑的所有算法顺序构造拆解问题的近似方法，确保解决方案每次添加一个元素。$f_1, f_2, \dots, f_n$ 是按照顺序添加的节点标签。我们定义 $S_t = \{f_1, \dots, f_t\}$ 为集合由相应元素组成时的算法近似解。如果 $S_0 = \emptyset$ 且 $S_n = V$，对于所有 $t=0, \dots, n$，显然有 $P(S_t) \geq P(S_{t+1})$。我们通过衡量 AUD 来评估近似算法的性能：

$$AUD = \frac{1}{N} \sum_{i=1}^{N} (F(S) - F(S \setminus \{v_i\}))$$

$F(V)$ 是与图中节点相关的成本。这是 Schneider 等人引入的所谓鲁棒性指标。由于计算原因，我们通过累加 $N$ 个贡献来近似 AUD，这提供了真实值的良好近似。这种能力之一可以是多层网络拆解问题的扩展，例如多层 $\mathcal{N}$ 或通过冗余依赖关系连接的网络。我们将此类扩展留给未来研究。

注意 AUD 和 $C$ 都定义在 [0, 1] 。对于指标，低值表示良好的性能。

我们提供了 Multilayer 中使用的编码器、解码器和拆解策略的细节。

### 编码器

`MGNN` 的框架如图 5 所示。`MGNN` 由层内图和层注意力模块组成，用于聚合来自不同层的信息。网络嵌入中的初始化特征对于建立坚实基础和收敛至关重要。借鉴 `FINDER` 的初始化方法，`MGNN` 利用多层 MLP 编码：

$$H^{(l)} = \text{ReLU}(W_l X^{(l)})$$

其中 $X^{(l)}$ 是节点 $i$ 在层 $l$ 中的归一化度（通过节点最大度定义节点度）。$\text{ReLU}(\cdot)$ 是激活函数，$W_l$ 是权重矩阵，$\cdot$ 表示 l2 归一化。

使用初始化特征，我们通过迭代聚合节点特征及其表示的信息，将层内图卷积神经网络应用于节点嵌入：

$$H^{(l)} = \text{ReLU}(W_l H^{(l-1)} + U_l \cdot \sum_{j \neq l} H^{(j-1)})$$

在方程 (l) 中，$H^{(l)}$ 代表前向传播步中节点 $i$ 在层 $l$ 中的嵌入。它捕捉了 $h$ 个隐藏信息。$W_l$ 和 $U_l$ 是权重矩阵，$N^{(l)}$ 表示层 $l$ 中的邻居节点集。最终表示可以表示为 $H^{(L)}$。

```
$h_i^{(l)} = \text{tanh}(W_l h_i^{(l-1)} + b_l);$
```

我们聚合了所有层中节点 $v$ 的结果

```
$Q(s, a) = \sum_{t=1}^{\infty} \gamma^t r(s_t, a_t);$
```

之前的聚合技术通常使用跨层权重来量化层间重叠，忽略了同一层内连接的真实性。其中 $Q(s, a)$ 是在节点 $v$ 下采取动作 $a$ 的期望 $Q$ 值，对于互连网络的整体交互。

这些高阶层网络注意力增强克服了以往方法的局限性。在这里，我们使用多层层间注意力机制来捕捉跨层交互，使模型能够有效学习依赖网络不同层之间的交互：损失和函数依赖。对于观察到的结果，我们使用节点移除对网络连通性的影响来量化跨越的直接奖励：

```
$a_i^{(l)} = \sigma(W_i^{(l)}h_i^{(l-1)} + b_i^{(l)})$, 
```

```
$r(v) = f(G) - f(G-v);$
```

其中 $P(l)$ 是当节点 $v$ 存在时图的 LMCC 大小，$f(G)$ 是移除它的成本。其中 $a^{(l)}$ 是节点 $v$ 从层 $q$ 到 $t$ 的计算出的层间注意力，$W$ 是可训练的权重矩阵，$b$ 定义了偏置，$p$ 是一个向量，$L$ 是层数，$S$ 是标准奖励。

移除节点的影响可能不是立即产生的，并可能对网络连通性产生延迟影响。我们应用的 $n$-步 DQN 使用重放缓冲区中的 $n$-步回报，通过考虑多步的累积奖励来更好地捕捉延迟效应。它聚合了层表示和层间特征，使用通过累积奖励计算出的目标 $Q$ 值形成最终的节点嵌入。潜在动作 $a$ 下下一个时间步的直接奖励表示为 $\max_{a'} Q(s', a')$。解码器框架评估时间 $t$ 处动作 $a$ 的预测奖励，表示为 $Q(s, a)$。$Q$-learning 损失旨在最小化预测 $Q$ 值与目标 $Q$ 值之间的差异

```
$x_i^{(l)} = \sum_{p=1}^{l} \alpha_p^{(l)} h_i^{(p)};$
```

其中 $x_i^{(l)}$ 是节点 $v$ 在层 $l$ 中的最终表示。解码器将状态和动作向量作为输入，并计算网络中所有可能动作的 $Q$ 值。在本文，我们使用来自 `MGAN` 的节点表示作为动作：$x_i^{(l)}$ 是节点 $v$ 在层 $l$ 中的动作。该状态代表移除节点 $v$ 对网络的影响。我们使用图神经网络来估计节点的移除，因此我们在状态中添加了一个虚拟节点 $v$。所有残留节点都是节点 $s$ 的直接邻居，但没有考虑该层中的任何其他节点。

```
$Loss_Q = \mathbb{E}_{(s,a,r,s') \sim UB} [(r + \gamma \max_{a'} Q(s', a'; \theta^-) - Q(s, a; \theta))^2]$
```

其中 $UB$ 表示经验缓冲区 $B$ 上的均匀采样分布，$\theta$ 是当前网络参数，$\theta^-$ 从 $\theta$ 定期更新，$\gamma$ 是增强未来奖励的折扣因子。

在不同的层中，我们使用了各种奖励：直接奖励和节点 $v$ 的移除奖励；例如，一个节点在某层中可能作为社区的核心连接节点，但在另一层中可能作为外围节点。为了从不同层全面视角节点重要性，我们使用奖励级融合机制来量化最终节点奖励，同时我们添加了图重构损失以保留网络拓扑结构

```
$Loss_R = \sum_{i=1}^{n} ||\hat{x}_i - x_i||^2$;
```

```
$Loss = Loss_Q + \beta Loss_R$;
```

```
$\omega^{(l)} = \frac{1}{M} \sum_{i=1}^{M} \text{RelU}(r^{(i)}, \mathbf{M}_i);$
```

其中 $\omega^{(l)}$ 是节点 $v$ 在层 $l$ 中的奖励重要性，$M$ 和 $\mathbf{M}_i$ 是可训练矩阵。其中 $\beta$ 是平衡节点重要性的超参数。通过建立既定的环境、编码和优化框架，我们使用贪婪选择程序根据 $Q$ 值确定最佳动作和节点移除。在训练阶段，使用了 $\epsilon$-greedy 策略，以 $(1-\epsilon)$ 的概率选择 $Q$ 值最高的动作，以 $\epsilon$ 的概率选择随机动作。$Q$ 的值用于平衡探索与利用。在应用阶段，

在这里我们描述了实验中使用的其他算法。例如层去噪算法，我们解释了它们如何在多个网络中构建和利用。这些泛化算法也使用全局得分来达到每个单个层上估计的中心性最大值。这种启发式方法通过将目标攻击协议从单层推广到一对一网络进行了精炼。然而，我们强调将得分合并为全局得分：未来的工作可以利用深度学习方法来推断结果的适当规则。`CoreHLDA` 用于网络回收和分解多层网络的精炼过程。一种在网络中使用的新颖评分方法，它结合了来自单层的得分。

有关研究设计的更多信息请参见本文的链接。

研究中使用的所有数据均可获得。为了便于结果的可复现性，所有必要数据均可在 https://doi.org/10.1038/s41256-020-01070-2 (ref 51) 获取。

### DDA

我们为每个节点 $s_i = k_i^{(k)}$ 分分，$k_i$ 是节点 $i$ 的度；节点按度排序。我们移除度最高的节点。当节点具有相同度时，我们随机选择其中一个。一旦节点被移除，剩余节点的度将得到更新。为本研究开发的代码可在 https://doi.org/10.1038/s41256-020-01070-2 获取

- 1. Watts, D. J., & Strogatz, S. Collective dynamics of 'small-world' networks. Nature 398, 440–442 (1998).
- 2. Holme, P. Complex networks: structure and dynamics. Phys. Rep. 42, 175–308 (2006).
- 3. Cohen, R., Perez, A., Duvani, A., & Havlin, S. Robustness of the internet under attack. Phys. Rev. 86, 3682 (2001).
- 4. Molnar, F., & Higham, A. Influence propagation in multiplex networks. Nature 524, 65–68 (2015).
- 5. Barabasi, A., Guiltner, N., & Marchal, J. Quantifying efficiency in exchange market. Science 394, 1285–994 (2002).
- 6. Bertagnoni, G., Gilli, A., & De Manci, M. Power grids susceptible to cascading failures. Complex Systems 15, 125 (2021).
- 7. Chen, Y., Paul, G., Lledijos, R., & Stanley, H. E. A better immunization strategy. Phys. Rev. Lett. 101, 058701 (2008).
- 8. Braunstein, A., Dalla, L., Sergiani, J., & Zoblik, L. Targeted attacks on complex networks. Science 313, 1232–1230 (2006).
- 9. Cohen, A., et al. Robustness and resilience of complex networks. Nature 414, 113–116 (2001).

### FINDER

`FINDER` 使用 DRL 框架识别单层网络的关键节点。它估计从层中移除的节点。在多层网络中，我们为每个节点分配 $s_i = \max(k_i^{(l)})$ 并移除度最高的节点。我们在单元场景中使用训练良好的 `FINDER` 版本。对于其他需求（如度和移除约束），我们保留了具有相同训练参数的 `FINDER` 模型。`FINDER` 的函数实现可通过 GitHub

### MinSum

我们使用 `MinSum` 通过拆解得分来识别连通组件。节点 $i$ 在层拆解过程中的位置由 $s_i = m_i/w_i$ 表示；我们为节点 $i$ 分配得分并移除得分最小的节点。当得分相同时，我们随机选择其中一个。`MinSum` 算法的实现可在 https://github.com/abaysalzer/dismantling 获取。

18. Chen, Y., Tang, M., & Li, Y. 多层网络中非马尔可夫旅行者的流行动力学. Commun. Phys. 6, 263 (2020).
19. Orta, S., Faget, A., & Radicchi, F. 多路网络上的金融渗透. Nat. Commun. 8, 1540 (2017).
20. Baxter, J. J., Timár, G., & Mendes, J. 相互依赖网络的针对性破坏. Phys. Rev. E 98, 032618 (2018).
21. Coignard, F., & Radicchi, F. 控制多层网络真实响应的韧性. Nat. Phys. 13, 1037 (2017).
22. Han, J., Shi, Y., Zhao, L., & Li, J. 一种破坏多层网络的影响因子层自适应策略. Eur. Phys. J. 94, 74 (2021).
23. Schwarz, M. J., Brusaker, K. J., & Katagberger, G. 受物理启发的图神经网络的社区优化. Nat. Mach. Intell. 4, 367–377 (2022).
24. Khalil, E., Dai, J., Zhang, Y., Dilaina, B., & Song, L. 图上的组合优化学习. Adv. in Neural Information Learning. Inf. Proc. Syst. 32 (2019).
25. Wu, C., Pu, L., Li, W., Xie, L., & G, R. M. 基于图同构的多层网络鲁棒性分析. IEEE Trans. Networks 54, 6630–6642 (2016).
26. Kleinberg, K., Boguná, N., Morales, S., & Papadopoulos, H. 多层网络中的几何相关性. Nat. Phys. 12, 1078– (2016).
27. Baxter, M. 等. 几何网络. Nat. Phys. 9, 114–135 (2013).
28. Fakeeh, A., Orta, S., & Radicchi, F. 复杂网络中流行与社区结构之间动力学的表征. Phys. Rev. Lett. 121, 098301 (2018).
29. Ramirez, S., W. K., Fortunato, S., & Radicchi, F. 复杂网络中的流行扩散. Phys. Rev. X 13, E01054 (2023).
30. Sutton, B. R. 通过时间差分方法学习. Machine Learning, 3, 99–114 (1990).
31. Wen, R.-L., Lin, G., Hedberg, A., & Antulia, F. 通用去中心化挖掘. Proc. Natl. Acad. Sci. USA 116, 6554–6559 (2019).
32. Ramsey, F. P. 见经典组合数学 1–24 (Springer-Verlag, 1998).
33. Kivela, M., 等. 多层网络. J. Complex Net. 2, 203–234 (2017).
34. Sun, Y., Wang, L., & Guang, R. 复杂网络的结构鲁棒性：指标综述. IEEE Circuits Syst. Mag. 23, 12–35 (2017).
35. Ma, Y., Wang, S., Aggrawal, C., Yan, D., & Han, J. 多维图卷积网络. 在 Proc. 2019 第8 届国际数据挖掘会议 657–675 (2019).
36. Dong, Y., Wang, X., & Wang, S. Metapatch22.0: 异构网络的可扩展表示. 在 Proc. 2017 第23 届 ACM SIGKDD 知识发现与数据挖掘国际会议 135–144 (2017).

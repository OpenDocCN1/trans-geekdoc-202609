
对于潜在变量模型，这意味着计算

$$\boldsymbol{h}^* = \arg\max_{\boldsymbol{h}} p(\boldsymbol{h} \mid \boldsymbol{v}) \tag{19.9}$$

这被称为 **最大后验** 推断，简称为 MAP 推断。

MAP 推断通常不被视为近似推断——它确实计算了 $\boldsymbol{h}^*$ 的精确最可能值。然而，如果我们希望基于最大化 $\mathcal{L}(\boldsymbol{v},\boldsymbol{h},q)$ 来开发学习过程，那么将 MAP 推断视为提供 $q$ 值的一种过程是有帮助的。在这种意义上，我们可以将 MAP 推断视为近似推断，因为它并不能提供最优的 $q$。

回顾第 19.1 节，精确推断包括最大化

$$\mathcal{L}(\boldsymbol{v},\boldsymbol{\theta},q) = \mathbb{E}_{\boldsymbol{h}\sim q}[\log p(\boldsymbol{h},\boldsymbol{v})] + H(q) \tag{19.10}$$

关于 $q$，在不受限制的概率分布族上，使用精确优化算法。我们可以通过限制 $q$ 可能取自的分布族，将 MAP 推断推导为一种近似推断的形式。具体来说，我们要求 $q$ 取狄拉克分布：

$$q(\boldsymbol{h} \mid \boldsymbol{v}) = \delta(\boldsymbol{h} - \boldsymbol{\mu}) \tag{19.11}$$

这意味着我们现在可以通过 $\boldsymbol{\mu}$ 完全控制 $q$。去掉 $\mathcal{L}$ 中不随 $\boldsymbol{\mu}$ 变化的项，我们剩下优化问题

$$\boldsymbol{\mu}^* = \arg\max_{\boldsymbol{\mu}} \log p(\boldsymbol{h}=\boldsymbol{\mu},\boldsymbol{v}) \tag{19.12}$$

这等价于 MAP 推断问题

$$\boldsymbol{h}^* = \arg\max_{\boldsymbol{h}} p(\boldsymbol{h} \mid \boldsymbol{v}) \tag{19.13}$$

我们因此可以证明一种类似于 EM 的学习过程，其中我们交替执行 MAP 推断以推断 $\boldsymbol{h}^*$，然后更新 $\boldsymbol{\theta}$ 以增大 $\log p(\boldsymbol{h}^*,\boldsymbol{v})$。与 EM 一样，这是一种对 $\mathcal{L}$ 的坐标上升，其中我们交替使用推断来优化 $\mathcal{L}$ 关于 $q$，并使用参数更新来优化 $\mathcal{L}$ 关于 $\boldsymbol{\theta}$。整个过程可以由 $\mathcal{L}$ 是 $\log p(\boldsymbol{v})$ 的下界这一事实来证明。在 MAP 推断的情况下，这种证明相当空洞，因为由于狄拉克分布的微分熵为负无穷，该界无限松弛。对 $\boldsymbol{\mu}$ 添加噪声会使该界再次变得有意义。

MAP 推断在深度学习中常被用作特征提取器和学习机制。它主要用于稀疏编码模型。

回顾第 13.4 节，稀疏编码是一种线性因子模型，对其隐藏单元施加稀疏诱导先验。常见选择是因子化拉普拉斯先验，

$$p(h_i)=\frac{\lambda}{2}e^{-\lambda|h_i|}.$$ (19.14)

可见单元随后通过执行线性变换并添加噪声生成：

$$p(\boldsymbol{x}\mid\boldsymbol{h})=\mathcal{N}(\boldsymbol{v};\boldsymbol{W}\boldsymbol{h}+\boldsymbol{b},\beta^{-1}\boldsymbol{I}).$$ (19.15)

计算甚至表示 $p(\boldsymbol{h}\mid\boldsymbol{v})$ 都是困难的。每个变量对 $h_i$ 和 $h_j$ 都是 $\boldsymbol{v}$ 的父节点。这意味着当 $\boldsymbol{v}$ 被观测时，图形模型包含连接 $h_i$ 和 $h_j$ 的活动路径。所有隐藏单元因此在 $p(\boldsymbol{h}\mid\boldsymbol{v})$ 中参与一个巨大的团。如果模型是高斯的，那么这些交互可以通过协方差矩阵有效地建模，但稀疏先验使这些交互非高斯。

因为 $p(\boldsymbol{h}\mid\boldsymbol{v})$ 难以处理，对数似然及其梯度的计算也是如此。我们因此不能使用精确的最大似然学习。相反，我们使用 MAP 推断并通过最大化由狄拉克分布在 $\boldsymbol{h}$ 的 MAP 估计周围定义的 ELBO 来学习参数。

如果我们将训练集中所有的 $\boldsymbol{h}$ 向量连接成矩阵 $\boldsymbol{H}$，并将所有的 $\boldsymbol{v}$ 向量连接成矩阵 $\boldsymbol{V}$，那么稀疏编码学习过程包括最小化

$$J(\boldsymbol{H},\boldsymbol{W})=\sum_{i,j}|H_{i,j}|+\sum_{i,j}\left(\boldsymbol{V}-\boldsymbol{H}\boldsymbol{W}^{\top}\right)_{i,j}^2.$$ (19.16)

大多数稀疏编码应用还涉及权重衰减或对 $\boldsymbol{W}$ 列范数的约束，以防止 $\boldsymbol{H}$ 极小而 $\boldsymbol{W}$ 很大的病态解。

我们可以通过在关于 $\boldsymbol{H}$ 的最小化和关于 $\boldsymbol{W}$ 的最小化之间交替来最小化 $J$。两个子问题都是凸的。事实上，关于 $\boldsymbol{W}$ 的最小化只是一个线性回归问题。然而，关于两个参数的 $J$ 的最小化通常不是凸问题。

关于 $\boldsymbol{H}$ 的最小化需要专门的算法，例如特征符号搜索算法 (Lee et al., 2007)。

## 19.4 变分推断与学习

我们已经看到证据下界 $\mathcal{L}(v, \boldsymbol{\theta}, q)$ 是 $\log p(v; \boldsymbol{\theta})$ 的下界，推断可以被视为关于 $q$ 最大化 $\mathcal{L}$，学习可以被视为关于 $\boldsymbol{\theta}$ 最大化 $\mathcal{L}$。我们看到 EM 算法使我们能够在 $q$ 固定的情况下进行大步学习，而基于 MAP 推断的学习算法使我们能够使用 $p(h | v)$ 的点估计进行学习，而不是推断整个分布。现在我们开发更一般的变分学习方法。

变分学习的核心理念是我们可以对受限的分布族 $q$ 最大化 $\mathcal{L}$。该族应选择使得计算 $E_q\log p(h, v)$ 容易。一种典型的方法是引入关于 $q$ 如何分解的假设。

变分学习的一种常见方法是施加 $q$ 为因子分布的限制：

$$q(h \mid v)=\prod_{i} q(h_i \mid v) . \quad(19.17)$$

这被称为 **均值场** 方法。更一般地，我们可以在 $q$ 上施加任意选择的图形模型结构，以灵活决定近似应捕捉多少交互。这种完全通用的图形模型方法称为 **结构化变分推断** (Saul and Jordan, 1996)。

变分方法的美妙之处在于我们不需要为 $q$ 指定特定的参数形式。我们指定它应如何分解，然后优化问题决定在这些分解约束内的最优概率分布。对于离散潜在变量，这只是意味着我们使用传统的优化技术来优化描述 $q$ 分布的有限数量变量。对于连续潜在变量，这意味着我们使用称为变分法的数学分支来在函数空间上执行优化，并实际确定应使用哪个函数来表示 $q$。变分法是“变分学习”和“变分推断”名称的来源，尽管这些名称即使在潜在变量离散且不需要变分法时也适用。对于连续潜在变量，变分法是一种强大的技术，它减少了模型设计者的人为责任，现在他只需指定 $q$ 如何分解，而无需猜测如何设计一个能够准确近似后验的特定 $q$。

因为 $\mathcal{L}(v, \boldsymbol{\theta}, q)$ 定义为 $\log p(v, \boldsymbol{\theta}) - D_{\mathrm{KL}}(q(h \mid v) \| p(h \mid v; \boldsymbol{\theta}))$，我们可以将关于 $q$ 最大化 $\mathcal{L}$ 视为最小化 $D_{\mathrm{KL}}(q(h \mid v) \| p(h \mid v))$。


# 随机游走与 Metropolis 方法

随机游走是一种流行的模型，能够忠实地模拟许多现实世界的现象，例如热噪声、气体分子运动以及股票价值变化。此外，此类链有助于我们理解更复杂的马尔可夫链的行为，稍后将对此进行讨论。根据转移概率的选择不同，存在各种随机游走模型（参见例如 [32]）。此处，我们假设变量为离散的，并在有限集合 `{0, 1, …, N}` 中取整数值。因此，状态总数为 `N + 1`。在每个时间瞬间，变量的值可以分别以概率 `p` 增加或减少 1，或者以概率 `q` 保持不变，前提是当前状态在索引集合 `{1, 2, …, N − 1}` 内。即，若 `0 < x[n − 1] < N`，

```
P(x[n] = x[n − 1] + 1) = P(x[n] = x[n − 1] − 1) = p, P(x[n] = x[n − 1]) = q.
```

该序列在 `n = 10` 时已收敛。注意，收敛后，`P^(n)` 的所有列向量相等，且元素之和为 1。此外，观察到

```
P[∞] ∝ [a[1], a[1], a[1]].
```

如果 `x[n-1] = 0`，则 `x[n]` 要么以概率 `q[e]` 保持同一状态，要么以概率 `p` 增加 1。如果 `x[n-1] = N`，则 `x[n]` 要么以概率 `q[e]` 保持同一状态，要么以概率 `p` 减少 1。显然，

```
2p + q = 1,  p + q[e] = 1.
```

当 `N = 4`、`p = 1/4`、`q = 1/2` 和 `q_e = 3/4` 时，转移概率矩阵为

```
P = [3/4  1/4  0    0    0
     1/4  1/2  1/4  0    0
     0    1/4  1/2  1/4  0
     0    0    1/4  1/2  1/4
     0    0    0    1/4  3/4].
```

对应的特征值为 `λ[1] = 1`、`λ[2] = 0.904`、`λ[3] = 0.654`、`λ[4] = 0.345` 和 `λ[5] = 0.095`。观察可知，除 `λ[1] = 1` 外，所有特征值的模均小于 1。对应的特征向量为

```
a[1] = [0.447, 0.447, 0.447, 0.447, 0.447]^T
a[2] = [−0.601, −0.371, 0, 0.371, 0.601]^T
a[3] = [−0.511, 0.195, 0.632, 0.195, −0.511]^T
a[4] = [−0.371, 0.6015, 0, −0.601, 0.371]^T
a[5] = [0.195, −0.511, 0.632, −0.511, 0.195]^T.
```

![Equation](img/si238.png)

与 `λ[1]` 对应的特征向量其所有分量均相等且为正。因此，在必要的缩放后，不变分布（`p`：`P p = p`）变为均匀分布，`p = [1/5, 1/5, 1/5, 1/5, 1/5]^T`。类似的论证适用于任意 `N` 值。请注意，所有其他特征向量的分量之和均为零。

图 14.8 显示了 `N = 4` 时概率分布 `p[n]` 在 `n = 10`、50 和 100 时刻的情况。`p[0]` 的分量是随机选择的。图 14.9 对应 `N = 9` 的情况。可以观察到，`N` 值越大，收敛越慢。

![图 14.8 示例 14.5 中随机游走链的概率分布，N=4 且时间点为 (A) n=10, (B) n=50, 和 (C) n=100。](img/gr008.jpg)

图 14.8 示例 14.5 中随机游走链的概率分布，`N = 4` 且时间点为 (A) `n = 10`, (B) `n = 50`, 和 (C) `n = 100`。

## 示例 14.6

在本示例中，我们考虑一个具有（可数）无限多状态的随机游走；在每个时刻，随机变量的值要么以概率 `p` 增加 1，要么以概率 `p` 减少 1，要么以概率 `q` 保持在同一状态，即

```
P(x[n] = x[n−1] + 1) = P(x[n] = x[n−1] − 1) = p, P(x[n] = x[n−1]) = q
```

且

```
2p + q = 1
```

与前一个示例的区别在于，现在不存在“边界”点，随机变量可以取任意整数值。我们的目标是计算均值和方差作为时间 `n` 的函数，其中起点被确定性地选为 `x[0] = 0`。

很容易看出 `𝔼[x[n]] = 0`，因为该变量增加和减少的可能性相等，因此它取任何正值或负值的可能性也相等。

对于方差，我们得到（问题 14.11）

```
𝔼[x[n]²] = 𝔼[x[n−1]²] + 2p = 2pn + 𝔼[x[0]²] = 2pn
```

因为 `𝔼[x[0]²] = 0`。注意方差随时间趋于无穷大，因此无限状态空间随机游走*不*具有极限分布。这验证了我们之前所说的；适用于有限状态空间的结果不一定适用于状态数变为无限的情况。

仔细观察公式 (14.47) 可知，平均而言，经过 `n` 个时间瞬间后，`x[n]` 将落在 `±√(2pn)` 范围内。如果 `x[n]` 表示一个点从起始原点出发向后或向前移动的距离，则其行进距离仅与其花费的行进时间的平方根成正比。尽管该结果是针对无限状态空间情况推导的，但它仍能解释我们在有限状态空间情况下前一个示例中观察到的向不变分布收敛缓慢的现象。正如文献 [30] 所述，一旦状态空间中的所有点都被访问过，就能实现向不变分布的收敛，而这对时间具有平方根依赖关系。为了获得极限分布的足够好近似，必须有足够的耐心计算 `O(N²)` 次迭代。

# 14.8 Metropolis 方法

Metropolis 方法（有时称为 Metropolis 算法）建立在一个令人惊讶的简单想法之上，它是第一个利用马尔可夫链理论进行采样的方法。它出现在经典文献 [27] 中，可能是最流行、最广为人知的采样技术，并衍生出大量变体。与拒绝采样和重要性采样不同，建议分布现在是随时间变化的，遵循马尔可夫链的演化；后者的构建使得其转移概率矩阵（密度核）具有期望分布 `p(x)` 作为其不变分布。此外，与拒绝采样和重要性采样技术不同，并不要求建议分布“看起来像”期望分布，该方法在实践中才有用。建议分布取决于前一状态的值 `x[n-1]`，即 `q(·|x[n-1])`。换句话说，抽取新样本（生成新状态）取决于前一个状态的值。在其原始版本中，建议分布被选为对称的，即：

```
q(x|y) = q(y|x).
```

后来，Hastings [14] 将其推广以包含非对称情况。该通用方案称为 Metropolis-Hastings 算法，总结如下。

## Algorithm 14.3

### Metropolis-Hastings 算法

*   令期望分布为 $p(\cdot) = \frac{1}{Z}\phi(\cdot)$。
*   选择建议分布为 `q(·|·)`。
*   选择初始状态 `x[0]` 的值。
*   **For** `n = 1, 2, ..., N`，**Do**
    1.  抽取 `x ~ q(·|x[n-1])`。
    2.  计算接受率

### Metropolis–Hastings 算法步骤

1.  **计算接受率：**

    `α(x|x_{n-1}) = min{ 1, (q(x_{n-1}|x)φ(x)) / (q(x|x_{n-1})φ(x_{n-1})) }`

2.  **抽取** `u ~ U(0, 1)`

3.  **若** `u ≤ α(x|x_{n-1})`：
    *   `x_n = x`

4.  **否则**：
    *   `x_n = x_{n-1}`

**循环结束**

### 关键性质

*   该算法不需要 `p` 的确切形式。仅需知道其归一化常数 `Z` 即可。这是因为 `p` 仅在计算接受率的比率中出现。
*   若提议分布是对称的，接受率变为：

    `α(x|x_{n-1}) = min{ 1, φ(x) / φ(x_{n-1}) }` (14.48)

    在这种情况下，我们有时称之为 **Metropolis 算法**。
*   注意，如果样本未被接受，我们将保留前一状态的值。
*   观察可知，样本的接受或拒绝取决于 `α(x|x_{n-1})` 的值。通过查看基于公式 (14.48) 的原始算法形式，这一点更容易理解。如果概率 `p(x)` 大于 `p(x_{n-1})`，则接受新样本。否则，根据其相对值决定接受或拒绝。
*   连续样本**不**独立。

### 变体与理论背景

针对接受率函数的选择，存在上述基本方案的变体。文献 [33] 基于所得近似值方差的最优性证明，给出了支持 Metropolis–Hastings 方案基本原理的论据。

现在让我们转向理解前述算法与马尔可夫链理论的联系。我们将处理更一般的连续状态空间模型，并定义

```
p(x|y) = q(x|y)α(x|y) + δ(x − y)r(x),
```

其中 `r(x)` 为拒绝概率，

```
r(x) = ∫(1 − α(x|y))q(x|y) dy，
```

而 `δ(·)` 为狄拉克 δ 函数。稍加思考可知，按上述定义，`p(·|·)` 即为等价马尔可夫链的转移密度核（有限离散空间的转移矩阵），即 `p(x[n]|x[n − 1])`。此外，该马尔可夫链具有所需的分布 `p(x)` 作为其不变分布，即

```
p(x) = ∫p(x|y)p(y) dy，
```

正如第 14.7 节已指出的那样，这是满足以下详细平稳条件的直接结果（问题 14.12）：

```
p(x|y)p(y) = p(y|x)p(x)。
```

原来，只要 `p(x|y)` 和 `p(x)` 为*严格正值*，该等价马尔可夫链就是遍历的，因此收敛于不变（所需）分布。这保证了从任意状态出发均可到达任意状态，且概率非零。

因此，Metropolis–Hastings 算法等价地从由公式 (14.49) 给出的转移密度所定义的马尔可夫链中抽取样本，尽管样本是从选定的（易于采样的）建议分布中抽取的。常用于充当建议分布的典型分布有高斯分布和柯西分布。后者因其重尾特性，允许大幅变化偶尔发生。有时也会使用均匀分布。对于离散情况，均匀分布似乎是一个常用的选择。

#### 烧入阶段

收敛后，该过程等同于从期望的 `p(x)` 中抽取样本。然而，世界上没有完美的事物；马尔可夫链蒙特卡洛技术的一个主要弱点在于，很难评估马尔可夫链*是否已收敛*，因此也难以确定所生成的样本是否真正有效独立且真正具有代表性。在链收敛之前生成的样本不代表期望分布，必须予以拒绝；这被称为*烧入阶段*。马尔可夫链收敛所需的区间称为*混合时间*（例如，[21]）。

为此，人们提出了许多诊断方法，但没有一种可被视为万能药（相关讨论见，例如，[6,8,35]）。文献 [2] 从理论上论证了评估此类技术收敛性的困难性，并指出这是一个计算上不可处理的任务。

在实践中，在拒绝烧入阶段的样本后，会运行一条长链并丢弃每 `M` 个样本中的一个。对于足够大的 `M` 值，预期可以获得独立样本。此过程也称为*稀疏化*。另一种途径是运行几条，例如三到四条，不同的（从不同初始点开始的）中等规模（例如 100,000）的链，在丢弃各自烧入阶段的样本（例如前一半）后，从每条链中获取样本。

##### 14.8.1 收敛问题

在处理拒绝采样和重要性采样时，我们讨论过这些方法不随维度良好扩展。相比之下，Metropolis 方法表现出好得多的行为，且是一种适合于大空间应用的算法。话虽如此，该方法并非没有缺点。为了详细说明，我们将利用从随机游走示例中获得的经验，并采用类似于文献 [30] 中给出的论证。

考虑一个二维任务，并采用高斯分布作为建议分布 `q(x|x[n-1])`，其协方差矩阵为 `σ²I`，且每次以 `x[n-1]` 为中心。待采样的期望分布是另一个细长的高斯分布 `N(x|0, Σ)`，如图 14.10A 所示。数值 `σ[max], σ[min]` 表示与椭圆两个轴相关的尺度（标准差）（回顾第 2 章，这是由 `Σ` 的特征结构定义的），这对应于 `p(x)` 的一个标准差等高线（高斯分布中的指数等于 `−1/2`）。

![Figure 14.10 (A) The region of significant probability mass is enclosed by the ellipse, with scales σmax and σmin, respectively, as defined by the major and minor axes. The region of significant probability mass of the proposal distribution is spherical of scale equal to σ, which is of the same order as σmin. (B) Starting from the point shown as a circle, 50 generated points are shown using a proposal distribution of variance equal to σ² = 0.1; rejected points are shown in red. (C) The snapshot with 100 points and (D) with 3000 points. Observe that even in the latter case, still there are parts in the high-probability region of the desired distribution that have not been covered.](img/gr010.jpg)

图 14.10 (A) 显著概率质量区域被椭圆包围，其尺度分别为 `σ[max]` 和 `σ[min]`，由长轴和短轴定义。建议分布的显著概率质量区域是球形的，尺度等于 `σ`，其量级与 `σ[min]` 相同。(B) 从圆圈所示点开始，展示了使用方差等于 `σ² = 0.1` 的建议分布生成的 50 个点；被拒绝的点显示为红色。(C) 100 个点的快照和 (D) 3000 个点的快照。观察到即使在后一种情况下，期望分布的高概率区域仍有部分未被覆盖。

Each time a sample is drawn from $\mathcal{N}(\mathbf{x}|\mathbf{x}_{n-1}, \sigma² \mathbf{I})$, the new sample will fall with high probability inside a circle of radius $\sigma$ centered on $\mathbf{x}_{n-1}$. For the new sample to have a high probability of falling inside the high-probability ellipsoidal region, $\sigma$ must be of order $\sigma_{\text{min}}$ or smaller. If a larger value of $\sigma$ is chosen, the sample will most likely fall outside the ellipsoid and be rejected. Thus, once the sampling has started inside the ellipsoid, a small value of $\sigma$ will ensure, with high probability, that the samples stay inside the ellipsoid and are therefore accepted. On the other hand, if $\sigma$ is small, a large number of iterations will be required to cover the interior of the ellipsoid adequately with points. If the sampling process is viewed as an approximate random walk with step size $\sigma$, the number of iterations required to cover a scale of order $\sigma_{\text{max}}$ will be $\left( \frac{\sigma_{\text{max}}}{\sigma} \right)^{2}$; if $\sigma \approx \sigma_{\text{min}}$, this becomes $\left( \frac{\sigma_{\text{max}}}{\sigma_{\text{min}}} \right)^{2}$. In high-dimensional spaces, where some dimension is likely to have a scale that is relatively small compared to the maximum scale, this square dependence rule of thumb will significantly slow down convergence.

Figure 14.10 B–D shows the case where the target bivariate Gaussian has zero mean and a covariance matrix given by

$$

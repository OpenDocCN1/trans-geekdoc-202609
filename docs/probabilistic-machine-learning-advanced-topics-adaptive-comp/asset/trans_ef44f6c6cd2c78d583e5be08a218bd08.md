

![](img/ca72c1626f4850f058a9edc138c1ac73_531_0.png)

图 12.2: 2D MRF 的棋盘格图示。这允许并行更新。

我们现在证明每个此类建议的接受率为 100%，因此整体算法的接受率也是 100%。我们有

```
$$\alpha = \frac{p(x')q_t(x|x')}{p(x)q_t(x'|x)} = \frac{p(x'_i|x'_{-i})p(x'_{-i})p(x_i|x'_{-i})}{p(x_i|x_{-i})p(x_{-i})p(x'_i|x_{-i})}\\ = \frac{p(x'_i|x_{-i})p(x_{-i})p(x_i|x_{-i})}{p(x_i|x_{-i})p(x_{-i})p(x'_i|x_{-i})} = 1$$
```

这里利用了 x'_{-i} = x_{-i} 这一事实。

接受率为 100% 这一事实并不意味着 Gibbs 会快速收敛，因为它一次只更新一个坐标（参见第 12.3.7 节）。但是，如果我们可以将相关变量分组，则可以将其作为一个组进行采样，这可以显著帮助混合。

## 12.3.3 示例：Ising 模型的 Gibbs 采样

在第 4.3.2.1 节中，我们讨论了 Ising 模型和 Potts 模型，它们是具有 2D 网格结构的成对 MRF。联合分布的形式为

```
$$p(x) = \frac{1}{Z} \prod_{i \sim j} \psi_{ij}(x_i, x_j | \theta)$$
```

其中 i ~ j 表示 i 和 j 是图中的邻居。

要将 Gibbs 采样应用于此类模型，我们只需从每个全条件分布中迭代采样：

```
$$p(x_i | x_{-i}) \propto \prod_{j \in \text{nbr}(i)} \psi_{ij}(x_i, x_j)$$
```

需要注意的是，尽管 Gibbs 采样是一种顺序算法，但我们有时可以利用条件独立性属性来执行并行更新 [RS97a]。在 2D 网格的情况下，我们可以使用图 12.2 所示的棋盘格图案对节点进行颜色编码。这具有以下属性：给定白色节点时，黑色节点彼此条件独立，反之亦然。因此，我们可以并行采样所有黑色节点（作为一个组），然后采样所有白色节点，等等。

![](img/ca72c1626f4850f058a9edc138c1ac73_532_0.png)

图 12.3: 使用 Gibbs 采样进行图像去噪的示例。我们使用 J = 1 的 Ising 先验和 σ = 2 的高斯噪声模型。(a) 对图像进行一次扫掠后从后验中采样。(b) 5 次扫掠后的采样。(c) 后验均值，通过对 15 次扫掠求平均计算。与图 10.9 比较，后者显示了平均场推断的结果。由 ising_image_denoise_demo.ipynb 生成。

要执行采样，我们需要计算公式 (12.24) 中的全条件分布。对于具有边势 ψ(x_i, x_j) = exp(Jx_i x_j) 的 Ising 模型，其中 x_i ∈ {-1, +1}，全条件分布变为

```
p(x_i = +1|x_{-i}) = \frac{\prod_{j \in \text{nbr}(i)} \psi_{ij}(x_i = +1, x_j)}{\prod_{j \in \text{nbr}(i)} \psi(x_i = +1, x_j) + \prod_{j \in \text{nbr}(i)} \psi(x_i = -1, x_j)} (12.25)
= \frac{\exp[J \sum_{j \in \text{nbr}(i)} x_j]}{\exp[J \sum_{j \in \text{nbr}(i)} x_j] + \exp[-J \sum_{j \in \text{nbr}(i)} x_j]} (12.26)
= \frac{\exp[J\eta_i]}{\exp[J\eta_i] + \exp[-J\eta_i]} = \sigma(2J\eta_i) (12.27)
```

其中 J 是耦合强度，η_i \triangleq \sum_{j \in \text{nbr}(i)} x_j，σ(u) = 1/(1 + e^{-u}) 是 Sigmoid 函数。（如果我们使用 x_i ∈ {0, 1}，则变为 p(x_i = +1|x_{-i}) = σ(Jη_i)。）很容易看出 η_i = x_i(a_i - d_i)，其中 a_i 是与节点 i 同意（具有相同符号）的邻居数量，d_i 是不同意的邻居数量。如果这两个数量相等，则对 x_i 的“力”会相互抵消，因此全条件分布是均匀的。该模型的一些样本如图 4.17 所示。

Ising 模型的一个应用是作为二进制图像去噪问题的先验。具体来说，假设 y 是 x 的噪声版本，我们希望计算后验 p(x|y) ∝ p(x)p(y|x)，其中 p(x) 是 Ising 先验，p(y|x) = \prod_i p(y_i|x_i) 是逐站似然项。假设这是一个高斯分布。令 ψ_i(x_i) = N(y_i|x_i, σ^2) 为相应的“局部证据”项。全条件分布变为

```
p(x_i = +1|x_{-i}, y) = \frac{\exp[J\eta_i]\psi_i(+1)}{\exp[J\eta_i]\psi_i(+1) + \exp[-J\eta_i]\psi_i(-1)} (12.28)
= \sigma \left( 2J\eta_i - \log \frac{\psi_i(+1)}{\psi_i(-1)} \right) (12.29)
```

现在，x_i 进入每个状态的概率既由它与邻居的兼容性（Ising 先验）决定，也由它与数据的兼容性（局部似然项）决定。

有关该算法应用于简单图像去噪问题的示例，请参见图 12.3。结果与图 10.9 中的平均场结果相似。

## 12.3.4 示例：Potts 模型的 Gibbs 采样

我们可以如下将第 12.3.3 节扩展到 Potts 模型。回顾该模型具有以下形式：

\( p(\boldsymbol{x}) = \frac{1}{Z} \exp(-\mathcal{E}(\boldsymbol{x})) \tag{12.30} \)

\( \mathcal{E}(\boldsymbol{x}) = -J \sum_{i \sim j} \mathbb{I}(x_i = x_j) \tag{12.31} \)

对于具有邻居 nbr(i) 的节点 i，全条件分布因此由以下给出

\( p(x_i = k|\boldsymbol{x}_{-i}) = \frac{\exp(J \sum_{n \in \text{nbr}(i)} \mathbb{I}(x_n = k))}{\sum_{k'} \exp(J \sum_{n \in \text{nbr}(i)} \mathbb{I}(x_n = k'))} \tag{12.32} \)

因此，如果 J > 0，当大多数邻居已经处于状态 k 时，节点 i 更有可能进入状态 k，这对应于吸引型 MRF。如果 J < 0，节点 i 更有可能进入与其邻居不同的状态，这对应于排斥型 MRF。有关使用此方法创建的该模型的一些样本，请参见图 4.18。

## 12.3.5 示例：GMM 的 Gibbs 采样

在本节中，我们考虑从以下形式的贝叶斯高斯混合模型中进行采样

\( p(z=k, \boldsymbol{x}|\boldsymbol{\theta}) = \pi_k \mathcal{N}(\boldsymbol{x}|\boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k) \tag{12.33} \)

\( p(\boldsymbol{\theta}) = \text{Dir}(\boldsymbol{\pi}|\boldsymbol{\alpha}) \prod_{k=1}^K \mathcal{N}(\boldsymbol{\mu}_k|\boldsymbol{m}_0, \mathbf{V}_0) \text{IW}(\boldsymbol{\Sigma}_k|\mathbf{S}_0, \nu_0) \tag{12.34} \)

### 12.3.5.1 已知参数

假设最初参数 \(\boldsymbol{\theta}\) 是已知的。我们可以通过祖先采样轻松从 \(p(\boldsymbol{x}|\boldsymbol{\theta})\) 绘制独立样本：先采样 \(z\)，再采样 \(\boldsymbol{x}\)。但是，为了说明目的，我们将使用 Gibbs 采样来绘制相关样本。\(p(\boldsymbol{x}|z=k, \boldsymbol{\theta})\) 的全条件分布就是 \(\mathcal{N}(\boldsymbol{x}|\boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k)\)，而 \(p(z=k|\boldsymbol{x})\) 的全条件分布由贝叶斯规则给出：

\( p(z=k|\boldsymbol{x}, \boldsymbol{\theta}) = \frac{\pi_k \mathcal{N}(\boldsymbol{x}|\boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k)}{\sum_{k'} \pi_{k'} \mathcal{N}(\boldsymbol{x}|\boldsymbol{\mu}_{k'}, \boldsymbol{\Sigma}_{k'})} \tag{12.35} \)

该程序的一个示例，应用于两个均值分别为 -20 和 +20 的 1D 高斯混合，如图 12.4 所示。我们看到样本是自相关的，这意味着如果我们处于状态 1，则可能会在该状态停留一段时间，并生成靠近 \(\mu_1\) 的值；然后我们会随机跳转到状态 2，并在附近停留一段时间，等等。（有关衡量此方法的方式，请参见第 12.6.3 节。）相比之下，来自联合分布的独立样本根本不会相关。

在第 12.3.5.2 节中，我们修改此示例以从后验 \(p(\boldsymbol{\theta}|\mathcal{D})\) 采样 GMM 的参数，而不是从 \(p(\mathcal{D}|\boldsymbol{\theta})\) 采样。

![](img/ca72c1626f4850f058a9edc138c1ac73_534_0.png)

### 12.3.5.2 未知参数

现在假设参数未知，因此我们希望将模型拟合到数据。如果我们使用条件共轭分解先验，则完全联合分布由以下给出

$p(\boldsymbol{x}, \boldsymbol{z}, \boldsymbol{\mu}, \boldsymbol{\Sigma}, \boldsymbol{\pi}) = p(\boldsymbol{x}|\boldsymbol{z}, \boldsymbol{\mu}, \boldsymbol{\Sigma})p(\boldsymbol{z}|\boldsymbol{\pi})p(\boldsymbol{\pi}) \prod_{k=1}^K p(\boldsymbol{\mu}_k)p(\boldsymbol{\Sigma}_k)$ (12.36)

$= \left( \prod_{i=1}^N \prod_{k=1}^K (\pi_k \mathcal{N}(\boldsymbol{x}_i|\boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k))^{\mathbb{I}(z_i=k)} \right) \times$ (12.37)

$\text{Dir}(\boldsymbol{\pi}|\boldsymbol{\alpha}) \prod_{k=1}^K \mathcal{N}(\boldsymbol{\mu}_k|\boldsymbol{m}_0, \mathbf{V}_0)\text{IW}(\boldsymbol{\Sigma}_k|\mathbf{S}_0, \nu_0)$ (12.38)

我们为每个混合组件使用相同的先验。

全条件分布如下。对于离散指示变量，我们有

$p(z_i = k | \boldsymbol{x}_i, \boldsymbol{\mu}, \boldsymbol{\Sigma}, \boldsymbol{\pi}) \propto \pi_k \mathcal{N}(\boldsymbol{x}_i | \boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k)$ (12.39)

对于混合权重，我们有（使用第 3.4.2 节的结果）

$p(\boldsymbol{\pi} | \boldsymbol{z}) = \text{Dir}(\{\alpha_k + \sum_{i=1}^N \mathbb{I}(z_i = k)\}_{k=1}^K)$ (12.40)


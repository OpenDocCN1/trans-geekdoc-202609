

定理 3.10 的证明见第 A.8 节。要理解上述 (b) 的含义，假设我们希望使用 AMP 来获得 \(v \equiv v(n)\) 的估计 \(\tilde{v} \equiv \tilde{v}(n)\)，使得（渐近）\(\ell_1\) 估计误差 \(n^{-1}\sum_{i=1}^n |\tilde{v}_i - v_i|\) 很小。根据 (3.23) 和定理 3.10(b)，将 \(\psi\) 取为绝对误差损失 \(\psi_1 : (x, y) \mapsto |x - y|\)，我们应首先在每次迭代中运行 Bayes-AMP 以获得尽可能高的有效信噪比 \(\rho^*_k\)。然后对于每个 \(k \in \mathbb{N}\)，我们应考虑 \(g^*_{k, \psi_1} : \mathbb{R} \to \mathbb{R}\)，使得 \(g^*_{k, \psi_1}(y)\) 是 \(V\) 在给定 \(\mu_k V + \sigma_k G = y\) 条件下的（即后验）分布的中位数，对（勒贝格几乎处处）每个 \(y \in \mathbb{R}\) 成立。如果我们可以找到具有此性质的 Lipschitz \(g^*_{k, \psi_1}\)，则 \(\hat{v}^{k, \psi_1} := g^*_{k, \psi_1}(v^{k, \mathsf{B}})\) 在某些形式为 (3.3) 的 AMP 算法的第 \(k\) 次迭代所得所有估计量中，达到最低可能的极限平均绝对误差 \(R_{\pi, \psi_1}(\rho^*_k) = \inf_g \mathbb{E}[|V - g(\sqrt{\rho^*_k} V + G)|]\)。在没有合适的 Lipschitz \(g^*_{k, \psi_1}\) 的情况下，例如当 \(V\) 具有离散分布时，上述方法的一种可能修改是在构造估计量时用 Lipschitz 近似替换 \(g^*_{k, \psi_1}\)，希望得到的渐近 \(\ell_1\) 误差接近 \(R_{\pi, \psi_1}(\rho^*_k)\)。

关于定理 3.10(c)，可以将 Bayes-AMP 所实现的渐近均方误差 (3.24) 和经验相关性 (3.25) 与相应的贝叶斯最优量进行比较（即，_任何_ 估计量所能达到的最佳可能极限值）。在尖峰模型 (3.1) 中，其中 \(v \equiv v(n)\) 的项服从分布 \(\pi\) 的 i.i.d. 分布，Barbier _等人_ (2016) 和 Lelarge 和 Miolane (2019) 严谨地建立了贝叶斯估计量 \(\mathbb{E}(v|A)\) 的闭式渐近表达式。结果表明，贝叶斯最优性能由 \(\rho = \lambda^2(1 - \mathsf{mmse}(\rho))\) 的一个特定固定点 \(\rho^*_\mathsf{B}\) 表征，该固定点最大化某个自由能泛函；详情见 Montanari 和 Venkataramanan (2021, 第 2.4 节)。因此，我们可以精确表征对称秩一矩阵估计中 Bayes-AMP 与贝叶斯最优估计之间的性能差距。特别是，当方程 \(\rho = \lambda^2(1 - \mathsf{mmse}(\rho))\) 具有唯一正解时（如图 1.1 中 \(U\{-1, 1\}\) 前验的情况），Bayes-AMP 达到贝叶斯最优性能。此外，在 \(\rho^*_\mathsf{AMP} \neq \rho^*_\mathsf{B}\) 的情况下（即 AMP 不是贝叶斯最优），目前尚无已知多项式时间算法在 (3.25) 的极限有效信噪比方面优于 Bayes-AMP。

我们注意到，Bayes-AMP 在多项式时间算法中的最优性仅对某些统计问题类（如低秩矩阵估计和广义线性模型）被推测成立。对于 tensor PCA，Hopkins _等人_ (2015) 提出了一种基于和平方层次的多项式时间算法，其估计性能严格优于 AMP (Montanari 和 Richard, 2014)。随后，Wein _等人_ (2019) 开发了基于统计物理的广义谱方法，其性能与和平方法在 tensor PCA 中相匹配。

### 备注 3.11.

假设极限前验分布 \(\pi\) 是对称的，即 \(V \stackrel{d}{=} -V\)，在此情况下 \(v\) 和 \(-v\) 渐进不可区分。那么 \(\mathbb{E}(V) = 0\)，并且如前言 3.6 中所述，无法以数据驱动的方式一致地选择谱初始化器的符号，以确保每个 \(n\) 的 \(\langle \hat{\varphi}, v \rangle_n \ge 0\)。尽管如此，Bayes-AMP（带谱初始化）的两个可能状态演化轨迹显然仅在每个 \(\mu_k\) 的符号上相同，因此 (3.24) 和 (3.25) 中的极限对下列各式分别保持有效：

\(\min_{\epsilon \in \{-1, 1\}} \|\hat{v}^{k,\mathrm{B}} - \epsilon v\|_n^2 \quad \text{and} \quad \min_{\epsilon \in \{-1, 1\}} \frac{\langle \hat{v}^{k,\mathrm{B}}, \epsilon v \rangle_n}{\|\hat{v}^{k,\mathrm{B}}\|_n \|v\|_n} \quad \text{respectively.}\)

### 备注 3.12.

如果极限前验分布 \(\pi\) 已知，但 \(\lambda, \mu_0, \sigma_0\) 中的某些或全部未知，则从某个 \(n\) 的 \(\hat{v}^0 \equiv \hat{v}^0(n)\) 开始，我们可以基于每个 \(k\) 的 \(\mu_k, \sigma_k\) 估计构造一种 "经验 Bayes-AMP 算法"。具体地，回顾备注 3.3 并进行归纳，我们可以使用 (3.17) 根据以下式子定义 \(\hat{g}_k^*\)：

\(\hat{\mu}_k := (\|v^k\|_n^2 - \|\hat{v}^{k-1}\|_n^2)^{1/2} \quad \text{and} \quad \hat{\sigma}_k := \|\hat{v}^{k-1}\|_n,\)

然后对于每个 \(k\) 通过 (3.3) 得到 \(\hat{v}^k = \hat{g}_k^*(v^k)\) 和 \(v^{k+1}\)。或者，由于 Bayes-AMP 中 \(\mu_k^* = \lambda(\sigma_k^*)^2 \ge 0\)，我们可以取 \(\hat{\mu}_k = \hat{\lambda}\hat{\sigma}_k^2 = \hat{\lambda}\|\hat{v}^{k-1}\|_n^2$，其中

\(\hat{\lambda} := \frac{\lambda_1(A) + \sqrt{\lambda_1(A)^2 - 4}}{2}\)

根据 (3.2) 是 \(\lambda\) 的一个强一致估计量。另一种方法是首先通过 \(\hat{\rho}_1 := \hat{\mu}_1^2 / \hat{\sigma}_1^2\) 和 \(\hat{\rho}_{k+1} := \hat{\lambda}^2(1 - \mathsf{mmse}(\hat{\rho}_k))\) 对每个 \(k\) 递归定义 \((\hat{\rho}_k)\)。根据 (3.20)，我们可以分别用 \(\hat{\rho}_{k+1}/\hat{\lambda}\) 和 \(\hat{\rho}_{k+1}/\hat{\lambda}^2\) 估计 \(\mu_k, \sigma_k^2\)，并利用这些量如上述方式对每个 \(k\) 定义 \(\hat{g}_k^*\) 从而得到 \(\hat{v}^k, v^{k+1}\)。定理 3.1 和 3.5 的理论保证可以相当直接地扩展到经验 Bayes-AMP；详情见 Montanari 和 Venkataramanan (2021, 引理 G.1)。

### 稀疏信号恢复：

为了给出另一个示例，说明 AMP 过程 (3.3) 可以适当特化，假设 V 的精确分布 \(\pi\) 未知，但对于某个固定 \(s \in (0, 1)\) 和每个 \(n \in \mathbb{N}\)，已知峰值 \(v \equiv v(n)\) 最多有 \(sn\) 个非零项。这意味着 \(\pi\) 满足 \(\pi(\{0\}) \ge 1 - s\)。与经典稀疏向量去噪理论（Donoho 和 Johnstone, 1994, 1998; Montanari, 2012, 第 9.3 节）一致，我们可以取 \((g_k)_{k \in \mathbb{N}_0}\) 为一系列软阈值函数

```
g_k(y) = \text{ST}_{t_k}(y) := \text{sgn}(y)(|y| - t_k)_+ ,
```

这样 AMP 算法 (3.3) 变为

```
\hat{v}^k = \text{ST}_{t_k}(v^k), \quad b_k = \frac{1}{n} \sum_{i=1}^n \mathbb{1}_{\{\hat{v}_i^k \neq 0\}} \equiv \frac{\|\hat{v}^k\|_0}{n}, \\
v^{k+1} = A\hat{v}^k - b_k \hat{v}^{k-1} \quad \text{for } k \in \mathbb{N}_0. (3.26)
```

当每个阈值 \(t_k \in (0, \infty)\) 根据 \(\lambda\) 和状态演化参数 \(\sigma_k\)（或其一致估计量）适当选择时，Montanari 和 Venkataramanan (2021) 建立了有效信噪比 \(\rho_k = (\mu_k/\sigma_k)^2\) 的下界，该下界在满足 \(\pi(\{0\}) \ge 1 - s\) 的分布 \(\pi\) 类上均匀成立。结合推论 3.2，该分析对满足 (M1) 的任何 \(ns\)-稀疏峰值序列 \(v \equiv v(n)\) 的 (3.26) 性能提供了理论保证；见上述论文中的命题 2.1。

我们还提到，Barbier _等人_ (2020) 最近在渐近设置中建立了稀疏信号恢复的统计和计算极限，其中 \(v \equiv v(n)\) 的非零项期望数是 \(n\) 的次线性函数。具体地，对于每个 \(n\)，\(v\) 的项独立地从前验 \(\pi_n\) 中绘制，其中 \(\pi_n(\{0\}) \ge 1 - s_n\) 且 \(s_n \to 0\) 当 \(n \to \infty\)。在此设置中，分析使用了 AMP 主定理的有限样本版本（见备注 A.3）。


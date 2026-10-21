

```
# lambda is alpha !
mod = lm.Lasso(alpha=.1)

# Fit models on dataset
n_features, r2_train, r2_test, snr = fit_on_increasing_size(model=mod)

argmax = n_features[np.argmax(r2_test)]

# plot
fig, axis = plt.subplots(1, 2, figsize=(9, 3))

# Left pane: all features
plot_r2_snr(n_features, r2_train, r2_test, argmax, snr, axis[0])

# Right pane: Zoom on 200 first features
plot_r2_snr(n_features[n_features <= 200],
            r2_train[n_features <= 200], r2_test[n_features <= 200],
            argmax,
            snr[n_features <= 200],
            axis[1])
plt.tight_layout()
```

![](img/c2ad4b400bf63af9804b2d44510f76a6_182_0.png)

![](img/c2ad4b400bf63af9804b2d44510f76a6_182_1.png)

## 12.5.1 ℓ₁ 范数的稀疏性

### 奥卡姆剃刀

奥卡姆剃刀（英文也写作 Ockham’s razor，拉丁语为 lex parsimoniae，意为“简约法则”）是一种解决问题的原则，由奥卡姆的威廉（1287-1347）提出，他是一位英国方济各会修士、经院哲学家和神学家。该原则可解释为：在相互竞争的假设中，应当选择假设最少的那一个。

### 简约原则

两个相互竞争的理论中，更简单的那个应被优先选择。简约的定义：符合奥卡姆剃刀精神的解释经济性。

在损失相近的候选模型中，选择最简单的模型：

- 选择系数向量最小的模型，即 β 的 ℓ₂（‖β‖₂）或 ℓ₁（‖β‖₁）范数最小，也就是施加 ℓ₂ 或 ℓ₁ 惩罚。另见偏差-方差权衡。
- 选择使用预测变量数量最少的模型。换句话说，选择许多预测变量权重为零的模型。有两种方法可以实现： (i) 在学习算法应用之前，将特征选择作为预处理步骤执行；或 (ii) 将特征选择过程嵌入到学习过程中。

### 基于稀疏性的惩罚，或使用 ℓ₁ 惩罚的嵌入式特征选择

基于 ℓ₁ 范数的惩罚会促进**稀疏性**（分散、不密集）：它迫使许多系数恰好为零。这也使得系数向量变得分散。

下图展示了在系数向量 ℓ₁ 范数约束下的 OLS 损失。也就是说，它展示了以下优化问题：

minimize_β ‖y − Xβ‖₂²
subject to ‖β‖₁ ≤ 1.

![](img/c2ad4b400bf63af9804b2d44510f76a6_183_0.png)

图 12.2：L1 范数的稀疏性

## 12.5.2 优化问题

*本节待补充*

- 不再有闭式解。
- 凸但不可微。
- 需要特定的优化算法，例如快速迭代收缩阈值算法（FISTA）：Amir Beck 和 Marc Teboulle，*A Fast Iterative Shrinkage-Thresholding Algorithm for Linear Inverse Problems* SIAM J. Imaging Sci., 2009.

## 12.6 弹性网络回归（ℓ₂-ℓ₁-正则化）

弹性网络估计器结合了 ℓ₁ 和 ℓ₂ 惩罚，得到如下问题

Enet(β) = ||y − Xᵀβ||₂² + α (ρ ||β||₁ + (1 − ρ) ||β||₂²), (12.14)

其中 α 作为全局惩罚，ρ 作为 ℓ₁/ℓ₂ 比率。

### 12.6.1 理由

- 如果存在高度相关变量的分组，Lasso 往往会任意地从每组中只选择一个变量。这类模型难以解释，因为与结果强相关的协变量并未包含在预测模型中。相反，弹性网络会鼓励分组效应，即强相关的预测变量往往一起被选入或一起被排除在模型之外。
- 对真实数据和模拟研究的研究表明，弹性网络通常优于 Lasso，同时具有类似的稀疏表示特性。

```
import matplotlib.pyplot as plt
import numpy as np
import sklearn.linear_model as lm

mod = lm.ElasticNet(alpha=.5, l1_ratio=.5)

# Fit models on dataset
n_features, r2_train, r2_test, snr = fit_on_increasing_size(model=mod)

argmax = n_features[np.argmax(r2_test)]

# plot
fig, axis = plt.subplots(1, 2, figsize=(9, 3))

# Left pane: all features
plot_r2_snr(n_features, r2_train, r2_test, argmax, snr, axis[0])

# Right pane: Zoom on 100 first features
plot_r2_snr(n_features[n_features <= 100],
            r2_train[n_features <= 100], r2_test[n_features <= 100],
            argmax,
            snr[n_features <= 100],
            axis[1])
plt.tight_layout()
```

![](img/c2ad4b400bf63af9804b2d44510f76a6_185_0.png)

![](img/c2ad4b400bf63af9804b2d44510f76a6_185_1.png)

其中 **X**_c 是 $(N \times P)$ 维数据矩阵，按各自均值中心化：

$$\boldsymbol{X}_c = \begin{bmatrix} \boldsymbol{X}_0 - \boldsymbol{\mu}_0 \\ \boldsymbol{X}_1 - \boldsymbol{\mu}_1 \end{bmatrix},$$

其中 **X**_0 和 **X**_1 分别是类别 $C_0$ 和 $C_1$ 的 $(N_0 \times P)$ 和 $(N_1 \times P)$ 样本矩阵。

令 $\boldsymbol{S}_B$ 为“类间”散布矩阵，由下式给出

$$\boldsymbol{S}_B = (\boldsymbol{\mu}_1 - \boldsymbol{\mu}_0)(\boldsymbol{\mu}_1 - \boldsymbol{\mu}_0)^T.$$

特征的线性组合 $\boldsymbol{w}^T x$ 的均值为 $\boldsymbol{w}^T \mu_i$（$i = 0,1$），方差为 $\boldsymbol{w}^T \boldsymbol{X}_c^T \boldsymbol{X}_c \boldsymbol{w}$。Fisher 将这两个分布之间的分离度定义为类间方差与类内方差之比：

$F_{\text{Fisher}}(\boldsymbol{w}) = \frac{\sigma^2_{\text{between}}}{\sigma^2_{\text{within}}}$ (13.3)

$= \frac{(\boldsymbol{w}^T \boldsymbol{\mu}_1 - \boldsymbol{w}^T \boldsymbol{\mu}_0)^2}{\boldsymbol{w}^T \boldsymbol{X}_c^T \boldsymbol{X}_c \boldsymbol{w}}$ (13.4)

$= \frac{(\boldsymbol{w}^T (\boldsymbol{\mu}_1 - \boldsymbol{\mu}_0))^2}{\boldsymbol{w}^T \boldsymbol{X}_c^T \boldsymbol{X}_c \boldsymbol{w}}$ (13.5)

$= \frac{\boldsymbol{w}^T (\boldsymbol{\mu}_1 - \boldsymbol{\mu}_0)(\boldsymbol{\mu}_1 - \boldsymbol{\mu}_0)^T \boldsymbol{w}}{\boldsymbol{w}^T \boldsymbol{X}_c^T \boldsymbol{X}_c \boldsymbol{w}}$ (13.6)

$= \frac{\boldsymbol{w}^T \boldsymbol{S}_B \boldsymbol{w}}{\boldsymbol{w}^T \boldsymbol{S}_W \boldsymbol{w}}.$ (13.7)

## 13.1.1 Fisher 最大判别投影

在两类情况下，最大分离是通过使用马氏距离度量 $\boldsymbol{S}_W^{-1}$ 投影到 $(\boldsymbol{\mu}_1 - \boldsymbol{\mu}_0)$ 上实现的，因此

$$\boldsymbol{w} \propto \boldsymbol{S}_W^{-1}(\boldsymbol{\mu}_1 - \boldsymbol{\mu}_0).$$

### 证明

对 $F_{\text{Fisher}}(w)$ 关于 $w$ 求导，得到

$$\nabla_{\boldsymbol{w}} F_{\text{Fisher}}(\boldsymbol{w}) = 0$$

$$\nabla_{\boldsymbol{w}} \left( \frac{\boldsymbol{w}^T \boldsymbol{S}_B \boldsymbol{w}}{\boldsymbol{w}^T \boldsymbol{S}_W \boldsymbol{w}} \right) = 0$$

$$(\boldsymbol{w}^T \boldsymbol{S}_W \boldsymbol{w})(2 \boldsymbol{S}_B \boldsymbol{w}) - (\boldsymbol{w}^T \boldsymbol{S}_B \boldsymbol{w})(2 \boldsymbol{S}_W \boldsymbol{w}) = 0$$

$(\boldsymbol{w}^T \boldsymbol{S}_W \boldsymbol{w})(\boldsymbol{S}_B \boldsymbol{w}) = (\boldsymbol{w}^T \boldsymbol{S}_B \boldsymbol{w})(\boldsymbol{S}_W \boldsymbol{w})$

$$\boldsymbol{S}_B \boldsymbol{w} = \frac{\boldsymbol{w}^T \boldsymbol{S}_B \boldsymbol{w}}{\boldsymbol{w}^T \boldsymbol{S}_W \boldsymbol{w}} (\boldsymbol{S}_W \boldsymbol{w})$$

$$\boldsymbol{S}_B \boldsymbol{w} = \lambda (\boldsymbol{S}_W \boldsymbol{w})$$

$$\boldsymbol{S}_W^{-1} \boldsymbol{S}_B \boldsymbol{w} = \lambda \boldsymbol{w}.$$

由于我们不关心 $w$ 的大小，只关心其方向，因此我们将标量因子 $(w^T S_B w)/(w^T S_W w)$ 替换为 $\lambda$。

在多类情况下，解 $w$ 由 $\boldsymbol{S}_W^{-1} \boldsymbol{S}_B$ 的对应于 $K-1$ 个最大特征值的特征向量确定。

然而，在两类情况下（其中 $S_B = (\mu_1 - \mu_0)(\mu_1 - \mu_0)^T$），很容易证明 $w = S_W^{-1}(\mu_1 - \mu_0)$ 是 $S_W^{-1} S_B$ 的唯一特征向量：

$S_W^{-1}(\mu_1 - \mu_0)(\mu_1 - \mu_0)^T w = \lambda w$

$S_W^{-1}(\mu_1 - \mu_0)(\mu_1 - \mu_0)^T S_W^{-1}(\mu_1 - \mu_0) = \lambda S_W^{-1}(\mu_1 - \mu_0)$

其中这里的 $\lambda = (\mu_1 - \mu_0)^T S_W^{-1}(\mu_1 - \mu_0)$。这导致了结果

$w \propto S_W^{-1}(\mu_1 - \mu_0)$.

## 13.1.2 分离超平面

分离超平面是一个 $P-1$ 维的超曲面，与投影向量 $w$ 正交。关于如何找到平面沿 $w$ 方向的起点，或等价地，决定一个点应被分类为属于 $C_0$ 还是 $C_1$ 的分类阈值，并没有单一的最佳方法。但是，如果投影点具有大致相同的分布，则阈值可以选为两个均值投影之间的正中间超平面，即

$T = w \cdot \frac{1}{2}(\mu_1 - \mu_0)$.

```
%matplotlib inline
import warnings
warnings.filterwarnings(action='once')
```

## 13.2 线性判别分析（LDA）

线性判别分析（LDA）是 Fisher 线性判别的一种概率化推广。它使用贝叶斯规则，根据类别的先验概率来确定阈值。

- 首先计算给定类别 $C_k$ 时 $x$ 的类条件分布：$p(x|C_k) = \mathcal{N}(x|\mu_k, S_W)$。其中 $\mathcal{N}(x|\mu_k, S_W)$ 是定义在 P 维连续变量向量 $x$ 上的多元高斯分布，由 $\mathcal{N}(x|\mu_k, S_W) = \frac{1}{(2\pi)^{P/2}|S_W|^{1/2}} \exp\{-\frac{1}{2}(x - \mu_k)^T S_W^{-1}(x - \mu_k)\}$ 给出
- 估计类别 $k$ 的先验概率：$p(C_k) = N_k/N$。
- 使用贝叶斯规则，将条件分布与先验结合，计算后验概率（即给定样本时每个类别的概率）：


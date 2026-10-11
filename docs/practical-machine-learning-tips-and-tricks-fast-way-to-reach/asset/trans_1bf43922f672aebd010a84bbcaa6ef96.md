
# 核方法

## 核函数与特征映射

因此我们看到，位网格中的各个部分可以通过计算由特征向量隐式定义的一些特征向量的内积来确定。如果 $D = 1$，并且我们利用这个位来表征高斯过程（见第 15 章 TODO），我们得到 Ornstein-Uhlenbeck 过程，它描述了经历布朗运动的粒子的速度（对应的函数是连续但不可微的，因此非常锯齿状）。

一般来说，如果核是 Mercer 核，则存在一个将 $x \in \mathcal{X}$ 映射到 $\mathbb{R}^D$ 的函数 $\phi$，使得

$$
\kappa(x, x') = \phi(x)^T \phi(x') \tag{14.9}
$$

其中 $\phi$ 依赖于 $\kappa$ 的特征元素（因此 $D$ 是一个潜在的无限维空间）。

### 字符串核

令 $\phi_s(x)$ 表示子串 $s$ 在字符串 $x$ 中出现的次数。

我们将两个字符串 $x$ 和 $x'$ 之间的核定义为

$$
\kappa(x, x') = \sum_{s \in A^*} w_s \phi_s(x) \phi_s(x') \tag{14.13}
$$

其中 $w_s \ge 0$，且 $A^*$ 是字母表 $A$ 上所有可能字符串（任意长度）的集合（这被称为 Kleene 星算子）。这是一个 Mercer 核，并且可以在 $O(|x| + |x'|)$ 时间内计算（对于特定的权重 $\{w_s\}$ 设置），利用后缀树（Leslie et al. 2003; Vishwanathan and Smola 2003; Shawe-Taylor and Cristianini 2004）。

对于多项式核 $\kappa(x, x') = (\gamma x^T x' + r)^M$（其中 $r > 0$），可以证明相应的特征向量 $\phi(x)$ 将包含所有最高 $M$ 次的项。例如，如果 $M = 2, \gamma = r = 1$ 且 $x, x' \in \mathbb{R}^2$，我们有

$$
(x^T x' + 1)^2 = (1 + x_1 x'_1 + x_2 x'_2)^2
$$

$$
\begin{aligned}
\phi(x) &= (1, \sqrt{2}x_1, \sqrt{2}x_2, x_1^2, x_2^2, \sqrt{2}x_1 x_2) \\
\kappa(x, x') &= \phi(x)^T \phi(x')
\end{aligned}
$$

在高斯核的情况下，特征映射存在于无限维空间中。在这种情况下，显式表示特征向量显然是不可行的。

通常，证明一个核是 Mercer 核是困难的，需要泛函分析的方法。然而，可以证明可以通过一组标准规则从更简单的核构建新的 Mercer 核。例如，如果 $\kappa_1$ 和 $\kappa_2$ 都是 Mercer 核，那么 $\kappa(x, x') = \kappa_1(x, x') + \kappa_2(x, x')$ 也是 Mercer 核（详见 Schoelkopf and Smola 2002）。

如果我们只考虑固定长度 $k$ 的字符串，我们得到 $k$ 谱核。这已被用于将蛋白质分类到 SCOP 超家族中（Leslie et al. 2003）。

### 金字塔匹配核

### 从概率生成模型导出的核

假设我们有一个特征向量的概率生成模型 $p(x|\theta)$。然后有几种方法可以利用该模型定义核函数，从而使模型适合判别任务。我们在下面简述两种方法。

#### 概率乘积核

$$
\kappa(x_i, x_j) = \int p(x|x_i)^\rho p(x|x_j)^\rho dx \tag{14.14}
$$

其中 $\rho > 0$，且 $p(x|x_i)$ 通常由 $p(x|\hat{\theta}(x_i))$ 近似，其中 $\hat{\theta}(x_i)$ 是利用单个数据向量计算的参数估计。这被称为概率乘积核。虽然拟合单个数据点的模型似乎很奇怪，但请记住，拟合的模型仅用于衡量两个对象的相似性。具体来说，如果我们将模型拟合到 $x_i$，然后模型认为 $x_j$ 很可能，这意味着 $x_i$ 和 $x_j$ 是相似的。

例如，假设 $p(x|\theta) \sim \mathcal{N}(\mu, \sigma^2 I)$，其中 $\sigma^2$ 是固定的。如果 $\rho = 1$，且我们使用 $\hat{\mu}(x_i) = x_i$ 和 $\hat{\mu}(x_j) = x_j$，我们发现（Jebara et al. 2004, p825）

$$
\kappa(x_i, x_j) = \frac{1}{(4\pi\sigma^2)^{D/2}} \exp\left(-\frac{\|x_i - x_j\|^2}{4\sigma^2}\right) \tag{14.15}
$$

这（在常数因子下）是 RBF 核。似乎可以为各种生成模型计算公式 14.14，包括带有潜在变量的模型，如 HMM。这提供了一种在变长序列上定义核的方法。此外，该方法即使序列是实值向量也适用，这与第 14.2.6 节的字符串核不同。详见 (Jebara et al. 2004)。

#### Fisher 核

利用生成模型定义核的一种更有效方法是使用 Fisher 核，其定义如下：

$$
\kappa(x_i, x_j) = g(x_i)^T F^{-1} g(x_j) \tag{14.16}
$$

其中 $g$ 是对数似然的梯度（或得分向量），在 MLE $\hat{\theta}$ 处评估：

$$
g(x) \triangleq \frac{d \log p(x|\theta)}{d\theta} \Big|_{\hat{\theta}} \tag{14.17}
$$

而 $F$ 是 Fisher 信息矩阵，本质上是 Hessian 矩阵：

$$
F \triangleq \frac{\partial^2}{\partial\theta\partial\theta^T} \log p(x|\theta) \Big|_{\hat{\theta}} \tag{14.18}
$$

注意 $\hat{\theta}$ 是所有数据的函数，因此 $x_i$ 和 $x_j$ 的相似性是相对于所有数据计算的。同样，注意我们只需要拟合一个模型。

## 在 GLM 中使用核

### 核机器

我们将核机器定义为输入特征向量具有以下形式的 GLM：

$$
\phi(x) = (\kappa(x, \mu_1), \dots, \kappa(x, \mu_K)) \tag{14.19}
$$

其中 $\mu_k \in \mathcal{X}$ 是一组 $K$ 个中心点。如果 $\kappa$ 是 RBF 核，这被称为 RBF 网络。我们将在下文讨论选择 $\mu_k$ 参数的方法。

我们将公式 14.19 称为核化特征向量。注意在这种方法中，核不必是 Mercer 核。我们可以通过定义 $p(y|x,\theta) = \text{Ber}(y|w^T \phi(x))$ 将核化特征向量用于逻辑回归。这提供了一种定义非线性决策边界的简单方法。例如，见图 14.1。我们也可以通过定义 $p(y|x,\theta) = \mathcal{N}(y|w^T \phi(x), \sigma^2)$ 在线性回归模型中使用核化特征向量。

### L1VM、RVM 和其他稀疏向量机

核机器的主要问题是：我们如何选择中心点 $\mu_k$？我们可以使用稀疏向量机，如 `L1VM`、`L2VM`、`RVM`、`SVM`。

## 核技巧

与其将特征向量显式表示为核函数的形式 $\phi(x) = (\kappa(x, x_1), \dots, \kappa(x, x_N))$，我们可以保留原始特征向量 $x$，但修改算法，使其将所有形式为 $\langle x_i, x_j \rangle$ 的内积替换为对核函数 $\kappa(x_i, x_j)$ 的调用。这被称为核技巧。事实证明，许多算法都可以通过这种方式核化。我们在下面给出几个例子。注意，为了使该技巧生效，我们要求核必须是 Mercer 核。

### 核化 KNN

欧几里得距离可以展开为

$$
\|x_i - x_j\|^2 = \langle x_i, x_i \rangle + \langle x_j, x_j \rangle - 2 \langle x_i, x_j \rangle \tag{14.20}
$$

然后，通过将所有 $\langle x_i, x_j \rangle$ 替换为 $\kappa(x_i, x_j)$，我们得到核化 KNN。

### 核化 K-medoids 聚类

K-medoids 算法类似于 K-means（见第 11.4.4 节），但不是用分配给该簇的所有数据向量的均值来表示每个簇的中心，而是使每个中心成为数据向量本身之一。因此我们始终处理整数索引，而不是数据对象。

该算法可以通过使用公式 14.20 替换距离计算来核化。

### 核化岭回归

将核技巧应用于基于距离的方法是直接的。将其应用于参数模型（如岭回归）则不那么明显。尽管如此，这是可以做到的，我们现在将解释。这将作为研究 SVM 的良好准备。

#### 基本问题

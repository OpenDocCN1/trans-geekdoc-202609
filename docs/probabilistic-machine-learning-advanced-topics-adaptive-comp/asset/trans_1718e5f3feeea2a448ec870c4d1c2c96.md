

- 在某些正则性条件下，指数族是具有有限尺寸充分统计量的唯一分布族，如第 2.4.5 节所述。
- 指数族的所有成员都有一个**共轭先验** [DY79]，这简化了参数的贝叶斯推断，如第 3.4 节所述。

## 2.4.1 定义

考虑一族由 $\eta \in \mathbb{R}^K$ 参数化的概率分布，其在 $\mathcal{X}^D \subseteq \mathbb{R}^D$ 上具有固定支撑集。若分布 $p(x|\eta)$ 的密度可按以下方式表示，则称其属于**指数族**：

```
$p(x|\eta) \triangleq \frac{1}{Z(\eta)}h(x)\exp[\eta^T\mathcal{T}(x)] = h(x)\exp[\eta^T\mathcal{T}(x) - A(\eta)]$ (2.160)
```

其中，$h(x)$ 是一个缩放常数（也称为**基测度**，通常为 1），$\mathcal{T}(x) \in \mathbb{R}^K$ 是**充分统计量**，$\eta$ 是**自然参数**或**规范参数**，$Z(\eta)$ 是称为**配分函数**的归一化常数，而 $A(\eta) = \log Z(\eta)$ 是**对数配分函数**。在第 2.4.3 节中，我们表明 $A$ 是在凸集 $\Omega \triangleq \{\eta \in \mathbb{R}^K : A(\eta) < \infty\}$ 上的凸函数。

如果自然参数相互独立，则很方便。形式上，如果不存在 $\eta \in \mathbb{R}^K \\ \{0\}$ 使得 $\eta^T\mathcal{T}(x) = 0$，则称指数族为**极小**。在多项分布的情况下，由于参数上的和为一约束，最后一个条件可能会被违反；不过，如下所示，使用 $K-1$ 个独立参数很容易重新参数化该分布。

通过定义 $\eta = f(\phi)$ 可以将等式 (2.160) 推广，其中 $\phi$ 是另一组（可能更小）的参数。在此情况下，分布形式为

```
$p(x|\phi) = h(x) \exp[f(\phi)^T\mathcal{T}(x) - A(f(\phi))]$ (2.161)
```

如果从 $\phi$ 到 $\eta$ 的映射是非线性的，我们称之为**曲线指数族**。如果 $\eta = f(\phi) = \phi$，则模型被认为处于**规范形式**。此外，如果 $\mathcal{T}(x) = x$，则称其为**自然指数族**或 **NEF**。在此情况下，可以写成

```
$p(x|\eta) = h(x) \exp[\eta^T x - A(\eta)]$ (2.162)
```

我们将**矩参数**定义为充分统计量向量的均值：

```
$m = \mathbb{E}[\mathcal{T}(x)]$ (2.163)
```

下面我们将看到一些示例。

## 2.4.2 示例

在本节中，我们考虑指数族中分布的一些常见示例。每个示例对应定义 $h(x)$ 和 $\mathcal{T}(x)$ 的不同方式（因为 $Z$ 进而 $A$ 都可由 $h$ 和 $\mathcal{T}$ 得出）。

### 2.4.2.1 伯努利分布

伯努利分布可以按指数族形式写成如下：

```
$$
\text{Ber}(x|\mu) = \mu^x(1-\mu)^{1-x} \tag{2.164}
= \exp[x \log(\mu) + (1-x) \log(1-\mu)] \tag{2.165}
= \exp[\mathcal{T}(x)^\top \boldsymbol{\eta}] \tag{2.166}
$$
```

其中 \(\mathcal{T}(x) = [\mathbb{I}(x=1), \mathbb{I}(x=0)]\)，\(\boldsymbol{\eta} = [\log(\mu), \log(1-\mu)]$，且 \(\mu\) 是均值参数。不过，这是一种**过完表示**，因为特征之间存在线性相关。

我们可以这样看出：

```
$$
\mathbf{1}^\top \mathcal{T}(x) = \mathbb{I}(x=0) + \mathbb{I}(x=1) = 1 \tag{2.167}
$$
```

如果表示是过完的，\(\boldsymbol{\eta}\) 则不是唯一可识别的。通常使用**极小表示**，这意味着分布关联着唯一的 \(\boldsymbol{\eta}\)。在此情况下，我们可以定义

```
$$
\text{Ber}(x|\mu) = \exp \left[ x \log \left( \frac{\mu}{1-\mu} \right) + \log(1-\mu) \right] \tag{2.168}
$$
```

我们可以通过定义将其写成指数族形式

```
$$
\eta = \log \left( \frac{\mu}{1-\mu} \right) \tag{2.169}
\mathcal{T}(x) = x \tag{2.170}
A(\eta) = -\log(1-\mu) = \log(1 + e^\eta) \tag{2.171}
h(x) = 1 \tag{2.172}
$$
```

我们可以使用规范参数 \(\eta\) 来恢复均值参数 \(\mu\)

```
$$
\mu = \sigma(\eta) = \frac{1}{1+e^{-\eta}} \tag{2.173}
$$
```

这就是我们熟知的 logistic（Sigmoid）函数。

### 2.4.2.2 分类分布

我们可以将具有 $K$ 个类别的离散分布表示如下（其中 $x_k = \mathbb{I}(x = k)$）：

\(\text{Cat}(x|\boldsymbol{\mu}) = \prod_{k=1}^K \mu_k^{x_k} = \exp \left[ \sum_{k=1}^K x_k \log \mu_k \right]\) (2.174)
\(= \exp \left[ \sum_{k=1}^{K-1} x_k \log \mu_k + \left( 1 - \sum_{k=1}^{K-1} x_k \right) \log(1 - \sum_{k=1}^{K-1} \mu_k) \right]\) (2.175)
\(= \exp \left[ \sum_{k=1}^{K-1} x_k \log \left( \frac{\mu_k}{1 - \sum_{j=1}^{K-1} \mu_j} \right) + \log(1 - \sum_{k=1}^{K-1} \mu_k) \right]\) (2.176)
\(= \exp \left[ \sum_{k=1}^{K-1} x_k \log \left( \frac{\mu_k}{\mu_K} \right) + \log \mu_K \right]\) (2.177)

其中 \(\mu_K = 1 - \sum_{k=1}^{K-1} \mu_k\)。我们可以将其写成指数族形式如下：

\(\text{Cat}(x|\boldsymbol{\eta}) = \exp(\boldsymbol{\eta}^\mathsf{T}\mathcal{T}(x) - A(\boldsymbol{\eta}))\) (2.178)
\(\boldsymbol{\eta} = [\log \frac{\mu_1}{\mu_K}, \dots, \log \frac{\mu_{K-1}}{\mu_K}]\) (2.179)
\(A(\boldsymbol{\eta}) = -\log(\mu_K)\) (2.180)
\(\mathcal{T}(x) = [\mathbb{I}(x = 1), \dots, \mathbb{I}(x = K - 1)]\) (2.181)
\(h(x) = 1\) (2.182)

我们可以使用规范参数来恢复均值参数

\(\mu_k = \frac{e^{\eta_k}}{1 + \sum_{j=1}^{K-1} e^{\eta_j}}\) (2.183)

如果定义 \(\eta_K = 0\)，则可以重写如下：

\(\mu_k = \frac{e^{\eta_k}}{\sum_{j=1}^K e^{\eta_j}}\) (2.184)

对于 \(k = 1 : K\)。因此 \(\boldsymbol{\mu} = \text{softmax}(\boldsymbol{\eta})\)，其中 softmax 是方程 (15.136) 中的 softmax 或多项式 logit 函数。由此，我们得出

\(\mu_K = 1 - \frac{\sum_{k=1}^{K-1} e^{\eta_k}}{1 + \sum_{k=1}^{K-1} e^{\eta_k}} = \frac{1}{1 + \sum_{k=1}^{K-1} e^{\eta_k}}\) (2.185)

因此

\(A(\boldsymbol{\eta}) = -\log(\mu_K) = \log \left( \sum_{k=1}^K e^{\eta_k} \right)\) (2.186)

### 2.4.2.3 一元高斯分布

一元高斯分布通常写作如下：

$$\mathcal{N}(x|\mu, \sigma^2) = \frac{1}{(2\pi\sigma^2)^{\frac{1}{2}}} \exp[-\frac{1}{2\sigma^2}(x - \mu)^2]\tag{2.187}$$

$$= \frac{1}{(2\pi)^{\frac{1}{2}}} \exp[\frac{\mu}{\sigma^2}x - \frac{1}{2\sigma^2}x^2 - \frac{1}{2\sigma^2}\mu^2 - \log \sigma]\tag{2.188}$$

我们可以通过定义将其写成指数族形式

$$\boldsymbol{\eta} = \begin{pmatrix} \mu/\sigma^2 \\ -\frac{1}{2\sigma^2} \end{pmatrix}\tag{2.189}$$

$$\mathcal{T}(x) = \begin{pmatrix} x \\ x^2 \end{pmatrix}\tag{2.190}$$

$$A(\boldsymbol{\eta}) = \frac{\mu^2}{2\sigma^2} + \log \sigma = \frac{-\eta_1^2}{4\eta_2} - \frac{1}{2} \log(-2\eta_2)\tag{2.191}$$

$$h(x) = \frac{1}{\sqrt{2\pi}}\tag{2.192}$$

矩参数为

$$\mathbf{m} = [\mu, \mu^2 + \sigma^2]\tag{2.193}$$

### 2.4.2.4 固定方差的一元高斯分布

如果固定 $\sigma^2 = 1$，我们可以通过定义将高斯分布写成自然指数族

$$\eta = \mu\tag{2.194}$$

$$\mathcal{T}(x) = x\tag{2.195}$$

$$A(\mu) = \frac{\mu^2}{2\sigma^2} + \log \sigma = \frac{\mu^2}{2}\tag{2.196}$$

$$h(x) = \frac{1}{\sqrt{2\pi}} \exp[-\frac{x^2}{2}] = \mathcal{N}(x|0, 1)\tag{2.197}$$

注意，在此示例中，基测度 \(h(x)\) 不是常数。

### 2.4.2.5 多元高斯分布

通常使用均值向量 \(\mu\) 和协方差矩阵 \(\Sigma\) 来参数化多元正态分布（MVN）。相应的概率密度函数由以下给出

\(\begin{aligned} \mathcal{N}(x|\mu, \Sigma) &= \frac{1}{(2\pi)^{D/2}\sqrt{\text{det}(\Sigma)}} \exp \left( -\frac{1}{2}x^T\Sigma^{-1}x + x^T\Sigma^{-1}\mu - \frac{1}{2}\mu^T\Sigma^{-1}\mu \right) \\ &= c \exp \left( x^T\Sigma^{-1}\mu - \frac{1}{2}x^T\Sigma^{-1}x \right) \\ c \triangleq \frac{\exp(-\frac{1}{2}\mu^T\Sigma^{-1}\mu)}{(2\pi)^{D/2}\sqrt{\text{det}(\Sigma)}} \end{aligned}\)

不过，我们也可以使用规范参数或自然参数（也称为信息形式）来表示高斯分布：

\(\begin{aligned} \Lambda &= \Sigma^{-1} \\ \xi &= \Sigma^{-1}\mu \\ \mathcal{N}_c(x|\xi, \Lambda) \triangleq c' \exp \left( x^T\xi - \frac{1}{2}x^T\Lambda x \right) \\ c' &= \frac{\exp(-\frac{1}{2}\xi^T\Lambda^{-1}\xi)}{(2\pi)^{D/2}\sqrt{\text{det}(\Lambda^{-1})}} \end{aligned}\)

这里我们使用符号 \(\mathcal{N}_c()\) 将其与标准参数化 \(\mathcal{N}()\) 区分开来。在此，\(\Lambda\) 被称为精度矩阵，\(\xi\) 是精度加权均值向量。

我们可以将其转换为指数族记法，如下：

\(\begin{aligned} \mathcal{N}_c(x|\xi, \Lambda) &= \underbrace{(2\pi)^{-D/2}}_{h(x)} \underbrace{\exp \left[ \frac{1}{2} \log |\Lambda| - \frac{1}{2} \xi^T \Lambda^{-1} \xi \right]}_{g(\eta)} \exp \left[ -\frac{1}{2} x^T \Lambda x + x^T \xi \right] \\ &= h(x)g(\eta) \exp \left[ -\frac{1}{2} x^T \Lambda x + x^T \xi \right] \\ &= h(x)g(\eta) \exp \left[ -\frac{1}{2} (\sum_{ij} x_i x_j \Lambda_{ij}) + x^T \xi \right] \\ &= h(x)g(\eta) \exp \left[ -\frac{1}{2} \text{vec}(\Lambda)^T \text{vec}(xx^T) + x^T \xi \right] \\ &= h(x) \exp [\eta^T T(x) - A(\eta)] \end{aligned}\)


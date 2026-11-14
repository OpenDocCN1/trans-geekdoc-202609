

其中

$$h(x) = (2\pi)^{-D/2}$$

$$\eta = [\xi; -\frac{1}{2}\text{vec}(\Lambda)] = [\Sigma^{-1}\mu; -\frac{1}{2}\text{vec}(\Sigma^{-1})]$$

$$\mathcal{T}(x) = [x; \text{vec}(xx^\mathsf{T})]$$

$$A(\eta) = -\log g(\eta) = -\frac{1}{2} \log |\Lambda| + \frac{1}{2} \xi^\mathsf{T} \Lambda^{-1} \xi$$

由此可见，均值（矩）参数由以下公式给出

$$m = \mathbb{E}[\mathcal{T}(x)] = [\mu; \mu\mu^\mathsf{T} + \Sigma]$$

（注意，上述表示并非最小表示，因为 \(\Lambda\) 是对称矩阵。我们可以通过对每个矩阵使用其上半部分或下半部分来转换为最小形式。）

## 2.4.2.6 反例

并非所有感兴趣的分布都属于指数族。例如，Student 分布（第 2.2.2.3 节）不属于指数族，因为其概率密度函数（pdf，公式 (2.30)）不具有所需的形式。（不过，有一种推广形式，称为 \(\phi\)-指数族 [Nau04; Tsa88]，它确实包含了 Student 分布。）

作为一个更微妙的例子，考虑均匀分布，\(Y \sim \text{Unif}(\theta_1, \theta_2)\)。其概率密度函数形式为

$$p(y|\theta) = \frac{1}{\theta_2 - \theta_1} \mathbb{I}(\theta_1 \le y \le \theta_2)$$

很容易认为这属于指数族，其中 \(h(y) = 1\)、\(\mathcal{T}(y) = \mathbf{0}\) 且 \(Z(\theta) = \theta_2 - \theta_1\)。然而，该分布的支撑集（即值的集合 \(\mathcal{Y} = \{y : p(y) > 0\}\)）取决于参数 \(\theta\)，这违反了指数族的一个假设。

## 2.4.3 对数配分函数是累积量生成函数

分布的一阶和二阶**累积量**是其均值 \(\mathbb{E}[X]\) 和方差 \(\mathbb{V}[X]\)，而一阶和二阶原点矩是 \(\mathbb{E}[X]\) 和 \(\mathbb{E}[X^2]\)。我们也可以计算高阶累积量（和矩）。指数族的一个重要性质是，对数配分函数的导数可用于生成充分统计量的所有**累积量**。特别是，一阶和二阶累积量由以下公式给出

$$\nabla_\eta A(\eta) = \mathbb{E}[\mathcal{T}(x)]$$

$$\nabla_\eta^2 A(\eta) = \text{Cov}[\mathcal{T}(x)]$$

我们在下文证明此结果。

### 2.4.3.1 均值的推导

为简化起见，我们关注一维情况。对一阶导数，我们有

$$
\begin{align}
\frac{dA}{d\eta} &= \frac{d}{d\eta} \left( \log \int \exp(\eta \mathcal{T}(x)) h(x) dx \right) \label{eq:deriv_mean_1} \\
&= \frac{\frac{d}{d\eta} \int \exp(\eta \mathcal{T}(x)) h(x) dx}{\int \exp(\eta \mathcal{T}(x)) h(x) dx} \label{eq:deriv_mean_2} \\
&= \frac{\int \mathcal{T}(x) \exp(\eta \mathcal{T}(x)) h(x) dx}{\exp(A(\eta))} \label{eq:deriv_mean_3} \\
&= \int \mathcal{T}(x) \exp(\eta \mathcal{T}(x) - A(\eta)) h(x) dx \label{eq:deriv_mean_4} \\
&= \int \mathcal{T}(x) p(x) dx = \mathbb{E} [\mathcal{T}(x)] \label{eq:deriv_mean_5}
\end{align}
$$

例如，考虑伯努利分布。我们有 \(A(\eta) = \log(1 + e^\eta)\)，因此均值由以下公式给出

\(\frac{dA}{d\eta} = \frac{e^\eta}{1 + e^\eta} = \frac{1}{1 + e^{-\eta}} = \sigma(\eta) = \mu\)

### 2.4.3.2 方差的推导

为简化起见，我们关注一维情况。对二阶导数，我们有

$$
\begin{align}
\frac{d^2 A}{d\eta^2} = \frac{d}{d\eta} \int \mathcal{T}(x) \exp(\eta \mathcal{T}(x) - A(\eta)) h(x) dx \label{eq:deriv_var_1} \\
= \int \mathcal{T}(x) \exp(\eta \mathcal{T}(x) - A(\eta)) h(x) (\mathcal{T}(x) - A'(\eta)) dx \label{eq:deriv_var_2} \\
= \int \mathcal{T}(x) p(x) (\mathcal{T}(x) - A'(\eta)) dx \label{eq:deriv_var_3} \\
= \int \mathcal{T}^2(x) p(x) dx - A'(\eta) \int \mathcal{T}(x) p(x) dx \label{eq:deriv_var_4} \\
= \mathbb{E} [\mathcal{T}^2(X)] - \mathbb{E} [\mathcal{T}(x)]^2 = \mathbb{V} [\mathcal{T}(x)] \label{eq:deriv_var_5}
\end{align}
$$

这里我们使用了 \(A'(\eta) = \frac{dA}{d\eta} = \mathbb{E} [\mathcal{T}(x)]\) 这一事实。例如，对于伯努利分布，我们有

\(\frac{d^2 A}{d\eta^2} = \frac{d}{d\eta} (1 + e^{-\eta})^{-1} = (1 + e^{-\eta})^{-2} e^{-\eta}\)

$$
= \frac{e^{-\eta}}{1 + e^{-\eta}} \frac{1}{1 + e^{-\eta}} = \frac{1}{e^\eta + 1} \frac{1}{1 + e^{-\eta}} = (1 - \mu)\mu
$$

### 2.4.3.3 与 Fisher 信息矩阵的联系

在第 3.3.4 节中，我们表明，在某些正则性条件下，Fisher 信息矩阵由以下公式给出

\(\mathbf{F}(\boldsymbol{\eta}) \triangleq \mathbb{E}_{p(\boldsymbol{x}|\boldsymbol{\eta})} [\nabla \log p(\boldsymbol{x}|\boldsymbol{\eta}) \nabla \log p(\boldsymbol{x}|\boldsymbol{\eta})^T] = - \mathbb{E}_{p(\boldsymbol{x}|\boldsymbol{\eta})} [\nabla^2_{\boldsymbol{\eta}} \log p(\boldsymbol{x}|\boldsymbol{\eta})]\)

因此，对于指数族模型，我们有

\(\mathbf{F}(\boldsymbol{\eta}) = - \mathbb{E}_{p(\boldsymbol{x}|\boldsymbol{\eta})} [\nabla^2_{\boldsymbol{\eta}} (\boldsymbol{\eta}^T \mathcal{T}(\boldsymbol{x}) - A(\boldsymbol{\eta}))] = \nabla^2_{\boldsymbol{\eta}} A(\boldsymbol{\eta}) = \text{Cov}[\mathcal{T}(\boldsymbol{x})]\)

因此，对数配分函数的 Hessian 矩阵与 FIM 相同，也与充分统计量的协方差相同。详情见第 3.3.4.6 节。

## 2.4.4 规范（自然）参数与均值（矩）参数

设 \(\Omega\) 为可归一化自然参数的集合：

\(\Omega \triangleq \{ \boldsymbol{\eta} \in \mathbb{R}^K : Z(\boldsymbol{\eta}) < \infty \}\)

如果 \(\Omega\) 是开集，则称指数族为**正则**。可以证明，\(\Omega\) 是一个凸集，且 \(A(\boldsymbol{\eta})\) 是定义在该集合上的凸函数。

在第 2.4.3 节中，我们证明对数配分函数的导数等于充分统计量的均值，即，

\(\boldsymbol{m} = \mathbb{E}[\mathcal{T}(\boldsymbol{x})] = \nabla_{\boldsymbol{\eta}} A(\boldsymbol{\eta})\)

有效矩参数的集合由以下公式给出

\(\mathcal{M} = \{ \boldsymbol{m} \in \mathbb{R}^K : \mathbb{E}_p[\mathcal{T}(\boldsymbol{x})] = \boldsymbol{m} \}\)

对于某些分布 \(p\)。

我们已经看到，可以使用以下公式从自然参数转换为矩参数

\(\boldsymbol{m} = \nabla_{\boldsymbol{\eta}} A(\boldsymbol{\eta})\)

如果该族是最小的，可以证明

\(\boldsymbol{\eta} = \nabla_{\boldsymbol{m}} A^*(\boldsymbol{m})\)

其中 \(A^*(\boldsymbol{m})\) 是 \(A\) 的共轭函数：

\(A^*(\boldsymbol{m}) \triangleq \sup_{\boldsymbol{\eta} \in \Omega} \boldsymbol{\mu}^T \boldsymbol{\eta} - A(\boldsymbol{\eta})\)

因此，算子对 \((\nabla A, \nabla A^*)\) 使我们能够在自然参数 \(\boldsymbol{\eta} \in \Omega\) 和均值参数 \(\boldsymbol{m} \in \mathcal{M}\) 之间来回转换。

供以后参考，请注意，与 \(A\) 和 \(A^*\) 关联的 Bregman 散度（第 5.1.10 节）如下：

\(B_A(\boldsymbol{\lambda}_1 || \boldsymbol{\lambda}_2) = A(\boldsymbol{\lambda}_1) - A(\boldsymbol{\lambda}_2) - (\boldsymbol{\lambda}_1 - \boldsymbol{\lambda}_2)^T \nabla_{\boldsymbol{\lambda}} A(\boldsymbol{\lambda}_2)\)

\(B_{A^*}(\boldsymbol{\mu}_1 || \boldsymbol{\mu}_2) = A(\boldsymbol{\mu}_1) - A(\boldsymbol{\mu}_2) - (\boldsymbol{\mu}_1 - \boldsymbol{\mu}_2)^T \nabla_{\boldsymbol{\mu}} A(\boldsymbol{\mu}_2)\)

## 2.4.5 指数族的极大似然估计

指数族模型的似然函数形式为

$$p(\mathcal{D}|\boldsymbol{\eta}) = \left[ \prod_{n=1}^N h(\mathbf{x}_n) \right] \exp \left( \boldsymbol{\eta}^\mathsf{T} [\sum_{n=1}^N \mathcal{T}(\mathbf{x}_n)] - N A(\boldsymbol{\eta}) \right) \propto \exp \left[ \boldsymbol{\eta}^\mathsf{T} \mathcal{T}(\mathcal{D}) - N A(\boldsymbol{\eta}) \right] \quad (2.242)$$

其中 \(\mathcal{T}(\mathcal{D})\) 为充分统计量：

$$\mathcal{T}(\mathcal{D}) = [\sum_{n=1}^N \mathcal{T}_1(\mathbf{x}_n), \dots, \sum_{n=1}^N \mathcal{T}_K(\mathbf{x}_n)] \quad (2.243)$$

例如，对于伯努利模型，\(\mathcal{T}(\mathcal{D}) = [\sum_n \mathbb{I}(x_n = 1)]\)；对于一维高斯分布，\(\mathcal{T}(\mathcal{D}) = [\sum_n x_n, \sum_n x_n^2]\)。

**Pitman-Koopman-Darmois 定理**指出，在某些正则性条件下，指数族是唯一具有有限充分统计量的分布族。（这里，有限是指大小与数据集大小无关。）换句话说，对于具有自然参数 \(\boldsymbol{\eta}\) 的指数族，我们有

$$p(\mathcal{D}|\boldsymbol{\eta}) = p(\mathcal{T}(\mathcal{D})|\boldsymbol{\eta}) \quad (2.244)$$

我们现在展示如何使用此结果来计算 MLE。对数似然由以下公式给出

$$\log p(\mathcal{D}|\boldsymbol{\eta}) = \boldsymbol{\eta}^\mathsf{T} \mathcal{T}(\mathcal{D}) - N A(\boldsymbol{\eta}) + \text{const} \quad (2.245)$$

由于 \(-A(\boldsymbol{\eta})\) 在 \(\boldsymbol{\eta}\) 中是凹的，且 \(\boldsymbol{\eta}^\mathsf{T}\mathcal{T}(\mathcal{D})\) 在 \(\boldsymbol{\eta}\) 中是线性的，我们看到对数似然是凹函数，因此具有唯一的全局最大值。为了推导这个最大值，我们使用第 2.4.3 节所示的事实，即对数配分函数的导数给出充分统计量向量的期望值：

$$\nabla_{\boldsymbol{\eta}} \log p(\mathcal{D}|\boldsymbol{\eta}) = \nabla_{\boldsymbol{\eta}} \boldsymbol{\eta}^\mathsf{T} \mathcal{T}(\mathcal{D}) - N \nabla_{\boldsymbol{\eta}} A(\boldsymbol{\eta}) = \mathcal{T}(\mathcal{D}) - N \mathbb{E} [\mathcal{T}(\mathbf{x})] \quad (2.246)$$

对于单个数据点，这变为

$$\nabla_{\boldsymbol{\eta}} \log p(\mathbf{x}|\boldsymbol{\eta}) = \mathcal{T}(\mathbf{x}) - \mathbb{E} [\mathcal{T}(\mathbf{x})] \quad (2.247)$$

将公式 (2.246) 中的梯度设为零，我们看到在 MLE 处，充分统计量的经验平均值必须等于模型的理论期望充分统计量，即，\(\hat{\boldsymbol{\eta}}\) 必须满足

$$\mathbb{E} [\mathcal{T}(\mathbf{x})] = \frac{1}{N} \sum_{n=1}^N \mathcal{T}(\mathbf{x}_n) \quad (2.248)$$

这称为**矩匹配**。例如，在伯努利分布中，\(\mathcal{T}(x) = \mathbb{I}(X = 1)\)，因此 MLE 满足

$$\mathbb{E} [\mathcal{T}(x)] = p(X = 1) = \mu = \frac{1}{N} \sum_{n=1}^N \mathbb{I}(x_n = 1) \quad (2.249)$$


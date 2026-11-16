

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_103_0.png)

图 15.1：Sigmoid（logistic）函数的二次下界。以实线红色绘制 $\sigma(x)$ 关于 $x$ 的图。以虚线蓝色绘制 $\psi = 2.5$ 时下界 $L(x, \psi)$ 关于 $x$ 的图。(a) JJ 界。在 $\psi = \pm 2.5$ 处紧。(b) Bohning 界（第 15.1.2.2 节）。在 $\psi = 2.5$ 处紧。由 sigmoid_lower_bounds.py 生成。

Since this is a quadratic function of $\boldsymbol{w}$, we can derive a Gaussian posterior approximation as follows:

由于这是关于 $\boldsymbol{w}$ 的二次函数，我们可以按如下方式推导高斯后验近似：

$q(\boldsymbol{w}|\boldsymbol{\psi}) = \mathcal{N}(\boldsymbol{w}|\boldsymbol{\mu}_N, \mathbf{V}_N) \tag{15.9}$
$\boldsymbol{\mu}_N = \mathbf{V}_N \left( \mathbf{V}_0^{-1} \boldsymbol{\mu}_0 + \sum_{n=1}^N (y_n - 1/2) \mathbf{x}_n \right) \tag{15.10}$
$\mathbf{V}_N^{-1} = \mathbf{V}_0^{-1} + 2 \sum_{n=1}^N \lambda(\psi_n)\mathbf{x}_n \mathbf{x}_n^T \tag{15.11}$

This is more flexible than a Laplace approximation, since the variational parameters $\boldsymbol{\psi}$ can be used to optimize the curvature of the posterior covariance. To find the optimal $\boldsymbol{\psi}$, we can maximize the ELBO, which is given by

这比 Laplace 近似更灵活，因为变分参数 $\boldsymbol{\psi}$ 可用于优化后验协方差的曲率。为找到最优 $\boldsymbol{\psi}$，我们可以最大化 ELBO，其由以下给出

$\log p(\boldsymbol{y}|\mathbf{X}) = \log \int p(\boldsymbol{y}|\mathbf{X}, \boldsymbol{w}) p(\boldsymbol{w}) d\boldsymbol{w} \ge \log \int h(\boldsymbol{w}, \boldsymbol{\psi}) p(\boldsymbol{w}) d\boldsymbol{w} = \mathbb{L}(\boldsymbol{\psi}) \tag{15.12}$

where

其中

$h(\boldsymbol{w}, \boldsymbol{\psi}) = \prod_{n=1}^N \sigma(\psi_n) \exp [\eta_n y_n - (\eta_n + \psi_n)/2 - \lambda(\psi_n)(\eta_n^2 - \psi_n^2)] \tag{15.13}$

We can evaluate the lower bound analytically to get

我们可以解析地计算下界以得到

$\mathbb{L}(\boldsymbol{\psi}) = \frac{1}{2} \log \frac{|\mathbf{V}_N|}{|\mathbf{V}_0|} + \frac{1}{2} \boldsymbol{\mu}_N^T \mathbf{V}_N^{-1} \boldsymbol{\mu}_N - \frac{1}{2} \boldsymbol{\mu}_0^T \mathbf{V}_0^{-1} \boldsymbol{\mu}_0 + \sum_{n=1}^N \left[ \log \sigma(\psi_n) - \frac{1}{2} \psi_n + \lambda(\psi_n)\psi_n^2 \right] \tag{15.14}$

If we solve for $\nabla_\psi \mathbb{L}(\boldsymbol{\psi}) = \mathbf{0}$, we get the following iterative update equation for each variational parameter:

若求解 $\nabla_\psi \mathbb{L}(\boldsymbol{\psi}) = \mathbf{0}$，则可得到每个变分参数的以下迭代更新方程：

$(\psi_n^{\text{new}})^2 = \mathbf{x}_n \mathbb{E} [\boldsymbol{w} \boldsymbol{w}^T] \mathbf{x}_n = \mathbf{x}_n (\mathbf{V}_N + \boldsymbol{\mu}_N \boldsymbol{\mu}_N^T) \mathbf{x}_n \tag{15.15}$

Once we have estimated $\psi_n$, we can plug it into the above Gaussian approximation $q(\boldsymbol{w}|\boldsymbol{\psi})$.

一旦我们估计了 $\psi_n$，就可将其代入上述高斯近似 $q(\boldsymbol{w}|\boldsymbol{\psi})$。

## 15.1.2 Multinomial logistic regression

## 15.1.2 多项逻辑回归

In this section we discuss how to approximate the posterior $p(\boldsymbol{w}|\mathcal{D})$ for multinomial logistic regression using variational inference, extending the approach of Section 15.1 to the multi-class case. The key idea is to create a “Gaussian-like” lower bound on the multi-class logistic regression likelihood due to [Boh92]. We can then compute the variational posterior in closed form. This will let us deterministically optimize the ELBO.

本节将讨论如何使用变分推断来近似多项逻辑回归的后验 $p(\boldsymbol{w}|\mathcal{D})$，将第 15.1 节的方法扩展到多类情况。关键思想是基于 [Boh92] 为多类逻辑回归似然构建一个“类高斯”的下界。随后我们可以以封闭形式计算变分后验。这将使我们能够确定性地优化 ELBO。

Let $\boldsymbol{y}_i \in \{0, 1\}^C$ be a one-hot label vector, and define the logits for example $i$ to be

令 $\boldsymbol{y}_i \in \{0, 1\}^C$ 为一个 one-hot 标签向量，并定义样本 $i$ 的 logits 为

$\boldsymbol{\eta}_i = [\boldsymbol{x}_i^T \boldsymbol{w}_1, \dots, \boldsymbol{x}_i^T \boldsymbol{w}_C] \tag{15.16}$

If we define \(\mathbf{X}_i = \mathbf{I} \otimes \mathbf{x}_i\), where \(\otimes\) is the kronecker product, and \(\mathbf{I}\) is \(C \times C\) identity matrix, then we can write the logits as \(\boldsymbol{\eta}_i = \mathbf{X}_i\mathbf{w}\). (For example, if \(C = 2\) and \(\mathbf{x}_i = [1, 2, 3]\), we have \(\mathbf{X}_i = [1, 2, 3, 0, 0, 0; 0, 0, 0, 1, 2, 3]\).) Then the likelihood is given by

若定义 \(\mathbf{X}_i = \mathbf{I} \otimes \mathbf{x}_i$，其中 \(\otimes\) 为 Kronecker 积，\(\mathbf{I}\) 为 \(C \times C\) 单位矩阵，则可将 logits 写为 \(\boldsymbol{\eta}_i = \mathbf{X}_i\mathbf{w}$。（例如，若 \(C = 2$ 且 \(\mathbf{x}_i = [1, 2, 3]$，则 \(\mathbf{X}_i = [1, 2, 3, 0, 0, 0; 0, 0, 0, 1, 2, 3]$。）似然如下给出

\(p(\mathbf{y}|\mathbf{X}, \mathbf{w}) = \prod_{i=1}^N \exp[\mathbf{y}_i^\mathsf{T}\boldsymbol{\eta}_i - \text{lse}(\boldsymbol{\eta}_i)]\) (15.17)

where lse() is the log-sum-exp function

其中 lse() 为 log-sum-exp 函数

\(\text{lse}(\boldsymbol{\eta}_i) \triangleq \log \left( \sum_{c=1}^C \exp(\eta_{ic}) \right)\) (15.18)

For identifiability, we can set \(\mathbf{w}_C = \mathbf{0}$, so

为保证可识别性，我们可设置 \(\mathbf{w}_C = \mathbf{0}$，因此

\(\text{lse}(\boldsymbol{\eta}_i) = \log \left( 1 + \sum_{m=1}^M \exp(\eta_{im}) \right)\) (15.19)

where \(M = C - 1$. (We subtract 1 so that in the binary case, \(M = 1$.)

其中 \(M = C - 1$。（我们减去 1，使得在二分类情况下 \(M = 1$。）

### 15.1.2.1 Bohning's quadratic bound to the log-sum-exp function

### 15.1.2.1 Bohning 对 log-sum-exp 函数的二次界

The above likelihood is not conjugate to the Gaussian prior. However, we can now convert it to a quadratic form. Consider a Taylor series expansion of the log-sum-exp function around \(\boldsymbol{\psi}_i \in \mathbb{R}^M$:

上述似然与高斯先验非共轭。不过，我们现在可以将其转换为二次形式。考虑 log-sum-exp 函数在 \(\boldsymbol{\psi}_i \in \mathbb{R}^M$ 处的泰勒级数展开：

\(\text{lse}(\boldsymbol{\eta}_i) = \text{lse}(\boldsymbol{\psi}_i) + (\boldsymbol{\eta}_i - \boldsymbol{\psi}_i)^\mathsf{T}\mathbf{g}(\boldsymbol{\psi}_i) + \frac{1}{2}(\boldsymbol{\eta}_i - \boldsymbol{\psi}_i)^\mathsf{T}\mathbf{H}(\boldsymbol{\psi}_i)(\boldsymbol{\eta}_i - \boldsymbol{\psi}_i)\) (15.20)
\(\mathbf{g}(\boldsymbol{\psi}_i) = \exp[\boldsymbol{\psi}_i - \text{lse}(\boldsymbol{\psi}_i)] = \mathcal{S}(\boldsymbol{\psi}_i)\) (15.21)
\(\mathbf{H}(\boldsymbol{\psi}_i) = \text{diag}(\mathbf{g}(\boldsymbol{\psi}_i)) - \mathbf{g}(\boldsymbol{\psi}_i)\mathbf{g}(\boldsymbol{\psi}_i)^\mathsf{T}\) (15.22)

where \(\mathbf{g}$ and \(\mathbf{H}$ are the gradient and Hessian of lse, and \(\boldsymbol{\psi}_i \in \mathbb{R}^M$, where \(M = C - 1$ is the number of classes minus 1. An upper bound to lse can be found by replacing the Hessian matrix \(\mathbf{H}(\boldsymbol{\psi}_i)$ with a matrix \(\mathbf{A}_i$ such that \(\mathbf{A}_i \unknown \mathbf{H}(\boldsymbol{\psi}_i)$ for all \(\psi_i$. [Boh92] showed that this can be achieved if we use the matrix \(\mathbf{A}_i = \frac{1}{2} \left[ \mathbf{I}_M - \frac{1}{M+1}\mathbf{1}_M\mathbf{1}_M^\mathsf{T} \right]$. In the binary case, this becomes \(A_i = \frac{1}{2}(1 - \frac{1}{2}) = \frac{1}{4}$.

其中 \(\mathbf{g}$ 和 \(\mathbf{H}$ 分别为 lse 的梯度和黑塞矩阵，\(\boldsymbol{\psi}_i \in \mathbb{R}^M$，其中 \(M = C - 1$ 为类别数减 1。通过将黑塞矩阵 \(\mathbf{H}(\boldsymbol{\psi}_i)$ 替换为满足 \(\mathbf{A}_i \unknown \mathbf{H}(\boldsymbol{\psi}_i)$（对所有 \(\psi_i$ 成立）的矩阵 \(\mathbf{A}_i$，可以得到 lse 的一个上界。[Boh92] 表明，若使用矩阵 \(\mathbf{A}_i = \frac{1}{2} \left[ \mathbf{I}_M - \frac{1}{M+1}\mathbf{1}_M\mathbf{1}_M^\mathsf{T} \right]$，即可实现此目标。在二分类情况下，这变为 \(A_i = \frac{1}{2}(1 - \frac{1}{2}) = \frac{1}{4}$。

Note that \(\mathbf{A}_i$ is independent of \(\boldsymbol{\psi}_i$; however, we still write it as \(\mathbf{A}_i$ (rather than dropping the \(i$ subscript), since other bounds that we consider below will have a data-dependent curvature term. The upper bound on lse therefore becomes

需注意 \(\mathbf{A}_i$ 与 \(\boldsymbol{\psi}_i$ 无关；不过，我们仍将其写作 \(\mathbf{A}_i$（而非省略下标 \(i$），因为下文将考虑的其他边界会包含数据依赖的曲率项。因此 lse 的上界变为

\(\text{lse}(\boldsymbol{\eta}_i) \leq \frac{1}{2}\boldsymbol{\eta}_i^\mathsf{T}\mathbf{A}_i\boldsymbol{\eta}_i - \mathbf{b}_i^\mathsf{T}\boldsymbol{\eta}_i + c_i\) (15.23)
\(\mathbf{A}_i = \frac{1}{2} \left[ \mathbf{I}_M - \frac{1}{M+1}\mathbf{1}_M\mathbf{1}_M^\mathsf{T} \right]\) (15.24)
\(\mathbf{b}_i = \mathbf{A}_i\boldsymbol{\psi}_i - \mathbf{g}(\boldsymbol{\psi}_i)\) (15.25)
\(c_i = \frac{1}{2}\boldsymbol{\psi}_i^\mathsf{T}\mathbf{A}_i\boldsymbol{\psi}_i - \mathbf{g}(\boldsymbol{\psi}_i)^\mathsf{T}\boldsymbol{\psi}_i + \text{lse}(\boldsymbol{\psi}_i)\) (15.26)

where \(\boldsymbol{\psi}_i \in \mathbb{R}^M$ is a vector of variational parameters.

其中 \(\boldsymbol{\psi}_i \in \mathbb{R}^M$ 是变分参数向量。

We can use the above result to get the following lower bound on the softmax likelihood:

我们可以利用上述结果得到 softmax 似然的以下下界：

\(\log p(y_i = c|\mathbf{x}_i, \mathbf{w}) \geq \left[ \mathbf{y}_i^\mathsf{T}\mathbf{X}_i\mathbf{w} - 4\frac{1}{2}\mathbf{w}^\mathsf{T}\mathbf{X}_i\mathbf{A}_i\mathbf{X}_i\mathbf{w} + \mathbf{b}_i^\mathsf{T}\mathbf{X}_i\mathbf{w} - c_i \right]_c\) (15.27)

To simplify notation, define the pseudo-measurement

为简化记法，定义伪测量

\(\tilde{\mathbf{y}}_i \triangleq \mathbf{A}_i^{-1}(\mathbf{b}_i + \mathbf{y}_i)\) (15.28)

Then we can get a “Gaussianized” version of the observation model:

然后可以得到观测模型的“高斯化”版本：

\(p(y_i|x_i, w) \ge f(x_i, \psi_i) \mathcal{N}(\tilde{y}_i|X_i w, \mathbf{A}_i^{-1})\) (15.29)

where \(f(x_i, \psi_i)$ is some function that does not depend on \(w$. Given this, it is easy to compute the posterior \(q(w) = \mathcal{N}(m_N, \mathbf{V}_N)$, using Bayes rule for Gaussians.

其中 \(f(x_i, \psi_i)$ 是某个不依赖于 \(w$ 的函数。基于此，利用高斯的贝叶斯法则，可以轻松计算后验 \(q(w) = \mathcal{N}(m_N, \mathbf{V}_N)$。

Given the posterior, we can write the ELBO as follows:

给定后验后，ELBO 可表示如下：

\(\mathcal{L}(\psi) \triangleq -D_{\text{KL}} (q(w)\|p(w)) + \mathbb{E}_q \left[ \sum_{i=1}^N \log p(y_i|x_i, w) \right]\) (15.30)
\(= -D_{\text{KL}} (q(w)\|p(w)) + \mathbb{E}_q \left[ \sum_{i=1}^N y_i^\mathsf{T} \eta_i - \text{lse}(\eta_i) \right]\) (15.31)
\(= -D_{\text{KL}} (q(w)\|p(w)) + \sum_{i=1}^N y_i^\mathsf{T} \mathbb{E}_q [\eta_i] - \sum_{i=1}^N \mathbb{E}_q \left[ \text{lse}(\eta_i) \right]\) (15.32)

where \(p(w) = \mathcal{N}(w|m_0, \mathbf{V}_0)$ is the prior and \(q(w) = \mathcal{N}(w|m_N, \mathbf{V}_N)$ is the approximate posterior. The first term is just the KL divergence between two Gaussians, which is given by

其中 \(p(w) = \mathcal{N}(w|m_0, \mathbf{V}_0)$ 为先验，\(q(w) = \mathcal{N}(w|m_N, \mathbf{V}_N)$ 为近似后验。第一项即两个高斯分布之间的 KL 散度，其由以下给出

\(-D_{\text{KL}} (\mathcal{N}(m_N, \mathbf{V}_N)\|\mathcal{N}(m_0, \mathbf{V}_0)) = -\frac{1}{2} \left[ \text{tr}(\mathbf{V}_N \mathbf{V}_0^{-1}) - \log |\mathbf{V}_N \mathbf{V}_0^{-1}| \right]\)
\(+(m_N - m_0)^\mathsf{T} \mathbf{V}_0^{-1}(m_N - m_0) - DM]\) (15.33)

where \(DM$ is the dimensionality of the Gaussian, and we assume a prior of the form \(p(w) = \mathcal{N}(m_0, \mathbf{V}_0)$, where typically \(\mu_0 = \mathbf{0}_{DM}$, and \(\mathbf{V}_0$ is block diagonal. The second term is simply

其中 \(DM$ 为高斯分布的维度，且我们假设先验形式为 \(p(w) = \mathcal{N}(m_0, \mathbf{V}_0)$，通常 \(\mu_0 = \mathbf{0}_{DM}$，且 \(\mathbf{V}_0$ 为分块对角矩阵。第二项仅为

\(\sum_{i=1}^N y_i^\mathsf{T} \mathbb{E}_q \left[ \eta_i \right] = \sum_{i=1}^N y_i^\mathsf{T} \tilde{m}_i\) (15.34)

where \(\tilde{m}_i \triangleq \mathbf{X}_i m_N$. The final term can be lower bounded by taking expectations of our quadratic upper bound on lse as follows:

其中 \(\tilde{m}_i \triangleq \mathbf{X}_i m_N$。最后一项可通过对 lse 的二次上界取期望来下界化，如下所示：

\(-\sum_{i=1}^N \mathbb{E}_q \left[ \text{lse}(\eta_i) \right] \ge -\frac{1}{2} \text{tr}(\mathbf{A}_i \tilde{\mathbf{V}}_i) - \frac{1}{2} \tilde{m}_i \mathbf{A}_i \tilde{m}_i + b_i^\mathsf{T} \tilde{m}_i - c_i\) (15.35)

where \(\tilde{\mathbf{V}}_i \triangleq \mathbf{X}_i \mathbf{V}_N \mathbf{X}_i^\mathsf{T}$. Hence we have

其中 \(\tilde{\mathbf{V}}_i \triangleq \mathbf{X}_i \mathbf{V}_N \mathbf{X}_i^\mathsf{T}$。因此我们有

\(\mathcal{L}(\psi) \ge -\frac{1}{2} \left[ \text{tr}(\mathbf{V}_N \mathbf{V}_0^{-1}) - \log |\mathbf{V}_N \mathbf{V}_0^{-1}| + (m_N - m_0)^\mathsf{T} \mathbf{V}_0^{-1}(m_N - m_0) \right]\)
\(-\frac{1}{2} DM + \sum_{i=1}^N y_i^\mathsf{T} \tilde{m}_i - \frac{1}{2} \text{tr}(\mathbf{A}_i \tilde{\mathbf{V}}_i) - \frac{1}{2} \tilde{m}_i \mathbf{A}_i \tilde{m}_i + b_i^\mathsf{T} \tilde{m}_i - c_i\) (15.36)

We will use coordinate ascent to optimize this lower bound. That is, we update the variational posterior parameters \(\mathbf{V}_N$ and \(m_N$, and then the variational likelihood parameters \(\psi_i$. We leave the detailed derivation as an exercise, and just state the results. We have

我们将使用坐标上升来优化此下界。即，先更新变分后验参数 \(\mathbf{V}_N$ 和 \(m_N$，再更新变分似然参数 \(\psi_i$。详细推导留作练习，这里仅给出结果。我们有

\(\mathbf{V}_N = \left( \mathbf{V}_0 + \sum_{i=1}^N \mathbf{X}_i^\mathsf{T} \mathbf{A}_i \mathbf{X}_i \right)^{-1}\) (15.37)
\(m_N = \mathbf{V}_N \left( \mathbf{V}_0^{-1} m_0 + \sum_{i=1}^N \mathbf{X}_i^\mathsf{T}(y_i + b_i) \right)\) (15.38)
\(\psi_i = \tilde{m}_i = \mathbf{X}_i m_N\) (15.39)


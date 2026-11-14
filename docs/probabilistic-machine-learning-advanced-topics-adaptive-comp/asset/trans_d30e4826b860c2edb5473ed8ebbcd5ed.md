

此处需要的性质是 $D_{KL}(q \| p) \ge 0$ 且当且仅当 $q = p$ 时 $D_{KL}(q \| p) = 0$。因此，我们可以通过令每个 $q_n^* = p(\mathbf{z}_n|\mathbf{y}_n, \boldsymbol{\theta})$ 来最大化关于 $\{q_n\}$ 的下界 $\mathcal{L}(\boldsymbol{\theta}, \{q_n\}|\mathcal{D})$。这称为 **E 步**。这确保了 ELBO 是一个紧下界：

$\mathbb{L}(\boldsymbol{\theta}, \{q_n^*\}|\mathcal{D}) = \sum_n \log p(\mathbf{y}_n|\boldsymbol{\theta}) = \ell(\boldsymbol{\theta}|\mathcal{D})$

要看这与界优化（bound optimization）如何联系，让我们定义

$Q(\boldsymbol{\theta}, \boldsymbol{\theta}^t) = \mathbb{L}(\boldsymbol{\theta}, \{p(\mathbf{z}_n|\mathbf{y}_n; \boldsymbol{\theta}^t)\})$

则有 $Q(\boldsymbol{\theta}, \boldsymbol{\theta}^t) \le \ell(\boldsymbol{\theta})$ 且 $Q(\boldsymbol{\theta}^t, \boldsymbol{\theta}^t) = \ell(\boldsymbol{\theta}^t)$，如所要求。

然而，如果我们无法精确计算后验 $p(\mathbf{z}_n|\mathbf{y}_n; \boldsymbol{\theta}^t)$，仍可使用近似分布 $q(\mathbf{z}_n|\mathbf{y}_n; \boldsymbol{\theta}^t)$；这将对似然对数产生一个非紧下界。EM 的这种推广版本称为变分 EM [NH98b]。详情见第 6.5.6.1 节。

### 6.5.3.3 M 步

在 M 步中，我们需要最大化关于 $\boldsymbol{\theta}$ 的 $\mathbb{L}(\boldsymbol{\theta}, \{q_n^t\})$，其中 $q_n^t$ 是在第 $t$ 次迭代的 E 步中计算得到的分布。由于熵项 $\mathbb{H}(q_n)$ 关于 $\boldsymbol{\theta}$ 为常数，我们可以在 M 步中将其舍弃。剩下

$\ell^t(\boldsymbol{\theta}) = \sum_n \mathbb{E}_{q_n^t(\mathbf{z}_n)} [\log p(\mathbf{y}_n, \mathbf{z}_n|\boldsymbol{\theta})]$

这称为 **期望完全数据对数似然**。若联合概率属于指数族（第 2.4 节），则可将其改写为

$\ell^t(\boldsymbol{\theta}) = \sum_n \mathbb{E} \left[ \mathcal{T}(\mathbf{y}_n, \mathbf{z}_n)^\mathsf{T} \boldsymbol{\theta} - A(\boldsymbol{\theta}) \right] = \sum_n (\mathbb{E} [\mathcal{T}(\mathbf{y}_n, \mathbf{z}_n])^\mathsf{T} \boldsymbol{\theta} - A(\boldsymbol{\theta}))$

其中 $\mathbb{E} [\mathcal{T}(\mathbf{y}_n, \mathbf{z}_n)]$ 称为 **期望充分统计量**。

在 M 步中，我们最大化期望完全数据对数似然以得到

$\boldsymbol{\theta}^{t+1} = \arg \max_{\boldsymbol{\theta}} \sum_n \mathbb{E}_{q_n^t} [\log p(\mathbf{y}_n, \mathbf{z}_n|\boldsymbol{\theta})]$

在指数族的情况下，极大化可通过匹配期望充分统计量的矩（第 2.4.5 节）以解析形式求解。

从上文可见，E 步实际上不需要返回完整的后验分布集合 $\{q(\mathbf{z}_n)\}$，而只需返回期望充分统计量之和 $\sum_n \mathbb{E}_{q(\mathbf{z}_n)} [\mathcal{T}(\mathbf{y}_n, \mathbf{z}_n)]$ 即可。

EM 的一个常见应用是拟合混合模型；我们在本书的前作 [Mur22] 中讨论过此问题。下面给出另一个示例。

## 6.5.4 示例：用于带缺失数据的 MVN 的 EM

当我们拥有完整观测的数据矩阵时，计算多元正态分布的 MLE 很容易：只需计算样本均值和协方差即可。在本节中，我们考虑存在缺失数据或部分观测数据的情况。例如，可以将 Y 的条目视为调查问卷的答案；其中有些答案可能未知。缺失数据有多种类型，如第 3.11 节所述。在本节中，为简化起见，我们做缺失忽略（missing at random, MAR）假设。在 MAR 假设下，可见数据的对数似然形式为

$$
\log p(\mathbf{X}|\boldsymbol{\theta}) = \sum_n \log p(\mathbf{x}_n|\boldsymbol{\theta}) = \sum_n \log \left[ \int p(\mathbf{x}_n, \mathbf{z}_n|\boldsymbol{\theta}) d\mathbf{z}_n \right]
$$

其中 $\mathbf{x}_n$ 为第 $n$ 个病例的可见变量，$\mathbf{z}_n$ 为隐藏变量，$\mathbf{y}_n = (\mathbf{z}_n, \mathbf{x}_n)$ 为所有变量。不幸的是，该目标难以最大化。因为我们无法将对数推入期望内部。幸运的是，我们可以轻松应用 EM，如下文所述。

### 6.5.4.1 E 步

假设我们拥有前一轮迭代得到的参数 $\boldsymbol{\theta}^{t-1}$。那么，在第 $t$ 轮迭代中，期望完全数据对数似然可计算为：

$$
Q(\boldsymbol{\theta}, \boldsymbol{\theta}^{t-1}) = \mathbb{E} \left[ \sum_{n=1}^N \log \mathcal{N}(\mathbf{y}_n|\boldsymbol{\mu}, \boldsymbol{\Sigma}) | \mathcal{D}, \boldsymbol{\theta}^{t-1} \right]
$$

$$
= -\frac{N}{2} \log |2\pi\boldsymbol{\Sigma}| - \frac{1}{2} \sum_n \mathbb{E} [(\mathbf{y}_n - \boldsymbol{\mu})^\top \boldsymbol{\Sigma}^{-1} (\mathbf{y}_n - \boldsymbol{\mu})]
$$

$$
= -\frac{N}{2} \log |2\pi\boldsymbol{\Sigma}| - \frac{1}{2} \text{tr}(\boldsymbol{\Sigma}^{-1} \sum_n \mathbb{E} [(\mathbf{y}_n - \boldsymbol{\mu})(\mathbf{y}_n - \boldsymbol{\mu})^\top]
$$

$$
= -\frac{N}{2} \log |\boldsymbol{\Sigma}| - \frac{ND}{2} \log(2\pi) - \frac{1}{2} \text{tr}(\boldsymbol{\Sigma}^{-1} \mathbb{E} [\mathbf{S}(\boldsymbol{\mu})])
$$

where

$$
\mathbb{E}[\mathbf{S}(\boldsymbol{\mu})] \triangleq \sum_n \left( \mathbb{E}[\mathbf{y}_n \mathbf{y}_n^\top] + \boldsymbol{\mu}\boldsymbol{\mu}^\top - 2\boldsymbol{\mu}\mathbb{E}[\mathbf{y}_n^\top] \right)
$$

为简洁起见，这里省略了期望对 $\mathcal{D}$ 和 $\boldsymbol{\theta}^{t-1}$ 的条件。可见，我们需要计算 $\sum_n \mathbb{E}[\mathbf{y}_n]$ 和 $\sum_n \mathbb{E}[\mathbf{y}_n \mathbf{y}_n^\top]$；这些即为期望充分统计量。

为计算这些量，我们使用第 2.3.1.3 节的结果。有

$$
p(\mathbf{z}_n | \mathbf{x}_n, \boldsymbol{\theta}) = \mathcal{N}(\mathbf{z}_n | \mathbf{m}_n, \mathbf{V}_n)
$$

$$
\mathbf{m}_n \triangleq \boldsymbol{\mu}_h + \boldsymbol{\Sigma}_{hv} \boldsymbol{\Sigma}_{vv}^{-1} (\mathbf{x}_n - \boldsymbol{\mu}_v)
$$

$$
\mathbf{V}_n \triangleq \boldsymbol{\Sigma}_{hh} - \boldsymbol{\Sigma}_{hv} \boldsymbol{\Sigma}_{vv}^{-1} \boldsymbol{\Sigma}_{vh}
$$

其中我们根据隐藏和可见索引 $h$ 与 $v$ 将 $\boldsymbol{\mu}$ 和 $\boldsymbol{\Sigma}$ 划分为块。因此，期望充分统计量为

$$
\mathbb{E}[\mathbf{y}_n] = (\mathbb{E}[\mathbf{z}_n] ; \mathbf{x}_n) = (\mathbf{m}_n ; \mathbf{x}_n)
$$

为计算 $\mathbb{E} [\boldsymbol{y}_n \boldsymbol{y}_n^\top]$，我们使用结果 $\text{Cov} [\boldsymbol{y}] = \mathbb{E} [\boldsymbol{y}\boldsymbol{y}^\top] - \mathbb{E} [\boldsymbol{y}] \mathbb{E} [\boldsymbol{y}^\top]$。因此

$$
\mathbb{E} [\boldsymbol{y}_n \boldsymbol{y}_n^\top] = \mathbb{E} \left[ \begin{pmatrix} \boldsymbol{z}_n \\ \boldsymbol{x}_n \end{pmatrix} \begin{pmatrix} \boldsymbol{z}_n^\top & \boldsymbol{x}_n^\top \end{pmatrix} \right] = \begin{pmatrix} \mathbb{E} [\boldsymbol{z}_n \boldsymbol{z}_n^\top] & \mathbb{E} [\boldsymbol{z}_n] \boldsymbol{x}_n^\top \\ \boldsymbol{x}_n \mathbb{E} [\boldsymbol{z}_n]^\top & \boldsymbol{x}_n \boldsymbol{x}_n^\top \end{pmatrix}
$$ (6.161)

$$
\mathbb{E} [\boldsymbol{z}_n \boldsymbol{z}_n^\top] = \mathbb{E} [\boldsymbol{z}_n] \mathbb{E} [\boldsymbol{z}_n]^\top + \mathbf{V}_n
$$ (6.162)

### 6.5.4.2 M 步

通过求解 $\nabla Q(\boldsymbol{\theta}, \boldsymbol{\theta}^{(t-1)}) = \mathbf{0}$，可以证明 M 步等同于将这些 ESS 代入通常的 MLE 方程以得到

$$
\boldsymbol{\mu}^t = \frac{1}{N} \sum_n \mathbb{E} [\boldsymbol{y}_n]
$$ (6.163)

$$
\boldsymbol{\Sigma}^t = \frac{1}{N} \sum_n \mathbb{E} [\boldsymbol{y}_n \boldsymbol{y}_n^\top] - \boldsymbol{\mu}^t (\boldsymbol{\mu}^t)^\top
$$ (6.164)

由此可见，EM *不* 等同于仅将变量替换为其期望并应用标准 MLE 公式；那样做会忽略后验方差并导致错误估计。相反，我们必须计算充分统计量的期望，并将其代入 MLE 的通常方程中。

### 6.5.4.3 初始化

为启动算法，我们可以基于数据矩阵中完全观测的行来计算 MLE。如果没有这样的行，则可以利用观测到的边缘统计量来估计 $\boldsymbol{\Sigma}$ 的对角项。随后即可开始 EM。

### 6.5.4.4 示例

作为该程序运行的示例，让我们考虑一个插补问题，其中有 $N=100$ 个 10 维数据案例，假设它们来自高斯分布。我们生成合成数据，其中 50% 的观测值随机缺失。首先使用 EM 拟合参数。将得到的参数记为 $\hat{\boldsymbol{\theta}}$。现在，我们可以通过计算 $\mathbb{E} \left[ \boldsymbol{z}_n | \boldsymbol{x}_n, \hat{\boldsymbol{\theta}} \right]$ 使用模型进行预测。图 6.8 表明，使用学习参数获得的结果几乎与使用真实参数一样好。毫不奇怪，随着数据增多或缺失数据比例降低，性能会提高。

## 6.5.5 示例：使用 Student 似然的稳健线性回归

在本节中，我们讨论如何使用 EM 拟合线性回归模型，其似然使用 Student 分布而非更常见的高斯分布，以实现稳健性，该想法最早由 [Zel76] 提出。更准确地说，似然由以下公式给出

$$
p(y | \boldsymbol{w}, \sigma^2, \nu) = \mathcal{T}(y | \boldsymbol{w}^\top \boldsymbol{x}, \sigma^2, \nu)
$$ (6.165)


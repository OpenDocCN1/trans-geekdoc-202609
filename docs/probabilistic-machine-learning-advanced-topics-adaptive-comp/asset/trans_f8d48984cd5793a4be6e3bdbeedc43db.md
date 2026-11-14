

对应的 ELBO 变为

\(\mathbf{L}(\boldsymbol{\theta}, \boldsymbol{\phi}|\mathcal{D}) = \sum_{n=1}^N [\mathbb{E}_{q_\phi(\mathbf{z}_n|\mathbf{x}_n)} [\log p_\theta(\mathbf{x}_n, \mathbf{z}_n) - \log q_\phi(\mathbf{z}|\mathbf{x}_n)]]\)

如果将此与 SVI 结合，我们得到方程 (10.27) 的摊销版本。例如，如果我们使用大小为 1 的小批量，我们得到

\(\mathbf{L}(\boldsymbol{\theta}, \boldsymbol{\phi}|\mathbf{x}_n) \approx N [\mathbb{E}_{q_\phi(\mathbf{z}_n|\mathbf{x}_n)} [\log p_\theta(\mathbf{x}_n, \mathbf{z}_n) - \log q_\phi(\mathbf{z}|\mathbf{x}_n)]]\)

我们可以按算法 10.1 所示优化此目标。注意，M 步中关于 \(\boldsymbol{\theta}\) 的（部分）极大化通常使用梯度更新完成，但 E 步中关于 \(\boldsymbol{\phi}\) 的极大化更棘手，因为损失使用 \(\boldsymbol{\phi}\) 来定义期望算子，因此我们不一定能将梯度算子移到内部；我们在 10.2 节和 10.3 节讨论优化变分参数的方法。

| 算法 10.1：摊销随机变分 EM |
|---|
| 1 初始化 \(\boldsymbol{\theta}, \boldsymbol{\phi}\) |
| 2 重复 |
| 3 采样 \(\mathbf{x}_n \sim p_\mathcal{D}\) |
| 4 E 步：\(\boldsymbol{\phi} = \text{argmax}_\boldsymbol{\phi} \mathbf{L}(\boldsymbol{\theta}, \boldsymbol{\phi}|\mathbf{x}_n)\) |
| 5 M 步：\(\boldsymbol{\theta} = \text{argmax}_\boldsymbol{\theta} \mathbf{L}(\boldsymbol{\theta}, \boldsymbol{\phi}|\mathbf{x}_n)\) |
| 6 直到收敛 |

## 10.1.6 半摊销推断

摊销 SVI 广泛用于拟合 LVM，例如，用于 VAEs（参见 21.2 节）、主题模型 [SS17a]、概率编程 [RHG16]、CRFs [TG18] 等。然而，使用推理网络可能导致局部变分参数 \(\boldsymbol{\psi}_n\) 的非最优设置。这称为**摊销差距** [CLD18]。我们可以通过使用推理网络为 \(\boldsymbol{\psi}_n\) 的优化器进行热启动来缩小这一差距；这被称为**半摊销 VI** [Kim+18c]。（另参见 [MYM18]，他们提出一种密切相关的方法，称为**迭代摊销推断**。）另一种方法是将推理网络用作提议分布。如果我们将其与重要性采样相结合，我们得到 10.5.1 节的 IWAE 界限。如果我们将其与 Metropolis-Hastings 结合使用，我们得到一个 VI-MCMC 混合模型（参见 10.4.5 节）。

## 10.2 基于梯度的 VI

在本节中，我们将为 \(q_\psi(\mathbf{z})\) 选择某种方便的形式，例如用于连续 \(\mathbf{z}\) 的高斯分布，或用于离散 \(\mathbf{z}\) 的分类分布乘积，然后使用基于梯度的方法优化 ELBO。

![](img/ca72c1626f4850f058a9edc138c1ac73_471_0.png)

图 10.4：重参数化技巧示意图。目标 f 取决于变分参数 \(\phi\)、观测数据 \(x\) 和隐性随机变量 \(z \sim q_\phi(z|x)\)。左侧显示计算图的标准形式。右侧显示重参数化形式，其中我们将随机性移入噪声源 \(\epsilon\)，并确定性地计算 \(z\)，\(z = g(\phi, x, \epsilon)\)。图的其余部分是确定性的，因此我们可以将标量 \(f\) 关于 \(\phi\) 的梯度通过 \(z\) 反向传播到 \(\phi\)。源自 [KW19a] 的图 2.3。经 Durk Kingma 友好许可使用。

```
\(\nabla_\theta \mathbf{L}(\theta, \phi | x) = \nabla_\theta \mathbb{E}_{q_\phi(z|x)} [\log p_\theta(x, z) - \log q_\phi(z|x)]\)
\(= \mathbb{E}_{q_\phi(z|x)} [\nabla_\theta \{ \log p_\theta(x, z) - \log q_\phi(z|x) \}]\)
\(\approx \nabla_\theta \log p_\theta(x, z^s)\)
```

其中 \(z^s \sim q_\phi(z|x)\)。这是梯度的无偏估计，因此可以与 SGD 一起使用。

关于推理参数 \(\phi\) 的梯度更难计算，因为

```
\(\nabla_\phi \mathbf{L}(\theta, \phi | x) = \nabla_\phi \mathbb{E}_{q_\phi(z|x)} [\log p_\theta(x, z) - \log q_\phi(z|x)]\)
\(\neq \mathbb{E}_{q_\phi(z|x)} [\nabla_\phi \{ \log p_\theta(x, z) - \log q_\phi(z|x) \}]\)
```

然而，我们通常可以使用重参数化技巧，我们将在 10.2.1 节讨论。否则，我们可以使用黑盒 VI，我们将在 10.2.3 节讨论。

### 10.2.1 重参数化 VI

在本节中，我们讨论用于对连续隐性变量 \(z \sim q_\phi(z|x)\) 的分布求梯度的**重参数化技巧**。我们在 6.3.5 节详细解释了这一点，但我们在此总结基本思想。

关键技巧是将随机变量 \( z \sim q_\phi(z|x) \) 重写为另一个不依赖于 \(\phi\) 的随机变量 \( \epsilon \sim p(\epsilon) \) 的某个可微分（且可逆）变换 \( g \)，即，我们假设可以写成

\( z = g(\phi, x, \epsilon) \quad (10.36) \)

例如，

\( z \sim \mathcal{N}(\mu, \text{diag}(\sigma)) \Longleftrightarrow z = \mu + \epsilon \odot \sigma, \quad \epsilon \sim \mathcal{N}(\mathbf{0}, \mathbf{I}) \quad (10.37) \)

使用此方法，我们有

\( \mathbb{E}_{q_\phi(z|x)} [f(z)] = \mathbb{E}_{p(\epsilon)} [f(z)] \quad \text{s.t.} \quad z = g(\phi, x, \epsilon) \quad (10.38) \)

其中我们定义

\( f_{\theta, \phi}(z) = \log p_\theta(x, z) - \log q_\phi(z|x) \quad (10.39) \)

因此

\( \nabla_\phi \mathbb{E}_{q_\phi(z|x)} [f(z)] = \nabla_\phi \mathbb{E}_{p(\epsilon)} [f(z)] = \mathbb{E}_{p(\epsilon)} [\nabla_\phi f(z)] \quad (10.40) \)

我们可以用单个蒙特卡罗样本来近似它。这使我们能够通过 \( f \) 函数反向传播梯度。有关说明，请参见图 10.4。这称为**重参数化 VI** 或 **RVI**。

由于我们现在处理的是随机变量 \(\epsilon\)，我们需要使用变量变换公式来计算

\( \log q_\phi(z|x) = \log p(\epsilon) - \log \left| \det \left( \frac{\partial z}{\partial \epsilon} \right) \right| \quad (10.41) \)

其中 \(\frac{\partial z}{\partial \epsilon}\) 是雅可比矩阵：

\( \frac{\partial z}{\partial \epsilon} = \begin{pmatrix} \frac{\partial z_1}{\partial \epsilon_1} & \cdots & \frac{\partial z_1}{\partial \epsilon_k} \\ \vdots & \ddots & \vdots \\ \frac{\partial z_k}{\partial \epsilon_1} & \cdots & \frac{\partial z_k}{\partial \epsilon_k} \end{pmatrix} \quad (10.42) \)

我们设计变换 \( z = g(\epsilon) \)，使得该雅可比矩阵易于计算。我们下面给出一些示例。

### 10.2.1.1 对角协方差高斯分布（均值场）

假设我们使用完全分解的高斯后验。那么重参数化过程变为

\( \epsilon \sim \mathcal{N}(\mathbf{0}, \mathbf{I}) \quad (10.43) \)

\( z = \mu + \sigma \odot \epsilon \quad (10.44) \)

其中推理网络生成变换的参数：

\((\boldsymbol{\mu}, \log \boldsymbol{\sigma}) = f_\phi^{\text{inf}}(\boldsymbol{x})\)

因此，要从后验 \(q_\phi(\boldsymbol{z}|\boldsymbol{x})\) 中采样，我们采样 \(\boldsymbol{\epsilon} \sim \mathcal{N}(\boldsymbol{0}, \mathbf{I})\)，然后计算 \(\boldsymbol{z}\)。

给定样本后，我们需要评估 ELBO：

\(f(\boldsymbol{z}) = \log p_\theta(\boldsymbol{x}|\boldsymbol{z}) + \log p_\theta(\boldsymbol{z}) - \log q_\phi(\boldsymbol{z}|\boldsymbol{x})\)

要评估 \(p_\theta(\boldsymbol{x}|\boldsymbol{z})\) 项，我们可以直接将 \(\boldsymbol{z}\) 代入似然函数。要评估 \(\log q_\phi(\boldsymbol{z}|\boldsymbol{x})\) 项，我们需要使用方程 (10.41) 中的变量变换公式。雅可比矩阵由 \(\frac{\partial \boldsymbol{z}}{\partial \boldsymbol{\epsilon}} = \text{diag}(\boldsymbol{\sigma})\) 给出。因此

\(\log q_\phi(\boldsymbol{z}|\boldsymbol{x}) = \sum_{k=1}^K [\log \mathcal{N}(\epsilon_k|0, 1) - \log \sigma_k] = - \sum_{k=1}^K \left[ \frac{1}{2} \log(2\pi) + \frac{1}{2} \epsilon_k^2 + \log \sigma_k \right]\)

最后，要评估 \(p(\boldsymbol{z})\) 项，我们可以使用变换 \(\boldsymbol{z} = \mathbf{0} + \mathbf{1} \odot \boldsymbol{\epsilon}\)，因此雅可比矩阵为单位矩阵，我们得到

\(\log p(\boldsymbol{z}) = \sum_{k=1}^K \left[ \frac{1}{2} \epsilon_k^2 + \frac{1}{2} \log(2\pi) \right]\)

另一种方法是使用目标

\(f'(\boldsymbol{z}) = \log p_\theta(\boldsymbol{x}|\boldsymbol{z}) + D_{\text{KL}}(q_\phi(\mathbf{Z}|\boldsymbol{x}) \parallel p_\theta(\mathbf{Z}))\)

在某些情况下，我们解析地评估第二项，而不需要蒙特卡罗。例如，如果我们假设对角高斯先验 \(p(\boldsymbol{z}) = \mathcal{N}(\boldsymbol{z}|\mathbf{0}, \mathbf{I})\) 和对角高斯后验 \(q(\boldsymbol{z}|\boldsymbol{x}) = \mathcal{N}(\boldsymbol{z}|\boldsymbol{\mu}, \text{diag}(\boldsymbol{\sigma}))\)，我们可以使用方程 (5.78) 以闭式计算 KL：

\(D_{\text{KL}}(q \| p) = -\frac{1}{2} \sum_{k=1}^K [\log \sigma_k^2 - \sigma_k^2 - \mu_k^2 + 1]\)

目标 \(f'(\boldsymbol{z})\) 通常比 \(f(\boldsymbol{z})\) 方差更小，因为它解析地计算 KL。然而，将此目标推广到先验和/或后验不是高斯的设置中更为困难。

### 10.2.1.2 完整协方差高斯分布

现在考虑使用完整协方差高斯后验。我们将计算协方差的 Cholesky 分解，\(\boldsymbol{\Sigma} = \mathbf{L}\mathbf{L}^\mathsf{T}\)，其中 \(\mathbf{L}\) 是对角线上具有非零元素的下三角矩阵。因此重参数化变为

\(\boldsymbol{\epsilon} \sim \mathcal{N}(\mathbf{0}, \mathbf{I})\)

\(\boldsymbol{z} = \boldsymbol{\mu} + \mathbf{L}\boldsymbol{\epsilon}\)




## 25 扩散模型

### 25.1 简介

本章我们考虑一类称为 **扩散模型** 的模型。这类模型最近引起了广泛关注，因为其能够生成多样化、高质量的样本，且训练方案相对简单，能够支持大规模训练非常大的模型。扩散模型与 VAEs（第 21 章）、归一化流（第 23 章）和 EBMs（第 24 章）密切相关，如我们将看到的那样。

这些模型背后的基本想法基于这样的观察：将噪声转换为结构化数据很难，但将结构化数据转换为噪声很容易。具体来说，我们可以使用 **前向过程** 或 **扩散过程**，通过将数据传递经过随机编码器 \(q(\boldsymbol{x}_t|\boldsymbol{x}_{t-1})\) 的 \(T\) 个步骤，逐步将观测数据 \(\boldsymbol{x}_0\) 转换为噪声版本 \(\boldsymbol{x}_T\)。经过足够多的步骤后，我们得到 \(\boldsymbol{x}_T \sim \mathcal{N}(\mathbf{0}, \mathbf{I})\)，或其他某些方便的参考分布。然后我们学习一个 **逆向过程** 来撤销此操作，通过将噪声传递经过解码器 \(p_\theta(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t)\) 的 \(T\) 个步骤，直到生成 \(\boldsymbol{x}_0\)。请参见图 25.1 以了解该方法的总体草图。在接下来的章节中，我们将更详细地讨论这类模型。我们的介绍部分基于优秀的教程 [KGV22]。更多细节可见近期综述论文 [Yan+22; Cao+22]，以及专门论文，例如 [Kar+22]。网上还有许多其他优秀资源，例如 https://github.com/heejkoo/Awesome-Diffusion-Models 和 https://scorebasedgenerativemodeling.github.io/。有关底层数学的详细教程，请参见 [McA23]。

### 25.2 去噪扩散概率模型（DDPM）

在本节中，我们讨论 **去噪扩散概率模型** 或 **DDPM**，该模型在 [SD+15b] 中提出，随后在 [HJA20; Kin+21] 及许多其他工作中得到扩展。我们可以将 DDPM 视为与分层变分自编码器（第 21.5 节）类似，不同之处在于所有隐藏状态（记为 \(t=1:T\) 时的 \(\boldsymbol{x}_t\)）与输入 \(\boldsymbol{x}_0\) 具有相同的维度。（在这方面，DDPM 与归一化流（第 23 章）类似；然而，在扩散模型中，隐藏层是随机的，不需要使用可逆变换。）此外，编码器网络 \(q\) 是一个简单的线性高斯模型，而不是被学习\(^1\)，解码器网络 \(p\) 在所有时间步之间共享。这些限制导致了一个非常简单的训练目标，该目标

![](img/ca72c1626f4850f058a9edc138c1ac73_889_0.png)

图 25.1：去噪扩散概率模型。前向扩散过程 $q(\mathbf{x}_t|\mathbf{x}_{t-1})$ 实现（未学习的）推理网络；这只是在每个步骤添加高斯噪声。逆向扩散过程 $p_\theta(\mathbf{x}_{t-1}|\mathbf{x}_t)$ 实现解码器；这是一个学习的高斯模型。来自 [KGV22] 的第 16 张幻灯片。经 Arash Vahdat 友好授权使用。

![](img/ca72c1626f4850f058a9edc138c1ac73_889_1.png)

图 25.2：1D 数据上扩散模型的示意图。前向扩散过程逐渐将经验数据分布 $q(\mathbf{x}_0)$ 转换为简单的目标分布，这里为 $q(\mathbf{x}_T) = \mathcal{N}(\mathbf{0}, \mathbf{I})$。要从模型生成数据，我们采样一个点 $\mathbf{x}_T \sim \mathcal{N}(\mathbf{0}, \mathbf{I})$，然后反向运行马尔可夫链，通过采样 $\mathbf{x}_t \sim p_\theta(\mathbf{x}_t|\mathbf{x}_{t+1})$ 直到获得原始数据空间中的样本 $\mathbf{x}_0$。来自 [KGV22] 的第 19 张幻灯片。经 Arash Vahdat 友好授权使用。

使得深度模型可以轻松训练，而没有后验坍塌（第 21.4 节）的风险。特别是，在第 25.2.3 节中，我们将看到训练归结为一系列加权非线性最小二乘问题。

### 25.2.1 编码器（前向扩散）

前向编码器过程定义为一个简单的线性高斯模型：

$$
q(\mathbf{x}_t|\mathbf{x}_{t-1}) = \mathcal{N}(\mathbf{x}_t | \sqrt{1 - \beta_t}\mathbf{x}_{t-1}, \beta_t \mathbf{I})
$$

其中 $\beta_t \in (0, 1)$ 的值根据噪声调度选择（参见第 25.2.4 节）。给定输入时，所有隐藏状态上的联合分布由以下给出：

$$
q(\mathbf{x}_{1:T}|\mathbf{x}_0) = \prod_{t=1}^T q(\mathbf{x}_t|\mathbf{x}_{t-1})
$$

由于这定义了一个线性高斯马尔可夫链，我们可以以封闭形式计算其边缘分布。特别是，我们有

$$q(\mathbf{x}_t|\mathbf{x}_0) = \mathcal{N}(\mathbf{x}_t|\sqrt{\bar{\alpha}_t}\mathbf{x}_0, (1 - \bar{\alpha}_t)\mathbf{I}) \quad (25.3)$$

其中我们定义

$$\alpha_t \triangleq 1 - \beta_t, \bar{\alpha}_t = \prod_{s=1}^t \alpha_s \quad (25.4)$$

我们选择噪声调度使得 $\bar{\alpha}_T \approx 0$，因此 $q(\mathbf{x}_T|\mathbf{x}_0) \approx \mathcal{N}(\mathbf{0}, \mathbf{I})$。

分布 $q(\mathbf{x}_t|\mathbf{x}_0)$ 称为 **扩散核**。将此应用于输入数据分布，然后计算结果 **无条件边缘分布** 相当于高斯卷积：

$$q(\mathbf{x}_t) = \int q_0(\mathbf{x}_0)q(\mathbf{x}_t|\mathbf{x}_0)d\mathbf{x}_0 \quad (25.5)$$

随着 $t$ 的增加，边缘分布变得更简单，如图 25.2 所示。在图像领域，此过程首先会移除高频内容（即低级细节，如纹理），随后会移除低频内容（即高级或“语义”信息，如形状），如图 25.1 所示。

### 25.2.2 解码器（逆向扩散）

在逆向扩散过程中，我们希望反转前向扩散过程。如果我们知道输入 $\mathbf{x}_0$，可以按以下方式推导一个前向步骤的逆过程：$^2$

$$q(\mathbf{x}_{t-1}|\mathbf{x}_t, \mathbf{x}_0) = \mathcal{N}(\mathbf{x}_{t-1}|\tilde{\mu}_t(\mathbf{x}_t, \mathbf{x}_0), \tilde{\beta}_t \mathbf{I}) \quad (25.6)$$
$$
\tilde{\mu}_t(\mathbf{x}_t, \mathbf{x}_0) = \frac{\sqrt{\bar{\alpha}_{t-1}}\beta_t}{1 - \bar{\alpha}_t}\mathbf{x}_0 + \frac{\sqrt{\alpha_t}(1 - \bar{\alpha}_{t-1})}{1 - \bar{\alpha}_t}\mathbf{x}_t \quad (25.7)$$
$$
\tilde{\beta}_t = \frac{1 - \bar{\alpha}_{t-1}}{1 - \bar{\alpha}_t}\beta_t \quad (25.8)$$

当然，在生成新数据点时，我们不知道 $\mathbf{x}_0$，但我们将训练生成器来逼近关于 $\mathbf{x}_0$ 平均后的上述分布。因此我们选择生成器采用如下形式

$$p_{\boldsymbol{\theta}}(\mathbf{x}_{t-1}|\mathbf{x}_t) = \mathcal{N}(\mathbf{x}_{t-1}|\boldsymbol{\mu}_{\boldsymbol{\theta}}(\mathbf{x}_t, t), \mathbf{\Sigma}_{\boldsymbol{\theta}}(\mathbf{x}_t, t)) \quad (25.9)$$

我们通常设置 $\mathbf{\Sigma}_{\boldsymbol{\theta}}(\mathbf{x}_t, t) = \sigma_t^2 \mathbf{I}$。我们将在第 25.2.4 节讨论如何学习 $\sigma_t^2$，但两种自然选择是 $\sigma_t^2 = \beta_t$ 和 $\sigma_t^2 = \tilde{\beta}_t$；这些分别对应逆向过程熵的上界和下界，如 [HJA20] 所示。

所有生成变量上的相应联合分布由 $p_{\boldsymbol{\theta}}(\mathbf{x}_{0:T}) = p(\mathbf{x}_T) \prod_{t=1}^T p_{\boldsymbol{\theta}}(\mathbf{x}_{t-1}|\mathbf{x}_t)$ 给出，其中我们设置 $p(\mathbf{x}_T) = \mathcal{N}(\mathbf{0}, \mathbf{I})$。我们可以使用算法 25.2 中的伪代码从此分布采样。

2. 我们只需要对高斯分布使用贝叶斯法则。有关详细推导，请参见例如 https://lilianweng.github.io/posts/2021-07-11-diffusion-models/。

### 25.2.3 模型拟合

我们将通过最大化证据下界（ELBO）来拟合模型，类似于我们训练 VAEs 的方式（参见第 21.2 节）。特别是，对于每个数据示例 \(\mathbf{x}_0\) 我们有

\[
\begin{aligned}
\log p_\theta(\mathbf{x}_0) &= \log \left[ \int d\mathbf{x}_{1:T} q(\mathbf{x}_{1:T}|\mathbf{x}_0) \frac{p_\theta(\mathbf{x}_{0:T})}{q(\mathbf{x}_{1:T}|\mathbf{x}_0)} \right] \\
&\ge \int d\mathbf{x}_{1:T} q(\mathbf{x}_{1:T}|\mathbf{x}_0) \log \left( p(\mathbf{x}_T) \prod_{t=1}^T \frac{p_\theta(\mathbf{x}_{t-1}|\mathbf{x}_t)}{q(\mathbf{x}_t|\mathbf{x}_{t-1})} \right) \\
&= \mathbb{E}_q \left[ \log p(\mathbf{x}_T) + \sum_{t=1}^T \log \frac{p_\theta(\mathbf{x}_{t-1}|\mathbf{x}_t)}{q(\mathbf{x}_t|\mathbf{x}_{t-1})} \right] \triangleq \mathfrak{L}(\mathbf{x}_0)
\end{aligned}
\]

我们现在讨论如何计算 ELBO 中的各项。根据马尔可夫性质，我们有 \(q(\mathbf{x}_t|\mathbf{x}_{t-1}) = q(\mathbf{x}_t|\mathbf{x}_{t-1}, \mathbf{x}_0)\)，根据贝叶斯法则，我们有

\[
q(\mathbf{x}_t|\mathbf{x}_{t-1}, \mathbf{x}_0) = \frac{q(\mathbf{x}_{t-1}|\mathbf{x}_t, \mathbf{x}_0)q(\mathbf{x}_t|\mathbf{x}_0)}{q(\mathbf{x}_{t-1}|\mathbf{x}_0)}
\]

将方程 (25.13) 代入 ELBO，我们得到

\[
\begin{aligned}
\mathfrak{L}(\mathbf{x}_0) = \mathbb{E}_{q(\mathbf{x}_{1:T}|\mathbf{x}_0)} \Bigg[ &\log p(\mathbf{x}_T) + \sum_{t=2}^T \log \frac{p_\theta(\mathbf{x}_{t-1}|\mathbf{x}_t)}{q(\mathbf{x}_{t-1}|\mathbf{x}_t, \mathbf{x}_0)} + \underbrace{\sum_{t=2}^T \log \frac{q(\mathbf{x}_{t-1}|\mathbf{x}_0)}{q(\mathbf{x}_t|\mathbf{x}_0)}}_* \\
&+ \log \frac{p_\theta(\mathbf{x}_0|\mathbf{x}_1)}{q(\mathbf{x}_1|\mathbf{x}_0)} \Bigg]
\end{aligned}
\]

标记为 * 的项是一个裂项求和，可以如下简化：

\[
\begin{aligned}
* = \quad & \log q(\mathbf{x}_{T-1}|\mathbf{x}_0) + \dots + \log q(\mathbf{x}_2|\mathbf{x}_0) + \log q(\mathbf{x}_1|\mathbf{x}_0) \\
- \quad & \log q(\mathbf{x}_T|\mathbf{x}_0) - \log q(\mathbf{x}_{T-1}|\mathbf{x}_0) - \dots - \log q(\mathbf{x}_2|\mathbf{x}_0) \\
= \quad & - \log q(\mathbf{x}_T|\mathbf{x}_0) + \log q(\mathbf{x}_1|\mathbf{x}_0)
\end{aligned}
\]

因此负 ELBO（变分上界）变为

\[
\begin{aligned}
\mathcal{L}(\mathbf{x}_0) &= -\mathbb{E}_{q(\mathbf{x}_{1:T}|\mathbf{x}_0)} \Bigg[ \log \frac{p(\mathbf{x}_T)}{q(\mathbf{x}_T|\mathbf{x}_0)} + \sum_{t=2}^T \log \frac{p_\theta(\mathbf{x}_{t-1}|\mathbf{x}_t)}{q(\mathbf{x}_{t-1}|\mathbf{x}_t, \mathbf{x}_0)} + \log p_\theta(\mathbf{x}_0|\mathbf{x}_1) \Bigg] \\
&= \underbrace{D_{\text{KL}}(q(\mathbf{x}_T|\mathbf{x}_0) \| p(\mathbf{x}_T))}_{L_T(\mathbf{x}_0)} \\
&\quad + \sum_{t=2}^T \mathbb{E}_{q(\mathbf{x}_t|\mathbf{x}_0)} \underbrace{D_{\text{KL}}(q(\mathbf{x}_{t-1}|\mathbf{x}_t, \mathbf{x}_0) \| p_\theta(\mathbf{x}_{t-1}|\mathbf{x}_t))}_{L_{t-1}(\mathbf{x}_0)} - \underbrace{\mathbb{E}_{q(\mathbf{x}_1|\mathbf{x}_0) \log p_\theta(\mathbf{x}_0|\mathbf{x}_1)}}_{L_0(\mathbf{x}_0)}
\end{aligned}
\]


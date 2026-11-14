

将可能值的空间划分为有限个区域，称它们为 \(\boldsymbol{r}_1, \dots, \boldsymbol{r}_K\)，每个区域表示参数空间中体积为 \(\Delta\) 且以 \(\boldsymbol{\theta}_k\) 为中心的区域。这称为 **网格近似**。落在每个区域内的概率由 \(p(\boldsymbol{\theta} \in \boldsymbol{r}_k | \mathcal{D}) \approx p_k \Delta\) 给出，其中

\[
p_k = \frac{\tilde{p}_k}{\sum_{k'=1}^K \tilde{p}_{k'}} \tag{7.20}
\]
\[
\tilde{p}_k = p(\mathcal{D}|\boldsymbol{\theta}_k)p(\boldsymbol{\theta}_k) \tag{7.21}
\]

随着 \(K\) 增加，我们减小每个网格单元的大小。因此，分母只是积分的一个简单数值近似

\[
p(\mathcal{D}) = \int p(\mathcal{D}|\boldsymbol{\theta})p(\boldsymbol{\theta})d\boldsymbol{\theta} \approx \sum_{k=1}^K \Delta \tilde{p}_k \tag{7.22}
\]

作为一个简单示例，我们将使用近似 beta-Bernoulli 模型后验的问题。具体来说，目标是近似

\[
p(\boldsymbol{\theta}|\mathcal{D}) \propto \left[ \prod_{n=1}^N \text{Ber}(y_n|\boldsymbol{\theta}) \right] \text{Beta}(1,1) \tag{7.23}
\]

其中 \(\mathcal{D}\) 包含 10 个正面和 1 个反面（因此观测总数为 \(N=11\)），采用均匀先验。虽然我们可以使用第 3.4.1 节讨论的方法精确计算此后验，但这作为一个有用的教学示例，因为我们可以将近似与精确答案进行比较。此外，由于目标分布只是 1 维，因此结果易于可视化。

在图 7.3a 中，我们展示了将网格近似应用于我们 1 维问题的情况。可以看到，它能够轻松捕捉偏斜的后验（这是由于使用了 10 个正面和 1 个反面的不平衡样本所致）。不幸的是，这种方法无法扩展到 2 或 3 维以上的问题，因为网格点的数量随维度数呈指数增长。

## 7.4.3 拉普拉斯（二次）近似

在本节中，我们讨论了一种使用多元高斯分布近似后验的简单方法；这称为 **拉普拉斯近似** 或 **二次近似**（参见，例如，[TK86; RMC09]）。

假设我们将后验写为如下形式：

\[
p(\boldsymbol{\theta}|\mathcal{D}) = \frac{1}{Z} e^{-\mathcal{E}(\boldsymbol{\theta})} \tag{7.24}
\]

其中 \(\mathcal{E}(\boldsymbol{\theta}) = -\log p(\boldsymbol{\theta},\mathcal{D})\) 称为能量函数，\(Z = p(\mathcal{D})\) 是归一化常数。在众数 \(\hat{\boldsymbol{\theta}}\)（即最低能量状态）附近进行泰勒级数展开，我们得到

\[
\mathcal{E}(\boldsymbol{\theta}) \approx \mathcal{E}(\hat{\boldsymbol{\theta}}) + (\boldsymbol{\theta}-\hat{\boldsymbol{\theta}})^\mathsf{T} \boldsymbol{g} + \frac{1}{2}(\boldsymbol{\theta}-\hat{\boldsymbol{\theta}})^\mathsf{T} \mathbf{H} (\boldsymbol{\theta}-\hat{\boldsymbol{\theta}}) \tag{7.25}
\]

其中 \(\boldsymbol{g}\) 是众数处的梯度，\(\mathbf{H}\) 是海森矩阵。由于 \(\hat{\boldsymbol{\theta}}\) 是众数，梯度项为零。因此

\[
\hat{p}(\theta, \mathcal{D}) = e^{-\mathcal{E}(\hat{\theta})} \exp \left[ -\frac{1}{2} (\theta - \hat{\theta})^\top \mathbf{H} (\theta - \hat{\theta}) \right] \tag{7.26}
\]

\[
\hat{p}(\theta|\mathcal{D}) = \frac{1}{Z} \hat{p}(\theta, \mathcal{D}) = \mathcal{N}(\theta|\hat{\theta}, \mathbf{H}^{-1}) \tag{7.27}
\]

\[
Z = e^{-\mathcal{E}(\hat{\theta})} (2\pi)^{D/2} |\mathbf{H}|^{-\frac{1}{2}} \tag{7.28}
\]

最后一行源自多元高斯分布的归一化常数。

拉普拉斯近似易于应用，因为我们可以利用现有优化算法计算 MAP 估计，然后只需计算众数处的海森矩阵。（在高维空间中，我们可以使用对角线近似。）

在图 7.3b 中，我们展示了将此方法应用于我们 1 维问题的情况。不幸的是，我们发现这并不是一个特别好的近似。这是因为后验是偏斜的，而高斯分布是对称的。此外，感兴趣的参数位于受限区间 \(\theta \in [0, 1]\) 上，而高斯分布假设的是无约束空间 \(\theta \in \mathbb{R}^D\)。幸运的是，我们可以通过变量变换来解决后一个问题。例如，在此情况下，我们可以将拉普拉斯近似应用于 \(\alpha = \operatorname{logit}(\theta)\)。这是一种简化推断工作的常见技巧。关于拉普拉斯近似在贝叶斯逻辑回归中的应用，参见第 15.3.5 节；关于在贝叶斯神经网络中的应用，参见第 17.3.2 节。

## 7.4.4 变分推断

在第 7.4.3 节中，我们讨论了拉普拉斯近似，它使用优化程序来找到 MAP 估计，然后基于海森矩阵近似该点处后验的曲率。在本节中，我们讨论 **变分推断 (VI)**，也称为 **变分贝叶斯 (VB)**。这是另一种基于优化的后验推断方法，但具有更大的建模灵活性（因此可以给出更准确的近似）。

VI 试图用一个可处理的分布 \(q(\theta)\) 来近似一个不可处理的概率分布（如 \(p(\theta|\mathcal{D})\)），以最小化分布之间的某些差异 \(D\)：

\[
q^* = \operatorname{argmin}_{q \in \mathcal{Q}} D(q, p) \tag{7.29}
\]

其中 \(\mathcal{Q}\) 是某个可处理的分布族（例如，完全因子化分布）。与其优化函数 \(q\)，我们通常优化函数 \(q\) 的参数；我们将这些 **变分参数** 记为 \(\psi\)。

通常使用 KL 散度（第 5.1 节）作为差异度量，其由下式给出

\[
D(q, p) = D_{\mathrm{KL}}(q(\theta|\psi) \parallel p(\theta|\mathcal{D})) = \int q(\theta|\psi) \log \frac{q(\theta|\psi)}{p(\theta|\mathcal{D})} d\theta \tag{7.30}
\]

其中 \(p(\theta|\mathcal{D}) = p(\mathcal{D}|\theta)p(\theta)/p(\mathcal{D})\)。推断问题随后归结为以下优化问题：

![](img/ca72c1626f4850f058a9edc138c1ac73_378_0.png)

图 7.4: 应用于 beta-Bernoulli 模型的 ADVI。(a) 近似后验与真实后验。(b) 随时间变化的负 ELBO。(c) 随时间变化的变分 \(\mu\) 参数。(d) 随时间变化的变分 \(\sigma\) 参数。由 adv_beta_binom.ipynb 生成。

\[
\psi^* = \underset{\psi}{\text{argmin}} D_{\text{KL}} (q(\theta|\psi) \parallel p(\theta|\mathcal{D}))
\]

\[
= \underset{\psi}{\text{argmin}} \mathbb{E}_{q(\theta|\psi)} \left[ \log q(\theta|\psi) - \log \left( \frac{p(\mathcal{D}|\theta)p(\theta)}{p(\mathcal{D})} \right) \right]
\]

\[
= \underset{\psi}{\text{argmin}} \underbrace{\mathbb{E}_{q(\theta|\psi)} [-\log p(\mathcal{D}|\theta) - \log p(\theta) + \log q(\theta|\psi)]}_{-\text{L}(\psi)} + \log p(\mathcal{D})
\]

注意 \(\log p(\mathcal{D})\) 与 \(\psi\) 无关，因此在拟合近似后验时可以忽略它，只需专注于最大化以下项

\[
\text{L}(\psi) \triangleq \mathbb{E}_{q(\theta|\psi)} [\log p(\mathcal{D}|\theta) + \log p(\theta) - \log q(\theta|\psi)]
\]

由于 \(D_{\text{KL}} (q \parallel p) \ge 0\)，我们有 \(\text{L}(\psi) \le \log p(\mathcal{D})\)。量 \(\log p(\mathcal{D})\)，即 log 边缘似然，也称为 **证据**。因此 \(\text{L}(\psi)\) 称为 **证据下界** 或 **ELBO**。通过最大化这个下界，我们使变分后验更接近真实后验。（详情见第 10.1 节。）

我们可以选择任何喜欢的近似后验类型。例如，我们可以使用高斯分布，\(q(\theta|\psi) = \mathcal{N}(\theta|\boldsymbol{\mu}, \boldsymbol{\Sigma})\)。这与拉普拉斯近似不同，因为在 VI 中，我们优化

![](img/ca72c1626f4850f058a9edc138c1ac73_379_0.png)

图 7.5: 使用 MCMC 近似 beta-Bernoulli 模型的后验。(a) 由 4 条独立链的样本推导的核密度估计。(b) 链生成后验样本的迹图。由 hmc_beta_binom.ipynb 生成。

\(\Sigma\)，而不是将其等同于海森矩阵。如果 \(\Sigma\) 是对角的，我们假设后验是完全因子化的；这称为 **平均场近似**。

高斯近似并不总是适用于所有变分推断。例如，在我们的 1 维示例中，我们有约束 \(\theta \in [0, 1]\)。我们可以使用形式 \(q(\theta|\psi) = \text{Beta}(\theta|a, b)\) 的变分近似，其中 \(\psi = (a, b)\)。然而，选择合适的变分分布形式需要一定的专业知识。为了创建一种更易于应用，或者说 “开箱即用” 的方法，适用于广泛的模型，我们可以使用一种称为自动微分变分推断 (ADVI) [Kuc+16] 的方法。该方法使用变量变换将参数转换为无约束形式，然后计算高斯变分近似。该方法还使用自动微分来推导计算变换变量密度所需的雅可比项。详情见第 10.2.2 节。

我们现在将 ADVI 应用于我们的 1 维 beta-Bernoulli 模型。令 \(\theta = \sigma(z)\)，其中我们将 \(p(\theta|\mathcal{D})\) 替换为 \(q(z|\psi) = \mathcal{N}(z|\mu, \sigma)\)，其中 \(\psi = (\mu, \sigma)\)。我们使用 SGD 优化 ELBO 的随机近似。结果如图 7.4 所示，似乎很合理。

## 7.4.5 马尔可夫链蒙特卡洛 (MCMC)

虽然 VI 很快，但它可能会给出有偏的后验近似，因为它被限制在特定的函数形式 \(q \in \mathcal{Q}\) 中。一种更灵活的方法是使用一组样本的非参数近似，\(q(\boldsymbol{\theta}) \approx \frac{1}{S} \sum \delta(\boldsymbol{\theta} - \boldsymbol{\theta}^*)\)。这称为蒙特卡洛近似。关键问题是如何有效地创建后验样本 \(\boldsymbol{\theta}^* \sim p(\boldsymbol{\theta}|\mathcal{D})\)，而无需计算归一化常数 \(p(\mathcal{D}) = \int p(\boldsymbol{\theta}, \mathcal{D})d\boldsymbol{\theta}\)。

对于低维问题，我们可以使用重要性采样等方法，我们将在第 11.5 节讨论。然而，对于高维问题，更常见的是使用马尔可夫链蒙特卡洛 (MCMC)。我们将在第 12 章详细介绍，但在此简要介绍。

最常见的 MCMC 类型称为 Metropolis-Hastings 算法。MH 的基本思路如下：我们从参数空间中的一个随机点开始，然后通过从提议分布 \(q(\boldsymbol{\theta}'|\boldsymbol{\theta})\) 中采样新状态（参数）来进行随机游走。如果仔细选择 \(q\)，则得到的马尔可夫链分布将满足这样一个性质，即所占比例的


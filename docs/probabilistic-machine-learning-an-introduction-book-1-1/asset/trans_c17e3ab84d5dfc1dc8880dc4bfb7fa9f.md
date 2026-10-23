

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_257_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_257_1.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_257_2.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_257_3.png)

*图 7.29：使用对 logits 的高斯近似来近似 beta-Bernoulli 模型的后验分布，即 \(q(\alpha)=\mathcal{N}(\alpha|\mu,\sigma)\)，其中 \(\alpha = \mathrm{logit}(\theta)\)。(a) 随时间变化的变分均值估计。(b) 随时间变化的变分标准差估计。(c) 随时间变化的 ELBO。(d) 从变分后验分布的样本中推导出的原始参数 \(\theta \in [0,1]\) 的内核密度估计。由 beta_binom_approx_post_pymc3.py 生成。*

由于 \(\mathbb{E}[\mathrm{KL}(q\|p)] \ge 0\)，因此 \(\mathcal{L}(q) \le \log p(\mathcal{D})\)。量 \(\log p(\mathcal{D})\)（即对数边缘似然）也被称为**证据**（evidence）。因此，\(\mathcal{L}(q)\) 被称为**证据下界**（evidence lower bound）或 **ELBO**。

使用高斯近似后验 \(q(\theta|\xi)=\mathcal{N}(\theta|\mu,\Sigma)\) 很常见，其中 \(\xi=(\mu,\Sigma)\) 是我们要优化的**变分参数**。（这与拉普拉斯近似不同，在拉普拉斯近似中，高斯参数是通过在众数附近构建二次近似来选择的，而不是通过优化来使整体拟合分布。）如果 \(\Sigma\) 是对角矩阵，则假设后验是完全因子化的；这被称为**均值场**近似。

在参数受限（例如 \(\theta \in [0,1]\)）的情况下，我们可以为每个未知变量使用不同类型的变分后验，例如 beta 分布或 Dirichlet 分布。（这是均值场假设的一个优点。）然而，选择最优的后验形式需要一定程度的专业知识。为了创建一种更容易应用或“即插即用”、适用于广泛模型的方法，我们可以使用一种称为**自动微分变分推断**（automatic differentiation variational inference）或 **ADVI** 的方法 [Kuc+16]。该方法使用自动微分（第 13.3 节）来推导计算变换变量密度所需的雅可比项；然后将其与高斯变分推断相结合，并通过优化 ELBO 来拟合。

我们在图 7.29 中对我们的 1D beta-Bernoulli 模型应用 ADVI。具体来说，我们使用以下近似：

\[
p(\alpha|\mathcal{D}) \approx q(\alpha) = \mathcal{N}(\alpha|\mu,\sigma), \text{ 其中 } \alpha = \mathrm{logit}(\theta).
\]

我们使用 SGD（随机梯度下降）优化 ELBO（这被称为**随机变分推断**）。在面板 a-b 中，我们将 \(\mu\) 和 \(\sigma\) 绘制为优化步数的函数。我们可以看到 \(\mu\) 已收敛，但 \(\sigma\) 仍在优化中。在面板 c 中，我们绘制了负的 ELBO。我们可以看到它（近似地）收敛到一个常数，该常数是负对数边缘似然的上界。最后，在面板 d 中，我们从 \(q(\alpha)\) 中绘制样本，转换为 \(\theta = \sigma(\alpha)\)，然后绘制 \(p(\theta|\mathcal{D})\) 的 KDE 近似。我们可以看到这是对图 7.28 中显示的真实 beta 后验分布的一个相当好的近似。

## 7.7.4 马尔可夫链蒙特卡罗（MCMC）近似

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_258_0.png)

*图 7.30：使用 MCMC 近似 beta-Bernoulli 模型的后验分布。(a) 从 4 个独立链的样本中推导出的内核密度估计。(b) 链生成后验样本时的迹线图。由 beta_binom_approx_post_pymc3.py 生成。*

尽管变分推断（VI）是一种基于优化的快速方法，但它可能给出后验分布的有偏近似，因为它受限于特定的函数形式 \(q \in \mathcal{Q}\)。一种更灵活的方法是使用一组样本的非参数近似，

\[
q(\theta) \approx \frac{1}{S} \sum_{s=1}^S \delta(\theta - \theta^s).
\]

这被称为后验分布的**蒙特卡洛近似**。关键问题是如何有效地生成后验样本 \(\theta^s \sim p(\theta|\mathcal{D})\)，而无需评估归一化常数 \(p(\mathcal{D}) = \int p(\theta,\mathcal{D})\,d\theta\)。解决此问题的一种常见方法被称为**马尔可夫链蒙特卡罗**（Markov chain Monte Carlo）或 **MCMC**；其最常见的变体被称为**Metropolis–Hastings 算法**。

Metropolis-Hastings (MH) 的基本思想如下：我们从参数空间中的一个随机点开始，然后通过从**提议分布** \(q(\theta'|\theta)\) 中采样新状态（参数）来进行随机游走。如果 \(q\) 选择得当，生成的马尔可夫链分布将满足这样一个性质：我们在空间中访问每个点的时间比例与该点的后验概率成正比。（有关理论细节，参见例如 [BZ20]。）关键点是，为了决定是移动到新提议的点 \(\theta'\) 还是停留在当前点 \(\theta\)，我们只需要评估未归一化的密度比

\[
\frac{p(\theta|\mathcal{D})}{p(\theta'|\mathcal{D})}
= \frac{\frac{p(\mathcal{D}|\theta)p(\theta)}{p(\mathcal{D})}}{\frac{p(\mathcal{D}|\theta')p(\theta')}{p(\mathcal{D})}}
= \frac{p(\mathcal{D},\theta)}{p(\mathcal{D},\theta')} \tag{7.235}
\]

这避免了计算归一化常数 \(p(\mathcal{D})\) 的需要。（在实践中，我们通常使用对数概率而不是联合概率，以避免数值问题。）

我们看到算法的输入只是一个计算对数联合密度 \(\log p(\theta,\mathcal{D})\) 的函数，以及一个决定访问哪些状态的提议分布 \(q(\theta'|\theta)\)。通常使用高斯分布作为提议分布，\(q(\theta'|\theta)=\mathcal{N}(\theta'|\theta,\sigma I)\)；这被称为**随机游走 Metropolis** 算法。然而，这可能非常低效，因为它在空间中盲目行走，希望能找到高概率区域。

在具有条件独立结构的模型中，通常很容易逐个计算每个变量 \(d\) 的**全条件分布** \(p(\theta_d \mid \theta_{-d}, \mathcal{D})\)，然后从中采样。这类似于坐标上升的随机类比，被称为**吉布斯采样**（Gibbs sampling）。

对于所有未知变量都是连续的模型，我们通常可以计算对数联合密度 \(\nabla_{\theta} \log p(\theta, \mathcal{D})\) 的梯度。我们可以利用这些梯度信息来引导提议进入概率较高的空间区域。这种方法被称为**哈密顿蒙特卡罗**（Hamiltonian Monte Carlo）或 HMC，由于其速度，它是使用最广泛的 MCMC 算法之一。有关详情，参见例如 [Bet17]。

我们在图 7.30 中对我们的 beta-Bernoulli 模型应用 HMC。（我们对参数使用 logit 变换。）在面板 b 中，我们显示了算法从 4 个并行马尔可夫链生成的样本。我们可以看到它们围绕真实后验分布振荡，符合预期。（与变分推断不同，目标并不是使变分参数收敛到单点，因此这种随机波动是好的。）在面板 a 中，我们从每条链的后验样本中计算内核密度估计（我们也可以将样本合并为一个大型集合）；我们看到结果是对图 7.28 中真实后验分布的一个好的近似。

## 7.7.5 使用假设密度滤波的在线推断

在本节中，我们讨论如何递归地（即在线）计算（近似的）后验分布 \(p(\theta_t \mid \mathcal{D}_{1:t})\)，其中 \(\mathcal{D}_{1:t} = \{(x_n, y_n) : n = 1:t\}\) 是我们迄今为止看到的所有数据。这在数据以连续流形式到达的情况下特别有用。

我们将使用一种称为假设密度滤波（assumed density filtering）或 ADF [May79] 的技术，该技术通过用似然更新先验分布，然后强制精确的一步后验分布进入近似族，从而反复强制后验分布具有特定形式（在我们的情况下，为高斯分布）。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_259_0.png)

*图 7.31：假设密度滤波的预测-更新-投射循环示意图。*

更具体地说，我们（通过归纳法）假设我们的先验分布 \(q(\theta_{t-1}) \approx p(\theta_{t-1} \mid \mathcal{D}_{t-1})\) 满足 \(q_{t-1} \in \mathcal{Q}\)，其中 \(\mathcal{Q}\) 是一个可处理分布族（例如具有对角协方差矩阵的高斯分布，或离散分布的乘积）。我们可以使用新的测量值更新先验分布，如下所示得到近似后验分布。首先我们计算**一步前预测分布**

\[
q_{t\mid t-1}(\theta_t) = \int p(\theta_t \mid \theta_{t-1}) q_{t-1}(\theta_{t-1})\,d\theta_{t-1} \tag{7.236}
\]


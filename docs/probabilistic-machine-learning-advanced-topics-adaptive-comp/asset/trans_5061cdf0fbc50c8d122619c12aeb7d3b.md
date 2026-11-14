

在伯努利模型的情况下，我们证明了后验是一个贝塔分布。贝塔后验的方差由

```
\(\mathbb{V} [\theta | \mathcal{D}] = \frac{\tilde{\alpha}\tilde{\beta}}{(\tilde{\alpha} + \tilde{\beta})^2(\tilde{\alpha} + \tilde{\beta} + 1)} = \frac{(\tilde{\alpha} + N_1)(\tilde{\beta} + N_0)}{(\tilde{\alpha} + N_1 + \tilde{\beta} + N_0)^2(\tilde{\alpha} + N_1 + \tilde{\beta} + N_0 + 1)}\)
```

如果 \(N \gg \tilde{\alpha} + \tilde{\beta}\)，这简化为

```
\(\mathbb{V} [\theta | \mathcal{D}] \approx \frac{N_1 N_0}{(N_1 + N_0)^2(N_1 + N_0)} = \frac{N_1}{N} \frac{N_0}{N} \frac{1}{N} = \frac{\hat{\theta}(1 - \hat{\theta})}{N}\)
```

其中 \(\hat{\theta} = N_1/N\) 是最大似然估计（MLE）。因此标准误差由

```
\(\sigma = \sqrt{\mathbb{V} [\theta | \mathcal{D}]} \approx \sqrt{\frac{\hat{\theta}(1 - \hat{\theta})}{N}}\)
```

我们看到，不确定性以降低 \(1/\sqrt{N}\) 的速率下降。我们也看到，不确定性（方差）在 \(\hat{\theta} = 0.5\) 时最大，当 \(\hat{\theta}\) 接近 0 或 1 时最小。这很合乎逻辑，因为确定一枚硬币有偏比确定它是公平的更容易。

## 3.2.1.7 可信区间

后验分布（通常）是一个高维对象，难以可视化和处理。总结此类分布的常用方法是计算一个点估计，例如后验均值或众数，然后计算一个**可信区间**，它量化了与该估计相关的不确定性。（可信区间不同于置信区间，后者是频率派统计学的一个概念，我们将在 3.3.5.1 节中讨论。）

```
\(C_\alpha(\mathcal{D}) = (\ell, u) : P(\ell \le \theta \le u | \mathcal{D}) = 1 - \alpha\)
```

可能有许多区间满足公式 (3.18)，因此我们通常选择一个使得每个尾部的概率质量为 \((1 - \alpha)/2\) 的区间；这称为**中心区间**。如果后验具有已知的函数形式，我们可以使用 \(\ell = F^{-1}(\alpha/2)\) 和 \(u = F^{-1}(1 - \alpha/2)\) 计算后验中心区间，其中 \(F\) 是后验的累积分布函数（cdf），\(F^{-1}\) 是逆累积分布函数。例如，如果后验是高斯分布，\(p(\theta | \mathcal{D}) = \mathcal{N}(0, 1)\)，且 \(\alpha = 0.05\)，则我们有 \(\ell = \Phi^{-1}(\alpha/2) = -1.96\)，\(u = \Phi^{-1}(1 - \alpha/2) = 1.96\)，其中 \(\Phi\) 表示高斯分布的累积分布函数。这证明了以 \(\mu \pm 2\sigma\) 的形式引用可信区间的常见做法是合理的，其中 \(\mu\) 表示后验均值，\(\sigma\) 表示后验标准差，而 2 是 1.96 的一个良好近似。

中心区间的一个问题是，中心区间外部可能存在比内部概率更高的点，如图 3.2(a) 所示。这促使了一种替代量，称为**最高后验密度**或 **HPD** 区域，即概率高于某个阈值的点集合。更准确地说，我们在概率密度函数（pdf）上找到阈值 \(p^*\)，使得

```
\(1 - \alpha = \int_{\theta : p(\theta | \mathcal{D}) > p^*} p(\theta | \mathcal{D}) d\theta\)
```

![](img/ca72c1626f4850f058a9edc138c1ac73_99_0.png)

图 3.2：(a) 中心区间和 (b) Beta(3,9) 后验的 HPD 区域。CI 为 (0.06, 0.52)，HPD 为 (0.04, 0.48)。改编自 [Hof09] 中的图 3.6。由 betaHPD.ipynb 生成。

然后定义 HPD 为

\( C_\alpha(\mathcal{D}) = \{ \theta : p(\theta|\mathcal{D}) \ge p^* \} \)

在一维中，HPD 区域有时也被称为**最高密度区间**或 **HDI**。例如，图 3.2(b) 显示了 Beta(3,9) 分布的 95% HDI，即 (0.04, 0.48)。我们看到，它比中心区间更窄，尽管它仍然包含了 95% 的概率质量；此外，其内部每个点的密度都高于外部每个点的密度。

## 3.2.1.8 后验预测分布

假设我们想要预测未来的观测值。最优的贝叶斯方法是通过对所有未知参数进行边缘化来计算**后验预测分布**：

\( p(\mathbf{y}|\mathcal{D}) = \int p(\mathbf{y}|\boldsymbol{\theta})p(\boldsymbol{\theta}|\mathcal{D})d\boldsymbol{\theta} \)

有时计算这个积分可能很困难（即使我们已经获得了后验）。一种常见的近似是直接“代入”参数的一个点估计，\(\hat{\boldsymbol{\theta}} = \delta(\mathcal{D})\)，其中 \(\delta()\) 是某些估计器，例如用于计算 MLE 或 MAP 的方法，这给出了

\( p(\mathbf{y}|\mathcal{D}) \approx p(\mathbf{y}|\hat{\boldsymbol{\theta}}) \)

这称为**插件近似**。这等同于使用一个以点估计为中心的退化分布来建模后验

\( p(\boldsymbol{\theta}|\mathcal{D}) \approx \delta(\boldsymbol{\theta} - \hat{\boldsymbol{\theta}}) \)

其中 \(\delta\) 是狄拉克三角函数。这源自三角函数的**筛选性质**：

\( p(\mathbf{y}|\mathcal{D}) = \int p(\mathbf{y}|\boldsymbol{\theta})p(\boldsymbol{\theta}|\mathcal{D})d\boldsymbol{\theta} = \int p(\mathbf{y}|\boldsymbol{\theta})\delta(\boldsymbol{\theta} - \hat{\boldsymbol{\theta}})d\boldsymbol{\theta} = p(\mathbf{y}|\hat{\boldsymbol{\theta}}) \)

不幸的是，插件近似可能导致过拟合。例如，考虑抛硬币示例，假设我们连续观察到 \(N=3\) 次正面。MLE 是 \(\hat{\theta} = 3/3 = 1\)。然而，如果我们使用这个估计进行预测，我们会预测反面是不可能的，如果反面真的出现，我们会非常惊讶。\(^1\)

与使用插件近似相反，我们可以对所有参数值进行边缘化以计算精确的后验预测，如下所示：

\(p(y=1|\mathcal{D}) = \int_0^1 p(y=1|\theta)p(\theta|\mathcal{D})d\theta\)

\(= \int_0^1 \theta \text{Beta}(\theta|\widehat{\alpha}, \widehat{\beta})d\theta = \mathbb{E}[\theta|\mathcal{D}] = \frac{\widehat{\alpha}}{\widehat{\alpha} + \widehat{\beta}}\)

如果我们使用均匀先验，\(p(\theta) = \text{Beta}(\theta|1, 1)\)，则预测分布变为

\(p(y=1|\mathcal{D}) = \frac{N_1 + 1}{N_1 + N_0 + 2}\)

这被称为**拉波恩连续法则**。请注意，这相当于代入公式 (3.10) 中的加一平滑估计；然而，那依赖于相当不自然的 Beta(2,2) 先验，而拉波恩平滑使用的是均匀先验。

## 3.2.1.9 边缘似然

模型 \(\mathcal{M}\) 的边缘似然或证据定义为

\(p(\mathcal{D}|\mathcal{M}) = \int p(\theta|\mathcal{M})p(\mathcal{D}|\theta, \mathcal{M})d\theta\)

在对特定模型的参数进行推断时，我们可以忽略这一项，因为它关于 \(\theta\) 是常数。然而，在选择不同模型时，这一量起着至关重要的作用，我们将在 3.8.1 节中讨论。它对于从数据中估计超参数（一种称为经验贝叶斯的方法）也很有用，我们将在 3.7 节中讨论。

一般来说，计算边缘似然可能很困难。然而，在 beta-Bernoulli 模型的情况下，边缘似然与后验归一化常数与先验归一化常数之比成正比。要看到这一点，回顾后验由 \(p(\theta|\mathcal{D}) = \text{Beta}(\theta|\widehat{\alpha}, \widehat{\beta})\) 给出，其中 \(\widehat{\alpha}=\tilde{\alpha}+N_1\) 和 \(\widehat{\beta}=\tilde{\beta}+N_0\)。我们知道后验的归一化常数是 \(B(\widehat{\alpha}, \widehat{\beta})\)，其中 \(B\) 是 beta 函数。因此

\(p(\theta|\mathcal{D}) = \frac{p(\mathcal{D}|\theta)p(\theta)}{p(\mathcal{D})} = \frac{1}{p(\mathcal{D})} [\theta^{N_1}(1-\theta)^{N_0}] [\frac{1}{B(\widehat{\alpha}, \widehat{\beta})}\theta^{\widehat{\alpha}-1}(1-\theta)^{\widehat{\beta}-1}]\)

\(= \frac{1}{p(\mathcal{D})} \frac{1}{B(\widehat{\alpha}, \widehat{\beta})} [\theta^{\widehat{\alpha}+N_1-1}(1-\theta)^{\widehat{\beta}+N_0-1}] = \frac{1}{B(\widehat{\alpha}, \widehat{\beta})} [\theta^{\widehat{\alpha}}(1-\theta)^{\widehat{\beta}}]\)

因此，边缘似然由后验和先验的归一化常数之比给出：

\(p(\mathcal{D}) = \frac{B(\widehat{\alpha}, \widehat{\beta})}{B(\tilde{\alpha}, \tilde{\beta})}\)

1. 这类似于**黑天鹅事件**，指的是 1697 年荷兰探险家首次抵达澳大利亚时发现黑天鹅，而他们此前终生只见过白天鹅（详情见 https://en.wikipedia.org/wiki/Black_swan_theory）。


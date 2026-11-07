
对三个响应变量同时进行一次 `MANOVA` 会使 I 型错误率保持固定在为该 `MANOVA` 设定的 `α`（例如，0.05）水平上。这是对执行 `MANOVA` 而非多个 `ANOVAs` 的统计学优势；然而，如果从实质上讲 `MANOVA` 没有意义，如前所述，仅出于统计原因进行 `MANOVA` 模型是没有意义的。这里科学或实质性的理由应优先于统计学理由。

### 4.6.2 扩展单变量模型：Hotelling’s T²
将单变量模型扩展到多变量模型最简单、最直接的方式是通过简单组间 `t`-检验并推广到 Hotelling 的 `T²`，它是多变量对应物，其中我们对多于一个连续响应变量进行建模。这本质上可以推广到更复杂的模型，但我们关注 `t`-检验，因为它强调了从单变量到多变量的转变中的核心原理。

回顾我们在基本统计回顾中讨论过的单变量 `t`-检验：212

$$\\begin{array}{l} {t = \\frac{E\\left( {\\overline{y}}\_{1} \\right) - E\\left( {\\overline{y}}\_{2} \\right) - \\delta\_{0}}{\\sqrt{\\frac{\\left( n\_{1} - 1 \\right)s\_{1}^{2} + \\left( n\_{2} - 1 \\right)s\_{2}^{2}}{n\_{1} - n\_{2} - 2}\\left( {\\frac{1}{n\_{1}} + \\frac{1}{n\_{2}}} \\right)}}} \\\\ {\\,\\,\\, = \\frac{\\mu\_{1} - \\mu\_{2} - \\delta\_{0}}{\\sqrt{\\frac{\\left( n\_{1} - 1 \\right)s\_{1}^{2} + \\left( n\_{2} - 1 \\right)s\_{2}^{2}}{n\_{1} - n\_{2} - 2}\\left( {\\frac{1}{n\_{1}} + \\frac{1}{n\_{2}}} \\right)}}} \\\\ \\end{array}$$

现在考虑将 `t` 平方时会发生什么，

$$t^{2} = \\frac{\\left( {\\overline{y}}\_{1} - {\\overline{y}}\_{2} \\right)^{2}}{\\frac{\\left( n\_{1} - 1 \\right)s\_{1}^{2} + \\left( n\_{2} - 1 \\right)s\_{2}^{2}}{n\_{1} - n\_{2} - 2}\\left( {\\frac{1}{n\_{1}} + \\frac{1}{n\_{2}}} \\right)}$$

接下来，我们将分母表示为逆，使其没有分母：

$$t^{2} = \\left( {\\overline{y}}\_{1} - {\\overline{y}}\_{2} \\right)\\left\\lbrack {\\frac{\\left( n\_{1} - 1 \\right)s\_{1}^{2} + \\left( n\_{2} - 1 \\right)s\_{2}^{2}}{n\_{1} - n\_{2} - 2}\\left\\lbrack {\\frac{1}{n\_{1}} + \\frac{1}{n\_{2}}} \\right\\rbrack} \\right\\rbrack^{- 1}\\left( {\\overline{y}}\_{1} - {\\overline{y}}\_{2} \\right)$$

最后，我们得到

$$T^{2} = \\frac{n\_{1}n\_{2}}{n\_{1} + n\_{2}}\\left( {\\overline{y}}\_{1} - {\\overline{y}}\_{2} \\right)'\\left( S^{- 1} \\right)\\left( {\\overline{y}}\_{1} - {\\overline{y}}\_{2} \\right)$$

(4.24)

对于单样本均值向量，对应的 `T²` 如下：

$$\\begin{array}{l} {T^{2} = \\left( \\overline{y} - \\mu\_{0} \\right)'\\left( {\\frac{1}{n}S} \\right)^{- 1}\\left( \\overline{y} - \\mu\_{0} \\right)} \\\\ {\\,\\,\\,\\,\\,\\,\\, = n\\left( \\overline{y} - \\mu\_{0} \\right)'S^{- 1}\\left( \\overline{y} - \\mu\_{0} \\right)} \\\\ \\end{array}$$

(4.25)

`T²` 的分布为 $\\frac{\\left( n - 1 \\right)p}{\\left( n - p \\right)}F\_{p,n - p}$，其中 `p` 和 `n - p` 为自由度，其中 `p` 为变量数，`n` 为样本量。有关似然比检验与 `T²` 关系的详细内容，请参阅 Johnson 和 Wichern（[2007](#ref.xhtml#re_CIT000173)，第 217–218 页）。`T²` 和多变量总体的置信区域也可以计算（见 Johnson & Wicher，[2007](#ref.xhtml#re_CIT000173)，第 220–221 页）。

### 4.6.3 多变量检验统计量
在单变量 `ANOVA` 设定中，只有一个 `F`-检验需要执行。在多变量设定中，由于响应变量的协方差在自变量组内可能以不同方式结构化，已开发出多种多变量检验，并在几乎所有软件中均可用。这些包括 `Wilk’s lambda`、`Pillai’s trace`、`Roy’s largest root` 和 `Lawley-Hotelling’s trace`。我们仅对多变量检验的多样性提供一个粗略的“一瞥”。有关这些检验如何产生的完整推导，请参阅 [Johnson 和 Wichern (2007)](#ref.xhtml#re_CIT000173)。213

Wilk’s lambda，`Λ`，由下式给出

$$\\Lambda = \\frac{\\left| E \\right|}{\\left| H + E \\right|} = \\frac{\\left| E \\right|}{\\left| T \\right|}$$

(4.26)

在零假设下，

$$\\Lambda = \\frac{\\left| E \\right|}{\\left| 0 + E \\right|} = \\frac{\\left| E \\right|}{\\left| E \\right|} = 1.0$$

其中 `H` 是“假设”矩阵，`E` 是“误差”矩阵。请注意，Wilk’s 是一个逆准则，意味着如果没有效应，我们期望 `Λ` 等于 1.0。这与单变量 `ANOVA` 中的 `F`-比值不同，后者更偏好较大的 F 而非较小的。

在相反的极端情况下，如果 `H` 解释了所有变异，则，

$$\\Lambda = \\frac{\\left| 0 \\right|}{\\left| H + 0 \\right|} = \\frac{\\left| 0 \\right|}{\\left| H \\right|} = 0$$

Wilk’s lambda 也可以用 `E^(-1)H` 的特征值表示：

$$\\Lambda = {\\prod\\limits\_{i = 1}^{s}\\frac{1}{1 + \\lambda\_{i}}}$$

(4.27)

其中 `λ[i]` 是从分析中提取的特征值。

Pillai’s trace 定义为

$$V^{(s)} = {tr}\\left\\lbrack {\\left( E + H \\right)^{- 1}H} \\right\\rbrack = {\\sum\\limits\_{i = 1}^{s}\\frac{\\lambda\_{i}}{1 + \\lambda\_{i}}}$$

(4.28)

请注意，Pillai’s 使用所有特征值（通常称为“根”），`λ[i]`。如果我们仅使用其中最大的根，就会得到 `Roy’s largest root`。也就是说，Roy’s largest root 只是提取的最大特征值，因此仅代表数据背后最大的维度。Roy’s largest root 在一个维度主导所有其他维度时特别有用，这意味着一个特征值远大于其他特征值。当特征值的分布更分散时，Pillai’s 更合适，因为很可能不止一个维度是感兴趣的。

最后，Lawley-Hotelling’s trace 只是特征值的和，因此由下式给出

$$U^{(s)} = \\text{tr}\\left( E^{- 1}H \\right) = {\\sum\\limits\_{i = 1}^{s}\\lambda\_{i}}$$

(4.29)

### 4.6.4 评估协方差矩阵相等性：The Box-M Test
请回忆，在单变量 `ANOVA` 中，我们需要评估所有方差相等的假设。在多变量对应物中，我们不仅要处理方差；我们还要处理协方差。因此，假设现在包括自变量各水平（或单元格）之间的所有协方差相等，即214

`H[0]`: `Σ[1]` = `Σ[2]` = `Σ[3]`... = `Σ[p]`

(4.30)

其中 `Σ[p]` 是自变量各水平下每个总体的 `p` 个协方差矩阵。

评估该假设有不同的方法。其中一种只是粗略的（但仍有用的）视觉方法，以了解协方差矩阵是否彼此相对相似，从而认为其总体对应物至少近似相等并继续进行 `MANOVA`。`Box-M test` 是另一种评估该假设的方法，可在 R 的 `biotools` 包中获得（[da Silva, 2021](#ref.xhtml#re_CIT000075)），在 `boxM` 检验下，可直接从该包在 iris 数据上轻松演示：

```
> library(biotools)
> data(iris)
> boxM(iris[, -5], iris[, 5])
Box M-test for Homogeneity of Covariance Matrices
data: iris[, -5]
Chi-Sq (approx.) = 140.94, df = 20, p-value < 2.2e-16
```

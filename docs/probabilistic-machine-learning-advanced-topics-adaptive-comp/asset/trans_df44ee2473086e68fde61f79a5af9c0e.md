

估计，其中动作空间是返回一个参数向量，我们将其表示为 \(\hat{\theta} = \delta(\mathcal{D})\)。例如，\(\hat{\theta}\) 可以是最大似然估计、MAP 估计或矩估计。

估计器的**抽样分布**是如果我们多次将估计器应用于从某个分布中抽取的不同数据集时所看到的结果分布；在参数估计的背景下，它是 \(\hat{\theta}\) 的分布，视为依赖于随机样本 \(\mathcal{D}\) 的随机变量。更详细地说，想象从某个真实模型 \(p(\boldsymbol{x}|\boldsymbol{\theta}^*)\) 中抽取 \(S\) 个不同的数据集，每个大小为 \(N\)，以生成

```
\(\tilde{\mathcal{D}}^{(s)} = \{ \boldsymbol{x}_n \sim p(\boldsymbol{x}_n | \boldsymbol{\theta}^*) : n = 1 : N \} \tag{3.36}\)
```

为简洁起见，我们将此表示为 \(\tilde{\mathcal{D}}^{(s)} \sim \boldsymbol{\theta}^*\)。现在将估计器应用于每个 \(\tilde{\mathcal{D}}^{(s)}\) 以得到一组估计，\(\{ \hat{\theta}(\tilde{\mathcal{D}}^{(s)}) \}\)。当 \(S \to \infty\) 时，该集合诱导的分布是估计器的抽样分布。更准确地说，我们有

```
\(p(\delta(\tilde{\mathcal{D}}) = \boldsymbol{\theta} | \tilde{\mathcal{D}} \sim \boldsymbol{\theta}^*) \approx \frac{1}{S} \sum_{s=1}^S \delta(\boldsymbol{\theta} - \delta(\tilde{\mathcal{D}}^{(s)})) \tag{3.37}\)
```

我们通常通过蒙特卡洛方法近似此分布，如第 3.3.2 节所述，尽管在某些情况下我们可以解析地计算它，如第 3.3.3 节所述。

## 3.3.2 抽样分布的自助法近似

在估计器是数据的复杂函数，或者样本量较小时，使用一种称为 **自助法** [ET93] 的蒙特卡洛技术来近似其抽样分布通常很有用。

其想法很简单。如果我们知道真实参数 \(\boldsymbol{\theta}^*\)，我们可以从真实分布中生成许多（假设为 \(S\)）伪数据集，每个大小为 \(N\)，使用 \(\tilde{\mathcal{D}}^{(s)} = \{ \boldsymbol{x}_n \sim p(\boldsymbol{x}_n | \boldsymbol{\theta}^*) : n = 1 : N \}\)。然后我们可以从每个样本中计算估计值 \(\hat{\boldsymbol{\theta}}^s = \delta(\tilde{\mathcal{D}}^{(s)})\)，并使用结果 \(\hat{\theta}^s\) 的经验分布作为抽样分布的估计，如公式 (3.37) 所示。由于 \(\boldsymbol{\theta}^*\) 未知，**参数自助法**的想法是使用 \(\hat{\boldsymbol{\theta}} = \delta(\mathcal{D})\) 而不是 \(\boldsymbol{\theta}^*\) 来生成每个采样数据集，即，在公式 (3.37) 中使用 \(\tilde{\mathcal{D}}^{(s)} = \{ \boldsymbol{x}_n \sim p(\boldsymbol{x}_n | \hat{\boldsymbol{\theta}}) : n = 1 : N \}\)。这是对抽样分布的插件近似。

上述方法要求我们为数据拥有一个参数生成模型 \(p(\boldsymbol{x} | \boldsymbol{\theta})\)。一种替代方法，称为 **非参数自助法**，是从原始数据集中有放回地抽取 \(N\) 个数据点。这创建了一个与原始数据集大小相同的新分布 \(\mathcal{D}^{(s)}\)。然而，自助样本中唯一数据点的数量平均只有 \(0.632 \times N\)。（要看到这一点，请注意，某个项目至少被选中一次的概率是 \((1 - (1 - 1/N)^N)\)，对于大 \(N\)，这趋近于 \(1 - e^{-1} \approx 0.632\)。）幸运的是，已经开发出各种改进版本的自助法（见例如 [ET93]）。

图 3.4(a-b) 展示了一个示例，其中我们使用参数自助法计算伯努利分布 MLE 的抽样分布。（使用非参数自助法的结果基本相同。）当 \(N=10\) 时，我们看到抽样分布是不对称的，因此远离高斯分布，但当 \(N=100\) 时，分布看起来更像高斯分布，正如理论所暗示的那样（参见第 3.3.3 节）。

![](img/ca72c1626f4850f058a9edc138c1ac73_105_0.png)

![](img/ca72c1626f4850f058a9edc138c1ac73_105_1.png)

![](img/ca72c1626f4850f058a9edc138c1ac73_105_2.png)

![](img/ca72c1626f4850f058a9edc138c1ac73_105_3.png)

图 3.4：Bootstrap（顶行）vs 贝叶斯（底行）。N 个数据案例是从 Ber(\(\theta = 0.7\)) 生成的。左列：N = 10。右列：N = 100。（a-b）伯努利分布 MLE 抽样分布的 Bootstrap 近似。我们展示了从 B = 10,000 个 Bootstrap 样本得出的直方图。（c-d）使用均匀先验从后验分布中抽取 10,000 个样本的直方图。由 bootstrap_demo_bernoulli.ipynb 生成。

一个自然的问题是：自助法计算的参数估计 \(\hat{\theta}^s = \delta(\mathcal{D}^{(s)})\) 与从后验 \(\theta^s \sim p(\cdot|\mathcal{D})\) 中抽样的参数值之间有什么联系？从概念上讲，它们相当不同。但在估计器是 MLE 且先验不很强的常见情况下，它们可能相当相似。例如，图 3.4(c-d) 展示了一个示例，其中我们使用均匀 Beta(1,1) 先验计算后验，然后从中采样。我们看到后验和抽样分布相当相似。因此，可以将自助分布视为“穷人的”后验 [HTF01, p235]。

然而，也许令人惊讶的是，自助法可能比后验采样更慢。原因在于自助法必须生成 S 个采样数据集，然后对每个数据集拟合一个模型。相比之下，在后验采样中，给定单个数据集后，我们只需要“拟合”一次模型。（一些在大规模数据集上应用自助法时加速的方法在 [Kle+11] 中有讨论。）

## 3.3.3 MLE 抽样分布的渐近正态性

最常见的估计器是 MLE。当样本量变大时，某些模型的 MLE 的抽样分布变为高斯分布。这被称为抽样分布的**渐近正态性**。更正式地，我们有以下结果：

### 定理 3.3.1. 在各种技术条件下，我们有

```
\(\sqrt{N}(\hat{\theta} - \theta^*) \to \mathcal{N}(\mathbf{0}, \mathbf{F}(\theta^*)^{-1})\)
```

其中 \(\mathbf{F}(\theta^*)\) 是 Fisher 信息矩阵，定义于公式 (3.40)，\(\theta^*\) 是估计器将要应用的数据生成过程的参数，而 \(\to\) 表示分布收敛。

Fisher 信息矩阵等于对数似然的黑塞矩阵，如第 3.3.4 节所示，因此 \(\mathbf{F}(\theta^*)\) 测量了在真实参数值处对数似然曲面的曲率。因此，我们可以这样解释该定理：当样本量趋于无穷时，MLE 的抽样分布将收敛到以真实参数为中心、精度等于 Fisher 信息的高斯分布。因此，具有信息量（尖峰）似然的问题将确保参数被数据“好好确定”，因此当该估计器应用于不同数据集 \(\hat{\mathcal{D}}\) 时，估计值 \(\hat{\theta}\) 围绕 \(\theta^*\) 的变化将非常小。

## 3.3.4 Fisher 信息矩阵

在本节中，我们讨论一个称为 **Fisher 信息矩阵** 的重要量，它与对数似然函数的曲率相关。这在频率派统计学中起着关键作用，用于表征第 3.3.3 节讨论的 MLE 的抽样分布。然而，它也用于贝叶斯统计（用于推导 Jeffreys’ 无信息先验，如第 3.5.2 节所述），以及在优化中（作为自然梯度下降程序的一部分，如第 6.4 节所述）。

### 3.3.4.1 定义

评分函数定义为对数似然的梯度：

```
\(\mathbf{s}(\theta) \triangleq \nabla \log p(\mathbf{x}|\theta)\)
```

**Fisher 信息矩阵 (FIM)** 定义为评分函数的协方差：

```
\(\mathbf{F}(\theta) \triangleq \mathbb{E}_{\mathbf{x} \sim p(\mathbf{x}|\theta)} [\nabla \log p(\mathbf{x}|\theta) \nabla \log p(\mathbf{x}|\theta)^\mathsf{T}]\)
```

因此，第 \((i,j)\) 项的形式为

```
\(F_{ij} = \mathbb{E}_{\mathbf{x} \sim \theta} [ \left( \frac{\partial}{\partial \theta_i} \log p(\mathbf{x}|\theta) \right) \left( \frac{\partial}{\partial \theta_j} \log p(\mathbf{x}|\theta) \right) ]\)
```

我们将在下面对这个量进行解释。

### 3.3.4.2 FIM 与 NLL 黑塞矩阵的等价性

在本节中，我们证明 Fisher 信息矩阵等于负对数似然（NLL）的期望黑塞矩阵

```
\(\text{NLL}(\theta) = - \log p(\mathcal{D}|\theta)\)
```


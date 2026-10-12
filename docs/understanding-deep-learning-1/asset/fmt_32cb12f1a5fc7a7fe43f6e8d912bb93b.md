
# 最大似然准则与损失函数构建

## 5.1.3 对数似然

最大似然准则（公式 5.1）不太实用。每一项 `Pr(y[i] | f[x[i], ϕ])` 都可能很小，因此许多此类项的乘积可能极小。用有限精度算术表示该量可能比较困难。幸运的是，我们可以等价地最大化似然的对数：

![c5-fig-5003.jpg](images/c5-fig-5003.jpg)

(5.3)

这个**对数似然**准则是等价的，因为对数是单调递增函数：如果 `z > z'`，则 `log[z] > log[z']`，反之亦然（[图 5.2](#c005.xhtml#c5-fig-0002)）。由此可见，当我们改变模型参数 `ϕ` 以改进对数似然准则时，也会改进原来的最大似然准则。这也意味着两个准则的整体最大值必定在同一位置，因此最佳模型参数 `ϕ̂` 在两种情况下是相同的。然而，对数似然准则具有使用项的和而非积的实际优势，因此用有限精度表示它不是问题。

![Figure 5.2 The log transform. a) The log function is monotonically increasing. If z > z′, then log[z] > log[z′]. It follows that the maximum of any function g[z] will be at the same position as the maximum of log[g[z]]. b) A function g[z]. c) The logarithm of this function log[g[z]]. All positions on g[z] with a positive slope retain a positive slope after the log transform, and those with a negative slope retain a negative slope. The position of the maximum remains the same.](images/c5-fig-0002.jpg)

[图 5.2](#c005.xhtml#c5-fig-0002a) 对数变换。a) 对数函数单调递增。如果 `z > z'`，则 `log[z] > log[z']`。由此可见，任意函数 `g[z]` 的最大值位置将与 `log[g[z]]` 的最大值位置相同。b) 函数 `g[z]`。c) 该函数的对数 `log[g[z]]`。`g[z]` 上所有具有正斜率的位置在对数变换后保持正斜率，具有负斜率的位置保持负斜率。最大值的位置保持不变。

### 5.1.4 最小化负对数似然

最后，按照惯例，模型拟合问题通常表述为最小化损失。要将最大对数似然准则转换为最小化问题，我们乘以负一，得到**负对数似然准则**：

![c5-fig-5005.jpg](images/c5-fig-5005.jpg)

(5.4)

这构成了最终的损失函数 `L[ϕ]`。

### 5.1.5 推理

网络不再直接预测输出 `y`，而是确定 `y` 上的概率分布。执行推理时，我们通常想要点估计而非分布，因此返回分布的最大值：

![c5-fig-5006.jpg](images/c5-fig-5006.jpg)

(5.5)

通常可以用模型预测的分布参数 `θ` 来表示该表达式。例如，在单变量正态分布中，最大值出现在均值 `μ` 处。

## 5.2 基于最大似然构建损失函数的配方

使用最大似然方法为训练数据 `{x[i], y[i]}` 构建损失函数的配方如下：

1.  选择一个合适的概率分布 `Pr(y | θ)`，其定义在预测 `y` 的域上，具有分布参数 `θ`。
2.  设置机器学习模型 `f[x, ϕ]` 来预测这些参数中的一个或多个，即 `θ = f[x, ϕ]` 且 `Pr(y | θ) = Pr(y | f[x, ϕ])`。
3.  为了训练模型，找到使训练数据集对 `{x[i], y[i]}` 上的负对数似然损失函数最小化的网络参数 `ϕ̂`：

    ![c5-fig-5007.jpg](images/c5-fig-5007.jpg)

    (5.6)

4.  对于新的测试样本 `x` 执行推理时，返回完整分布 `Pr(y | f[x, ϕ̂])` 或该分布的最大值。

本章其余大部分内容将致力于使用此配方为常见预测类型构建损失函数。

## 5.3 示例 1：单变量回归

我们首先考虑单变量回归模型。目标是使用具有参数 `ϕ` 的模型 `f[x, ϕ]` 从输入 `x` 预测单个标量输出 `y ∈ ℝ`。遵循该配方，我们选择输出域 `y` 上的概率分布。我们选择单变量正态分布（[图 5.3](#c005.xhtml#c5-fig-0003)），其定义在 `y ∈ ℝ` 上。该分布有两个参数（均值 `μ` 和方差 `σ²`），概率密度函数为：

![c5-fig-5008.jpg](images/c5-fig-5008.jpg)

(5.7)

![Figure 5.3 The univariate normal distribution (also known as the Gaussian distribution) is defined on the real line z ∈ ℝ and has parameters μ and σ2. The mean μ determines the position of the peak. The positive root of the variance σ2 (the standard deviation) determines the width of the distribution. Since the total probability density sums to one, the peak becomes higher as the variance decreases and the distribution becomes narrower.](images/c5-fig-0003.jpg)

[图 5.3](#c005.xhtml#c5-fig-0003a) 单变量正态分布（也称为高斯分布）定义在实数线 `z ∈ ℝ` 上，具有参数 `μ` 和 `σ²`。均值 `μ` 决定峰值的位置。方差 `σ²` 的正平方根（标准差）决定分布的宽度。由于总概率密度之和为 1，随着方差减小分布变窄，峰值会变高。

其次，我们设置机器学习模型 `f[x, ϕ]` 来计算该分布的一个或多个参数。这里我们只计算均值，即 `μ = f[x, ϕ]`：

![c5-fig-5009.jpg](images/c5-fig-5009.jpg)

(5.8)

我们旨在找到使训练数据 `{x[i], y[i]}` 在该分布下概率最大的参数 `ϕ`（[图 5.4](#c005.xhtml#c5-fig-0004)）。为此，我们基于负对数似然选择损失函数 `L[ϕ]`：

![c5-fig-5010.jpg](images/c5-fig-5010.jpg)

(5.9)

![Figure 5.4 Equivalence of least squares and maximum likelihood loss for the normal distribution. a) Consider the linear model from figure 2.2. The least squares criterion minimizes the sum of the squares of the deviations (dashed lines) between the model prediction f[xi, ϕ] (green line) and the true output values yi (orange points). Here the fit is good, so these deviations are small (e.g., for the two highlighted points). b) For these parameters, the fit is bad, and the squared deviations are large. c) The least squares criterion follows from the assumption that the model predicts the mean of a normal distribution over the outputs and that we maximize the probability. For the first case, the model fits well, so the probability Pr(yi|xi) of the data (horizontal orange dashed lines) is large (and the negative log probability is small). d) For the second case, the model fits badly, so the probability is small and the negative log probability is large.](images/c5-fig-0004.jpg)

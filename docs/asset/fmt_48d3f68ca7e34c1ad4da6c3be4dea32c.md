
## 5.1.4 最小化负对数似然

最后，按照惯例，模型拟合问题通常表述为最小化损失。要将最大对数似然准则转换为最小化问题，我们乘以负一，得到**负对数似然准则**：

![c5-fig-5005.jpg](img/c5-fig-5005.jpg)

(5.4)

这构成了最终的损失函数 `L[ϕ]`。

## 5.1.5 推理

网络不再直接预测输出 `y`，而是确定 `y` 上的概率分布。执行推理时，我们通常想要点估计而非分布，因此返回分布的最大值：

![c5-fig-5006.jpg](img/c5-fig-5006.jpg)

(5.5)

通常可以用模型预测的分布参数 `θ` 来表示该表达式。例如，在单变量正态分布中，最大值出现在均值 `μ` 处。

## 5.2 基于最大似然构建损失函数的配方

使用最大似然方法为训练数据 `{x[i], y[i]}` 构建损失函数的配方如下：

1.  选择一个合适的概率分布 `Pr(y | θ)`，其定义在预测 `y` 的域上，具有分布参数 `θ`。
2.  设置机器学习模型 `f[x, ϕ]` 来预测这些参数中的一个或多个，即 `θ = f[x, ϕ]` 且 `Pr(y | θ) = Pr(y | f[x, ϕ])`。
3.  为了训练模型，找到使训练数据集对 `{x[i], y[i]}` 上的负对数似然损失函数最小化的网络参数 `ϕ̂`：

    ![c5-fig-5007.jpg](img/c5-fig-5007.jpg)

    (5.6)

4.  对于新的测试样本 `x` 执行推理时，返回完整分布 `Pr(y | f[x, ϕ̂])` 或该分布的最大值。

本章其余大部分内容将致力于使用此配方为常见预测类型构建损失函数。

## 5.3 示例 1：单变量回归

我们首先考虑单变量回归模型。目标是使用具有参数 `ϕ` 的模型 `f[x, ϕ]` 从输入 `x` 预测单个标量输出 `y ∈ ℝ`。遵循该配方，我们选择输出域 `y` 上的概率分布。我们选择单变量正态分布（图 5.3），其定义在 `y ∈ ℝ` 上。该分布有两个参数（均值 `μ` 和方差 `σ²`），概率密度函数为：

![c5-fig-5008.jpg](img/c5-fig-5008.jpg)

(5.7)

![Figure 5.3 The univariate normal distribution (also known as the Gaussian distribution) is defined on the real line z ∈ ℝ and has parameters μ and σ2. The mean μ determines the position of the peak. The positive root of the variance σ2 (the standard deviation) determines the width of the distribution. Since the total probability density sums to one, the peak becomes higher as the variance decreases and the distribution becomes narrower.](img/c5-fig-0003.jpg)

图 5.3 单变量正态分布（也称为高斯分布）定义在实数线 `z ∈ ℝ` 上，具有参数 `μ` 和 `σ²`。均值 `μ` 决定峰值的位置。方差 `σ²` 的正平方根（标准差）决定分布的宽度。由于总概率密度之和为 1，随着方差减小分布变窄，峰值会变高。

其次，我们设置机器学习模型 `f[x, ϕ]` 来计算该分布的一个或多个参数。这里我们只计算均值，即 `μ = f[x, ϕ]`：

![c5-fig-5009.jpg](img/c5-fig-5009.jpg)

(5.8)

我们旨在找到使训练数据 `{x[i], y[i]}` 在该分布下概率最大的参数 `ϕ`（图 5.4）。为此，我们基于负对数似然选择损失函数 `L[ϕ]`：

![c5-fig-5010.jpg](img/c5-fig-5010.jpg)

(5.9)

![Figure 5.4 Equivalence of least squares and maximum likelihood loss for the normal distribution. a) Consider the linear model from figure 2.2. The least squares criterion minimizes the sum of the squares of the deviations (dashed lines) between the model prediction f[xi, ϕ] (green line) and the true output values yi (orange points). Here the fit is good, so these deviations are small (e.g., for the two highlighted points). b) For these parameters, the fit is bad, and the squared deviations are large. c) The least squares criterion follows from the assumption that the model predicts the mean of a normal distribution over the outputs and that we maximize the probability. For the first case, the model fits well, so the probability Pr(yi|xi) of the data (horizontal orange dashed lines) is large (and the negative log probability is small). d) For the second case, the model fits badly, so the probability is small and the negative log probability is large.](images/c5-fig-0004.jpg)

图 5.4 正态分布下最小二乘法与最大似然损失的等价性。a) 考虑图 2.2 中的线性模型。最小二乘准则最小化模型预测值 `f[x[i], ϕ]`（绿线）与真实输出值 `y[i]`（橙点）之间偏差（虚线）的平方和。此处拟合良好，因此这些偏差很小（例如两个高亮显示的点）。b) 对于这些参数，拟合效果差，平方偏差很大。c) 最小二乘准则源于这样一个假设：模型预测输出的正态分布的均值，且我们最大化概率。对于第一种情况，模型拟合良好，因此数据的概率 `Pr(y[i]∣x[i])`（橙色水平虚线）很大（负对数概率很小）。d) 对于第二种情况，模型拟合不佳，因此概率很小，负对数概率很大。

当我们训练模型时，我们寻找能最小化该损失的参数 `ϕ`。

### 5.3.1 最小二乘损失函数

现在让我们对损失函数进行一些代数操作。我们寻求：

```
(5.10)
```

其中，我们在第二行和第三行之间移除了第一项，因为它不依赖于 `ϕ`。我们在第三行和第四行之间移除了分母，因为这只是一个不影响最小值位置的常数缩放因子。

这些操作的结果是最小二乘损失函数，这正是我们在第 2 章讨论线性回归时最初引入的：

```
(5.11)
```

我们看到，最小二乘损失函数自然地源于以下假设：预测误差 (i) 相互独立，且 (ii) 服从均值为 `μ = f[x[i], ϕ]` 的正态分布（图 5.4）。

---

Notebook 5.1

最小二乘损失

---

### 5.3.2 推理

网络不再直接预测 `y`，而是预测 `y` 的正态分布的均值 `μ = f[x, ϕ]`。当我们进行推理时，通常想要一个单一的“最佳”点估计 `ŷ`，因此我们取预测分布的最大值：

```
(5.12)
```

对于一元正态分布，最大值的位置由均值参数 `μ` 决定（图 5.3）。这正是模型计算的内容，所以 `ŷ = f[x, ϕ]`。

### 5.3.3 估计方差

为了构建最小二乘损失函数，我们假设网络预测正态分布的均值。方程 5.11 的最终表达式（或许令人惊讶地）不依赖于方差 `σ²`。然而，没有什么能阻止我们将 `σ²` 视为模型的一个参数，并同时关于模型参数 `ϕ` 和分布方差 `σ²` 最小化方程 5.9：

```
(5.13)
```

在推理中，模型从输入中预测均值 `μ = f[x, ϕ]`，我们在训练过程中学习了方差 `σ²`。前者是最佳预测。后者告诉我们预测的不确定性。

### 5.3.4 异方差回归

上述模型假设数据的方差处处恒定。然而，这可能不切实际。当模型的不确定性随输入数据变化时，我们称之为*异方差*（相对于*同方差*，后者指不确定性恒定）。

建模这一点的一个简单方法是训练一个神经网络 `f[x, ϕ]`，使其同时计算均值和方差。例如，考虑一个具有两个输出的浅层网络。我们将第一个输出表示为 `f[1][x, ϕ]` 并用它来预测均值，将第二个输出表示为 `f[2][x, ϕ]` 并用它来预测方差。

这里有一个复杂性：方差必须为正，但我们无法保证网络总是产生正输出。为确保计算出的方差为正，我们将第二个网络输出通过一个将任意值映射为正值的函数。一个合适的选择是平方函数，得到：

```
(5.14)
```

从而得到损失函数：

```
(5.15)
```

同方差模型和异方差模型在图 5.5 中进行了比较。

![图 5.5 同方差与异方差回归。a) 用于同方差回归的浅层神经网络仅从输入 `x` 预测输出分布的均值 `μ`。b) 结果是，虽然均值（蓝线）是输入 `x` 的分段线性函数，但方差处处恒定（箭头和灰色区域显示 ±2 个标准差）。c) 用于异方差回归的浅层神经网络也预测方差 `σ²`（更准确地说，计算其平方根，然后再平方）。d) 标准差现在也成为输入 `x` 的分段线性函数。](img/c5-fig-0005.jpg)

图 5.5 同方差与异方差回归。a) 用于同方差回归的浅层神经网络仅从输入 `x` 预测输出分布的均值 `μ`。b) 结果是，虽然均值（蓝线）是输入 `x` 的分段线性函数，但方差处处恒定（箭头和灰色区域显示 ±2 个标准差）。c) 用于异方差回归的浅层神经网络也预测方差 `σ²`（更准确地说，计算其平方根，然后再平方）。d) 标准差现在也成为输入 `x` 的分段线性函数。

## 5.4 示例 2：二分类

在*二分类*中，目标是将数据 `x` 分配到两个离散类别 `y ∈ {0, 1}` 中的一个。在此背景下，我们称 `y` 为*标签*。二分类的例子包括：(i) 根据文本数据 `x` 预测餐厅评论是正面 (`y = 1`) 还是负面 (`y = 0`)；(ii) 根据 MRI 扫描 `x` 预测肿瘤是存在 (`y = 1`) 还是不存在 (`y = 0`)。

我们再次遵循第 5.2 节的配方来构建损失函数。首先，我们选择输出空间 `y ∈ {0, 1}` 上的概率分布。一个合适的选择是伯努利分布，它定义在域 `{0, 1}` 上。它有一个参数 `λ ∈ [0, 1]`，表示 `y` 取值为 1 的概率（图 5.6）：

```
(5.16)
```

![图 5.6 伯努利分布。伯努利分布定义在域 `z ∈ {0, 1}` 上，具有一个参数 `λ`，表示观测到 `z = 1` 的概率。由此可知，观测到 `z = 0` 的概率是 `1 − λ`。](img/c5-fig-0006.jpg)

图 5.6 伯努利分布。伯努利分布定义在域 `z ∈ {0, 1}` 上，具有一个参数 `λ`，表示观测到 `z = 1` 的概率。由此可知，观测到 `z = 0` 的概率是 `1 − λ`。

它也可以等价地写为：

```
(5.17)
```

### 第二，我们设置机器学习模型

第二，我们设置机器学习模型 `f[x, ϕ]` 来预测单个分布参数 `λ`。然而，`λ` 只能取 `[0, 1]` 范围内的值，我们无法保证网络输出会落在该范围内。因此，我们将网络输出通过一个将实数 `ℝ` 映射到 `[0, 1]` 的函数。一个合适的函数是 *logistic sigmoid*（图 5.7）：

![c5-fig-5019.jpg](img/c5-fig-5019.jpg)

(5.18)

***

##### 问题 5.1

***

![Figure 5.7 Logistic sigmoid function. This function maps the real line z ∈ ℝ to numbers between zero and one, so sig[z] ∈ [0, 1]. An input of 0 is mapped to 0.5. Negative inputs are mapped to numbers below 0.5, and positive inputs to numbers above 0.5.](images/c5-fig-0007.jpg)

图 5.7 Logistic sigmoid 函数。该函数将实数线 `z ∈ ℝ` 映射到 0 和 1 之间的数字，因此 `sig[z] ∈ [0, 1]`。输入 0 映射为 0.5。负输入映射到低于 0.5 的数字，正输入映射到高于 0.5 的数字。

因此，我们将分布参数预测为 `λ = sig[f[x, ϕ]]`。似然函数现在为：

![c5-fig-5020.jpg](img/c5-fig-5020.jpg)

(5.19)

图 5.8 展示了浅层神经网络模型的此过程。损失函数是训练集的负对数似然：

![c5-fig-5021.jpg](img/c5-fig-5021.jpg)

(5.20)

![Figure 5.8 Binary classification model. a) The network output is a piecewise linear function that can take arbitrary real values. b) This is transformed by the logistic sigmoid function, which compresses these values to the range [0, 1]. c) The transformed output predicts the probability λ that y = 1 (solid line). The probability that y = 0 is hence 1 − λ (dashed line). For any fixed x (vertical slice), we retrieve the two values of a Bernoulli distribution similar to that in figure 5.6. The loss function favors model parameters that produce large values of λ at positions xi that are associated with positive examples yi = 1 and small values of λ at positions associated with negative examples yi = 0.](images/c5-fig-0008.jpg)

图 5.8 二分类模型。a) 网络输出是一个分段线性函数，可以取任意实数值。b) 这通过 logistic sigmoid 函数进行变换，将这些值压缩到范围 `[0, 1]` 内。c) 变换后的输出预测 `y = 1` 的概率 `λ`（实线）。因此 `y = 0` 的概率为 `1 − λ`（虚线）。对于任意固定的 `x`（垂直切片），我们得到类似于图 5.6 中的伯努利分布的两个值。损失函数倾向于使模型参数在与正样本 `y[i] = 1` 相关的位置 `x[i]` 产生较大的 `λ` 值，在与负样本 `y[i] = 0` 相关的位置产生较小的 `λ` 值。

由于将在第 5.7 节中解释的原因，这被称为 *binary cross-entropy loss*（二元交叉熵损失）。

***

##### Notebook 5.2：二元交叉熵损失

***

变换后的模型输出 `sig[f[x, ϕ]]` 预测伯努利分布的参数 `λ`。这代表 `y = 1` 的概率，由此可知 `1 − λ` 代表 `y = 0` 的概率。当我们进行推理时，可能需要 `y` 的点估计，因此如果 `λ > 0.5` 则设 `y = 1`，否则设 `y = 0`。

***

##### 问题 5.2

***

## 5.5 示例 3：多类分类

*Multiclass classification*（多类分类）的目标是将输入数据样本 `x` 分配给 `K > 2` 个类别中的一个，即 `y ∈ {1, 2, …, K}`。现实世界的例子包括：(i) 预测手写数字图像 `x` 中出现的是 `K = 10` 个数字 `y` 中的哪一个；(ii) 预测在不完整句子 `x` 之后跟随的是 `K` 个可能单词 `y` 中的哪一个。

我们再次遵循第 5.2 节中的配方。我们首先选择预测空间 `y` 上的分布。在这种情况下，`y ∈ {1, 2, …, K}`，所以我们选择 *categorical distribution*（图 5.9），它定义在该域上。它有 `K` 个参数 `λ[1], λ[2], …, λ[K]`，它们决定每个类别的概率：

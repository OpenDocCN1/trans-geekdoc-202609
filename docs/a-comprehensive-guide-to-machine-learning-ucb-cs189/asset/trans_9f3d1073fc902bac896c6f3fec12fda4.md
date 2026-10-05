

## 6.3 QDA 分类

```
$= arg \max_{\mu_k, \sigma_k^2} \sum_{i=1}^{n_k} \frac{(x_i - \mu_k)^2}{2\sigma_k^2} - \ln(\sigma_k) - \ln(2\pi)$$
$$= arg \min_{\mu_k, \sigma_k^2} \frac{(x_i - \mu_k)^2}{2\sigma_k^2} + \ln(\sigma_k)
```

注意，上述目标函数不是凸的，因此我们不能简单地对其求数并令其为零！相反，我们将对 $\sigma_k^2$ 和 $\mu_k$ 的最小化分解为一个嵌套优化问题：

```
$$\min_{\mu_k, \sigma_k^2} \sum_{i=1}^{n_k} \frac{(x_i - \mu_k)^2}{2\sigma_k^2} + \ln(\sigma_k) = \min_{\sigma_k^2} \sum_{i=1}^{n_k} \frac{(x_i - \mu_k)^2}{2\sigma_k^2} + \ln(\sigma_k)
```

该优化问题已分解为在固定 $\sigma_k^2$ 的情况下针对 $\mu_k$ 的内部问题，以及在给定最优值 $\hat{\mu}_k$ 的情况下针对 $\sigma_k$ 的外部问题。我们首先求解内部问题。在固定 $\sigma_k^2$ 的情况下，目标函数关于 $\mu_k$ 是凸的，因此我们可以对 $\mu_k$ 求偏导并令其为零：

```
$$\frac{\partial}{\partial\mu_k} \sum_{i=1}^{n_k} \frac{(x_i - \mu_k)^2}{2\sigma_k^2} + \ln(\sigma_k) = \sum_{i=1}^{n_k} \frac{-(x_i - \mu_k)}{\sigma_k^2} = 0 \Rightarrow \hat{\mu}_k = \frac{1}{n_k} \sum x_i$$
```

解决内部问题后，我们得到：

```
$$\min_{\sigma_k^2} \sum_{i=1}^{n_k} \frac{(x_i - \hat{\mu}_k)^2}{2\sigma_k^2} + \ln(\sigma_k) = \min_{\sigma_k^2} \sum_{i=1}^{n_k} \frac{(x_i - \hat{\mu}_k)^2}{2\sigma_k^2} + \ln(\sigma_k)$$
```

注意此目标函数对于 $\sigma_k$ 不是凸的，因此我们不能假设目标函数的临界点就等于目标值。假设 $\sigma_k \geq 0$，临界点为：

- $\sigma_k = 0$：假设所有点 $x_i$ 都等于 $\hat{\mu}_k$，存在两个相互冲突的项：一个 $1/\sigma_k^2$ 项向 $\infty$ 逸散，另一个 $\ln(\sigma_k)$ 项在 $\sigma_k \rightarrow 0$ 时向 $-\infty$ 逸散。注意 $1/\sigma_k^2$ 项的发散速度更快，因此我们可以：
- $\sigma_k = \infty$：这种情况不会导致解，因为它给出的是最大值，而不是最小值。
- 对 $\sigma$ 导数为 0 的点

```
$$\lim_{\sigma_k \rightarrow 0} \sum_{i=1}^{n_k} \frac{(x_i - \hat{\mu}_k)^2}{2\sigma_k^2} + \ln(\sigma_k) = \infty$$

$$ \frac{\partial}{\partial\sigma_k} \sum_{i=1}^{n_k} \frac{(x_i - \hat{\mu}_k)^2}{2\sigma_k^2} + \ln(\sigma_k) = \sum_{i=1}^{n_k} \frac{-(x_i - \hat{\mu}_k)^2}{\sigma_k^3} + \frac{1}{\sigma_k} = 0 \Rightarrow \sigma_k^2 = \frac{1}{n_k} \sum_{i=1}^{n_k} (x_i - \hat{\mu}_k)^2$$
```

我们得出最优点为：

$$\sigma_k^2 = \frac{1}{n_k} \sum_{i=1}^{n_k} (x_i - \hat{\mu}_k)^2$$

## QDA 公式化

假设我们知道所有类别的协方差，我们可以使用贝叶斯规则直接求解优化问题：

```
$k^* = \arg \max P(k) f_k(\mathbf{x})$$
$$= \arg \max \ln P(k) + \ln f_k(\mathbf{x})$$
$$= \arg \max \ln P(k) - \frac{1}{2}(\mathbf{x} - \mu_k)^T \boldsymbol{\Sigma}_k^{-1} (\mathbf{x} - \mu_k) - \frac{1}{2} \ln(|\boldsymbol{\Sigma}_k|) = Q_k(\mathbf{x})$$
```

为了后后参考，我们使用 $Q_k(\mathbf{x}) = \ln P(k) - \frac{1}{2}(\mathbf{x} - \mu_k)^T \boldsymbol{\Sigma}_k^{-1} (\mathbf{x} - \mu_k) - \frac{1}{2} \ln(|\boldsymbol{\Sigma}_k|)$ 来简化我们的符号。

## 6.4 LDA

虽然 QDA 是一种合理的分类方法，但我们可能倾向于简化模型以减少参数数量。其中一种方法是使用**线性判别分析 (LDA)**。与 QDA 一样，LDA 假设类别概率分布从正态分布且具有不同的 $\mu_k$，但 LDA 与 QDA 的不同在于，它要求所有分布共享相同的协方差矩阵 $\boldsymbol{\Sigma}$。在偏差-方差权衡的背景下，这种简化增加了我们方法的偏差，但减少了方差。

LDA 的训练和分类步骤与 QDA 几乎相同。然而，经验协方差的计算方式为：

$$\boldsymbol{\Sigma} = \frac{1}{n} \sum_{i=1}^n (\mathbf{x}_i - \mu)(\mathbf{x}_i - \mu)$$

为了理解此公式作为协方差的加权平均，假设我们按类别排序了数据，并得到：

$$\boldsymbol{\Sigma} = \frac{1}{n} \sum_{i=1}^n (\mathbf{x}_i - \mu)(\mathbf{x}_i - \mu)$$

## 6.5 LDA 与 QDA：差异与决策边界

在 QDA 中，我们使用了二次项，而在 LDA 中是线性项。这些项决定了 x 空间中的决策边界形状。给定两个类别，决策边界是 x 空间中概率相等的点。让我们研究二分类示例。假设两个类别为 A 和 B。任意点 x 可以分类如下：

$$k^* = \begin{cases} A & P(A|x) > P(B|x) \\ B & P(A|x) < P(B|x) \\ \text{A 或 B} & P(A|x) = P(B|x) \end{cases}$$

最简单的情况是两个类别的先验概率相等，且它们的条件概率分布是向同性的。向同性高斯分布的协方差形式为 $\Sigma = \sigma^2I$，这意味着它们的等高线是圆。在这种情况下，$f_A(x)$ 和 $f_B(x)$ 具有相同形式的协方差 $\Sigma_A = \Sigma_B = \sigma^2I$。

![](img/99defe6abed215976e83d28151f33_86_0.png)

图6.1：$\mathbb{R}^2$ 中两个同分布高斯分布的等高线图。圆是高斯分布。

从几何上看，将二维点分类为两个类别之一的任务等同于确定它靠近哪个类别。使用我们之前的 $Q_k(\mathbf{x})$ 符号，这在数学上可以表示为：

$$Q_A(\mathbf{x}) = Q_B(\mathbf{x})$$

$$\ln\left(\frac{1}{2}\right)-\frac{1}{2}(\mathbf{x}-\mu_A)^T\sigma^2(\mathbf{x}-\mu_A)-\frac{1}{2}\ln\left(|\sigma^2|\right)=\ln\left(\frac{1}{2}\right)-\frac{1}{2}(\mathbf{x}-\mu_B)^T\sigma^2(\mathbf{x}-\mu_B)-\frac{1}{2}\ln\left(|\sigma^2|\right)$$
$$(\mathbf{x}-\mu_A)^T(\mathbf{x}-\mu_A)=(\mathbf{x}-\mu_B)^T(\mathbf{x}-\mu_B)$$

对于满足 $|\mathbf{x}-\mu_A||_2=|\mathbf{x}-\mu_B||_2$ 的 $x$，其决策边界是距离 $\mu_A$ 和 $\mu_B$ 等等的点集。该决策边界是线性的，因为距离 $\mu_A$ 和 $\mu_B$ 等等的点恰好是连接这两点的垂直平分线。

## 相同的向异性分布

下一种情况是两个类别的先验概率相等，且它们的条件概率分布是非向同性的。向异性高斯分布就是所有非向同性的高斯分布。


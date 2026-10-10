
这个函数。换句话说，我们最大化类间散度与类内散度的比值。梯度 `∇_w w` 是由 `w(w)` 对每个分量的导数组成的向量。利用导数法则、`[附录 A.2]` 给出的公式以及协方差矩阵和外积的对称性，结果为：

```
$$\mathbf{w}^T (\mathbf{\Sigma}_0 + \mathbf{\Sigma}_1) \mathbf{w} (\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)(\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)^T \mathbf{w} - (\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)^T \mathbf{w}^2 (\mathbf{\Sigma}_0 + \mathbf{\Sigma}_1) \mathbf{w} / 2 = 2 \frac{\mathbf{w}^T (\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)^T \mathbf{w}}{\mathbf{w}^T (\mathbf{\Sigma}_0 + \mathbf{\Sigma}_1) \mathbf{w}} \frac{(\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)^T \mathbf{w}}{\mathbf{w}^T (\mathbf{\Sigma}_0 + \mathbf{\Sigma}_1) \mathbf{w}} (\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1).$$
```

将其置为零并重新整理，得到：

```
$$\mathbf{w}^T (\mathbf{\Sigma}_0 + \mathbf{\Sigma}_1) \mathbf{w} / (\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)^T \mathbf{w} = (\mathbf{\Sigma}_0 + \mathbf{\Sigma}_1)^{-1} (\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1).$$
```

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn import datasets
```

```python
m = datasets.load_iris()
# 我们考虑两个品种。
# setosa 存储在前 50 条目中。
# versicolor 存储在接下来的 50 条目中。
# 我们考虑花瓣长度和宽度，前两个特征。
```

```python
# 计算每个品种的均值。
mean0 = np.mean(m.data[0:50, 0:2], axis = 0)
mean1 = np.mean(m.data[50:100, 0:2], axis = 0)
```

---

![](img/c6c76bf52016db7e78a5e30d4766ef81_120_0.png)

图 4.3：投影到坐标轴上。

朴素地看，可以将分离阈值移动到置信椭圆的交点处。然而，这是主观的，而且不同的置信度值（例如 99%）会移动这个点。此外，由于两个椭圆的轴角度不同，这意味着一类样本的投影比另一类样本的投影更分散。

目标是找到一条投影线，使得：

- 每一类的投影均值尽可能相互分远。
- 每一类的投影样本尽可能相互靠近。

在下一节中，我们将看到 Fisher (1936) 是如何解决这个问题的。

## 4.3 Fisher 判别与线性判别分析

回想，`C_i` 的*样本均值*为：

```
$$\mu_i = \frac{1}{N_i} \sum_{v \in C_i} \mathbf{v}$$
```

为了考虑到样本的变异，我们将 `C_i` 的*样本方差*定义为：

```
$$\Sigma_i = \frac{1}{N_i} \sum_{v \in C_i} (\mathbf{v} - \mathbf{\mu}_i)(\mathbf{v} - \mathbf{\mu}_i)^T. \quad (4.2)$$
```

![](img/c6c76bf52016db7e78a5e30d4766ef81_121_0.png)

图 4.4：垂直于样本均值与 95% 置信椭圆连线的分离。

上面的最后一个表达式是*外积*。外积是列向量与行向量的矩阵乘，而内积是行向量乘以列向量。在二维空间向量 `v1` 和 `v2` 之间，这是：

```
$v_1 v_2^T = \begin{pmatrix} v_{11} \\ v_{12} \end{pmatrix} \begin{pmatrix} v_{21} & v_{22} \end{pmatrix} = \begin{pmatrix} v_{11}v_{21} & v_{11}v_{22} \\ v_{12}v_{21} & v_{12}v_{22} \end{pmatrix}$.
```

一个 `2 × 1` 矩阵是一个 `2 × 2` 矩阵。外积是*张量积*的最简单形式。机器学习中张量的使用与物理等领域张量的使用不同。机器学习中的张量教材与特定的编程语言和实现挂钩。因此，我们在此不作建议。本文将继续使用矩阵。

如果 `M` 是特征的数量（在示例中 `M=2`），那么 `μ_i` 是一个包含 `M` 个元素的向量，第 `j` 个元素是类 `C_i` 中样本的第 `j` 个特征。另一方面，`Σ` 是一个 `M × M` 矩阵。`(j, j)` 对角线元素是类 `C_i` 中样本第 `j` 个特征的方差。方差描述了特征值的离散程度。`(j, k)` 非对角线元素是类 `C_i` 中样本第 `j` 个特征和第 `k` 个特征之间的协方差。协方差描述了不同特征之间相互影响程度。

协方差矩阵通常是*正定*的，因为：

```
$$\mathbf{v}^T \mathbf{\Sigma}_{\mathbf{v}} = \frac{1}{N_i} \sum_{\mathbf{v} \in C_i} \mathbf{v}^T (\mathbf{v} - \boldsymbol{\mu}_i)(\mathbf{v} - \boldsymbol{\mu}_i)^T \mathbf{v} = \frac{1}{N_i} \sum_{\mathbf{v} \in C_i} (\mathbf{v} - \boldsymbol{\mu}_i)^T \mathbf{v}^2 \ge 0.$$
```

并非平方和等于零，因为这意味着所有样本在与 `v` 正交的空间内相对于均值偏移。在这种情况下，特征空间的一个维度是冗余的，应该先进行*降维*。正定性意味着矩阵是非奇异的且可以逆。

令 `w` 为投影方向。投影线的位置被忽略，因为它在计算中抵消了。类 `C_i` 中投影样本的均值为 `w^T μ_i`，而类 `C_i` 中投影样本的方差为 `w^T Σ_i w`。我们看到，当：

```
$$\mathbf{w}^T \mathbf{\Sigma}_{01} \mathbf{w}\|^2 = \mathbf{w}^T (\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)(\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)^T.$$
```

尽可能大，投影均值尽可能分远。这被称为投影样本的*类间散度*。同时，我们让

```
$$\mathbf{w}^T \mathbf{\Sigma}_0 \mathbf{w} + \mathbf{w}^T \mathbf{\Sigma}_1 \mathbf{w} = \mathbf{w}^T (\mathbf{\Sigma}_0 + \mathbf{\Sigma}_1) \mathbf{w}$$
```

尽可能小时，投影样本靠近投影均值。这被称为投影样本的*类内散度*。根据 `w`，Fisher (1936) 定义的*分离* `w` 是通过使：

```
$$\mathbf{w}^T (\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)(\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)^T \mathbf{w} / \mathbf{w}^T (\mathbf{\Sigma}_0 + \mathbf{\Sigma}_1) \mathbf{w}$$
```

这个函数。换句话说，我们最大化类间散度与类内散度的比值。梯度 `∇_w w` 是由 `w(w)` 对每个分量的导数组成的向量。利用导数法则、`[附录 A.2]` 给出的公式以及协方差矩阵和外积的对称性，结果为：

```
$$\mathbf{w}^T (\mathbf{\Sigma}_0 + \mathbf{\Sigma}_1) \mathbf{w} (\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)(\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)^T \mathbf{w} - (\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)^T \mathbf{w}^2 (\mathbf{\Sigma}_0 + \mathbf{\Sigma}_1) \mathbf{w} / 2 = 2 \frac{\mathbf{w}^T (\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)^T \mathbf{w}}{\mathbf{w}^T (\mathbf{\Sigma}_0 + \mathbf{\Sigma}_1) \mathbf{w}} \frac{(\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)^T \mathbf{w}}{\mathbf{w}^T (\mathbf{\Sigma}_0 + \mathbf{\Sigma}_1) \mathbf{w}} (\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1).$$
```

将其置为零并重新整理，得到：

```
$$\mathbf{w}^T (\mathbf{\Sigma}_0 + \mathbf{\Sigma}_1) \mathbf{w} / (\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)^T \mathbf{w} = (\mathbf{\Sigma}_0 + \mathbf{\Sigma}_1)^{-1} (\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1).$$
```

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn import datasets
```

```python
m = datasets.load_iris()
# 我们考虑两个品种。
# setosa 存储在前 50 条目中。
# versicolor 存储在接下来的 50 条目中。
# 我们考虑花瓣长度和宽度，前两个特征。
```

```python
# 计算每个品种的均值。
mean0 = np.mean(m.data[0:50, 0:2], axis = 0)
mean1 = np.mean(m.data[50:100, 0:2], axis = 0)
```

![](img/c6c76bf52016db7e78a5e30d4766ef81_125_0.png)

(a)

(b)

(c)

![](img/c6c76bf52016db7e78a5e30d4766ef81_125_1.png)

(d)

(e)

(f)

图 4.6：使用不同特征的分类。

均值

`μ = 1/K Σ_{i=1}^{K} μ_i.`

**类间散度**定义为

`Σ_b = 1/K Σ_{i=1}^{K} (μ_i - \bar{μ})(μ_i - \bar{μ})^T`

在 `w` 方向上的类间间隔为

`s(w) = w^T Σ_b w / w^T Σ_w w`

为了分离 `K` 个类，我们需要找到方向 `w1, …, w_{K-1}` 使得 `s(w)` 最大。这等价于最大化

`S(W) = [W^T Σ_b W] / [W^T Σ_w W]`

其中 `W` 表示列为向量 `w1, …, w_{K-1}` 的矩阵，`|·|` 表示矩阵的行列式。如果特征数 `M` 大于或等于类别数 `K`，可以证明，当 `w1, …, w_{K-1}` 是对应于广义特征值问题 `K-1` 个最大广义特征值的广义特征向量，则 `S(W)` 取最大：

`Σ_B w = λ Σ_W w.`

这在 MATLAB 中通过 `ClassificationDiscriminant.fit` 实现。而在 Python 中的实现是 `sklearn.discrimin_analysis.LinearDiscriminantAnalysis`。

如图 4.6 所示，某些特征比其他特征更有用。我们在讨论特征选择时会进一步探讨这一点。当类别重叠时，需要考虑进入另一个类别区域的样本是离群点，还是无法使用这些特征进行分离。

## 4.5 在线学习与感知机

到目前为止，我们考虑的是训练数据预可用的学习任务。这被称为批量学习或离线学习。相反，在在线学习中，训练数据按顺序出现。

回想我们寻找一个方向向量 `w` 和间隔阈值 `b`，使得对于样本 `v`：

- `w^T v < b ⇒ v ∈ C0`,
- `w^T v > b ⇒ v ∈ C1`。

通过将向量 `w` 扩展为 `\hat{w}=w-b` 以及 `\hat{v}=(1,v)`，可以重新表述为：

- `\hat{w}^T \hat{v} - b < 0 ⇒ \hat{v} ∈ C0`，
- `\hat{w}^T \hat{v} - b > 0 ⇒ \hat{v} ∈ C1`。

这样，偏置 `b` 就变成了权重向量的一部分。

我们定义函数：

```
sgn(x) = \begin{cases} -1 & \text{if } x < 0 \\ 0 & \text{if } x = 0 \\ 1 & \text{if } x > 0 \end{cases}
```

## 硬限制

| 输入 | | 输出 |
|---|---|---|
| 2 | W, b | 3 |

图 4.7：感知机。

对于样本 `v`

```
$$sgn(w^T v) = -1 \Rightarrow v \in C_0,$$
sgn(w^T v) = 1 \Rightarrow v \in C_1. \quad (4.3)
```

Rosenblatt (1958) 发明了感知机。它是一台用于图像识别的物理机器。它包含 400 个光电池，权重由电位器实现，并通过电动机进行更新。

具体来说，感知机初始化 `w0 = 0`，并在每个新训练样本 `vi` 更新权重 `w_{i-1}`：

```
$$\mathbf{w}_i = \mathbf{w}_{i-1} + (c_i - sgn(\mathbf{w}_{i-1}^T v_i)) \mathbf{v}_i.$$
```

其中 `ci` 是 `vi` 的类别标签，如果 `vi ∈ C0` 则 `ci = -1`，如果 `vi ∈ C1` 则 `ci = 1`。

参数 `0 < α ≤ 1` 是学习率，由用户设置。如果学习率选择太大，任何变化将是剧烈的且会发生震荡。

注意 `wi` 与 `w_{i-1}` 相关。如果类别标签确定错误，分离线将向某个方向拉，使得样本被正确标记的概率更大。`ci - sgn(w_{i-1}^T vi)` 的符号决定了分离线拉动的方向。在任何阶段，权重向量 `wi` 都是迄今为止样本的线性组合。

感知机在 MATLAB 的神经网络框架内实现为单层网络（见图 4.7 和列表 4.2）。在考虑非线性分类时，我们会仔细观察神经网络。

感知机需要看到示例来建立分离线。一个 epoch（周期）是指向算法完整展示一次数据。

图 4.8 显示了感知机看到一定数量数据后不同的分离线。未见的数据用 `×` 标记。学习率设置为 1。由于这个值很大，在看到 90% 数据和看到完整数据集之间，分离线的位置发生了剧烈变化。

在 100 个 epoch 之后，感知机分类了除一个离群点以外的所有样本。感知机需要几百个 epoch 才能正确分类这个样本。给随机数赋予不同的种子：

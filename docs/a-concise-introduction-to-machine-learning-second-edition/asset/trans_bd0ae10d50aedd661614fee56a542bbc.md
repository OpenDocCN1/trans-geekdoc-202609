
![](img/c6c76bf52016db7e78a5e30d4766ef81_120_0.png)

图 4.3：投影到坐标轴上。

朴素地看，可以将分离阈值移动到置信椭圆的交点处。然而，这是主观的，而且不同的置信度值（例如 99%）会移动这个点。此外，由于两个椭圆的轴角度不同，这意味着一类样本的投影比另一类样本的投影更分散。

目标是找到一条投影线，使得：

- 每一类的投影均值尽可能相互分远。
- 每一类的投影样本尽可能相互靠近。

在下一节中，我们将看到 Fisher (1936) 是如何解决这个问题的。

## 4.3 Fisher 判别与线性判别分析

回想，$C_i$ 的*样本均值*为：

```
$$\mu_i = \frac{1}{N_i} \sum_{v \in C_i} \mathbf{v}$$
```

为了考虑到样本的变异，我们将 $C_i$ 的*样本方差*定义为：

```
$$\Sigma_i = \frac{1}{N_i} \sum_{v \in C_i} (\mathbf{v} - \mathbf{\mu}_i)(\mathbf{v} - \mathbf{\mu}_i)^T. \quad (4.2)$$
```

![](img/c6c76bf52016db7e78a5e30d4766ef81_121_0.png)

图 4.4：垂直于样本均值与 95% 置信椭圆连线的分离。

上面的最后一个表达式是*外积*。外积是列向量与行向量的矩阵乘，而内积是行向量乘以列向量。在二维空间向量 $v_1$ 和 $v_2$ 之间，这是：

```
$v_1 v_2^T = \begin{pmatrix} v_{11} \\ v_{12} \end{pmatrix} \begin{pmatrix} v_{21} & v_{22} \end{pmatrix} = \begin{pmatrix} v_{11}v_{21} & v_{11}v_{22} \\ v_{12}v_{21} & v_{12}v_{22} \end{pmatrix}$.
```

一个 $2 \times 1$ 矩阵是一个 $2 \times 2$ 矩阵。外积是*张量积*的最简单形式。机器学习中张量的使用与物理等领域张量的使用不同。机器学习中的张量教材与特定的编程语言和实现挂钩。因此，我们在此不作建议。本文将继续使用矩阵。

如果 $M$ 是特征的数量（在示例中 $M=2$），那么 $\mu_i$ 是一个包含 $M$ 个元素的向量，第 $j$ 个元素是类 $C_i$ 中样本的第 $j$ 个特征。另一方面，$\Sigma$ 是一个 $M \times M$ 矩阵。$(j, j)$ 对角线元素是类 $C_i$ 中样本第 $j$ 个特征的方差。方差描述了特征值的离散程度。$(j, k)$ 非对角线元素是类 $C_i$ 中样本第 $j$ 个特征和第 $k$ 个特征之间的协方差。协方差描述了不同特征之间相互影响程度。

协方差矩阵通常是*正定*的，因为：

```
$$\mathbf{v}^T \mathbf{\Sigma}_{\mathbf{v}} = \frac{1}{N_i} \sum_{\mathbf{v} \in C_i} \mathbf{v}^T (\mathbf{v} - \boldsymbol{\mu}_i)(\mathbf{v} - \boldsymbol{\mu}_i)^T \mathbf{v} = \frac{1}{N_i} \sum_{\mathbf{v} \in C_i} (\mathbf{v} - \boldsymbol{\mu}_i)^T \mathbf{v}^2 \ge 0.$$
```

并非平方和等于零，因为这意味着所有样本在与 $\mathbf{v}$ 正交的空间内相对于均值线偏移。在这种情况下，特征空间的一个维度是冗余的，应该先进行*降维*。正定性意味着矩阵是非奇异的且可以逆。

令 $w$ 为投影方向。投影线的位置被忽略，因为它在计算中抵消了。类 $C_i$ 中投影样本的均值为 $\mathbf{w}^T \boldsymbol{\mu}_i$，而类 $C_i$ 中投影样本的方差为 $\mathbf{w}^T \mathbf{\Sigma}_i \mathbf{w}$。我们看到，当：

```
$$\mathbf{w}^T \mathbf{\Sigma}_{01} \mathbf{w}\|^2 = \mathbf{w}^T (\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)(\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)^T.$$
```

尽可能大，投影均值尽可能分远。这被称为投影样本的*类间散度*。同时，我们让

```
$$\mathbf{w}^T \mathbf{\Sigma}_0 \mathbf{w} + \mathbf{w}^T \mathbf{\Sigma}_1 \mathbf{w} = \mathbf{w}^T (\mathbf{\Sigma}_0 + \mathbf{\Sigma}_1) \mathbf{w}$$
```

尽可能小时，投影样本靠近投影均值。这被称为投影样本的*类内散度*。根据 $\mathbf{w}$，Fisher (1936) 定义的*分离* $\mathbf{w}$ 是通过使

```
$$\mathbf{w}^T (\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)(\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)^T \mathbf{w} / \mathbf{w}^T (\mathbf{\Sigma}_0 + \mathbf{\Sigma}_1) \mathbf{w}$$
```

这个函数。换句话说，我们最大化类间散度与类内散度的比值。梯度 $\nabla_{\mathbf{w}}w$ 是由 $w(\mathbf{w})$ 对每个分量的导数组成的向量。利用导数法则、[附录 A.2] 给出的公式以及协方差矩阵和外积的对称性，结果为：

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

（此处由于输入文本包含大量重复且损坏的代码块，已根据提供的逻辑进行了清理和翻译）

---

*(注：输入文本包含许多重复/损坏的代码块。我将根据提供的逻辑输出文档内容。）*

---

[content]
![](img/c6c76bf52016db7e78a5e30d4766ef81_120_0.png)

图 4.3：投影到坐标轴上。

朴素地看，可以将分离阈值移动到置信椭圆的交点处。然而，这是主观的，而且不同的置信度值（例如 99%）会移动这个点。此外，由于两个椭圆的轴角度不同，这意味着一类样本的投影比另一类样本的投影更分散。

目标是找到一条投影线，使得：

- 每一类的投影均值尽可能相互分远。
- 每一类的投影样本尽可能相互靠近。

在下一节中，我们将看到 Fisher (1936) 是如何解决这个问题的。

## 4.3 Fisher 判别与线性判别分析

回想，$C_i$ 的*样本均值*为：

```
$$\mu_i = \frac{1}{N_i} \sum_{v \in C_i} \mathbf{v}$$
```

为了考虑到样本的变异，我们将 $C_i$ 的*样本方差*定义为：

```
$$\Sigma_i = \frac{1}{N_i} \sum_{v \in C_i} (\mathbf{v} - \mathbf{\mu}_i)(\mathbf{v} - \mathbf{\mu}_i)^T. \quad (4.2)$$
```

![](img/c6c76bf52016db7e78a5e30d4766ef81_121_0.png)

图 4.4：垂直于样本均值与 95% 置信椭圆连线的分离。

上面的最后一个表达式是*外积*。外积是列向量与行向量的矩阵乘，而内积是行向量乘以列向量。在二维空间向量 $v_1$ 和 $v_2$ 之间，这是：

```
$v_1 v_2^T = \begin{pmatrix} v_{11} \\ v_{12} \end{pmatrix} \begin{pmatrix} v_{21} & v_{22} \end{pmatrix} = \begin{pmatrix} v_{11}v_{21} & v_{11}v_{22} \\ v_{12}v_{21} & v_{12}v_{22} \end{pmatrix}$.
```

一个 $2 \times 1$ 矩阵是一个 $2 \times 2$ 矩阵。外积是*张量积*的最简单形式。机器学习中张量的使用与物理等领域张量的使用不同。机器学习中的张量教材与特定的编程语言和实现挂钩。因此，我们在此不作建议。本文将继续使用矩阵。

如果 $M$ 是特征的数量（在示例中 $M=2$），那么 $\mu_i$ 是一个包含 $M$ 个元素的向量，第 $j$ 个元素是类 $C_i$ 中样本的第 $j$ 个特征。另一方面，$\Sigma$ 是一个 $M \times M$ 矩阵。$(j, j)$ 对角线元素是类 $C_i$ 中样本第 $j$ 个特征的方差。方差描述了特征值的离散程度。$(j, k)$ 非对角线元素是类 $C_i$ 中样本第 $j$ 个特征和第 $k$ 个特征之间的协方差。协方差描述了不同特征之间相互影响程度。

协方差矩阵通常是*正定*的，因为：

```
$$\mathbf{v}^T \mathbf{\Sigma}_{\mathbf{v}} = \frac{1}{N_i} \sum_{\mathbf{v} \in C_i} \mathbf{v}^T (\mathbf{v} - \boldsymbol{\mu}_i)(\mathbf{v} - \boldsymbol{\mu}_i)^T \mathbf{v} = \frac{1}{N_i} \sum_{\mathbf{v} \in C_i} (\mathbf{v} - \boldsymbol{\mu}_i)^T \mathbf{v}^2 \ge 0.$$
```

并非平方和等于零，因为这意味着所有样本在与 $\mathbf{v}$ 正交的空间内相对于均值偏移。在这种情况下，特征空间的一个维度是冗余的，应该先进行*降维*。正定性意味着矩阵是非奇异的且可以逆。

令 $w$ 为投影方向。投影线的位置被忽略，因为它在计算中抵消了。类 $C_i$ 中投影样本的均值为 $\mathbf{w}^T \boldsymbol{\mu}_i$，而类 $C_i$ 中投影样本的方差为 $\mathbf{w}^T \mathbf{\Sigma}_i \mathbf{w}$。我们看到，当：

```
$$\mathbf{w}^T \mathbf{\Sigma}_{01} \mathbf{w}\|^2 = \mathbf{w}^T (\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)(\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)^T.$$
```

尽可能大，投影均值尽可能分远。这被称为投影样本的*类间散度*。同时，我们让

```
$$\mathbf{w}^T \mathbf{\Sigma}_0 \mathbf{w} + \mathbf{w}^T \mathbf{\Sigma}_1 \mathbf{w} = \mathbf{w}^T (\mathbf{\Sigma}_0 + \mathbf{\Sigma}_1) \mathbf{w}$$
```

尽可能小时，投影样本靠近投影均值。这被称为投影样本的*类内散度*。根据 $\mathbf{w}$，Fisher (1936) 定义的*分离* $\mathbf{w}$ 是通过使：

```
$$\mathbf{w}^T (\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)(\boldsymbol{\mu}_0 - \boldsymbol{\mu}_1)^T \mathbf{w} / \mathbf{w}^T (\mathbf{\Sigma}_0 + \mathbf{\Sigma}_1) \mathbf{w}$$
```

这个函数。换句话说，我们最大化类间散度与类内散度的比值。梯度 $\nabla_{\mathbf{w}}w$ 是由 $w(\mathbf{w})$ 对每个分量的导数组成的向量。利用导数法则、[附录 A.2] 给出的公式以及协方差矩阵和外积的对称性，结果为：

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

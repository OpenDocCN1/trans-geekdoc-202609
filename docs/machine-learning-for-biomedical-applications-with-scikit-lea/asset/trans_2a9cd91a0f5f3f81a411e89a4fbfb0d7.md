

![](img/d219b4c20ff50f4b97845dec7a9acecb_131_0.png)

**图 5.7** a) 不同脑区域的生长高度相关性；PCA 的目标是将所有数据投影到单一方向 $u_1$（黄色箭头）；b) 最优方向（绿线）是方差最大化的方向，数据点（蓝色）被投影在其上。

数据被投影在其上（图 5.7b），返回了通过特征空间的任何方向的最大方差估计值。我们可以通过考虑数据协方矩阵的特征向量来实现这一点。

## 5.4.1 数据协方矩阵的估计

协方矩阵是一个对称矩阵，其元素代表数据集中元素之间的方差，其中元素可以交替地称为数据集的特征或样本本身。例如，假设我们的数据集 $\mathbf{X} \in \mathbb{R}^{100 \times 4}$ 包含 100 个样本和 4 个特征，我们可以估计样本之间的协方差为：

```
$$\mathbf{C} = \frac{1}{N-1}\mathbf{X}_C\mathbf{X}_C^T. \quad (5.37)$$
```

在这种情况下，矩阵 $\mathbf{C}$ 的形状为 $100 \times 100$，或者我们估计特征之间的协方差为：

```
$$\mathbf{C} = \frac{1}{N-1}\mathbf{X}_C^T\mathbf{X}_C. \quad (5.38)$$
```

形状为 $4 \times 4$。重要的是，在每个实例中我们假设数据已进行均值化：$\mathbf{X}_C = \mathbf{X} - \mathbf{X}$，通过减去每个样本的均值（对应公式 (5.37)）或每个特征的均值（对应公式 (5.38)）。对于降维，我们对后者感兴趣即特征之间的协方差。在这种情况下，我们的协方矩阵看起来如下：

```
$C = \begin{pmatrix} COV_{11} & COV_{12} & COV_{13} & COV_{14} \\ COV_{21} & COV_{22} & COV_{23} & COV_{24} \\ COV_{31} & COV_{32} & COV_{33} & COV_{34} \\ COV_{41} & COV_{42} & COV_{43} & COV_{44} \end{pmatrix} \quad (5.39)$
```

每个单个特征的方差（$COV_{11}, COV_{33}, COV_{44}, COV_{55}$）位于对角线上，不同特征之间的协方差（$COV_{12}, COV_{13}, COV_{14}, COV_{21}, ...$）存储在非对角线上。在这种表示中，方差估计了沿单个特征维的数值分布，而协方差是特征之间共享信息的度。协方矩阵是对称的，这意味着它的特征向量形成了一个新的正交基，能够更好地表示方差特征。

## 5.4.2 推导 PCA

我们从三角函数中知道，数据点 $\mathbf{x}_n$ 在 $\mathbf{v}_1$ 上的投影可以估计为 $|\mathbf{x}_n|cos\theta$，且这两个向量的标量积（点积）为：

```
$\mathbf{x}_n\mathbf{v}_1 = |\mathbf{x}_n|\mathbf{v}_1|cos\theta. \quad (5.40)$
```

因此，通过重新排列公式 (5.40)，我们看到只要 $|\mathbf{v}_1| = 1$，点积就等于标量投影：

```
$|\mathbf{x}_n|cos\theta = \frac{\mathbf{x}_n\mathbf{v}_1}{\|\mathbf{v}_1|}. \quad (5.41)$
```

综合以上考虑，对于 PCA，我们正在寻找一个方向 $\mathbf{v}_1$，使得所有投影数据点的方差最大化。假设我们首先归一化特征向量（$\mathbf{v}_1 = \mathbf{v}_1/|\mathbf{v}_1|$），我们可以将投影到 $\mathbf{v}_1$ 上的点方差表示为：

```
$\frac{1}{N-1}(\mathbf{XC}\mathbf{v}_1)^T(\mathbf{XC}\mathbf{v}_1) = \mathbf{v}_1^T\mathbf{C}\mathbf{v}_1. \quad (5.42)$
```

为了找到使投影方差最大的方向，我们必须对方差 $\mathbf{v}_1$ 关于 $\mathbf{v}_1$ 求导。同时，我们通过约束估计的特征向量具有单位长度来强制执行合理的解。该约束通过拉格朗日乘子法实现：

```
$\mathcal{L}(\mathbf{v}_1, \lambda_1) = \mathbf{v}_1^T\mathbf{C}\mathbf{v}_1 + \lambda_1(1-\mathbf{v}_1^T\mathbf{v}_1). \quad (5.43)$
```

对 $\mathbf{v}_1$ 优化使得 $\mathcal{L}(\mathbf{v}_1, \lambda_1)=0$，则可以简化为：

```
$\mathbf{C}\mathbf{v}_1 = \lambda_1\mathbf{v}_1. \quad (5.44)$
```

这意味着 $\mathbf{v}_1$ 必须是 $\mathbf{C}$ 的特征向量，其中特征值 $\lambda_1 = \mathbf{v}_1^T\mathbf{C}\mathbf{v}_1$ 等于该方向上方差的大小。

## 扩展到高维

我们可以通过约束下一个特征向量与 $v_1$ 正交来将此过程扩展到更高维。这次，我们需要两个拉格朗日乘子 $\lambda_2$ 和 $\phi$，其中 $\phi$ 约束第二个特征向量的幅度并确保 $v_2$ 与 $v_1$ 正交（$v_1^T v_2 = 0$）：

```
$\mathcal{L}(v_2, \lambda_2, \phi) = v_2^T C v_2 + \lambda_2(1 - v_2^T v_2) - \phi v_1^T v_2. \quad (45)$
```

现在，当对 $v_2$ 求导并乘以 $v_1$ 时：

| 项 1 | 项 2 | 项 3 | 结果 |
| :--- | :--- | :--- | :--- |
| $C v_2$ | $-\lambda_2$ | $-\phi v_1$ | $= 0$ (46) |
| $v_1^T v_2$ | $-\lambda_2 v_1^T v_2$ | $-\phi v_1^T v_1$ | $= 0$ (47) |
| $0$ | $-0$ | $-\phi v_1^T v_1$ | $= 0$ (48) |

前两项必须为零，因为存在正交约束 $v_2^T v_1 = 0$，且由于 $v_1^T v_1 = 1$，公式 (48) 告诉我们 $\phi$ 必须为 0。这意味着 $\phi$ 中的所有项都消失了，我们再次得到一个特征方程，这次是针对 $v_2$ 的：

```
$C v_2 = \lambda_2 v_2 \quad (49)$
```

## 5.4.3 从协方矩阵的特征向量估计 PCA

推广到所有维度，$C$ 的特征值分解矩阵方程可以写为：

```
$CV = \Lambda V \quad (50)$
```

这里，$\Lambda$ 是特征值的对角矩阵

$\Lambda = \begin{pmatrix} \lambda_1 & 0 & \dots & 0 \\ 0 & \lambda_2 & \dots & \vdots \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \dots & \lambda_m \end{pmatrix} \quad (51)$

其中特征值代表了每个特征向量（或*主成分*）所描述的方差比例。通常做法是将主成分按幅度降序排列，使得 $\lambda_1$ 对应最大的特征值，$\lambda_2$ 对应第二大的，直到 $\lambda_m$（特征值）。在对特征值排序时，保留 $V$ 的列以保持特征值与特征向量之间的正确关系也是重要的。

> > > 由于协方矩阵是对称的，因此特征基是正交的。

> > 在这里矩阵乘法的特定顺序是重要的。

## 5.4.4 使用奇异值分解估计 PCA

协方矩阵通常不是满秩的（若干特征值为零）。当从具有大量特征的非方矩阵估计时，这种情况常见。在这种情况下，计算变得不稳定，更好的做法是使用奇异值分解（SVD）来实现 PCA。SVD 将特征值分解推广到任意形状的矩阵。例如，对于 $X \in \mathbb{R}^{n \times m}$：

```
X = U\Sigma V^T \quad (52)$
```

SVD 将 $X$ 分解为 $U \in \mathbb{R}^{n \times m}, V \in \mathbb{R}^{m \times m}$ 以及 $\Sigma \in \mathbb{R}^{n \times m}$。在这里，$U$ 和 $V$ 是左右奇异向量，具有单位幅度且相互正交；$\Sigma$ 代表奇异值的矩形对角矩阵 $(r_i)$。非零奇异值的数量由矩阵秩 $r \leq \min(n, m)$ 决定。

如果我们代入 $X$ 公式 (52)，就可以看到 PCA 和 SVD 之间的关系：

```
$X_C X_C^T = U\Sigma V^T (U\Sigma V^T)^T U = U\Sigma V^T V\Sigma^T U^T = U\Sigma^2 U^T \quad (53)$
```

因此，$U$ 反映了数据协方矩阵 $X_C X_C^T$ 的特征向量。V$ 代表 $X_C^T X_C$ 的特征向量。

```
$X_C^T X_C V = (U\Sigma V^T)^T U\Sigma V^T V = V\Sigma^2 V^T \quad (54)$
```

两种情况下，协方矩阵共享 $r$ 个非零特征值（$\Sigma \in \mathbb{R}^{r \times r}$），这些值与 SVD 奇异值的关系为

```
$\lambda_i = \frac{\sigma_i^2}{n-1} \quad (55)$
```

> > 为了可视化，暂时去掉了 $\frac{1}{n-1}$ 归一化项。

> > 在这里我们把归一化项放回来。


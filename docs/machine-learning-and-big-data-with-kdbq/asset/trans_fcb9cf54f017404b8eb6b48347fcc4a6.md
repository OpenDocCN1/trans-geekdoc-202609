
由于 $W$ 是正交矩阵，其逆矩阵由其转置给出，$W^{-1} = W^T$，因此可以通过下式得到逆变换：

```
$X' = ZW^T = XWW^T = X'. \quad (16.64)
```

有时权重——$W$ 的列 $W_{(1)}, W_{(2)}, \dots, W_{(p)}$被称为载荷（loadings）。然而，也可以将以下内容视为载荷——$W$ 的列通过对应特征值坐标的平方根进行缩放：

```
$L = \left( \sqrt{\lambda_{(1)}}w_{(1)} \sqrt{\lambda_{(2)}}w_{(2)} \dots \sqrt{\lambda_{(p)}}w_{(p)} \right) \in \mathbb{R}^{p \times p}. \quad (16.65)
```

由于这种歧义，我们应该完全避免这个术语。注意，与主成分分析（PCA）相关的术语中存在大量的歧义和混淆，特别是在不同领域之间。值得注意的是，主成分之间是不相关的：对于 $1 \le j \neq k \le p$，

```
$Cov[z_{(j)}, z_{(k)}] \propto (X'w_{(j)})^T (X'w_{(k)}) \quad (16.66)\\
= w_{(j)}^T (X')^T Xw_{(k)} \quad (16.67)\\
= w_{(j)}^T \lambda_{(k)}w_{(k)} \quad (16.68)\\
= \lambda_{(k)}w_{(j)}^T w_{(k)} \quad (16.69)\\
= \lambda_{(k)}w_{(k)}^T w_{(k)} \quad (16.70)\\
= \lambda_{(k)} \cdot 0 \quad (16.71)
```

根据正交性，不同的主成分之间是不相关的。

这还将 PCA 与方差解释联系起来。方差产生于：主成分在何种意义上“解释了方差”？线性代数中的事实是，由于 $C$ 是对称的，它可以对角化为：

```
$C = W\Lambda W^T = \sum_{i=1}^p \lambda_{(i)}w_{(i)}w_{(i)}^T. \quad (16.72)
```

其中 $W$ 是一个以 $C$ 的特征向量为列的矩阵：

```
$W = \left( \begin{array}{cccc} | & | & & | \\ w_{(1)} & w_{(2)} & \dots & w_{(p)} \\ | & | & & | \end{array} \right), \quad (16.73)
```

## 特征系统 PCA

且 $\mathbf{\Lambda}$ 是一个以 $\mathbf{C}$ 的特征值为对角线元素的对角矩阵：

$$
\mathbf{\Lambda} = \begin{pmatrix} \lambda_{(1)} & & & \lambda_{(2)} & & & \lambda_{(p)} \end{pmatrix} \quad (16.74)
$$

对于任何矩阵 $\mathbf{A}$ 和 $\mathbf{B}$，如果乘积 $\mathbf{AB}$ 和 $\mathbf{BA}$ 都存在，那么 $\text{tr} \mathbf{BA} $

$$
\text{tr} \mathbf{C} = \text{tr} \mathbf{W\Lambda W^T} = \text{tr} \mathbf{\Lambda^T W W^T} = \text{tr} \mathbf{\Lambda}. \quad (16.75)
$$

因此，前 $d, 1 \leq d \leq p$ 个主成分占据总变异的比例为

$$
\frac{\lambda_{(1)} + \lambda_{(2)} + \dots + \lambda_{(d)}}{\sum_{i=1}^d \lambda_{(i)}} = \frac{\lambda_{(1)} + \lambda_{(2)} + \dots + \lambda_{(p)}}{\sum_{i=1}^p \lambda_{(i)}} \quad (16.76)
$$

## 16.4.5 降维

在数据中寻找有助于我们解释因变量的模式受偏差-方差权衡（bias-variance trade-off）。这可以解释如下：平方偏差通常随着模型复杂性的增加而减少，而方差随着复杂性的增加而增加，总误差是平方偏差和方差分量的之和，因此通常存在一个最优模型复杂度，使得总误差最小。

通过只考虑可用特征的子集可以限制复杂度。特别是，我们可以通过删除列 $d+1, d+2, \dots, p$ 将我们的向量截断在 $1 \leq d < p$ 列：

$$
\mathbf{W}_d = \begin{pmatrix} \mathbf{w}_{(1)} & \mathbf{w}_{(2)} & \dots & \mathbf{w}_{(d)} \end{pmatrix} \in \mathbb{R}^{p \times p}. \quad (16.77)
$$

因此，我们只保留前 $d$ 个主成分：

$$
\mathbf{Z}_d := \mathbf{X}^T \mathbf{W} \in \mathbb{R}^{n \times d}. \quad (16.78)
$$

由于

$$
\text{Var}[\mathbf{Z}] = \text{Var}[\mathbf{X}^T \mathbf{W}] = \mathbf{W}^T \text{Var}[\mathbf{X}] \mathbf{W} \approx \mathbf{W}^T \mathbf{C} \mathbf{W} = \mathbf{\Lambda}, \quad (16.79)
$$

以及类似的，

$$
\text{Var}[\mathbf{Z}_d] = \mathbf{\Lambda}_d, \quad (16.80)
$$

截断的主成分以引入偏差为代价减少了方差 $$ \Lambda_{\Delta} < \Lambda$。

## 16.4.6 PCA 回归 (PCR)

使用 PCA 进行降维的自然扩展是 PCA 回归，或 PCR。在在线回归中，我们使用的模型为

$$
y = X\beta + \epsilon,
$$

其中 $y \in \mathbb{R}^n$ 是输出向量，$\tilde{X} \in \mathbb{R}^{nx^*}$ 是数据矩阵 $X$，左侧了一个全1向量以允许截距（在 $p^* = p+1$ 时）或不允许（在 $p^* = p$ 时）；$\beta \in \mathbb{R}^p$ 是系数向量；$\epsilon \in \mathbb{R}^n$ 是误差项。

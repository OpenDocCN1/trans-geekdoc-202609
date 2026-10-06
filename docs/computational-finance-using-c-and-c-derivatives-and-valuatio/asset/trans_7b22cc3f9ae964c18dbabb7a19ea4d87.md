

## 3.3.3 学生 $t$ 分布

如果 $S_t(\mu,v)$ 表示均值为 $\mu$，自由度为 $v$ 的学生 $t$ 分布，则 $X \sim S_t(0,v)$ 可以通过如下方式生成：

```
$X \sim \frac{Z}{\sqrt{Y/v}} \qquad (3.3.15)
```

其中 $Z \sim N(0,1)$ 且 $Y \sim \chi_v^2$。$X$ 的方差为

```
$E[X^2] = \frac{\nu}{\nu-2}$.
```

具有自由度 $v$、均值为 $\mu$、方差为 $s$ 的学生 $t$ 分布的变量 $X'$ 可以通过修改方程 (3.3.15) 来生成：

```
$X' \sim \mu + \frac{s^{1/2}}{\sqrt{v/(v-2)}}\sqrt{Y/v} \qquad (3.3.16)
```

$X'$ 的概率密度函数 $f(x)$ 为

```
$f(x) = \frac{\Gamma((v+1)/2)}{\Gamma(v/2)^{-1/2}\pi^{1/2}\Gamma(v/2)} \left[ 1 + \frac{(x-\mu)^2}{s(v-2)} \right]^{-(v+1)/2} \qquad (3.3.17)
```

其中 $v > 2$。

## 3.4 多变量分布的生成：相关变量

在本节中，我们将展示如何从具有已知均值和给定协方差矩阵或相关矩阵的多变量分布生成变量。适用于协方差矩阵的方法也适用于相关矩阵，在这种情况下，生成的变量将经过归一化以具有单位方差。

### 3.4.1 相关性和协方差的估计

在这里，我们展示如何从历史市场数据中获取有效的相关矩阵 $C_R$ 或协方差矩阵 $C$。

设 $\hat{X}$ 为 $n \times p$ 数据矩阵，第 $i$ 行包含第 $i$ 个观测值，第 $j$ 列包含第 $j$ 个变量的值。如果我们创建一个新矩阵 $X$，使得 $X$ 的第 $j$ 列的元素为 $X_{i,j} = \hat{X}_{i,j} - \mu_j, i=1,\dots,n$，其中 $\mu_j$ 是 $\hat{X}$ 第 $j$ 列的均值，则 $p \times p$ 矩阵 $C = X^T X$。

此外，如果定义另一个矩阵 $\tilde{X}$ 使得 $\tilde{X}_{i,j} = \frac{\hat{X}_{i,j}-\mu_j}{\sigma_j}, i=1,\dots,n$，其中 $\mu_j$ 是 $\hat{X}$ 第 $j$ 列的均值，$\sigma_j$ 是第 $j$ 列的标准差，则 $p \times p$ 矩阵 $C_r = \tilde{X}^T \tilde{X}$ 是 $\tilde{X}$ 的相关矩阵。

#### 相关矩阵

让我们首先考虑有效相关矩阵的性质。它们如下：

- 矩阵是对称的，且对角线为单位1。
- 矩阵必须是正定的，这意味着所有的特征值都为正。

我们现在证明，如果 $p \times p$ 矩阵 $C_r$ 可以被分解为 $C_r = X^T X$，其中 $X$ 是非奇异的 $n \times m$ 数据矩阵，则它是有效的相关矩阵。
证明如下：

由于 $X$ 是非奇异的，我们可以进行奇异值分解

```
$X = UKV^T$
```

其中 $U$ 是 $n$ 阶正交矩阵，$K$ 是 $n \times p$ 矩阵，包含（非零）奇异值 $\sigma_{i,1}=1\dots,p$ 作为对角元素且其他地方为零，$V$ 是 $p \times p$ 正交矩阵。
我们有：

```
$X^T X = (U K V^T)^T U V^T
= V K^T U^T U V^T
= V K^T K V^T
= V \Sigma V^T$
```

由于 $U^T U = UU^T = I_n$

因此，

```
$C_r = X^T X = V \Sigma V^T$
```

其中 $\Sigma$ 是包含 $C_r$ 特征值的 $p \times p$ 对角矩阵，$V$ 是对应的特征向量矩阵。由于第 $i$ 个特征值满足 $\lambda_i = \sigma_i^2$，可以看出所有特征值都是正的，因此 $C_r$ 必须是正定的。
如果 $C_r$ 是正定的，则可以对其进行 Cholesky 分解 $C_r = LL^T$，其中 $L$ 是下三角矩阵。

### 3.4.2 修复相关矩阵和协方差矩阵

存在提供的相关矩阵不是正定的情况。某些原因如下：

- 数据。相关矩阵中的元素可能是使用不同长度的两两相关性计算的。在这种情况下，方程 $C_r = X^T X$ 不再成立因此 $C_r$ 无法保证是正定的。
- 相关矩阵的手动调整可能发生，特别是当市场崩溃且某些股票价格高度相关时。在这种情况下，最好的办法是将相关矩阵 $C_r$ 修复为有效的相关矩阵 $\hat{C}_r$。

当 $C_r$ 不是正定时（Cholesky 分解失败），我们使用特征值分解

```
$C_r = V\Sigma V^T,$
```

其中

$$\Sigma = \begin{pmatrix} \lambda_1 & \lambda_2 & & \ddots & \lambda_p \end{pmatrix};$$

然后形成矩阵 $K$，它是通过取每个特征值的最大值和一个非常小的数字 $\epsilon$（例如 $10^{-16}$）得到的：

$$K = \begin{pmatrix} \max(\lambda_1, \epsilon) & \max(\lambda_2, \epsilon) & & \ddots & \max(\lambda_p, \epsilon) \end{pmatrix};$$

矩阵 $C_r^+$ 作为相关矩阵是接受的，因为尽管它是实对称且正定的，但其对角元素不是单位。可以通过在 $C_r^+$ 前乘或后乘对角矩阵 $F$ 来修复。为了实现这一点，$F$ 的对角元素必须满足：

$$F_{ii} = \frac{1}{\sqrt{C_{ii}}}.$$

我们有：

$$\hat{C}_r = F C_r^* F = F V K^T V^T = (F V K)(F K)^T. \quad (3.4.1)$$

最优修复矩阵 $C_r^*$ 最小化 $||C_r - C_r^*||$，可以通过 $n$ 维球面上的数值优化获得；然而，已经发现 $\hat{C}_r$ 是 $C_r^*$ 的良好近似。

在这里，我们提供了如何使用球面坐标获取最优修复矩阵的细节，参见 Rebonato 和 Jäck (1999)；另一种方法参见 Higham (2002) 或 Qi 和 Sun (2006)。$n$ 维球面半径为 $r$ 的第 $i$ 个点的可以表示为：

$x_{i,1} = r \cos(\theta_{i,1}),$
$x_{i,2} = r \sin(\theta_{i,1})\cos(\theta_{i,2}),$
$x_{i,3} = r \sin(\theta_{i,1})\sin(\theta_{i,2})\cos(\theta_{i,3}),$
$x_{i,4} = r \sin(\theta_{i,1})\sin(\theta_{i,2})\sin(\theta_{i,3})\cos(\theta_{i,4}),$
$\dots$
$x_{i,n-1} = r \sin(\theta_{i,1})\sin(\theta_{i,2})\dots\sin(\theta_{i,n-2})\cos(\theta_{i,n-1}),$
$x_{i,n} = r \sin(\theta_{i,1})\sin(\theta_{i,2})\dots\sin(\theta_{i,n-2})\sin(\theta_{i,n-1}).$

其中 $\theta_{i,k}$ 是球面坐标并满足以下约束：$0 \le \theta_{i,k} \le \pi, k = 1, \dots, n-2$，且 $0 \le \theta_{i,n-1} \le 2\pi$。

根据构造，球面的半径满足：

```
$r^2 = \sum_{k=1}^{n} (x_{i,k})^2.
```

这如下所示：

```
$(B^T B)_{i,i} = r^2 \{ \cos^2(\theta_{i,1}) + \sin^2(\theta_{i,1}) (\cos^2(\theta_{i,2}) + \sin^2(\theta_{i,2})) + \cos^2(\theta_{i,3}) + \sin^2(\theta_{i,3})) \times ( \cos^4(\theta_{i,1}) + \sin^2(\theta_{i,n-2})\cos^2(\theta_{i,n-1}) + \sin^2(\theta_{i,n-1}) \dots ) } = r^2,
```

其中我们使用了 $\cos^2(\theta_{i,k}) + \sin^2(\theta_{i,k}) = 1, k = 1, \dots, n-1$。

如果 $r = 1$，$n$ 维球面的坐标存储在 $n \times n$ 矩阵 $B^T$ 的 $n$ 行中，

$B_{i,1}^T = \cos(\theta_{i,1}),$
$B_{i,j}^T = \cos(\theta_{i,j}) \sin^{j-1}(\theta_{i,k}) \quad j=2,\dots,n-1,$
$B_{i,n}^T = \sin^{n-1}(\theta_{i,k}), \quad n>1,$

$B^T = \begin{pmatrix} 1 & 0 & 0 & \dots & \dots & \dots \\ \cos(\theta_{2,1}) & \sin(\theta_{2,1}) & 0 & \dots & \dots & \dots \\ \cos(\theta_{3,1}) & \sin(\theta_{3,1}) & \cos(\theta_{3,2}) & 0 & \dots & \dots \\ \vdots & \vdots & \vdots & \ddots & \vdots & \vdots \end{pmatrix}$

Cholesky 分解可以通过将 $B^T$ 的上三角元素设为零形成，这导致：

```
$L^T = \begin{pmatrix} 1 & 0 & 0 & \dots & \dots & \dots \\ \cos(\theta_{2,1}) & \sin(\theta_{2,1}) & 0 & \dots & \dots & \dots \\ \cos(\theta_{3,1}) & \sin(\theta_{3,1}) & \cos(\theta_{3,2}) & 0 & \dots & \dots \\ \vdots & \vdots & \vdots & \ddots & \vdots & \vdots \end{pmatrix}$
```

$L_{1,1}^T = 1,$
$L_{i,1}^T = \cos(\theta_{i,1}),$
$L_{i,j}^T = \cos(\theta_{i,j}) \sin^{j-1}(\theta_{i,k}) \quad j=2,\dots,i-1,$
$L_{i,j}^T = \sin^{i-1}(\theta_{i,k}), \quad i>1.$




## 附录3
## 奇异值分解

机器学习中使用的任何形式的数据都以矩阵的形式表示。在这些矩阵上执行矩阵加法、矩阵减法、H 乘积等各种操作，以构建机器学习的数学模型。当我们处理具有数十或数百个特征的数百万数据点时，矩阵操作必须经过优化。因此，我们需要使用线性代数来使这些操作在我们构建的机器学习模型计算机上变得可行。

矩阵操作简化的需求之一是在不丢失原始矩阵信息的情况下减小矩阵的尺寸。矩阵的**奇异值分解（SVD）**是一种在保留矩阵核心信息的同时降低矩阵维数的技术。

在本章中，我们将通过图像压缩的示例来理解 SVD。

## 结构

在本章中，我们将讨论以下主题：

- 使用 SVD 进行矩阵分解
- 使用 SVD 进行图像压缩

## 掌握机器学习的分类算法

- 压缩黑白图像
- 压缩彩色图像

## 使用 SVD 进行矩阵分解

设 A 为一个秩为 $r$ 的 $m \times n$ 矩阵。那么存在一个 $m \times n$ 矩阵 $\Sigma$，其 $D$ 中的对角元素是 A 的前 $r$ 个奇异值，$\sigma_1 \ge \sigma_2 \ge \cdots \ge \sigma_r > 0$，且存在 $m \times n$ 正交矩阵 $U$ 和 $n \times n$ 正交矩阵 $V$，使得：

```
A = U \Sigma V^T
```

任何分解形式 $A = U\Sigma V^T$，其中 $U$ 和 $V$ 为正交矩阵，$\Sigma = \begin{bmatrix} D & 0 \\ 0 & 0 \end{bmatrix}$ 且 $D$ 的对角元素为正，均称为 A 的奇异值分解（SVD）。$U$ 和 $V$ 矩阵并不由 A 唯一确定，但 $\Sigma$ 的对角元素必然是 A 的奇异值。在此类分解中，$U$ 的列称为 A 的左奇异向量，$V$ 的列称为 A 的右奇异向量。

> 注意：存在逆矩阵的方阵称为奇异矩阵。奇异矩阵的行列式始终为 0。

假设 A 和 B 是两个维度为 $n *$ 的矩阵。如果 $AB = I = BA$，则 A 和 B 是非奇异矩阵。这里，$I$ 是单位矩阵，即对角线元素为 1 而非对角线元素为 0 的矩阵。

让我们来理解这个例子。

考虑如下定义的矩阵 A。

```
A = \begin{bmatrix} 1 & 0 \\ 1 & 1 \end{bmatrix}
```

我们可以看到 A 是一个 $2 \times 3$ 矩阵，即 A 有两行三列。使用 SVD，我们将 A 分解为三个矩阵 $U$、$\Sigma$ 和 $V$，使得 $A = U\Sigma V^T$ 且 $\Sigma = \begin{bmatrix} D & 0 \\ 0 & 0 \end{bmatrix}$，其中 $D$ 是一个所有元素均为正对角矩阵。

首先，我们需要找到奇异值 $\sigma_i$。由于 A 不是方阵，我们找到 $A^T A$ 的特征值，其中 $A^T$ 是矩阵 A 的转置。

```
B = A^T A = \begin{bmatrix} 1 & 1 \\ -1 & 1 \end{bmatrix} \begin{bmatrix} 1 & 0 & -1 \\ 0 & 1 & 1 \end{bmatrix} = \begin{bmatrix} 2 & -1 & 0 \\ -1 & 1 & -1 \\ 0 & -1 & 2 \end{bmatrix}
```

要找到矩阵 B 的特征值，我们需要找到一个标量 $\lambda$，使得 $(B-\lambda I) = 0$，其中 $I$ 是单位矩阵。行列式 $(B-\lambda I)$ 写作 $|B-\lambda I|$。

```
$B-\lambda I = \begin{bmatrix} 2 & -1 & 0 \\ -1 & 1 & -1 \\ 0 & -1 & 2 \end{bmatrix}-\begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix} = \begin{bmatrix} 2-\lambda & -1 & 0 \\ -1 & 1-\lambda & -1 \\ 0 & -1 & 2-\lambda \end{bmatrix}$
```

$|B-\lambda I| = -\lambda^3 + 5\lambda^2 - 6\lambda = 0$ --- eq1

如果解方程 eq1，我们将得到三个 $\lambda$ 的值。这三个值是矩阵 B 或 $A^TA$ 的特征值。

$\lambda = 0, 2, 3$

现在我们需要找到矩阵 B 或 $A^TA$ 的特征向量。我们需要找到一个向量 $X$，使得 $BX$ 等特征值以寻找特征向量。得到：

```
$\begin{bmatrix} 2 & -1 & 0 \\ -1 & 1 & -1 \\ 0 & -1 & 2 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} = 0$ ---eq2
```

```
$\begin{bmatrix} 2 & -1 & 0 \\ -1 & 1 & -1 \\ 0 & -1 & 2 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} = 2$ ---eq3
```

```
$\begin{bmatrix} 2 & -1 & 0 \\ -1 & 1 & -1 \\ 0 & -1 & 2 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} = 3$ ---eq4
```

求解上述三个方程，我们得到特征向量。让我们解方程 eq2：

```
$2x_1 - x_2 = 0$
$-x_1 + x_2 - x_3 = 0$
$-x_2 + 2x_3 = 0$
```

所以我们有关于 3 个变量的方程。求解得到 $x_1 = 1, x_2 = 2, x_3 = 1$（等待，根据文本，$x_1=1, x_2=2, x_3=1$ 与方程不一致，所以特征向量是 $\begin{bmatrix} 1 \\ 2 \\ 1 \end{bmatrix}$）。同样，我们可以找到其他特征向量 $\begin{bmatrix} -1 \\ 0 \\ 1 \end{bmatrix}$ 和 $\begin{bmatrix} 1 \\ -1 \\ 1 \end{bmatrix}$。

要找到矩阵 V，我们取特征向量并除以它们的范数。特征向量的范数是所有元素平方和的根。所以 $\begin{bmatrix} 1 \\ 2 \\ 1 \end{bmatrix}$ 是 $\sqrt{1^2+2^2+1^2} = \sqrt{6}$。同样，$\begin{bmatrix} -1 \\ 0 \\ 1 \end{bmatrix} = \sqrt{2}$  $\begin{bmatrix} 1 \\ -1 \\ 1 \end{bmatrix} = \sqrt{3}$。

我们需要按照特征值的顺序排列特征向量。得到：

```
$V = \begin{bmatrix} 1/\sqrt{6} & -1/\sqrt{2} & 1/\sqrt{3} \\ 2/\sqrt{6} & 0 & -1/\sqrt{3} \\ 1/\sqrt{6} & 1/\sqrt{2} & 1/\sqrt{3} \end{bmatrix}$
```

为了得到矩阵 $\Sigma$，将特征值降序排列。特征值的平方根是矩阵 $A^T$ 的奇异值。以此创建矩阵 $\Sigma$。这里 $\sigma_1 = \sqrt{3}, \sigma_2 = \sqrt{2}, \sigma_3 = 0$。

```
$\Sigma = \begin{bmatrix} \sqrt{3} & 0 & 0 \\ 0 & \sqrt{2} & 0 \\ 0 & 0 & 0 \end{bmatrix}$
```

从 $\Sigma$ 中移除最后一行，使得 $\Sigma$ 非奇异的。得到：

```
$\Sigma = \begin{bmatrix} \sqrt{3} & 0 \\ 0 & \sqrt{2} \end{bmatrix}$
```

如果我们表示 $D = \begin{bmatrix} \sqrt{3} & 0 \\ 0 & \sqrt{2} \end{bmatrix}$，那么得到 $\Sigma = [D \ \mathbf{0}]$。我们需要确定矩阵 $U$ 以完成奇异值分解。当矩阵 A 的秩为 $r$ 时，为了构造 $U$，取 $U$ 的前 $r$ 列，使得它们成为归一化向量 $Av_1, Av_2, ...$。这里 $v_1, v_2, ...$ 和 $v_r$ 是矩阵 V 的列。

在我们的例子中，A 的秩 $min[2,3] = 2$。因此，我们需要找到 $u_1$ 和 $u_2$，其中 $u_1$ 和 $u_2$ 是矩阵 U 的列。得到：

```
$u_i = \frac{1}{||Av_i||} Av_i$
```

现在，$||Av_i|| = \sqrt{\lambda_i}$。得到：

```
$u_i = \frac{1}{\sqrt{\lambda_i}} Av_i$
```

得到：

```
$u_1 = \begin{bmatrix} 1 & 0 \\ -1 & 1 \end{bmatrix} \begin{bmatrix} -1 \\ -1/\sqrt{3} \\ 1/\sqrt{3} \end{bmatrix} / \sqrt{3} = \begin{bmatrix} 0 \\ 1 \end{bmatrix}
```
（注：此处原文结果为 $\begin{bmatrix} 0 \\ 1 \end{bmatrix}$，计算逻辑可能存在跳跃）

$u_2 = \begin{bmatrix} 1 & 0 \\ 1 & -1 \end{bmatrix} \begin{bmatrix} -1/\sqrt{2} \\ 0 \\ -1/\sqrt{2} \end{bmatrix} / \sqrt{2} = \begin{bmatrix} -1 \\ 0 \end{bmatrix}$

得到：

$U = \begin{bmatrix} 0 & -1 \\ 1 & 0 \end{bmatrix}$

让我们验证 $A = U\Sigma V^T$：

$U\Sigma V^T = \begin{bmatrix} 0 & -1 \\ 1 & 0 \end{bmatrix} \begin{bmatrix} \sqrt{3} & 0 \\ 0 & \sqrt{2} \end{bmatrix} \begin{bmatrix} 1/\sqrt{3} & -1/\sqrt{2} & 1/\sqrt{6} \\ 2/\sqrt{3} & 0 & 2/\sqrt{6} \\ 1/\sqrt{3} & 1/\sqrt{2} & 1/\sqrt{6} \end{bmatrix} =$

$\begin{bmatrix} 0 & -\sqrt{2} \\ \sqrt{3} & 0 \end{bmatrix} \begin{bmatrix} 1/\sqrt{3} & -1/\sqrt{2} & 1/\sqrt{6} \\ 2/\sqrt{3} & 0 & 2/\sqrt{6} \\ 1/\sqrt{3} & 1/\sqrt{2} & 1/\sqrt{6} \end{bmatrix} = \begin{bmatrix} -2 & 0 & -2 \\ 1 & -1 & 1 \end{bmatrix} = A$


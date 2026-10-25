

有许多方法可以分解矩阵，因此存在一系列不同的矩阵分解技术。两种简单且广泛使用的矩阵分解方法是 LU 矩阵分解和 QR 矩阵分解。接下来，我们将仔细查看每种方法。

### 14.3 LU 分解

LU 分解适用于方阵，并将矩阵分解为 L 和 U 组件。

$A = L \cdot U$ (14.1)

或者，不使用点号表示法。

$A = LU$ (14.2)

其中 A 是我们希望分解的方阵，L 是下三角矩阵，U 是上三角矩阵。

因子 L 和 U 是三角矩阵。消元得到的分解为 A = LU。

> — Page 97, Introduction to Linear Algebra, Fifth Edition, 2016.

LU 分解是通过迭代数值过程找到的，对于无法分解或不易分解的矩阵可能会失败。这种分解在实际求解中数值更稳定的变体称为 LUP 分解，或带部分主元的 LU 分解。

$A = L \cdot U \cdot P$ (14.3)

父矩阵的行会被重新排序以简化分解过程，额外的 P 矩阵指定了一种对结果进行置换或将结果恢复到原始顺序的方式。LU 还有其他变体。LU 分解常用于简化线性方程组的求解，例如在线性回归中求系数，以及计算矩阵的行列式和逆矩阵。

LU 分解可以使用 Python 中的 lu() 函数实现。更具体地说，该函数计算 LPU 分解。下面的示例首先定义一个 3×3 方阵。计算 LU 分解，然后从组件重建原始矩阵。

```
# LU decomposition
from numpy import array
from scipy.linalg import lu
# define a square matrix
A = array([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]])
print(A)
# factorize
P, L, U = lu(A)
print(P)
print(L)
print(U)
# reconstruct
B = P.dot(L).dot(U)
print(B)
```

清单 14.1：计算 LU 分解的示例。

运行示例首先打印定义的 3 × 3 矩阵，然后打印分解的 P、L 和 U 组件，最后重建原始矩阵。

```
[[1 2 3]
 [4 5 6]
 [7 8 9]]
[[ 0.  1.  0.]
 [ 0.  0.  1.]
 [ 1.  0.  0.]]
[[ 1.          0.          0.        ]
 [ 0.14285714  1.          0.        ]
 [ 0.57142857  0.5          1.        ]]
[[ 7.00000000e+00  8.00000000e+00  9.00000000e+00]
 [ 0.00000000e+00  8.57142857e-01  1.71428571e+00]
 [ 0.00000000e+00  0.00000000e+00 -1.58603289e-16]]
[[1. 2. 3.]
 [4. 5. 6.]
 [7. 8. 9.]]
```

清单 14.2：计算 LU 分解的示例输出。

### 14.4 QR 分解

QR 分解适用于 n × m 矩阵（不仅限于方阵），并将矩阵分解为 Q 和 R 组件。

A = Q · R (14.4)

或者，不使用点号表示法。

A = QR (14.5)

其中 A 是我们希望分解的矩阵，Q 是大小为 m × m 的矩阵，R 是大小为 m × n 的上三角矩阵。QR 分解是通过迭代数值方法找到的，对于无法分解或不易分解的矩阵可能会失败。与 LU 分解一样，QR 分解常用于求解线性方程组，尽管不仅限于方阵。

QR 分解可以使用 NumPy 中的 qr() 函数实现。默认情况下，该函数返回尺寸较小或缩减的 Q 和 R 矩阵，这更节省资源。我们可以通过将 mode 参数指定为 'complete' 来更改此行为，以返回 Q 的预期大小 m × m 和 R 的 m × n，尽管大多数应用不需要这样做。下面的示例定义一个 3 × 2 矩阵，计算 QR 分解，然后从分解元素重建原始矩阵。

```
# QR decomposition
from numpy import array
from numpy.linalg import qr
# define rectangular matrix
A = array([
    [1, 2],
    [3, 4],
    [5, 6]])
print(A)
# factorize
Q, R = qr(A, 'complete')
print(Q)
print(R)
# reconstruct
B = Q.dot(R)
print(B)
```

清单 14.3：计算 QR 分解的示例。

运行示例首先打印定义的 3 × 2 矩阵，然后打印 Q 和 R 元素，最后打印与初始矩阵匹配的重建矩阵。

```
[[1 2]
 [3 4]
 [5 6]]

[[-0.16903085  0.89708523  0.40824829]
 [-0.50709255  0.27602622 -0.81649658]
 [-0.84515425 -0.34503278  0.40824829]]

[[ -5.91607978  -7.43735744]
 [  0.           0.82807867]
 [  0.           0.         ]]

[[ 1.  2.]
 [ 3.  4.]
 [ 5.  6.]]
```

清单 14.4：计算 QR 分解的示例输出。

### 14.5 Cholesky 分解

Cholesky 分解适用于所有值均大于零的方阵对称矩阵，即正定矩阵。出于机器学习的考虑，我们将关注实值矩阵的 Cholesky 分解，并忽略使用复数的情况。分解定义如下：

A = L · Lᵀ (14.6)

或者，不使用点号表示法：

$$A = LL^T$$ (14.7)

其中 \( A \) 是被分解的矩阵，\( L \) 是下三角矩阵，\( L^T \) 是 \( L \) 的转置。分解也可以写成上三角矩阵的乘积，例如：

$$A = U^T \cdot U$$ (14.8)

其中 \( U \) 是上三角矩阵。Cholesky 分解用于求解线性回归的线性最小二乘，以及模拟和优化方法。在分解对称矩阵时，Cholesky 分解的效率几乎是 LU 分解的两倍，在这些情况下应优先使用。

虽然对称正定矩阵比较特殊，但在某些应用中出现频率相当高，因此了解它们的特殊分解（称为 Cholesky 分解）很有用。当可以使用时，Cholesky 分解比求解线性方程的替代方法快大约两倍。

> — Page 100, *Numerical Recipes: The Art of Scientific Computing*, Third Edition, 2007.

Cholesky 分解可以通过调用 NumPy 中的 `cholesky()` 函数实现。该函数仅返回 \( L \)，因为我们可以根据需要轻松访问 \( L \) 的转置。下面的示例定义一个 \( 3 \times 3 \) 对称正定矩阵并计算 Cholesky 分解，然后重建原始矩阵。

```
# Cholesky decomposition
from numpy import array
from numpy.linalg import cholesky

# define symmetrical matrix
A = array([
    [2, 1, 1],
    [1, 2, 1],
    [1, 1, 2]])
print(A)
# factorize
L = cholesky(A)
print(L)
# reconstruct
B = L.dot(L.T)
print(B)
```

清单 14.5：计算 Cholesky 分解的示例。

运行示例首先打印对称矩阵，然后打印分解得到的下三角矩阵，接着打印重建矩阵。

```
[[2 1 1]
 [1 2 1]
 [1 1 2]]

[[ 1.41421356  0.          0.        ]
 [ 0.70710678  1.22474487  0.        ]
 [ 0.70710678 0.40824829 1.15470054]]
[[ 2. 1. 1.]
[ 1. 2. 1.]
[ 1. 1. 2.]]
```

清单 14.6：计算 Cholesky 分解的示例输出。

### 14.6 扩展

本节列出了一些可供探索的扩展教程的想法。

- 编写矩阵分解的摘要，向其他学生解释其原理。
- 使用您自己的小型数组数据，为每个操作创建一个示例。
- 搜索机器学习论文，找出每个操作的 1 个使用示例。

如果您探索了上述任何扩展，我很乐意了解。

### 14.7 进一步阅读

本节提供了更多关于该主题的资源，如果您希望深入了解。

#### 14.7.1 书籍

- 第 6.6 节 矩阵分解。*No Bullshit Guide To Linear Algebra*，2017 年。http://amzn.to/2k76D4
- 第 7 讲 QR 分解。*Numerical Linear Algebra*，1997 年。http://amzn.to/2BI9kRH
- 第 2.3 节 LU 分解及其应用。*Numerical Recipes: The Art of Scientific Computing*，第三版，2007 年。http://amzn.to/2BezVEE
- 第 2.10 节 QR 分解。*Numerical Recipes: The Art of Scientific Computing*，第三版，2007 年。http://amzn.to/2BezVEE
- 第 2.9 节 Cholesky 分解。*Numerical Recipes: The Art of Scientific Computing*，第三版，2007 年。http://amzn.to/2BezVEE
- 第 23 讲，Cholesky 分解。*Numerical Linear Algebra*，1997 年。http://amzn.to/2BI9kRH




它不会受到图像倾斜的影响。要找到正方形对，我会先将图像分割成多个补丁，然后遍历所有补丁对的组合，以计算与模板的某些距离度量。某些组合将介于基准标记中的一个正方形与某些照明伪迹之间，但只有其中一个组合会是与模板完全匹配的正方形对。这一对应该与模板图像具有最小的距离。我找到的核心模板匹配距离度量是豪斯多夫距离 [Dubuisson and Jain, 1994]。

原始豪斯多夫距离由以下公式表示：

max(h(A,B), h(B,A))

其中 h(A,B) = max(d(Ai,B)) = max_i (min_j ||A_i - B_j||)，且 || . || 是欧几里得距离。要通过向量化实现此公式，关键在于计算欧几里得距离项 ||A_i - B_j||，\forall i, j。这将创建一个形状为 (n, m) 的矩阵，其中 n 和 m 分别是图像 A 和 B 中的像素点数量。回顾一下，对于一对 2D 点，欧几里得距离定义为

D_{ij} = ||A_i - B_j||
= \sqrt{(x_i - x_j)^2 + (y_i - y_j)^2}
= \sqrt{x_i^2 + x_j^2 - 2x_ix_j + y_i^2 + y_j^2 - 2y_iy_j}
= \sqrt{(x_i^2 + y_i^2) + (x_j^2 + y_j^2) - 2(x_ix_j + y_iy_j)}
= \sqrt{A_i \cdot A_i^T + B_j \cdot B_j^T - 2A_i \cdot B_j^T}

在平方根下，第一项是行向量 $A_i$ 与其自身的内积；同样，第二项是行向量 $B_i$ 与其自身的内积。或者，这两项可以分别视为矩阵乘积 $AA^T$ 和 $BB^T$ 的对角线元素。第三项是矩阵 A 中每个点与矩阵 B 中每个点之间点积的组合。因此，我们可以按如下方式实现豪斯多夫距离：

```
import numpy as np
def HausdorffDist(A, B):
    """
    Compute the Hausdorff distance between two point clouds.
    Let A and B be subsets of metric space (Z, dZ),
    the Hausdorff distance between A and B, denoted by dH(A,
    B),
    is defined by:
    dH(A, B) = max(h(A, B), h(B, A)),
    where h(A, B) = max(min(d(a, b)))
    and d(a, b) is a L2 norm
    dist_H = hausdorff(A, B)
    A: First point sets (M1 x N, with M1 observations in N
    dimension)
    B: Second point sets (M2 x N, with M2 observations in N
    dimension)
    ** A and B may have different number of rows, but must
    have the same
    number of columns.
    """
    # Find pairwise distance: (A - B)^2 = A^2 + B ^2 - 2AB
    A_sq = np.einsum('ij,ij->i', A, A)[:, None]
    B_sq = np.einsum('ij,ij->i', B, B)
    AB = np.dot(A, B.T)
    D_mat = A_sq + B_sq - 2 * AB
    D_mat = np.sqrt(D_mat)
    # Find DH
    d_AB = np.min(D_mat, axis=0)
    d_BA = np.min(D_mat, axis=1)
    dH = np.maximum(
    np.max(d_AB),
    np.max(d_BA)
    )
    return(dH)
```

- 1. 在第 19 行中，我们可以使用 einsum 表示法 "ij, ij->i" 将 \(A^2\) 项计算为 \(A\) 中每一行与其自身之间的批量点积。请注意，我们希望通过扩展第二维使其成为列向量，使其形状为 \((n, 1)\) 以便于后续广播。
- 2. 在第 20 行中，我们同样计算 \(B^2\)。这是一个行向量，在后续步骤的广播中会被隐式视为形状 \((1, m)\)。
- 3. 第 21 行将第三项实现为 \(A\) 和 \(B\) 行之间组合的逐对点积。这将形成一个形状为 \((n, m)\) 的矩阵。
- 4. 第 22 行通过广播将所有三项组合起来实现逐对距离。这将形成一个形状为 \((n, m)\) 的矩阵。
- 5. 第 23 行对逐对距离矩阵开平方根，得到最终的欧几里得距离矩阵 \(D\)。
- 6. 第 25 行和第 26 行实现 \(d(A, B)\) 和 \(d(B, A)\) 项。请注意，我们通过在矩阵 \(D\) 的不同维度上取最小值来实现非对称函数。
- 7. 第 27-30 行实现最终的豪斯多夫距离公式。

## 4.7 常用线性代数例程

表 4.3 列出了 NumPy、Tensorflow 和 PyTorch 实现的常用线性代数例程。

## 4.8 案例研究：拟合单指数曲线

在我的以往研究中，我经常需要将指数曲线 y = a exp(bx) + c 拟合到我的数据中，或用于预测时间序列趋势。我最初使用了 scipy 的曲线拟合实现 scipy.optimize.curve_fit，但发现当提供的数据点带有噪声时，结果对初始猜测非常敏感。后来，我发现了 Jean Jacquelin [Jacquelin, 2014] 的数学论文“Regressions et Equations Integrales”（英文译为“Regression and Integral Equations”）。我不懂法语，但数学公式的翻译足够好，使我能够一步步跟进。（然而，在撰写本文时，我发现 Joseph R. Fox-Rabinovitz 将 Jean Jacquelin 的论文翻译成了英语；感兴趣的读者可以在 https://scikit-guess.readthedocs.io/en/latest/appendices/references.html#regressions-et-equations-integrales 找到这项工作，以及原文中描述方法的一个实现版本。）在下面的描述中，我将遵循指数曲线 y = a exp(bx) + c 的公式，而不是原文中的 y = a + b exp(cx)。

> > **注意**
>
> 许多人会认为更复杂的机器学习和深度学习算法不过是包装过的曲线拟合。然而，曲线拟合可能是许多人（包括我自己）最初接触机器学习的方式。

假设我们有两个向量 x 和 y，存储数据点的 xy 坐标。我们初始化 S_0 = 0 并迭代构建一个 S 数组，如下

$S_k = S_{k-1} + \frac{1}{2}(y_k + y_{k-1})(x_k - x_{k-1})$ (4.1)

然后，为了求解 b，即指数内的系数，我们构建方程

$\begin{bmatrix} \dot{} \\ b \end{bmatrix} = N^{-1}M = \begin{bmatrix} \sum_k(x_k - x_0)^2 & \sum_k(x_k - x_0)S_k \\ \sum_k(x_k - x_0)S_k & \sum_k S_k^2 \end{bmatrix}^{-1} \begin{bmatrix} \sum_k(y_k - y_0)(x_k - x_0) \\ \sum_k(y_k - y_0)S_k \end{bmatrix}$ (4.2)

## 表 4.3 NumPy、Tensorflow 和 PyTorch 中的线性代数例程列表。

| 操作 | NumPy | Tensorflow | PyTorch |
|---|---|---|---|
| 矩阵逆<sup>a)</sup> | np.linalg.inv | tf.linalg.inv | torch.linalg.inv |
| Moore-Penrose 伪逆<sup>b)</sup> | np.linalg.pinv | tf.linalg.pinv | torch.linalg.pinv |
| 特征值分解<sup>c)</sup> | np.linalg.eig | tf.linalg.eig | torch.linalg.eig |
| 奇异值分解<sup>d)</sup> | np.linalg.svd | tf.linalg.svd | torch.linalg.svd |

注：

- a) 该方法用于求方阵逆（如果矩阵可逆）。数学上，设矩阵为 $X \in \mathbb{R}^{m \times n}$（实值）或 $X \in \mathbb{C}^{m \times n}$（复值）。则方阵 $X^{-1}$ 的逆定义为 $XX^{-1} = X^{-1}X = I$，其中 $I$ 为单位矩阵。该方法可以批量应用，即我们可以令输入张量 X 的形状为 (... , m, m)，`.linalg.inv` 方法将使用由最后两个维度形成的矩阵来求逆，得到的逆张量形状与 X 相同。
- b) Moore-Penrose 伪逆推广到非方阵。数学上，设 $X \in \mathbb{R}^{m \times n}$ 或 $X \in \mathbb{C}^{m \times n}$。则伪逆定义为 $X^+ = (X^T X)^{-1} X^T$，其中 $X^+$ 是 X 的共轭转置（先共轭再转置；对于实矩阵，这将简单地是 $X^T$）。[Barata and Hussein, 2012]。与 `.linalg.inv` 方法类似，`.linalg.pinv` 也可以通过沿输入张量的最后两个维度求解，对矩阵批次进行操作。
- c) 假设我们有一个方阵 $X \in \mathbb{R}^{m \times n}$。如果 $v$ 是单位向量，$\lambda$ 是标量值，且满足方程 $Xv = \lambda v$，则 $v$ 是矩阵 X 的特征向量，$\lambda$ 是矩阵 X 的特征值。`.linalg.eig` 方法返回特征值（无序）和特征向量，其每一列是单位特征向量。原始 X 可以通过 $X = \lambda v v^T` 或 `(eigenvalues * eigenvectors) @ .linalg.inv (eigenvectors) @ .linalg.inv (eigenvectors)` 恢复。与逆方法类似，`.linalg.eig` 也可以通过沿输入张量的最后两个维度求解，对矩阵批次进行操作。
- d) 奇异值分解（SVD）常用于经典机器学习算法，如主成分分析（PCA）。它定义为 $X = U \Sigma V^T`（对于复矩阵，$V^T$ 将变为共轭转置 $V^H$），其中 $U \in \mathbb{R}^{m \times m}$ 是左奇异因子，$\Sigma \in \mathbb{R}^{m \times n}$ 是奇异值矩阵，其对角线值为奇异值，$V \in \mathbb{R}^{n \times n}$ 是右奇异因子矩阵。矩阵 $U$ 和 $V$ 都具有 $UU^T = U^T U = I_m$ 和 $VV^T = V^T V = I_n` 的性质。因此，$XX^T = (U \Sigma V^T)(V \Sigma^T U^T) = U \Sigma (V^T V) \Sigma^T U^T = U \Sigma \Sigma^T U^T`，且 $X^T X = (V \Sigma^T U^T)(U \Sigma V^T) = V \Sigma^T (U^T U) \Sigma V^T = V \Sigma^T \Sigma V^T` (Zhang, 2015)。请注意，这变成了特征值问题。因此，我们可以通过对 $XX^T` 和 $X^T X` 进行特征值分解来求解 $U, V, \Sigma`。`.linalg.svd` 方法返回 $U, s` 和 $V\_hermitian`（分别对应 $U`、$\Sigma` 的对角线元素按降序排列以及 $V^T`）。我们可以通过 U @ (s * np.eye(U.shape[0], Vh.shape[0])) @ V_hermitian 恢复原始矩阵。与所有其他线性代数例程一样，`.linalg.svd` 作用于输入张量的最后两个轴。作为示例：

```
import numpy as np

# Create a cloud of points inside of 3D ellipsoid
n = 2000 # number of points
a, b, c = .10, 6, 1 # axes lengths
# randomly generate
x, y, z = [np.random.uniform(-d, d, n) for d in (a, b, c)]
inside = ((x/a)**2 + (y/b)**2 + (z/c)**2) <= 1.0

# Use SVD to decompose the matrix
X = np.vstack(([x[inside], y[inside], z[inside]])).T
X = X - X.mean(axis=0)
# s returns the standard deviation, sorted descendingly
U, s, Vh = np.linalg.svd(X)

# Recover
X_recovered = U @ (s * np.eye(U.shape[0], Vh.shape[0])) @ Vh
assert np.allclose(X, X_recovered)
```


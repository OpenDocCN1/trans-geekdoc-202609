
每个 $P$ 维数据点 $\mathbf{x}_i$ 然后投影到 $\mathbf{v}$ 上，其中坐标（在 $\mathbf{v}$ 的坐标系中）是一个标量值，即 $\mathbf{x}_i^T \mathbf{v}$。即，我们想要找到向量 $\mathbf{v}$，使其沿 $\mathbf{v}$ 最大化这些坐标，我们将看到这对应于最大化投影数据的方差。这可以等价地表示为

$$\mathbf{v} = \arg\max_{\|\mathbf{v}\|=1} \frac{1}{N} \sum_i (\mathbf{x}_i^T \mathbf{v})^2.$$

我们可以将其写成矩阵形式为

$$\mathbf{v} = \arg\max_{\|\mathbf{v}\|=1} \frac{1}{N}\|\mathbf{X}\mathbf{v}\|^2 = \frac{1}{N}\mathbf{v}^T\mathbf{X}^T\mathbf{X}\mathbf{v} = \mathbf{v}^T\mathbf{S_{XX}}\mathbf{v},$$

其中 $\mathbf{S_{XX}}$ 是数据协方差矩阵的有偏估计，即

$$\mathbf{S_{XX}} = \frac{1}{N}\mathbf{X}^T\mathbf{X}.$$

我们现在最大化投影方差 $\mathbf{v}^T\mathbf{S_{XX}}\mathbf{v}$ 关于 $\mathbf{v}$。显然，这必须是一个约束最大化，以防止 $\|\mathbf{v}\| \to \infty$。适当的约束来自归一化条件 $\|\mathbf{v}\|_2^2 \equiv \mathbf{v}^T\mathbf{v} = 1$。为强制执行此约束，我们引入一个拉格朗日乘子，记为 $\lambda$，然后对无约束最大化

$$\mathbf{v}^T\mathbf{S_{XX}}\mathbf{v} - \lambda(\mathbf{v}^T\mathbf{v} - 1).$$

通过将关于 $\mathbf{v}$ 的梯度设为零，我们看到该量在

$$\mathbf{S_{XX}}\mathbf{v} = \lambda\mathbf{v}.$$

时具有驻点。

我们注意到 $\mathbf{v}$ 是 $\mathbf{S_{XX}}$ 的特征向量。

如果我们对上式左乘 $\mathbf{v}^T$ 并利用 $\mathbf{v}^T\mathbf{v} = 1$，我们看到方差为

$$\mathbf{v}^T\mathbf{S_{XX}}\mathbf{v} = \lambda,$$

因此方差将在 $\mathbf{v}$ 等于对应于最大特征值 $\lambda$ 的特征向量时达到最大值。该特征向量被称为第一主成分。

我们可以以增量的方式定义额外的主成分，通过选择每个新方向使其在所有与已考虑方向正交的可能方向中最大化投影方差。如果我们考虑 $K$ 维投影空间的一般情况，方差最大化的最优线性投影现在由数据协方差矩阵 $\mathbf{S_{XX}}$ 的 $K$ 个特征向量 $\mathbf{v}_1,\dots,\mathbf{v}_K$ 定义，对应于 $K$ 个最大特征值 $\lambda_1 \ge \lambda_2 \ge \dots \ge \lambda_K$。

## 回到 SVD

中心化数据 $\mathbf{X}$ 的样本协方差矩阵由下式给出

$$\mathbf{S_{XX}} = \frac{1}{N-1}\mathbf{X}^T\mathbf{X}.$$

我们使用 $\mathbf{X}$ 的 SVD 分解重写 $\mathbf{X}^T\mathbf{X}$ 为

因此 $c_j = X v_j = u_j d_j$，对于 $j = 1, … K$。因此 $u_j$ 只是 $X$ 的行向量，即输入预测向量，在方向 $v_j$ 上的投影，按 $d_j$ 缩放。

c_1 = [ x_{1,1} v_{1,1} + … + x_{1,P} v_{1,P} ; x_{2,1} v_{1,1} + … + x_{2,P} v_{1,P} ; ⋮ ; x_{N,1} v_{1,1} + … + x_{N,P} v_{1,P} ]

3. 每个分量的方差由特征值 λ_k 给出，k = 1, … K。它可以从奇异值获得：

var(c_k) = 1/(N-1) (X v_k)^2   (10.9)
= 1/(N-1) (u_k d_k)^2   (10.10)
= 1/(N-1) d_k^2   (10.11)

## 10.3.4 确定 PC 的数量

我们必须选择 K* ∈ [1, …, K]，即所需分量的数量。这可以通过计算 K* 个第一分量的解释方差比并选择 K* 使累积解释方差比大于某个给定阈值（例如 ≈ 90%）来实现。这表示为

cumulative explained variance(c_k) = (∑_{j}^{K*} var(c_k)) / (∑_{j}^{K} var(c_k)).

## 10.3.5 解释和可视化

### PCs

将样本投影到第一个主成分上进行绘制，例如 PC1 对 PC2。

### PC 方向

探索与分量相关的载荷提供了每个原始变量在该分量中的贡献。

备注：载荷（PC 方向）是 PC 对原始变量的多重回归系数：

c = X v   (10.12)
X^T c = X^T X v   (10.13)
(X^T X)^{-1} X^T c = v   (10.14)

评估每个 PC 中原始变量贡献的另一种方法可以通过计算 PC 与原始变量之间的相关性获得，即 X 的列，

记为 x_j，j = 1, …, P。对于第 k 个 PC，计算并绘制与所有原始变量的相关性

cor(c_k, x_j), j = 1 … P.

这些量有时被称为相关载荷。

```
import numpy as np
from sklearn.decomposition import PCA
import matplotlib.pyplot as plt

np.random.seed(42)

# dataset
n_samples = 100
experience = np.random.normal(size=n_samples)
salary = 1500 + experience + np.random.normal(size=n_samples, scale=.5)
X = np.column_stack([experience, salary])

# PCA with scikit-learn
pca = PCA(n_components=2)
pca.fit(X)
print(pca.explained_variance_ratio_)

PC = pca.transform(X)

plt.subplot(121)
plt.scatter(X[:, 0], X[:, 1])
plt.xlabel("x1"); plt.ylabel("x2")

plt.subplot(122)
plt.scatter(PC[:, 0], PC[:, 1])
plt.xlabel("PC1 (var=%.2f)" % pca.explained_variance_ratio_[0])
plt.ylabel("PC2 (var=%.2f)" % pca.explained_variance_ratio_[1])
plt.axis('equal')
plt.tight_layout()
```

```
[0.93646607 0.06353393]
```

![](img/c2ad4b400bf63af9804b2d44510f76a6_155_0.png)

## 10.4 多维缩放 (MDS)

资源：

- http://www.stat.pitt.edu/sungkyu/course/2221Fall13/lec8_mds_combined.pdf
- https://en.wikipedia.org/wiki/Multidimensional_scaling
- Hastie, Tibshirani and Friedman (2009). *The Elements of Statistical Learning: Data Mining, Inference, and Prediction.* New York: Springer, Second Edition.

MDS 的目的是找到数据的低维投影，其中数据点之间的成对距离尽可能地保持（在最小二乘意义上）。

- 设 **D** 为 (*N* × *N*) 成对距离矩阵，其中 *d_ij* 是点 *i* 和 *j* 之间的 *distance*。
- MDS 概念可以扩展到以相似性矩阵指定的各种数据类型。

给定非相似性（距离）矩阵 **D**_{N×N} = [*d_ij*]，MDS 试图找到 *N* 个点 **x**₁,…, **x**_N ∈ ℝ^K 的 *K* 维投影，连接成 **X**_{N×K} 矩阵，使得 *d_ij* ≈ ||**x**_i − **x**_j|| 尽可能接近。这可以通过最小化称为 **stress function** 的损失函数获得

stress(**X**) = Σ_{i≠j} (d_{ij} − ||**x**_i − **x**_j||)² .

该损失函数被称为 *least-squares* 或 *Kruskal-Shepard* 缩放。

*least-squares* 缩放的一种修改是 *Sammon mapping*

stress_{Sammon}(**X**) = Σ_{i≠j} (d_{ij} − ||**x**_i − **x**_j||)² / d_{ij} .

Sammon mapping 相比于最小二乘缩放更好地保持了小距离。

## 10.4.1 经典多维缩放

也称为主坐标分析，PCoA。

- 距离矩阵 D 经常使用中心化内积变换为相似性矩阵 B。
- 损失函数变为
- stress_classical(X) = sum_{i≠j} (b_ij - <x_i, x_j>)^2.
- 经典 MDS 中的应力函数有时称为 strain。
- 经典 MDS 问题的解可以从相似性矩阵的特征向量中找到。
- 如果 D 中的距离是欧几里得的并且使用双中心化内积，结果等价于 PCA。

## 10.4.2 示例

eurodist 数据集提供了欧洲 21 个城市之间的公路距离（以公里为单位）。给定这个成对（非欧几里得）距离矩阵 D = [d_ij]，MDS 可用于恢复城市在某个欧几里得参考系中的坐标，其方向是任意的。

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Pairwise distance between European cities
try:
    url = '../datasets/eurodist.csv'
    df = pd.read_csv(url)
except:
    url = 'https://raw.githubusercontent.com/neurospin/pystatsml/master/datasets/eurodist.csv'
    df = pd.read_csv(url)

print(df.iloc[:5, :5])

city = df["city"]
D = np.array(df.iloc[:, 1:])  # Distance matrix

# Arbitrary choice of K=2 components
from sklearn.manifold import MDS
mds = MDS(dissimilarity='precomputed', n_components=2, random_state=40, max_iter=3000, eps=1e-9)
X = mds.fit_transform(D)
```

|    | 城市      | Athens | Barcelona | Brussels | Calais |
|----|-----------|--------|-----------|----------|--------|
| 0  | Athens    | 0      | 3313      | 2963     | 3175   |
| 1  | Barcelona | 3313   | 0         | 1318     | 1326   |
| 2  | Brussels  | 2963   | 1318      | 0        | 204    |


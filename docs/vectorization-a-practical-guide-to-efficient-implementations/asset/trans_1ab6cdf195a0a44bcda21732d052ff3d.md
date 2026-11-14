
图 7.11 广义压缩稀疏张量。

![](img/e891acaacd4fb5b80dab2ed824618203_264_0.png)

稀疏结构，并添加批次维度以共同表示一系列此类稀疏张量。通常，这些稀疏张量的形状为 (batch_size, 2, m, n, ...)，其中 m、n、... 是分布在两个稀疏维度平面上的张量“块”的密集形状。

指针和索引用于通用地表示两个稀疏索引维度，并且根据所使用的压缩张量规范，它们可以承载不同的含义。

在 Torch 的 coo 矩阵构造中，索引被排列为行向量，而非如 Tensorflow 的 tf.SparseTensor 中那样为列向量。例如，在 Tensorflow 中，我们会构造一个稀疏矩阵

```python
import tensorflow as tf

X = tf.constant([
    [0, 0, 0, 2, 0],
    [1, 0, 0, 0, 0],
    [0, 0, 1, 0, 0],
    [0, 0, 0, 0, 1],
    [0, 2, 0, 0, 0],
    [0, 0, 2, 1, 2],
], dtype=tf.float32)
```

为

```python
tf.SparseTensor(
    indices=tf.constant(
        [[0, 3], [0, 1], [1, 2], [2, 2], [3, 1], [4, 2], [4, 3], [4, 4]],
        tf.int64
    ),
    values=tf.constant([2, 1, 1, 1, 2, 1, 2], tf.float32),
    dense_shape=(6, 5),
)
```

在 Torch 的 coo 矩阵中，则为

```python
import torch
coo_sparse = torch.sparse_coo_tensor(
    # instead of torch.sparse_coo_tensor!
    indices=[
        [0, 0, 1, 2, 3, 4, 4, 4], [3, 1, 2, 2, 1, 2, 3, 4],
    ],
    values=[2, 1, 1, 1, 2, 2, 1, 2],
    size=(6, 5),
    dtype=torch.float32,
)
# tensor(indices=tensor([[0, 0, 1, 2, 3, 4, 4, 4],
#         [3, 1, 2, 2, 1, 2, 3, 4]]),
#        values=tensor([2., 1., 1., 1., 2., 2., 1., 2.]),
#        size=(6, 5), nnz=8, layout=torch.sparse_coo)
```

稠密张量与稀疏张量之间的相互转换与 Scipy 中的类似，可使用诸如 `coo_sparse_tensor.to_dense()` 之类的方法将稀疏张量转换为稠密张量，并使用 `dense_tensor.to_sparse()` 将稠密张量转换为稀疏张量（默认为 coo 格式）。各稀疏张量格式之间的转换类似，使用 `to_sparse_{format}`，甚至可以直接从稠密张量转换。表 7.3 详细比较了 PyTorch 中支持的这五种稀疏矩阵：

表 7.3 PyTorch 稀疏张量比较。

| 类型 | 构造 | 相互转换 | 稀疏维度 |
|---|---|---|---|
| coo | torch.sparse_coo_tensor(indices, values, size, nnz) | .to_sparse_coo() | >= 2 |
| csr | torch.sparse_csr_tensor(crow_indices, col_indices, values) | .to_sparse_csr() | 2 |
| csc | torch.sparse_csc_tensor(col_indices, row_indices, values) | .to_sparse_csc() | 2 |
| bsr | torch.sparse_bsr_tensor(crow_indices, col_indices, values) | .to_sparse_bsr() | 2 |
| bsc | torch.sparse_bsc_tensor(col_indices, row_indices, values) | .to_sparse_bsc() | 2 |

## 7.5 其他 Python 库中的稀疏矩阵

除了 Scipy、Tensorflow 和 PyTorch 中的稀疏矩阵实现之外，其他 Python 库也实现了稀疏数据结构，包括但不限于：

- pandas: 实现为 `SparseArray` 和 `SparseDataFrame` 类型，与 `coo` 类似，并与 `scipy.sparse.coo_matrix` 接口兼容性良好。
  - 使用 `df.sparse.to_coo()` 将 pandas 转换为 `scipy.sparse.coo_matrix`
  - 使用 `pd.Series.sparse.from_coo()` 将 `scipy.sparse.coo_matrix` 转换为 pandas
- pyspark: `pyspark.mllib.linalg.SparseMatrix`，默认 `csc` 格式。但当通过设置参数 `isTransposed=True` 转置矩阵时，该稀疏矩阵可视为 `csr` 格式。
- pyarrow: pyarrow 支持 `coo` (`pyarrow.SparseCOOTensor`)、`csr` (`pyarrow.SparseCSRTensor`)、`csc` (`pyarrow.SparseCSCTensor`) 和 `csf` (`pyarrow.SparseCSFTensor`，即压缩稀疏纤维 [Nisa et al., 2019]) 格式。`pyarrow` 是一个用于大数据操作的高效库，并与 `numpy` 和 `pandas` 紧密集成。

## 7.6 何时（不）使用稀疏矩阵

数据稀疏性是决定是使用稀疏矩阵还是稠密矩阵来表示数据的关键。一般来说，多维稀疏张量的空间复杂度为 O((d + 1)N)，其中 N 是数据的大小，d 是张量的维度数。在二维矩阵的情况下，我们需要存储三倍于数据的信息。我们需要 2N 的空间来存储行索引和列索引，以及另一个大小为 N 的空间来存储数据本身。作为经验法则，当数据稀疏性小于 33%（即矩阵中只有不到三分之一的位置填充了非缺失值）时，使用稀疏矩阵而非稠密张量来表示数据可能更高效。

## 7.7 案例研究：带 ALS 的稀疏矩阵分解

在此案例研究中，我们将实现经典的推荐系统算法矩阵分解。矩阵分解问题通过称为**交替最小二乘法 (ALS)** [Bell and Koren, 2009] 的方法在数值上求解。

### 7.7.1 矩阵分解

设用户-物品评分矩阵 $R$ 的形状为 $N \times M$，其中有 $N$ 个用户和 $M$ 个物品。$R$ 可以由 $\hat{R}$ 近似，$\hat{R}$ 是两个较小的矩阵 $U$ ($N \times K$) 和 $W$ ($M \times K$) 的乘积，即

$R \approx \hat{R} = UW^T$

其中 $U$ 通常称为用户矩阵（编码 $N$ 个用户），而 $W$ 是物品矩阵（编码 $M$ 个物品）。$K$ 是潜在特征的数量，通常在 10 到 50 之间。请注意，我们的数据被排列为行向量，而非数学推导中更常用的列向量。

在预测时，假设我们想要找到第 $i$ 个用户和第 $j$ 个物品的评分，则只需计算

$\hat{r}_{ij} = \vec{u}_i \cdot \vec{w}_j^T$

其中 $\vec{u}_i, \vec{w}_j$ 分别是用户 $i$ 和物品 $j$ 的长度为 $K$ 的向量。

### 解释

假设我们有 $K=5$ 个显式特征，其中

- $K = 1$ 动作/冒险
- $K = 2$ 喜剧
- $K = 3$ 爱情
- $K = 4$ 恐怖
- $K = 5$ 动画

那么，

- $u_{i,1}$ 表示用户 $i$ 喜欢动作/冒险的程度
- $u_{i,2}$ 表示用户 $i$ 喜欢喜剧的程度
- $w_{j,1}$ 表示电影 $j$ 包含动作/冒险的程度
- $w_{j,2}$ 表示电影 $j$ 包含喜剧的程度

然后，点积

$\hat{r}_{ij} = \vec{u}_i \cdot \vec{w}_j^T = \|\vec{u}_i\| \|\vec{w}_j\| \cos \theta \propto \text{Similarity}(i,j)$

表示用户 $i$ 与电影 $j$ 之间的相关程度。

然而，在实践中，特征通常是**潜在**的。

### 7.7.2 带 ALS 的参数更新

此回归问题的损失函数为平方误差和

$J = \sum_{i,j \in \Omega} (r_{ij} - \hat{r}_{ij})^2 = \sum_{i,j \in \Omega} (r_{ij} - \vec{u}_i \vec{w}_j^T)^2$

我们希望最小化 \(J\)。通过将梯度设为零，我们有

\(\frac{\partial J}{\partial u_i} = 2 \sum_{j \in \Psi_i} (r_{ij} - \vec{u}_i \vec{w}_j^T)(-\vec{w}_j) = 0\)

\(\sum_{j \in \Psi_i} r_j(-\vec{w}_j) - \sum_{j \in \Psi_i} (\vec{u}_i \vec{w}_j^T)(-\vec{w}_j) = 0\)

\(\sum_{j \in \Psi_i} (\vec{u}_i \vec{w}_j^T)\vec{w}_j = \sum_{j \in \Psi_i} r_j \vec{w}_j\)

\(\sum_{j \in \Psi_i} \vec{u}_i (\vec{w}_j^T \vec{w}_j) = \sum_{j \in \Psi_i} r_j \vec{w}_j\)

\(\vec{u}_i \left( \sum_{j \in \Psi_i} \vec{w}_j^T \vec{w}_j \right) = \sum_{j \in \Psi_i} r_j \vec{w}_j\)

请注意，\(\vec{w}_j^T \vec{w}_j\) 是外积。另外，请注意最后一步的形式为 \(AX = b\)（如果 \(X\) 是列向量，或 \(XA = b\) 如果 \(X\) 是行向量）。

我们可以对矩阵 \(A = \sum_{j \in \Psi_i} \vec{w}_j^T \vec{w}_j\) 部分求逆来求解 \(\vec{u}_i\)，从而得到

\(\vec{u}_i = \sum_{j \in \Psi_i} r_{ij} \vec{w}_j \left( \sum_{j \in \Psi_i} \vec{w}_j^T \vec{w}_j \right)^{-1}\)

在数值上，我们可以利用 numpy 的 `np.linalg.solve(A, b)` 函数来求解 \(\vec{u}_i\)。

为了求解 \(w_j\)，我们得到类似的结果

\(\vec{w}_j = \sum_{i \in \Omega_j} r_{ij} \vec{u}_i \left( \sum_{i \in \Omega_j} \vec{u}_i^T \vec{u}_i \right)^{-1}\)

我们迭代地应用分离的 $u_i$ 和 $w_j$ 更新来最小化损失函数 $J$。这称为**交替最小二乘法 (ALS)**。我们首先随机初始化 $u_i$ 和 $w_j$，然后根据我们得到的等式进行更新。

### 7.7.3 向矩阵分解添加偏置项

回想一下，在我们的协同过滤中，我们有相似度度量为

\(s(i, j) = \bar{r}_i + \frac{\sum_{l' \in \Omega_j} w_{il'}(r_{il'} - \bar{r}_{l'})}{\sum_{l' \in \Omega_j} \| w_{il'} \|}\)

其中我们有偏置项 \(\bar{r}_i\)。因此，我们修订评分为

\(\hat{r}_{ij} = \vec{u}_i \cdot \vec{w}_j^T + b_t + c_j + \mu\)


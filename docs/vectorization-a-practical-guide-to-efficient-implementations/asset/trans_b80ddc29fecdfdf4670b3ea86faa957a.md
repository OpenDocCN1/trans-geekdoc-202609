

### 7.1.7 对角存储稀疏矩阵 (dia_matrix)

构建对角矩阵或非对角矩阵时，dia_matrix 是最佳选择。它存储了稀疏矩阵的两项信息。

- offsets：对角偏移量数组。0 表示位于矩阵主对角线；负值表示在主对角线以下；正值表示在主对角线以上。该数组通常按升序排列（例如：主对角线以下、主对角线、主对角线以上）
- data：K × D 矩阵，其中 K 是对角线项的数量，D 是主对角线的大小。请注意，如果对角线位于非主对角线（即不在主对角线上），则
  1. 如果该对角线位于主对角线以下（offset < 0），则末尾将添加零到数组中以匹配主对角线数组的大小。
  2. 如果该对角线位于主对角线以上（offset > 0），则开头将添加零到数组中以匹配主对角线数组的大小。
  3. 这些零值实际上可以是任何其他值，但它们不会成为矩阵的一部分。在 scipy.sparse.dia_matrix 文档示例中，dia_matrix 是使用三个相同长度的向量构建的，放置在对角线 [-1, 0, 1] 上。然而，通过 A.data 访问数据时，初始构建后并未立即填充零，先转换为 coo_matrix 再转回 dia_matrix 并再次使用 A.data 访问数据将显示这些开头和末尾的零。

图 7.8 显示了一个 dia_matrix 示例。

可以使用以下方式构建 dia_matrix

```
from scipy.sparse import dia_matrix
A = dia_matrix([
    [1, 0, 0, 0, 0],
    [0, 1, 0, 0, 0],
    [0, 0, 1, 0, 0],
    [2, 0, 0, 1, 0],
    [0, 2, 0, 0, 1],
])
```

在图 7.8 所示的示例矩阵中，矩阵的两个属性为

```
A.data = [
    [2, 2, 0, 0, 0],
    [1, 1, 1, 1, 1],
]
A.offsets = [-3, 0]
```

图 7.8 dia_matrix 示例。

![](img/e891acaacd4fb5b80dab2ed824618203_254_0.png)

### 7.1.8 不同稀疏矩阵格式的比较

表 7.1 总结了构建和更新七种稀疏矩阵的方法。除了从稠密矩阵构建（其中 0 被视为空条目）之外，还有更高效的方法：直接针对每种数据结构指定索引和相应的数据值（以及其他所需属性）来构建这些矩阵。例如，构建 coo_matrix 时，可以直接指定稀疏矩阵的 row、col、data 和 shape，即 coo_matrix((data, (rows, cols)), [shape=(M, N)])。此外，对于 dok_matrix、lil_matrix 和 dia_matrix，我还包含了一些用于原地更新矩阵的方法，这些方法在 scipy 的文档中找不到。

除了使用 .to<format> 方法在不同稀疏矩阵格式之间转换之外，我们还可以使用 .asformat() 方法。如果我们希望实现一个函数，在另一种格式中执行某些操作，但在返回结果时仍保留原始格式，这将非常方便。例如，

```
def function_retaining_sparse_format(A):
    # Convert to csr_matrix
    B = A.tocsr() # this makes a copy
    # Do something on B ...
    # Convert back to the original format
    return B.asformat(A.format)
```

表 7.2 比较了每种稀疏矩阵多种操作的性能。通常，csc_matrix、csr_matrix 和

表 7.1 七种稀疏矩阵格式的构建、更新与相互转换。

| 类型 | 从稠密矩阵 | 相互转换 | 空矩阵 | 从数组和行/列索引 | 特定于格式的构建/更新 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| csc | csc_matrix(D) | .tocsc() | csc_matrix((M, N), [dtype]) | csc_matrix((data, (rows, cols)), [dtype]) | 索引 & indptr 构建: csc_matrix((data, indices, indptr), [shape=(M, N)]) |
| csr | csr_matrix(D) | .tocsr() | csr_matrix((M, N), [dtype]) | csr_matrix((data, (rows, cols)), [dtype]) | 索引 & indptr 构建: csr_matrix((data, indices, indptr), [shape=(M, N)]) |
| bsr | bsr_matrix(D, [blocksize = (R, C)]) | .tobsr([blocksize = (R, C)]) | bsr_matrix((M, N), [blocksize=(R, C), dtype]) | bsr_matrix((data, (rows, cols)), [blocksize=(R, C), shape=(M, N)]) | 索引 & indptr 构建: bsr_matrix((data, indices, indptr), [shape=(M, N)]) |
| coo | coo_matrix(D) | .tocoo() | coo_matrix((M, N), [dtype]) | coo_matrix((data, (rows, cols)), [shape=(M, N)]) | 添加新数据: mat_coo.data = np.r_[mat_coo.data, data], mat_coo.row = np.r_[mat_coo.row, rows], mat_coo.col = np.r_[mat_coo.col, cols] |
| dok | dok_matrix(D) | .todok() | dok_matrix((M, N), [dtype]) | N/A | 行 & 列更新: dict.update(mat_dok, zip(zip(rows, cols), data)) |
| lil | lil_matrix(D) | .tolil() | lil_matrix((M, N), [dtype]) | N/A | 行 & 列更新: mat_lil[rows, cols] = data |
| dia | dia_matrix(D) | .todia() | dia_matrix((M, N), [dtype]) | dia_matrix((data, offsets), shape=(M, N)) | mat_dia.setdiag(data, offset) |

| 类型 | 构建 | 添加新元素 | 切片 | 算术操作 |
|---|---|---|---|---|
|csc | 慢 | 非常慢 | 高效的列切片 | 高效 |
|csr | 慢 | 非常慢 | 高效的行切片 | 高效 |
|bsr | 慢 | 非常慢 | 高效的行切片 | 有时比 csr_matrix 更高效 |
|coo | 快 | 高效 | 原生不支持 | 原生不支持 |
|dok | 高效 | 高效 | 原生不支持，单个元素 O(1) 访问 | 慢 |
|lil | 高效，方便 | 高效 | 灵活切片，但列切片慢 | 慢 |
|dia | 高效 | 高效 | 原生不支持 | 高效 |

bsr_matrix 非常适合算术操作，而其他矩阵更适合矩阵构建。

## 7.2 稀疏矩阵广播

有许多情况我们希望对列、行或整个矩阵进行加、减或归一化，而不影响缺失数据。在本节中，我们将考虑几种稀疏矩阵广播的情况。

### 7.2.1 标量广播

与 numpy 不同，直接在稀疏矩阵上执行 mat_csc + 1 添加标量会报错。

> NotImplementedError: 添加非零标量到稀疏矩阵不受支持

幸运的是，矩阵的实际数据作为 numpy.ndarray 存储在 .data 属性中。因此，我们可以直接修改 .data 属性，

```
mat_csc.data += 1
```

### 7.2.2 按行广播

假设我们有一个大小为 M x N 的 csr 稀疏矩阵 mat_csr 和一个长度为 M 的行向量 array_r。我们希望按元素逐行将稀疏矩阵的每一行与行向量相加（或相减、相乘、相除）。回顾第 2 章，在 NumPy 中使用稠密矩阵（mat_dense）时，可以通过广播简单地实现这一点

```
mat_dense + array_r[np.newaxis, :]
```

对于稀疏矩阵，我们同样可以访问 .data 属性。还可以通过 .indices 属性访问每个数据点的列索引（见图 7.9），因此等效的稀疏矩阵按行广播为

```
mat_csr.data += np.take(array_r, mat_csr.indices)
```

对于其他类型的稀疏矩阵，首先使用 tocsr() 转换为 csr_matrix，进行广播计算，然后如果需要，再转换回原始格式。可以这样实现

```
def R_plus_rv(R, rv):
    """Sparse matrix plus a row vector"""
    R = R.tocsr()
    R.data += np.take(rv, R.indices)
    return R
```

![](img/e891acaacd4fb5b80dab2ed824618203_257_0.png)

图 7.9 按行广播示例。

### 7.2.3 按列广播

同样，对于按列广播，在 NumPy 中使用稠密矩阵，可以通过广播完成

```
mat_dense + array_c[:, np.newaxis]
```

对于稀疏矩阵，假设我们有一个大小为 M x N 的 `csc` 矩阵 `mat_csc` 和一个大小为 N 的向量 `array_c`。如果我们想将向量广播到稀疏矩阵的所有列（另见图 7.10），可以执行

```
mat_csc.data += np.take(array_c, mat_csc.indices)
```

同样，对于其他类型的稀疏矩阵，首先使用 `tocsc()` 转换为 `csc_matrix`，进行广播计算，然后如果需要，再转换回原始格式。可以这样实现

```
def R_plus_cv(R, cv):
    """Sparse matrix plus a column vector"""
    R = R.tocsc()
    R.data += np.take(cv, R.indices)
    return R
```

### 7.2.4 稀疏索引上的乘法

在矩阵分解问题中，我们通常需要在预测之后，通过相乘两个分解的稠密矩阵来计算损失函数。但由于损失

![](img/e891acaacd4fb5b80dab2ed824618203_258_0.png)

**图 7.10** 按列广播示例。


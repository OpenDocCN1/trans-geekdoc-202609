

机器学习应用经常需要指数和对数来计算误差和概率。为满足这一需求，TensorFlow 提供了与 NumPy 中相同的许多函数。[Table 3-7](#07_9788126592555-ch03.xhtml#c03-tbl-0007) 列出了其中 11 个，并提供了每个函数的描述。

[TABLE 3-7](#07_9788126592555-ch03.xhtml#rc03-tbl-0007) 指数和对数运算

| **Function** || **Description** |
| --- | --- |
| `square(x, name=None)` || 返回参数的平方 |
| --- | --- |
| `squared_difference(x, y, name=None)` || 用第二个参数减去第一个参数并返回平方 |
| `sqrt(x, name=None)` || 返回参数的平方根 |
| `rsqrt(x, name=None)` || 返回平方根的倒数 |
| `pow(x, y, name=None)` || 返回第一个张量元素对第二个张量元素求幂的结果 |
| `exp(x, name=None)` || 返回参数的指数函数 |
| `expm1(x, name=None)` || 返回参数的指数函数减一，`exp(x) - 1` |
| `log(x, name=None)` || 返回参数的自然对数 |
| `log1p(x, name=None)` || 返回参数加 1 的自然对数，`log(x + 1)` |
| `erf(x, name=None)` || 返回参数的误差函数 |
| `erfc(x, name=None)` || 返回参数的互补误差函数 |

这些函数使用起来很直接，理解起来也很简单。每个函数都按元素执行，并且以下代码演示了如何调用 `square`、`sqrt` 和 `rsqrt`：

```
t = tf.constant([4.])
t1 = tf.square(t) # 16
t2 = tf.sqrt(t) # 2
t3 = tf.rsqrt(t) # 0.5
```

`exp` 函数计算张量元素的指数函数，而 `expm1` 从每个指数中减去 1。如果 `x` 是输入张量中的一个值，则 `expm1` 的结果等于 `exp(x) – 1`。

类似地，`log` 函数计算张量元素的自然对数。`logp1` 在计算对数之前先给值加上 1，因此如果 `x` 是输入张量中的一个值，则 `logp1` 的结果等于 `log(x + 1)`。

### 向量和矩阵运算

机器学习应用在向量（一维张量）和矩阵（二维张量）中存储了大量数据。为了处理这些数据，TensorFlow 提供了许多在向量和矩阵上操作的函数。[Table 3-8](#07_9788126592555-ch03.xhtml#c03-tbl-0008) 列出了这些函数并提供了每个函数的描述。

[TABLE 3-8](#07_9788126592555-ch03.xhtml#rc03-tbl-0008) 向量和矩阵运算

| **Function** || **Description** |
| --- | --- |
| `tensordot(a, b, axes, name=None)` || 返回给定轴上元素的乘积之和 |
| --- | --- |
| `cross(a, b, name=None)` || 返回逐元素的叉积 |
| `diag(diagonal, name=None)` || 返回具有给定对角线值的矩阵，其他值设为零 |
| `trace(x, name=None)` || 返回对角线元素的总和 |
| `transpose(x, perm=None, name='transpose')` || 交换行和列 |
| `eye(num_rows, num_columns=None, batch_shape=None, dtype=tf.float32, name=None)` || 创建具有给定形状和数据类型的单位矩阵 |
| `matmul(a, b, transpose_a=False, transpose_b=False, adjoint_a=False, adjoint_b=False, a_is_sparse=False, b_is_sparse=False, name=None)` || 返回两个输入矩阵的乘积 |
| `norm(tensor, ord='euclidean', axis=None, keep_dims=False, name=None)` || 返回输入张量给定轴的范数，指定阶数 |
| `matrix_solve(A, b, adjoint=None, name=None)` || 返回张量 `x,` 使得 `Ax = b`，其中 `A` 是矩阵，`b` 是向量 |
| `qr(input, full_matrices=None, name=None)` || 返回给定矩阵或矩阵的特征向量和特征值 |
| `svd(tensor, full_matrices=False, compute_uv=True, name=None)` || 将矩阵分解为酉矩阵、对角矩阵和酉矩阵的共轭转置 |
| `einsum(equation, *inputs)` || 执行自定义数学运算 |

在这些函数中，最常见的两个是 `tensordot` 和 `matmul`。`tensordot` 返回两个输入张量的一个或多个轴的点积。也就是说，`tensordot` 将两个张量维度的对应元素相乘并返回乘积之和。

`axes` 参数告诉 `tensordot` 处理哪些维度。如果将此参数设为标量 `N`，函数将访问第一个张量的最后 `N` 个轴和第二个张量的前 `N` 个轴。如果将 `axes` 设为列表或张量，第一行标识第一个张量的轴，第二行标识第二个张量的轴。

我经常调用 `tensordot` 来计算两个一维张量的点积。以下代码展示了其外观：

```
t1 = tf.constant([4., 3., 2.])
t2 = tf.constant([3., 2., 1.])
dot = tf.tensordot(t1, t2, 1)
# 4*3 + 3*2 + 2*1 = 20
```

`matmul` 执行传统的矩阵乘法。也就是说，它将第一个张量的行与第二个张量的列相乘并返回包含和的矩阵。以下代码展示了如何使用它：

```
t1 = tf.constant([[1.0, 2.0, 3.0], [4.0, 5.0, 6.0]])
t2 = tf.constant([[1.0, 2.0], [3.0, 4.0], [5.0, 6.0]])
dot = tf.matmul(t1, t2)
# [[ 22. 28.], [ 49. 64.]]
```

我在 [Table 3-8](#07_9788126592555-ch03.xhtml#c03-tbl-0008) 中最喜欢的函数是 `einsum`，它使得创建和执行自定义数学运算成为可能。第一个参数是一个字符串，使用一种称为 *爱因斯坦求和约定* 的特殊格式来标识运算。该约定具有以下几个特征，包括：

* 运算假定有一个或两个输入。如果提供两个输入，必须用逗号分隔它们。
* 输入和输出矩阵的维度由下标表示（通常为 `i`、`j` 和 `k`）。输入下标必须与 `->` 符号分隔输出下标。
* 如果输入的下标重复且没有给出输出下标，则运算执行加法。因此，`einsum('i,i', t1, t2)` 计算张量 `t1` 和 `t2` 的点积。
* 如果输入的下标重复且给出输出下标，则运算执行乘法。因此，`einsum('i,i->i', t1, t2)` 计算张量 `t1` 和 `t2` 的逐元素乘积。

以下代码调用 `einsum` 来转置一个矩阵并将两个矩阵相乘：

```
m1 = tf.constant([[1, 2], [3, 4]])
m2 = tf.constant([[5, 6], [7, 8]])
e1 = tf.einsum('ij->ji', m1) # [[1, 3], [2, 4]]
e2 = tf.einsum('ij,jk->ik', m1, m2) # [[19, 22], [43, 50]]
```

有关爱因斯坦求和约定的更完整讨论，我推荐 Samuel Prime 在 [`https://samuelprime.wordpress.com/2015/03/25/einstein-summation-convention`](https://samuelprime.wordpress.com/2015/03/25/einstein-summation-convention) 的演示。

## 将理论付诸实践

`ch3/simple_math.py` 中的代码演示了本章介绍的许多函数。[Listing 3-1](#07_9788126592555-ch03.xhtml#c03-fea-0001) 展示了完整的应用程序。

[LISTING 3-1](#07_9788126592555-ch03.xhtml#rc03-fea-0001) 简单数学运算

```
# Math with constant tensors
const_a = tf.constant(3.6)
const_b = tf.constant(1.2)
total = const_a + const_b
quot = tf.div(const_a, const_b)

# Math with random tensors
rand_a = tf.random_normal([3], 2.0)
rand_b = tf.random_uniform([3], 1.0, 4.0)
diff = tf.subtract(rand_a, rand_b)

# Vector multiplication
vec_a = tf.linspace(0.0, 3.0, 4)
vec_b = tf.fill([4, 1], 2.0)
prod = tf.multiply(vec_a, vec_b)
dot = tf.tensordot(vec_a, vec_b, 1)

# Matrix multiplication
mat_a = tf.constant([[2, 3], [1, 2], [4, 5]])
```


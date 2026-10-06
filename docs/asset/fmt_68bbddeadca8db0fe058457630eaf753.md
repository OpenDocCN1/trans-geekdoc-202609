
```
t = tf.constant([-6.5, -3.5, 3.5, 6.5])
r1 = tf.round(t) # [-6. -4. 4. 6.]
r2 = tf.rint(t) # [-6. -4. 4. 6.]
r3 = tf.ceil(t) # [-6. -3. 4. 7.]
r4 = tf.floor(t) # [-7. -4. 3. 6.]
```

The next two functions in the table, `maximum` and `minimum`, are easy to understand. `maximum` returns a tensor containing the larger element of each input tensor, and `minimum` returns a tensor containing the smaller element of each input tensor.

`argmax` and `argmin` return the index values of the largest and smallest elements of a tensor. The following code shows how you can use these functions:

```
t1 = tf.constant([0, -2, 4, 6])
t2 = tf.constant([[1, 3], [7, 2]])
r1 = tf.argmin(t1) # 1
r2 = tf.argmax(t2) # [ 1 0 ]
```

If a tensor has multiple maximum/minimum values, `argmax` and `argmin` will return the index values of the first occurring element.

### Exponents and logarithms

机器学习应用经常需要指数和对数来计算误差和概率。为满足这一需求，TensorFlow 提供了与 NumPy 中相同的许多函数。Table 3-7 列出了其中 11 个，并提供了每个函数的描述。

TABLE 3-7 指数和对数运算

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

机器学习应用在向量（一维张量）和矩阵（二维张量）中存储了大量数据。为了处理这些数据，TensorFlow 提供了许多在向量和矩阵上操作的函数。Table 3-8 列出了这些函数并提供了每个函数的描述。

TABLE 3-8 向量和矩阵运算

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
#### 4*3 + 3*2 + 2*1 = 20
```

`matmul` 执行传统的矩阵乘法。也就是说，它将第一个张量的行与第二个张量的列相乘并返回包含和的矩阵。以下代码展示了如何使用它：

```
t1 = tf.constant([[1.0, 2.0, 3.0], [4.0, 5.0, 6.0]])
t2 = tf.constant([[1.0, 2.0], [3.0, 4.0], [5.0, 6.0]])
dot = tf.matmul(t1, t2)
#### [[ 22. 28.], [ 49. 64.]]
```

我在 Table 3-8 中最喜欢的函数是 `einsum`，它使得创建和执行自定义数学运算成为可能。第一个参数是一个字符串，使用一种称为 *爱因斯坦求和约定* 的特殊格式来标识运算。该约定具有以下几个特征，包括：

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

### 将理论付诸实践

`ch3/simple_math.py` 中的代码演示了本章介绍的许多函数。Listing 3-1 展示了完整的应用程序。

LISTING 3-1 简单数学运算

```
#### Math with constant tensors
const_a = tf.constant(3.6)
const_b = tf.constant(1.2)
total = const_a + const_b
quot = tf.div(const_a, const_b)

#### Math with random tensors
rand_a = tf.random_normal([3], 2.0)
rand_b = tf.random_uniform([3], 1.0, 4.0)
diff = tf.subtract(rand_a, rand_b)

#### Vector multiplication
vec_a = tf.linspace(0.0, 3.0, 4)
vec_b = tf.fill([4, 1], 2.0)
prod = tf.multiply(vec_a, vec_b)
dot = tf.tensordot(vec_a, vec_b, 1)

#### Matrix multiplication
mat_a = tf.constant([[2, 3], [1, 2], [4, 5]])
```

`mat_b = tf.constant([[6, 4, 1], [3, 7, 2]])`

`mat_prod = tf.matmul(mat_a, mat_b)`

#### Execute the operations

```python
with tf.Session() as sess:
    print("Sum: %f" % sess.run(total))
    print("Quotient: %f" % sess.run(quot))
    print("Difference: ", sess.run(diff))
    print("Element-wise product: ", sess.run(prod))
    print("Dot product: ", sess.run(dot))
    print("Matrix product: ", sess.run(mat_prod))
```

大部分代码应该看起来很熟悉。该应用程序创建并操作常量张量、随机张量、向量和矩阵。为了处理向量，应用程序使用 `tf.multiply` 执行逐元素乘法，然后使用 `tf.tensordot` 计算两个向量的点积。

代码的最后一部分值得解释。应用程序创建一个名为 `sess` 的 `Session` 并对每个要执行的运算调用其 `run` 方法。要理解会话是什么以及它们如何工作，你需要熟悉图。下一章将探讨会话和图相关主题。

#### Chapter 4

#### Executing Graphs in Sessions

IN THIS CHAPTER

![check](img/check.png) **Creating graphs and accessing their data**

![check](img/check.png) **Serializing data from a graph into a GraphDef**

![check](img/check.png) **Creating and launching sessions**

![check](img/check.png) **Printing messages to the log**

![check](img/check.png) **Visualizing summary data with TensorBoard**

上一章介绍了大量创建、转换和处理张量的函数。这些函数大多数返回一个张量，这可能会让你认为函数在被调用时立即执行其操作。这就是 Python 函数通常的工作方式，但这不是 TensorFlow 函数的工作方式。

当应用程序执行创建、转换或处理张量的 TensorFlow 函数时，该函数并不执行其操作。相反，它将操作存储在称为 *graph* 的数据结构中。图可以容纳许多操作，并且它们在应用程序在会话中执行图之前不会被执行。当会话执行图时，它会按顺序执行图的操作。

将操作存储在图中的好处是图可以导出到文件或在远程系统上启动。缺点是图往往会让 TensorFlow 新手感到困惑。在撰写本章时，我的目标是通过对图和会话的完整解释来减少这种困惑。

##### Forming Graphs

如果一个操作返回一个张量，则一个操作可以将输出馈送到另一个操作。为了演示此过程，以下代码将加法操作的结果馈送到乘法操作。

```python
c = tf.add(a, b)
e = tf.multiply(c, d)
```

Figure 4-1 说明了这些嵌套操作及其张量之间的关系。

![FIGURE 4-1: The addition operation receives the result of multiplication.](img/9788126592555-fg0401.png)

FIGURE 4-1: The addition operation receives the result of multiplication.

在 Figure 4-1 中，每个圆圈标识一个张量或操作，每个线条传输张量数据。数学家和计算机科学家将这种节点和边的结构称为 *graph*。图的圆圈称为 *nodes*，直线称为 *edges*。

当应用程序执行创建张量或操作的功能时，TensorFlow 将数据结构添加到名为 `Graph` 的容器结构中。`Graph` 不能嵌套，并且一次只能有一个 `Graph` 处于活动状态。应用程序可以通过调用 `get_default_graph` 来访问其默认 `Graph`。以下代码展示了如何使用它：

```python
graph = tf.get_default_graph()
```

应用程序可以通过调用不带参数的构造函数来创建新的 `Graph`。然后应用程序可以通过调用 `Graph` 的 `as_default` 方法将 `Graph` 设置为默认 `Graph`。以下代码演示了其工作原理：

```python
newgraph = tf.Graph()
with newgraph.as_default():
    …
```

调用 `as_default` 后，TensorFlow 将把新张量和操作添加到 `newgraph` 而不是原始 `Graph`。

`Graph` 类提供了许多访问和修改图内容的方法。此讨论将这些方法分为两类：

* **Accessing graph data:** Reading a graph's containers and elements
* **Creating `GraphDef`s:** Serializing a graph into a protocol buffer

###### Accessing graph data

图将其元素存储在一组命名集合中。Table 4-1 介绍了 `Graph` 类访问和更新这些集合的方法。

TABLE 4-1 Accessing Graph Data

| **Method** | | **Description** |

| --- | --- | --- |

| `get_tensor_by_name(name)` | | Returns the tensor with the given name |

| --- | --- | --- |

| `get_operation_by_name(name)` | | Returns the operation with the given name |

| `get_operations()` | | Returns a list containing the graph's operations |

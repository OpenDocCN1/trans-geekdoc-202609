

### 4.2.1 @ 运算符

@ 运算符是在 Python 3.5 中引入的（PEP 465 [Van Rossum and Drake, 2014]）。它可以帮助自然地表达张量乘法，从而提高实现某些数学运算的代码的可读性。它还可以帮助将类似 np.matmul(np.matmul(np.matmul(a, b), c), d) 的调用简化为 a @ b @ c @ d。该运算符与 * 运算符形成对比，* 运算符表示逐元素乘法。其使用规则与各个库中的 matmul 操作相同。Python 将根据张量表示的对象类型，假设调用哪个库的 matmul 操作。一个有趣的问题是：当存在混合变量时，哪个库的 matmul 操作会优先执行。我们可以通过一些实验来找出答案，如以下代码示例所示：

```python
import numpy as np
import tensorflow as tf
import torch

a = np.random.rand(7, 4, 3, 5)
b = np.random.rand(5)
c = np.random.rand(1, 1, 5, 3)
# this is working as expected, returns numpy.ndarray
a @ b
# This throws an error,
# Torch and NumPy is not compatible with @ operator
a @ torch.tensor(b)
# This will throw an error,
# since Tensorflow's matmul is called
a @ tf.constant(b)
# This will pass, returns a tf.Tensor
a @ tf.constant(c)
# This will pass, returns a tf.Tensor
# It does not matter if the first or
# second argument of matmul is tf.Tensor
tf.constant(a) @ c
# This will pass, returns a tf.Tensor
tf.constant(a) @ torch.tensor(c)
```

结论如下：

- PyTorch 要求输入在执行操作前必须都是 torch.Tensor，因此我们不能混合使用 NumPy 的 np.ndarray 和 Torch 张量。
- NumPy 和 Tensorflow 的张量可以混合使用（至少在急切模式下）。但 Tensorflow 的方法优先级更高，返回的结果会被转换为 tf.Tensor。广播机制在 NumPy 和 Tensorflow 之间也适用。
- Torch 和 Tensorflow 的张量也可以混合使用。在广播方面，其行为与将 Torch 张量视为 NumPy 张量相同。Tensorflow 的方法优先级更高，结果为 tf.Tensor。

## 4.3 tensordot 操作

tensordot（又称张量收缩）操作是上述所有矩阵乘法操作的推广。它沿特定轴执行点积（或者等价地说，先进行逐元素乘法，再进行求和归约操作）。它不仅接受两个相乘的输入，还接受第三个参数 axes，用于指定如果 axes 为整数，则要对多少个轴进行操作；如果为一对列表参数，则指定沿哪些特定轴对乘法结果进行求和。我们在第 4.2 节中介绍的几种数学运算可以使用 tensordot 表示：

- 向量之间的点积，$a \cdot b$，使用 tensordot(a, b, 1)：

```python
a = np.random.rand(5)
b = np.random.rand(5)
np.allclose(
    np.dot(a, b),
    np.tensordot(a, b, 1)
)
```

请注意，复共轭点积 vdot 可以通过 tensordot 使用 np.tensordot(a, b.conj(), 1) 实现。

- 向量之间的叉积（外积），$a \times b$，使用 tensordot(a, b, 0)：

```python
a = np.random.rand(5)
b = np.random.rand(3)
np.allclose(
    np.outer(a, b),
    np.tensordot(a, b, 0)
)
```

- 2D 矩阵乘法 ab：

```python
a = np.random.rand(5, 3)
b = np.random.rand(3, 5)
np.allclose(
    np.matmul(a, b),
    np.tensordot(a, b, 1)
)
```

tensordot 的典型用法是实现双重矩阵/张量收缩（通常表示为 a : b = Tr(a · b^T)），给定两个矩阵输入，使用 tf.tensordot(a, b, 2)：

```python
a = np.random.rand(5, 3)
b = np.random.rand(5, 3)
np.allclose(
    np.tensordot(a, b, 2),
    np.trace(a @ b.T)
)
```

tensordot 可用于更通用的张量乘法，尤其是当 axes 参数作为一对索引列表提供时。请注意 len(axes[0]) == len(axes[1])。维度列表中的值也可以是负数。例如，我们想要计算三个矩阵堆栈与另一个形状为 (4, 2) 的两个矩阵堆栈之间的矩阵收缩，

```python
a = np.random.rand(2, 4, 2)
b = np.random.rand(3, 4, 2)
# this results a tensor of shape (2, 3)
np.tensordot(a, b, axes=([1, 2], [1, 2]))
```

上述示例在图 4.1 中进行了说明。

![](img/e891acaacd4fb5b80dab2ed824618203_145_0.png)

**Figure 4.1** 形状为 (2, 4, 2) 和 (3, 4, 2) 的张量之间示例 tensordot 操作的说明。请注意，第一个列向量组合之间的点积结果是 2 x 2 矩阵左上角的瓦片，而第二个列向量组合之间的点积结果是 2 x 2 矩阵右下角的瓦片。2 x 2 矩阵对角线沿线的值之和是形状为 (2, 3) 的最终矩阵的值。

### 4.3.1 tensordot 操作的启发式

从上述示例可以注意到，当 `axes` 参数发生变化时，`tensordot` 操作的输出张量形状也会随之变化。`axes` 参数的不同整数值似乎决定了不同的张量乘法行为。但我们可以通过归纳推理推导出一条通用经验法则。

当 `axes=0` 时，给定两个向量输入 `(m, )` 和 `(n, )`，我们已经看到结果张量的形状为 `(m, n)`，仿佛进行了外积。一般来说，当给定两个形状为 `(m, n, ...)` 的张量 `a` 和形状为 `(p, q, ...)` 的张量 `b` 时，`axes=0` 的 tensordot 形状为 `(m, n, ..., p, q, ...)`。这仿佛张量 `a` 的每个单独元素都与张量 `b` 的每个单独元素相乘，形成最终张量，而无需进行求和以减少任何维度。图 4.2 说明了这一推广。以下代码片段演示了此启发式的一个示例：

```python
a = np.random.rand(2, 3, 4, 5)
b = np.random.rand(6, 7, 8)
np.allclose(
    np.tensordot(a, b, 0).shape,
    [2, 3, 4, 5, 6, 7, 8]
)
```

![](img/e891acaacd4fb5b80dab2ed824618203_146_0.png)

**Figure 4.2** 当 `axes=0` 时 `tensordot` 操作的说明。（a）对于形状为 `(5, )` 和 `(4, )` 的一对一维向量，两个向量之间每个元素的组合形成外积，形状为 `(5, 4)`。（b）在第一个输入中添加一个行维度，问题变成了形状为 `(2, 5)` 的矩阵与形状为 `(4, )` 的向量之间的 tensordot 操作。因此，结果张量的形状为 `(2, 5, 4)`（请注意，单例维度会被压缩掉）。（c）在第二个输入中添加一个额外的列维度，形成了形状为 `(2, 5)` 的矩阵与形状为 `(4, 2)` 的矩阵之间的 tensordot 问题。然后，结果张量的形状为 `(2, 5, 4, 2)`。

当 axes=1 时，我们已经看到当两个输入都是一维向量时，会返回两个张量的点积（一个标量）。一般来说，给定形状为 (m, n, ..., i) 的张量 a 和形状为 (i, ..., p, q, ...) 的张量 b，两个张量与 axes=1 的张量点积的形状为 (m, n, ..., p, q, ...)，其中 a 的最后一个维度和 b 的第一个维度被一起归约。这仿佛我们在两个向量批次的组合之间执行一系列点积。图 4.3 说明了此推广的示例。以下代码片段演示了此启发式的一个示例：

```python
a = np.random.rand(2, 3, 4, 5)
b = np.random.rand(5, 6, 7)
np.allclose(
    np.tensordot(a, b, 1).shape,
    [2, 3, 4, 6, 7]
)
```

当 axes=2 时，两个输入张量必须至少有两个维度。我们已经看到，给定两个矩阵时可以执行双重张量收缩操作。一般来说，给定形状为 (m, n, ..., i, j) 的张量 a 和形状为 (i, j, ..., p, q, ...) 的张量 b，a 和 b 与 axes=2 之间的张量点积形状为 (m, n, ..., p, q, ...)，其中 a 的最后两个维度和 b 的前两个维度被收缩。图 4.4 说明了此推广的示例。以下代码片段演示了此启发式的一个示例：

```python
a = np.random.rand(2, 3, 4, 5)
b = np.random.rand(4, 5, 6, 7)
np.allclose(
    np.tensordot(a, b, 2).shape,
    [2, 3, 6, 7]
)
```

在探讨了 axes=0、axes=1 和 axes=2 的上述启发式后，我们可以推导出当 axes 为整数参数时的更通用规则：给定第一个输入张量 a 形状为 (m, n, ..., s1, s2, ..., sk)，如果我们想要执行 axes=k 的张量点积，则需要使第二个输入张量 b 形状为 (s1, s2, ..., sk, ..., p, q, ...)。来自张量 a 的每个形状为 (s1, s2, ..., sk) 的张量子块与来自 b 的相同形状的张量子块逐元素相乘，然后求和形成一个单个标量。结果张量将具有形状 (m, n, ..., p, q, ...)，其中第一个输入 a 的最后 k 个维度和第二个输入 b 的前 k 个维度被收缩（即归约或求和）。


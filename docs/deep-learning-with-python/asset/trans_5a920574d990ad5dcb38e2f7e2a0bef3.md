

x = x.copy()
for i in range(x.shape[0]):
    for j in range(x.shape[1]):
        x[i, j] = max(x[i, j], 0)
return x

你也可以对加法做同样的操作：

```
def naive_add(x, y):
    assert len(x.shape) == 2
    assert x.shape == y.shape
    x = x.copy()
    for i in range(x.shape[0]):
        for j in range(x.shape[1]):
            x[i, j] += y[i, j]
    return x
```

基于同样的原理，你可以进行逐元素乘法、减法等运算。

在实践中，处理 NumPy 数组时，这些操作都有经过良好优化的内置 NumPy 函数可用，这些函数本身将繁重工作委托给基础线性代数子程序（BLAS）实现。BLAS 是低级的、高度并行、高效的张量操作例程，通常使用 Fortran 或 C 语言实现。

所以，在 NumPy 中，你可以执行以下逐元素操作，速度会非常快：

```
import numpy as np
z = x + y
z = np.maximum(z, 0.)
```

让我们实际计时一下差异：

```
import time

x = np.random.random((20, 100))
y = np.random.random((20, 100))

t0 = time.time()
for _ in range(1000):
    z = x + y
    z = np.maximum(z, 0.)

print("Took: {0:.2f} s".format(time.time() - t0))
```

这需要 0.02 秒。与此同时，天真版本需要惊人的 2.45 秒：

```
t0 = time.time()
for _ in range(1000):
    z = naive_add(x, y)
    z = naive_relu(z)

print("Took: {0:.2f} s".format(time.time() - t0))
```

同样，在 GPU 上运行 TensorFlow 代码时，逐元素操作通过完全向量化的 CUDA 实现执行，可以充分利用高度并行的 GPU 芯片架构。

## 2.3.2 广播机制

我们之前对 naive_add 的天真实现仅支持形状相同的秩-2 张量的加法。但如前面介绍的 Dense 层中，我们将一个秩-2 张量与向量相加。当相加的两个张量形状不同时，加法会发生什么？

在可能且无歧义的情况下，较小的张量将被广播以匹配较大张量的形状。广播包含两个步骤：

- 1 将轴（称为广播轴）添加到较小的张量，以匹配较大张量的 ndim。
- 2 沿着这些新轴重复较小的张量，以匹配较大张量的完整形状。

让我们看一个具体的示例。考虑形状为 (32, 10) 的 X 和形状为 (10,) 的 y：

```
import numpy as np
X = np.random.random((32, 10))
y = np.random.random((10,))
```

首先，我们在 y 的最前面添加一个空轴，其形状变为 (1, 10)：

```
y = np.expand_dims(y, axis=0)
```

然后，沿着这个新轴将 y 重复 32 次，从而得到形状为 (32, 10) 的张量 Y，其中对于 0 到 32 范围内的 i，Y[i, :] == y：

```
Y = np.concatenate([y] * 32, axis=0)
```

此时，我们可以继续相加 X 和 Y，因为它们形状相同。

从实现角度来看，不会创建新的秩-2 张量，因为这将极其低效。重复操作完全是虚拟的：它发生在算法级别，而不是内存级别。但将向量沿新轴重复 10 次视为一个有用的心智模型。天真的实现看起来如下：

```
def naive_add_matrix_and_vector(x, y):
    assert len(x.shape) == 2
    assert len(y.shape) == 1
    assert x.shape[1] == y.shape[0]
    x = x.copy()
    for i in range(x.shape[0]):
        for j in range(x.shape[1]):
            x[i, j] += y[j]
    return x
```

使用广播，通常可以对两个输入张量进行逐元素操作，前提是一个张量的形状为 `(a, b, ..., n + 1, ... m)`，另一个张量的形状为 `(n, n + 1, ... m)`。广播将自动发生在轴 a 到 n - 1 上。

以下示例通过广播将逐元素最大值操作应用于两个形状不同的张量：

```
import numpy as np
x = np.random.random((64, 3, 32, 10))
y = np.random.random((32, 10))
z = np.maximum(x, y)
```

## 2.3.3 张量积

*张量积*，或*点积*（不要与逐元素积混淆，即 `*` 运算符），是最常见、最有用的张量操作之一。

在 NumPy 中，张量积使用 `np.dot` 函数来完成（因为张量积的数学记号通常是一个点）：

```
x = np.random.random((32,))
y = np.random.random((32,))
z = np.dot(x, y)
```

在数学记号中，你会用一个点（⋅）来表示该操作：

```
z = x • y
```

从数学上讲，点操作做什么？让我们从两个向量 x 和 y 的点积开始。它的计算方式如下：

```
def naive_vector_dot(x, y):
    assert len(x.shape) == 1
    assert len(y.shape) == 1
    assert x.shape[0] == y.shape[0]
    z = 0.
    for i in range(x.shape[0]):
        z += x[i] * y[i]
    return z
```

你会注意到，两个向量之间的点积是一个标量，并且只有元素数量相同的向量才能进行点积运算。

你也可以对矩阵 x 和向量 y 求点积，这将返回一个向量，其中系数是 y 与 x 的行之间的点积。你可以这样实现：

```
def naive_matrix_vector_dot(x, y):
    assert len(x.shape) == 2
    assert len(y.shape) == 1
    assert x.shape[1] == y.shape[0]
    z = np.zeros(x.shape[0])
    for i in range(x.shape[0]):
        for j in range(x.shape[1]):
            z[i] += x[i, j] * y[j]
    return z
```

你还可以重用我们之前编写的代码，这突出了矩阵-向量积与向量积之间的关系：

```
def naive_matrix_vector_dot(x, y):
    z = np.zeros(x.shape[0])
    for i in range(x.shape[0]):
        z[i] = naive_vector_dot(x[i, :], y)
    return z
```

请注意，一旦两个张量中有一个的 ndim 大于 1，dot 就不再对称，也就是说 dot(x, y) 与 dot(y, x) 不相同。

当然，点积推广到具有任意数量轴的张量。最常见的应用可能是两个矩阵之间的点积。只有当 x.shape[1] == y.shape[0] 时，才能对两个矩阵 x 和 y 求点积（dot(x, y)）。结果是一个形状为 (x.shape[0], y.shape[1]) 的矩阵，其中系数是 x 的行与 y 的列之间的向量积。天真的实现如下：

```
def naive_matrix_dot(x, y):
    assert len(x.shape) == 2
    assert len(y.shape) == 2
    assert x.shape[1] == y.shape[0]
    z = np.zeros((x.shape[0], y.shape[1]))
    for i in range(x.shape[0]):
        for j in range(y.shape[1]):
            row_x = x[i, :]
            column_y = y[:, j]
            z[i, j] = naive_vector_dot(row_x, column_y)
    return z
```

为了理解点积形状兼容性，将输入和输出张量如图 2.5 所示对齐进行可视化会有所帮助。

在图中，x、y 和 z 被画成矩形（系数的字面框）。由于 x 的行和 y 的列必须具有相同的大小，因此 x 的宽度必须与 y 的高度匹配。如果你继续开发新的机器学习算法，你可能会经常绘制此类图表。

![](img/ab452ecf572a1f1372915be13bd8088f_67_0.png)

更一般地，你可以对更高维的张量求点积，遵循前面为 2D 情况概述的相同形状兼容性规则：

```
(a, b, c, d) • (d,) → (a, b, c)
(a, b, c, d) • (d, e) → (a, b, c, e)
```

等等。

## 2.3.4 张量重塑

第三种必须理解的张量操作是*张量重塑*。尽管它在我们第一个神经网络示例的 `Dense` 层中未被使用，但在将数据馈送到模型之前预处理数字数据时我们用到了它：

```
train_images = train_images.reshape((60000, 28 * 28))
```

重塑张量意味着重新排列其行和列以匹配目标形状。自然，重塑后的张量与初始张量具有相同的系数总数。重塑最好通过简单的示例来理解：

```
>>> x = np.array([[0., 1.],
   [2., 3.],
   [4., 5.]])
>>> x.shape
(3, 2)
>>> x = x.reshape((6, 1))
>>> x
array([[ 0.],
       [ 1.],
       [ 2.],
       [ 3.],
       [ 4.],
       [ 5.]])
```


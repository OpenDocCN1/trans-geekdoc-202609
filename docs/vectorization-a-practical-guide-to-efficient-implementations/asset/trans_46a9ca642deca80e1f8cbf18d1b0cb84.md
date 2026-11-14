

Chintala. torch.Tensor.index_reduce. https://pytorch.org/docs/stable/generated/torch.Tensor.index_reduce.html#torch-tensor-index-reduce, 2023b.

Adam Paszke, Sam Gross, Francisco Massa, Adam Lerer, James Bradbury, Gregory Chanan, Trevor Killeen, Zeming Lin, Natalia Gimelshein, Luca Antiga, Alban Desmaison, Andreas Köpf, Edward Yang, Zach DeVito, Martin Raison, Alykhan Tejani, Sasank Chilamkurthy, Benoit Steiner, Lu Fang, Junjie Bai, and Soumith Chintala. torch.Tensor.scatter_reduce. https://pytorch.org/docs/stable/generated/torch.Tensor.scatter_reduce.html#torch.Tensor.scatter_reduce, 2023c.

## 4 线性代数

在第 2 章中，我们介绍了张量或一对张量上的逐元素操作。具体来说，当对两个张量进行逐元素相乘时，我们执行的是称为 Hadamard 积（Hadamard Product）的数学运算，其数学表达式为 \( X \cdot Y \)。在本章中，我们将首先探讨与矩阵和张量乘法相关的操作，这些操作在数学上表示为 \( X \cdot Y \) 或简单地写作 \( XY \)。然后我们将探讨几种其他常见的线性代数例程，例如求矩阵逆和特征值分解。在向量、矩阵和高维张量之间进行乘法运算、求矩阵逆以及计算特征值分解，都是实现机器学习模型时的常见任务，这些任务通常使用数学术语来描述。

## 4.1 张量乘法

让我们先从张量乘法操作的概述开始讨论。表 4.1 总结了 NumPy、Tensorflow 和 PyTorch 库中实现的常用张量乘法操作。
然后我们将把接下来的两个部分专门用于讨论 `matmul`（第 4.2 节）和 `tensordot`（第 4.3 节）操作。

## 4.2 matmul 操作

`np.matmul` 操作执行应用于多维批次的通用矩阵乘法。

- 当输入张量为形状为 \( (n, k) \) 和 \( (k, m) \) 的 2D 矩阵时，则为常规矩阵乘法，结果为形状为 \( (n, m) \) 的矩阵。

表 4.1 NumPy、Tensorflow 和 PyTorch 中张量乘法操作示例。

| 操作 | NumPy | Tensorflow | PyTorch |
|---|---|---|---|
| 点积<sup>a)</sup> | np.dot | tf.experimental.numpy.dot | torch.dot |
| 复共轭点积<sup>b)</sup> | np.vdot | tf.experimental.numpy.vdot | torch.vdot |
| 内积<sup>c)</sup> | np.inner | tf.experimental.numpy.inner | torch.inner |
| 外积（叉积）<sup>d)</sup> | np.outer | tf.experimental.numpy.outer | torch.outer |
| 矩阵乘法 | np.matmul | tf.matmul | torch.matmul |
| 张量点积 | np.tensordot | tf.tensordot | torch.tensordot |

注释：

a) NumPy 的 `np.dot` 可支持 1D 向量之间、2D 矩阵之间（等同于 `np.matmul`）或 N-D 张量之间的点积。相比之下，`torch.dot` 仅支持 1D 向量。Tensorflow 在 `tf.experimental.numpy` 模块下实现了等效操作。

b) `np.vdot` 操作在求点积前会对第一个输入应用复共轭，而 `np.dot` 不执行复共轭。从数学上讲，对于两个复向量 $a, b$，$\text{dot}(a, b) = (x_a + i y_a) \cdot (x_b + i y_b)$，其中 $i$ 为虚数单位。相比之下，$\text{vdot}(a, b) = \bar{a} \cdot b = (\bar{x}_a + i \bar{y}_a) \cdot (x_b + i y_b) = (x_a - i y_a) \cdot (x_b + i y_b)$，其中上划线 (...) 表示复共轭。请注意，两个复向量之间的这种点积定义（即 `vdot()`）与 MATLAB 的实现一致，可能也与许多工程应用（如离散傅里叶变换）一致。然而，两个复向量之间点积的数学惯例使用 $(a, b) = \sum_i a_i \bar{b}_i$，其中第二个参数被复共轭。因此，在使用此函数将数学转换为代码时需特别注意，因为这两种惯例产生的结果互为复共轭。在多维张量上使用时，`np.vdot` 会在执行操作前将张量展平为 1D 向量。类似于 `torch.dot`，`torch.vdot` 仅支持用于复共轭点积的 1D 向量。Tensorflow 在 `tf.experimental.numpy` 模块下实现了等效操作。

c) `np.inner` 作用于一对 1D 向量，或至少将张量的最后一个维度视为 1D 向量。曾经有一个函数 `numpy.core.umath_tests.inner1d`，它沿一对矩阵的行执行批量内积，但已在较新版本的 NumPy 中弃用。相反，可以使用 `np.sum(a * b, axis=1)`，或 `einsum` 操作（我们将在第 4.4 节介绍）`np.einsum('ij, ij->i', a, b)`，以实现相同效果。请注意，此 einsum 操作与 `np.inner` $(a, b)$ 不同，因为 `np.inner` 会产生矩阵乘法 $a \cdot b^T$ 而非批量操作。我们可以使用以下示例来验证这一区别：

```
1  a = np.random.rand(5, 8)
2  b = np.random.rand(5, 8)
3  z1 = np.sum(a * b, axis=1) # shape (5, 8)
4  z2 = np.inner(a, b) # shape (5, 5)
5  np.allclose(
6      z2,
7      np.matmul(a, b.T)
8  )
```

d) `np.outer` 会在执行叉积前将任何多于一个维度的张量展平为向量。`torch.outer` 仅支持 1D 向量输入，在接收到多维输入时会抛出错误。Tensorflow 在 `tf.experimental.numpy` 模块下实现了 `outer` 操作。

- 当输入为多于 2 个维度的张量时，则使用最后两个维度作为乘法维度，而其他维度被视为批次维度，且必须相同或可相互广播。例如，如果我们有形状为 (a, b, n, k) 和 (1, 1, k, m) 的张量，则输出张量的维度为 (a, b, n, m)。

- 如果第一个输入是 1D 向量，则将其视为在向量长度维度之前添加单例维度的行向量，形状为 (1, ..., 1, n)，并遵循广播规则。但是，乘法后，会移除额外添加的维度。例如，长度为 (k,) 的向量与形状为 (a, b, n, k) 的张量相乘，则结果张量的形状为 (a, b, n)。

- 如果第二个输入是 1D 向量，则将其视为在向量长度维度之后添加单例维度的列向量，形状为 (m, 1, ..., 1)。但是，乘法后，会移除额外添加的维度。例如，形状为 (k, a, b, n) 的张量与长度为 (k,) 的向量相乘，则结果张量的形状为 (a, b, n)。

- 如果两个输入都是 1D 向量，则等同于点积。

与 NumPy 和 PyTorch 不同，tf.matmul 要求两个输入至少具有两个维度，因此如果任何输入是向量，它将抛出错误。此外，Tensorflow 的 tf.matmul 实现允许在执行矩阵乘法步骤之前，对两个输入进行转置（is_transpose）和共轭（is_adjoint，即转置和复共轭）预处理。假设我们想要相乘两个形状为 (5, 3) 和 (5, 3) 的矩阵。

```
import tensorflow as tf
a = tf.complex(
    tf.random.uniform((5, 3)),
    tf.random.uniform((5, 3))
)
b = tf.complex(
    tf.random.uniform((5, 3)),
    tf.random.uniform((5, 3))
)
# This will throw an error because of shape mismatch
tf.matmul(a, b)
# This will pass, with shape (5, 5)
tf.matmul(a, b, transpose_b=True)
# This will pass, with shape (3, 3)
tf.matmul(a, b, adjoint_a=True)
```

此外，tf.tensordot 也可用于矩阵乘法，例如，给定两个矩阵输入，可使用 tf.tensordot(a, b, 1)。


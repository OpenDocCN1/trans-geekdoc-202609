

## Table 2.10 (Continued)

| 操作 | Python | NumPy | Tensorflow | PyTorch |
|---|---|---|---|---|
| 展平为数组<sup>e)</sup> | N/A | np.ndarray.flatten, np.ravel | tf.experimental.numpy.flatten | torch.flatten |

涵盖了多种用例。这是许多机器学习应用（例如卷积神经网络）中的常见操作。在使用卷积神经网络进行图像分类时，通常将输入图像表示为 (batch_size, height, width, channels)（Tensorflow 约定）或 (batch_size, channels, height, width)。请注意，两种约定都表示一组图像，但张量的维度顺序不同。要从 Tensorflow 约定转换为 PyTorch 约定，我们可以利用转置操作。

```
import numpy as np
image_tf = np.random.rand(8, 32, 15, 3)
image_torch = np.transpose(image_tf, axes=[0, 3, 1, 2])
```

虽然需要两行代码，但我们也可以使用 np.swapaxes

```
image_torch = np.swapaxes(image_tf, 1, 3) # (8, 3, 15, 32)
image_torch = np.swapaxes(image_torch, 2, 3) # (8, 3, 32, 15)
```

注意 PyTorch torch.Tensor 具有 torch.Tensor.t() 方法，用于矩阵转置（<=2 维）。NumPy 的 np.ndarray 具有 np.ndarray.T，用于张量转置，这本质上反转了维度的顺序。这可能对应于转置的典型数学表示法，即 <sup>T</sup>。1D 数组的转置仍然是 1D 数组，因为没有其他维度可以交换。

e) NumPy 的 np.ndarray.flatten 方法始终返回数据的副本。要返回视图（如果可能），请改用 np.ravel。PyTorch 的 torch.flatten 更类似于 np.ravel，如果可能会返回视图。Tensorflow 的 tf.experimental.numpy.flatten 方法也会尽可能返回视图，因为其底层实现使用了 tf.reshape。请注意，在展平数组时，还要注意顺序的概念。

### 图 2.5 重塑中的顺序概念。

![](img/e891acaacd4fb5b80dab2ed824618203_62_0.png)

![](img/e891acaacd4fb5b80dab2ed824618203_62_1.png)

### 图 2.6 标量到向量的广播。

![](img/e891acaacd4fb5b80dab2ed824618203_63_0.png)

### 图 2.7 向量到矩阵的广播。

请注意，标量与数组之间的数学运算在数学上没有意义，

```
1 + [2 4 6]
```

但是，广播后，等效的数学运算变为

```
[1 1 1] \oplus [2 4 6] = [3 5 7]
```

其中 \oplus 表示按元素相加运算。同样，我将使用

- \ominus 表示按元素相减
- \odot 表示按元素相乘
- \oslash 表示按元素相除

同样，向量也可以广播到矩阵（图 2.7）。向量与矩阵之间的运算在数学上也没有意义，

```
[1 3 4 6] + [1 2 3 4 \n 2 3 4 5 \n 3 4 5 6]
```

等效的广播运算变为

```
[1 3 4 6 \n 1 3 4 6 \n 1 3 4 6] \oplus [1 2 3 4 \n 2 3 4 5 \n 3 4 5 6] = [2 5 7 8 \n 3 6 8 11 \n 4 7 9 12]
```

具有单例维度（.shape [axis]=1）的张量可以广播到具有非单例维度的另一个张量，前提是其余维度也可以广播。例如，形状为 (1,N) 的列向量与大小为 (M,N) 的矩阵之间的广播（图 2.8），

```
[1 \n 3 \n 6] + [1 2 3 4 \n 2 3 4 5 \n 3 4 5 6]
```

具有等效的广播运算

```
[1 1 1 1 \n 3 3 3 3 \n 6 6 6 6] \oplus [1 2 3 4 \n 2 3 4 5 \n 3 4 5 6] = [2 3 4 5 \n 5 6 7 8 \n 9 10 11 12]
```

### 图 2.8 具有单例维度的张量与非单例维度张量之间的广播。

![](img/e891acaacd4fb5b80dab2ed824618203_64_0.png)

一般来说，标量（ndim=0）始终可以广播到任何更高维度的张量。较低维度的张量（ndims > 0）可以广播到更高维度的张量，只要较低维度张量的某些或所有后置（右对齐）轴的大小要么是单例（即 .shape[axis]=1），要么与更高维度张量在相应后置轴上的大小匹配。为了更具体地定义这一点，假设较低维度的张量 X 具有形状 (a1, a2, a3, ..., an)，ai != 0，\forall i，而较高维度的张量 Y 具有形状 (b1, b2, ..., bm)，bj != 0，\forall j，其中 n <= m，那么要将 X 广播到 Y，我们必然需要满足

```
{
    a_n \in {b_m, 1},
    a_{n-1} \in {b_{m-1}, 1},
    ...
    a_{n-k} \in {b_{m-k}, 1},
    ...
    a_1 \in {b_{m-n+1}, 1}
}
```

广播运算将产生一个形状为 (c1, c2, ..., cm) 的张量 Z，其取 X 或 Y 中较大的大小，且维度数将为 Y.ndim，大于 X.ndim。即，

```
{
    c_m = max(a_n, b_m)
    c_{m-1} = max(a_{n-1}, b_{m-1})
    ...
    c_{n-k} = max(a_{n-k}, b_{m-k})
    ...
    c_{m-n+1} = max(a_1, b_{m-n+1})
    c_{m-n} = b_{m-n}
    c_{m-n-1} = b_{m-n-1}
    ...
    c_{m-n-p} = b_{m-n-p}
    ...
    c_1 = b_1
}
```

例如，

- 标量，例如 5（没有维度，ndim=0），可以广播到形状为 (3, 6, 5, 7) 的张量，从而产生形状为 (3, 6, 5, 7) 的张量。
- 形状 X 为 (5, 7) 的张量可以广播到另一个形状 Y 为 (3, 6, 5, 7) 的张量，因为 X 和 Y 的最后两个维度匹配。生成的张量 Z 形状为 (3, 6, 5, 7)。
- 形状 X 为 (5, 7) 的张量不能广播到另一个形状 Y 为 (7, 6, 2) 的张量，因为 X 和 Y 的最后两个维度不匹配，且 X 的任何轴都不是单例。
- 形状 X 为 (1, 7) 的张量可以广播到另一个形状 Y 为 (3, 6, 5, 7) 的张量，因为两个张量的最后一个维度匹配，且 X 的倒数第二个维度是单例。生成的张量 Z 形状为 (3, 6, 5, 7)。
- 形状 X 为 (6, 1, 7) 的张量可以广播到另一个形状 Y 为 (3, 1, 5, 7) 的张量，因为两个张量的最后一个维度匹配，X 的倒数第二个维度是单例，且 Y 的倒数第三个维度是单例。生成的张量 Z 将具有 (3, 6, 5, 7) 的形状。
- 形状 X 为 (0, 7) 的张量不能广播到另一个形状 Y 为 (3, 6, 5, 7) 的张量，因为 X 的第一个轴是 0，既不是单例，也与 Y 的最后一个维度（即 5）不匹配。
- 以下是关于 0 大小张量的一个奇怪示例。当尝试将形状为 (0, 7)（即空的、0 大小张量）的张量 X 广播到另一个形状为 (1, 7) 的张量时，该操作不会抛出错误。但是，生成的张量 Z 也将是形状为 (0, 7)，即类似于 X 的空张量。这就是为什么我们需要在广播规则中避免对空或 0 大小张量进行操作的原因。

> 请注意，广播的底层机制实际上并不是通过反复复制相同数据多次来重复要广播的元素，因为这不够内存高效。

## 2.12 案例研究

我们将使用按元素运算、重塑和广播的以下案例研究集来解决几个实际问题，作为本章的总结。

### 2.12.1 图像归一化

标量到张量广播的一个示例应用是图像的最小-最大归一化。给定图像 \( I \),

\(\text{Normalize}(I_i) = \frac{I_i - \min(I)}{\max(I) - \min(I)}, \forall i\) (2.1)

其中 \( i \) 是图像像素的索引。我们可以按如下方式实现上述内容：

```
import numpy as np

def normalize_image(image):
    """Normalize image pixel values to be between 0 and 1"""
    # image shape (height, width, channel)
    min_val = np.min(image) # scalar
    max_val = np.max(image) # scalar
    normalized_img = (image - min_val) / (max_val - min_val + 1e-6)
    return normalized_img
```

- 第 6 行和第 7 行计算全局最小值和最大值，它们是标量。
- 第 8 行实现公式 2.1。分母添加一个小 \(\epsilon = 10^{-6}\) 以防止除以零错误。如果最小值和最大值均为零，则图像中所有像素的值都应为零。在这种情况下，归一化图像也将全为零。

如果我们有一批图像，则使用向量广播，其实现方式如下

```
import numpy as np

def normalize_image_batch(images):
    """Normalize image pixel values to be between 0 and 1"""
    # image shape (batch_size, height, width, channel)
    # min / max (batch_size, 1, 1, 1)
    min_val = np.min(images, axis=(1, 2, 3), keepdims=True)
    max_val = np.max(images, axis=(1, 2, 3), keepdims=True)
    normalized_img = (images - min_val) / (max_val - min_val + 1e-6)
    return normalized_img
```


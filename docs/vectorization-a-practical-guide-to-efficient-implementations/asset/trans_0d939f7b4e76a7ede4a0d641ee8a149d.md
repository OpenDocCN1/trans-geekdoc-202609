

各维度上的真实条件。有关上述示例的说明，请参见图 3.4。

NumPy、TensorFlow（通过 `tf.experimental.numpy`）和 PyTorch 还实现了一个特殊的 where 操作，`nonzero` 及其扁平版本 `flatnonzero`（仅在 NumPy 中）。顾名思义，`nonzero` 返回张量沿各维度上非零元素的索引（以元组形式，等效于 `np.where(X != 0)`）；`flatnonzero` 返回非零索引，仿佛张量已被展平（等效于 `np.where(X.flatten() != 0)`）。由于零通常用于填充缺失数据（例如填充，我们将在第 5 章中看到），这些方便的操作有时可以帮助确定张量中存储的有效数据范围。

## 3.2 切片

在 3.1 节中，我们介绍了使用不同索引系统检索单个元素的方法。但是，有时，我们也希望从数组中选择一个片段或一段区间的值。这称为 **切片**。在 Python 中，我们可以通过选择列表 `l` 之间起始索引和结束索引的元素来“切片”数组，使用语法 `l[start:stop]`。例如，设 `l = [1, 3, 5, 7, 9]`，我们希望从索引 1 选择到索引 4（不包含）的所有元素，使用 `l[1:4]`，它将返回 `[3, 5, 7]`。与 **切片** 类似的概念是 **步进**：不是选择两个索引之间的所有连续元素，而是 **步进** 在两个索引之间持续跳过一定数量的元素来选择元素，语法为 `l[start:stop:step]`。例如，假设我们希望在索引 1 和索引 4（不包含）之间每隔一个元素选择一个元素（即在索引之间选择时跳过 1 个元素，或每隔两个元素选择一个元素。我们可以使用 `l[1:4:2]`，它将返回 `[3, 7]`。Python 中其他常用的切片和步进语法列于表 3.1 中。

在 NumPy、TensorFlow 和 PyTorch 中，切片和步进操作不仅可以应用于 1D 向量，还可以推广到多维张量的每个轴。图 3.5 和 3.6 分别说明了 2D 矩阵和 3D 张量中切片和步进操作的几个示例。

### 表 3.1 1D 数组中切片和步进操作及示例用法列表

| Operations | Syntax | Example |
|---|---|---|
| 两个索引之间的切片 | start:stop | l[1:4] -> [3, 5, 7] |
| 使用负索引的切片（转换为 start+n 和 stop+n） | start:stop | l[-4:-1] -> [3, 5, 7] |
| 从起始索引切片到最后一个元素 | start: | l[2:] -> [5, 7, 9] |
| 从第一个元素切片到停止索引 | :stop | l[:3] -> [1, 3, 5] |
| 步进 | start:stop:step | l[1:4:2] -> [3, 7] |
| 选择所有元素 | : | l[:] -> [1, 3, 5, 7, 9] |
| 选择除最后一个元素外的所有元素 | :-1 | l[:-1] -> [1, 3, 5, 7] |
| 选择除最后 N 个元素外的所有元素 | :-N | l[:-2] -> [1, 3, 5] |
| 反转数组 | ::-1 | l[::-1] -> [9, 7, 5, 3, 1] |
| 从第一个元素步进到停止索引 | :stop:step | l[:4:2] -> [1, 5] |
| 从起始索引步进到最后一个元素 | start::step | l[1::2] -> [3, 7] |
| 从第一个元素步进到最后一个元素 | ::step | l[::2] -> [1, 5, 9] |
| 从最后一个元素步进到第一个元素 | ::-step | l[::-2] -> [9, 5, 1] |

![](img/e891acaacd4fb5b80dab2ed824618203_92_0.png)

![](img/e891acaacd4fb5b80dab2ed824618203_92_1.png)

![](img/e891acaacd4fb5b80dab2ed824618203_92_2.png)

图 3.5 NumPy、TensorFlow 或 PyTorch 张量中 2D 矩阵切片和步进操作示例。(a) 切取行的子集但保持列上所有元素：X[1:4, :]；(b) 切取由行和列子集组成的矩阵块：X[1:4, 2:]；(c) 切取行的子集，并跨矩阵每两列步进：X[1:4, ::2]。

### (a) X[1:3, 1:4, :2]

![](img/e891acaacd4fb5b80dab2ed824618203_93_0.png)

### (b) X[1:3, 1:4, ::2]

![](img/e891acaacd4fb5b80dab2ed824618203_93_1.png)

图 3.6 NumPy、TensorFlow 或 PyTorch 张量中 3D 张量切片操作示例。(a) 沿行、列和深度维度切取张量元素的子集：X[1:3, 1:4, :2]；(b) 沿深度维度切取张量的第一层和第三层，并对每一层（2D 矩阵）选择元素的子集：X[1:3, 1:4, ::2]。

除了表 3.1 中列出的语法之外，还有两个额外的方便切片运算符，None（在 NumPy 中等效于 np.newaxis，在 TensorFlow 中等效于 tf.newaxis）和 ...（或等效于 Ellipsis，Python 的内置常量），它们仅可用于 NumPy、TensorFlow 和 PyTorch 张量切片，而不能用于 Python 列表。使用 None 或 np.newaxis 切片维度会在切片轴上添加一个额外的单例维度。

该操作分别等效于 NumPy 中的 np.expand_dims、TensorFlow 中的 tf.expand_dims 或 PyTorch 中的 torch.unsqueeze。例如，

```
import numpy as np
X = np.random.rand(4, 5) # shape (4, 5)
# Add an extra 3rd dimension
# shape (4, 5, 1)
assert np.allclose(
    X[:, :, None].shape,
    np.expand_dims(X, axis=2).shape
)
# Insert an extra dimension in the first dimension
# shape (1, 4, 5)
assert np.allclose(
    X[None, :, :].shape,
    np.expand_dims(X, axis=0).shape
)
# Insert an extra dimension between the original
# 1st and 2nd dimensions: shape (4, 1, 5)
assert np.allclose(
    X[:, np.newaxis, :].shape,
    np.expand_dims(X, axis=1).shape
)
```

...（省略号）运算符，另一方面，允许我们在切片跨多个连续维度的所有元素时简化表达式。例如，设 X 为形状为 [5, 2, 3, 8, 7] 的张量，我们希望沿维度 2–5 选择所有元素，但沿第一个维度选择子集。我们可以使用 X[2:4, :, :, :, :] 或等效地使用 X[2:4, ...]。

```
import numpy as np
X = np.random.rand(5, 2, 3, 8, 7)
# Selecting subset of a batch
assert np.allclose(
    X[2:4, :, :, :, :].shape,
    X[2:4, ...].shape
)
# Selecting the first slice of the last dimension
assert np.allclose(
    X[:, :, :, :, 0].shape,
    X[..., 0].shape
)
# Selecting a subset of the first dimension and
# the last slice from the last dimensions
assert np.allclose(
    X[1:3, :, :, :, -1].shape,
    X[1:3, ..., -1].shape
)
```

使用省略号 (...) 进行切片在实现接受变维张量的函数时很方便。例如，假设我们想要实现一个函数，它始终以以下形式之一提取序列中的项：(batch_size, seq_length)、(batch_size, seq_length, feature_size) 或 (batch_size, seq_length, feature_size, num_instances)。请注意，序列维度始终位于 axis=1，批次维度始终位于 axis=0，那么我们可以执行

```
import numpy as np

def extract_last_event(X):
    return X[:, -1, ...]

# (batch_size, seq_length)
X1 = np.random.rand(16, 50)
assert np.allclose(
    extract_last_event(X1).shape,
    (16, )
)

# (batch_size, seq_length, feature_size)
X2 = np.random.rand(16, 50, 32)
assert np.allclose(
    extract_last_event(X2).shape,
    (16, 32)
)
# (batch_size, seq_length, feature_size, num_instances)
X3 = np.random.rand(16, 50, 32, 8)
assert np.allclose(
    extract_last_event(X3).shape,
    (16, 32, 8)
)
```

使用省略号 ...，该函数可以处理所有三种序列输入变体。请注意，当输入形式为 (batch_size, seq_length) 时，只有两个维度，而在我们的实现中，看起来像是从至少三个维度中提取。事实证明，省略号运算符 ... 将忽略第三个维度的切片，因为该维度不存在。

最后，在指定切片时，只能有一个省略号 ... 运算符。指定多个省略号会抛出错误，例如：

```
X = np.arange(30).reshape(3, 2, 5)
X[..., 0, ...]
```

在 NumPy 中抛出错误：

```
IndexError: an index can only have a single ellipsis ('...')
```

这是因为两个省略号表示的切片维度是不明确的。X[..., 0, ...] 可能表示以下任何一种：

- X[0, :, :]
- X[:, 0, :]
- X[:, :, 0]

程序无法确定哪个是预期的切片操作。

在本书中，我有时会在描述函数用法时将省略号运算符 ... 重载为参数的未指定值，或用于省略列表中值的枚举。但是，这些用法绝不能出现在代码块中（因为所有代码块都应该按原样可运行）。当表示法变得令人困惑时，我会指明省略号的含义。

### 3.2.1 重用切片配置

有时我们可能希望将相同的切片逻辑应用于多于 1 个张量，或者也许我们希望将切片配置作为变量传递给函数。在这些场景中，我们需要构造切片对象。Python 提供了一个内置方法来构建切片，slice，其用法如下

- slice(stop)，等效于 l[:stop] 的切片；
- slice(start, stop)，等效于 l[start:stop] 的切片；
- slice(start, stop, step)，等效于 l[start:stop:step] 的切片。

同样，NumPy 实现了 np.s_，它以相同的方式使用，但使用比 slice 更常用的冒号 : 语法。表 3.2 再次列出了以前在表 3.1 中列出的切片操作示例，但使用 slice 和 np.s_ 来构建切片配置。


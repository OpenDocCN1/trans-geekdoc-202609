

![](img/e891acaacd4fb5b80dab2ed824618203_109_0.png)

图 3.10 对 2D 矩阵进行 torch.gather 操作的图示示例。(a) 沿行收集 (torch.gather(X, dim=0, index=index))。索引和输入都是二维矩阵。两个矩阵在左上角对齐（即 index (0, 0)）。索引矩阵的列对应于输入的列，而索引矩阵内的值对应于行索引。索引矩阵的列数可以小于（即实体区域）或等于（即实体区域与浅色区域合并）输入的列数。最终输出的形状与索引矩阵相同；(b) 沿列收集 (torch.gather(X, dim=1, index=index))。索引和输入都是二维矩阵，并在左上角对齐。索引矩阵的行对应于输入的行，而索引矩阵内的值对应于列索引。索引矩阵的行数同样可以小于或等于输入的行数。最终输出的形状与索引矩阵相同。

使其维度相同。图 3.10 提供了若干 torch.gather 工作原理的图示示例。我们将在后文更详细地讨论每种操作的使用模式，并附有更多示例。

对于 1D 张量，tf.gather(X, index) 和 torch.gather(X, dim=0, index=index) 等价于 np.take(X, index)。在这种情况下，设置 axis=None 或 axis=0 具有相同的效果。对于 TensorFlow，axis=None 与 batch_dims=0 配对（两者均为默认值）将导致 axis=0，此时元素沿 1D 向量的第一个（也是唯一的）维度取值。PyTorch 要求用户明确设置 dim=0（设置 dim=None 会抛出错误）。对于 NumPy，设置 axis=None 会指示函数将 1D 向量展平，结果即其自身。然后，沿同一向量取值。

```python
import numpy as np
import tensorflow as tf
import torch
X = np.arange(10)
index = [3, 5]
y_np = np.take(X, index)
y_tf = tf.gather(X, index)
y_torch = torch.gather(
    torch.tensor(X), 0, torch.tensor(index)
)
# all returns [3, 5]
```

对于多维张量，tf.gather(X, index) 等价于 np.take(X, index, axis=0)。同样，当 batch_dims=0 为默认值时，axis 被设置为 0（axis=0），因此 tf.gather(X, index) 等价于 tf.gather(X, index, axis=0)。对于 PyTorch 的 torch.gather，若要返回整个切片，必须在批次维度上重复索引（因此在这种情况下，建议直接使用切片）：

```python
import numpy as np
import tensorflow as tf
import torch
X = np.arange(20).reshape(4, 5)
index = np.array([[1, 3]])
y_np = np.take(X, index, axis=1)
y_tf = tf.gather(X, index, axis=1)
y_torch = torch.gather(
    torch.tensor(X),
    0,
    torch.tensor(np.repeat([index], X.shape[1], axis=0).T)
)
# all returns:
# [[ 5, 6, 7, 8, 9],
# [15, 16, 17, 18, 19]]
# In contrast, if we do not repeat the index
y_torch_index = torch.gather(
    torch.tensor(X), 0, torch.tensor(index[:, None]))
# tensor([[ 5],
#   [15]])
```

当向 `axis` 参数指定整数值时，`tf.gather(X, index, axis=...)` 等价于 `np.take(X, index, axis=...)`。`index` 也可以是多维的，并将以与 `np.take` 相同的方式处理：

```python
import numpy as np
import tensorflow as tf
X = np.arange(30).reshape(3, 5, 2)
slice_index = [[0, 3], [1, 1]]
block_np = np.take(X, slice_index, axis=1)
block_tf = tf.gather(X, slice_index, axis=1)
assert np.allclose(
    block_np, block_tf
)
```

`tf.gather` 还可以像 `np.take_along_axis`（以及 `torch.take_along_dims`）一样，通过将 `batch_dims` 指定为大于 0 的值，来对批次中的元素收集进行向量化。区别在于，`tf.gather` 仅允许在初始维度上进行批处理，而 `np.take_along_axis` 允许在任意维度上设置批次维度。例如，

```python
import numpy as np
import tensorflow as tf
import torch
X = np.random.randint(0, 10, size=(4, 3, 5))
reorder_index = np.random.randint(0, 5, size=(4, 3, 5))
y_np = np.take_along_axis(X, reorder_index, axis=2)
y_torch = torch.take_along_dim(
    torch.tensor(X), torch.tensor(reorder_index), axis=2
)
y_tf = tf.gather(X, reorder_index, axis=2, batch_dims=2)
```

关于广播，`tf.gather` 会广播除前导 `batch_dims` 批次维度和 `axis` 维度之外的任何维度（因此，将其余维度视为切片而非单个元素），而 `np.take_along_axis` 则要求我们添加额外的单例维度来指示广播，即：

```python
import numpy as np
import tensorflow as tf
import torch
X = np.random.randint(0, 10, size=(4, 3, 5, 6))
# 3rd dimension as the broadcasting dimension
reorder_index = np.random.randint(0, 5, size=(4, 3, 1, 7))
# Returns a tensor of shape (4, 3, 5, 7)
y_np = np.take_along_axis(
    X, reorder_index, axis=3
)
y_torch = torch.take_along_dim(
    torch.tensor(X),
    torch.tensor(reorder_index),
    axis=3
)
y_tf = tf.gather(
    # taking out the singleton dimension
    X, reorder_index[..., 0, :], axis=3, batch_dims=2
)
```

因此可以基于 [Abadi et al., 2023a] 推导 `tf.gather` 预期输出形状的启发式规则，并实现为

```python
np.concatenate([
    inputs.shape[:axis],
    index.shape[batch_dims:],
    inputs.shape[axis+1:]
]).astype(int)
```

## 3.4.4 N 维收集

NumPy 和 PyTorch 都使用多索引数组来选择多个元素/切片。TensorFlow 实现了一个特殊操作 `tf.gather_nd` 以实现相同目的。`tf.gather_nd` 操作使用多索引从多个索引维度收集元素，而非像 `tf.gather` 操作那样使用扁平索引从单个维度收集。举个简单的例子，

```python
import numpy as np
import tensorflow as tf
import torch
X = np.array([
    [1, 3, 2, 4],
    [6, 8, 7, 9],
])
# 2D indices
index = np.array([
    [0, 1],
    [0, 3],
    [1, 0],
    [1, 2],
])
# gather_nd
y_tf = tf.gather_nd(X, index)
# For numpy and torch, use indexing
y_np = X[index.T[0], index.T[1]]
y_torch = torch.tensor(X)[index.T[0], index.T[1]]
# array([3, 4, 6, 7])
```

请参见图 3.11 了解示意图。`tf.gather_nd` 操作是 TensorFlow 独有的，因为 TensorFlow 仅允许标量和切片用于索引，并且直接使用多索引数组来选择多个元素会抛出错误：

```python
import tensorflow as tf
X = tf.constant([
    [1, 3, 2, 4],
    [6, 8, 7, 9],
])
# 2D indices
index = tf.constant([
    [0, 1],
    [0, 3],
    [1, 0],
    [1, 2],
])
# This throws an error
X[index[:, 0], index[:, 1]]
```

将得到以下错误：

```
TypeError: Only integers, slices (`:`), ellipsis (`...`),
`tf.newaxis` (`None`) and scalar `tf.int32`/`tf.int64` tensors
are valid indices, got `<tf.Tensor: shape=(4,),
dtype=int32, numpy=array([0, 0, 1, 1], dtype=int32)>`
```

### 图 3.11 使用 N 维收集进行多元素多索引的图示

![](img/e891acaacd4fb5b80dab2ed824618203_113_0.png)

`tf.gather_nd` 支持使用多索引进行切片收集。例如，

```python
import tensorflow as tf
X = tf.random.uniform((4, 5, 6))
# Multi-indexing the first 2 dimensions,
# using last dimension as the slice/block dimension
index = tf.constant([
    [0, 3],
    [1, 2],
    [3, 0],
    [2, 2],
]) # (4, 2)

# Gather 4 slices from the 3D tensor
y = tf.gather_nd(X, index) # (4, 6)
```

使用多索引提取 X 中的 index.shape[1] 个前导维度，其余滞后维度保留为切片维度。如果 index.shape[1] == X.ndim，则通过从输入 X 中提取单个元素来创建 1D 向量。否则，将创建一个 (X.ndim - index.shape[1] + 1) 维张量。

`tf.gather_nd` 还可用于收集排列在多维批次中的切片。

```python
import tensorflow as tf
X = tf.random.uniform((2, 3, 5, 4))
index = tf.experimental.numpy.random.randint(
    0, 4, (2, 3, 4, 2)
)

batch_dims = 2
y = tf.gather_nd(X, index, batch_dims=batch_dims)
```

在此示例中，我们将 index 和 X 的前两个维度视为批次维度。然后，在批次中的每个位置，我们从每个 5 x 4 矩阵中取出 4 个 2D 点。请参见图 3.12 了解示意图。

TensorFlow 关于 tf.gather_nd 的文档 [Abadi et al., 2023b] 提供了更多示例。鼓励读者仔细研究这些示例，以进一步理解该操作。

`tf.gather_nd`（以及 NumPy 和 PyTorch 中类似的操作）在批次中按索引而非整个切片收集元素，对于从高维数据中提取异质感兴趣区域（ROI）非常有用，例如医学影像（如 fMRI 大脑结构）或视频数据（如移动物体），其中 2D 或 3D 图像序列随时间组织。


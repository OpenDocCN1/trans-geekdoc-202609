

- 计算唯一集合中各项出现次数的数量。在 NumPy 和 PyTorch 中，这需要设置 `return_counts=True`。在 TensorFlow 中，这需要调用 `tf.unique_with_counts` 并使用第三个返回输出。在我们实现一个函数来对矩阵行进行排序的案例研究中，我们将使用 `np.unique` 按字典顺序对行进行排序。

- d) 这些操作获取数组中的最大值或最小值（或其索引）。它们分别对应数学符号 max、min、argmax 和 argmin。

- e) top-k 操作返回数组中的前 k 个值及其索引。尽管 NumPy 没有现成的函数来提取前 k 个值，但如我们将在第 10.2 节的一个研究中看到，我们可以使用 `np.argpartition` 来实现 top-k 操作。

- f) `np.partition` 是 NumPy 独有的操作。它基于最终排序数组中的第 k 个值，将数组划分为两部分（但并未实际对整个数组进行排序）。左分区中的值均小于该值，而右分区中的值均大于该值。有关说明，请参见后续案例研究部分中的图 10.1。`np.argpartition` 用于获取划分和重新排序数组所需的索引。

- g) 给定一个已排序的数组，`searchsorted` 操作查找可以插入新值的索引，同时仍保持新数组的排序顺序（即仍然从小到大）。如果该值等于数组中已存在的某个值，则它将根据 `side="left"` 或 `side="right"` 的设置，分别插入到原数字的左侧或右侧。NumPy、Tensorflow 和 PyTorch 中 `searchsorted` 方法的实现可以同时对多个插入值进行向量化搜索。为了说明，

```
import numpy as np

X = np.array([1, 3, 6, 8, 10])
insertion_values = np.array([2, 5, 9, 10, 11])
insertion_indices = np.searchsorted(X, insertion_values)
# array([1, 2, 4, 4, 5])
# Insert the values based on the search sorted indices
y = np.insert(X, insertion_indices, insertion_values)
# array([ 1, 2, 3, 5, 6, 8, 9, 10, 10, 11])
```

## 10.2 案例研究：使用 argsort 和 argpartition 实现 top-k

Tensorflow（tf.math.top_k）和 PyTorch（torch.topk）都实现了一种方法，该方法返回数组中的前 k 个最大元素及其索引。对于 Tensorflow，

```
import tensorflow as tf
X = tf.constant([1, 3, 2, 5, 9, 8, 4])
top_values, top_indices = tf.math.top_k(X, k=3)
# top_values: <tf.Tensor: shape=(3,), dtype=int64, numpy=array([9, 8, 5])>
# top_indices: <tf.Tensor: shape=(3,), dtype=int32, numpy=array([4, 5, 3], dtype=int32)>
```

而对于 PyTorch

```
import torch
X = torch.tensor([1, 3, 2, 5, 9, 8, 4])
top_values, top_indices = torch.topk(X, k=3)
# top_values: tensor([9, 8, 5])
# top_indices: tensor([4, 5, 3])
```

撰写本章时，NumPy 没有现成的函数来检索前 k 个值及其索引。但是，可以通过排序来实现相同的目标。一种朴素的方法是使用 np.argsort 确定前几个值的索引，然后使用 np.take 检索前几个值。

```
import numpy as np
def top_k_argsort(X, k=3):
    """Get top-k values and indices along the last dimension."""
    top_indices = np.argsort(X)[..., -k:][..., ::-1]
    top_values = np.take_along_axis(X, top_indices, axis=-1)
    return top_values, top_indices
X = np.array([1, 3, 2, 5, 9, 8, 4])
top_values, top_indices = top_k_argsort(X)
# top_values: array([9, 8, 5])
# top_indices: array([4, 5, 3])
```

- 第 5 行：np.argsort 首先获取用于排序每个数组的索引。由于它按升序（从小到大）对值进行排序，我们然后使用 [..., -k] 沿输入的最后一个维度切片出前 k 个值的最后 k 个索引。然后，[..., ::-1] 反转前 k 个索引，使其现在从大到小排列。

- 第 6 行：np.take_along_axis 沿最后一个维度将从 top_indices 获得的排序顺序应用于输入。

但是，这将涉及对整个序列进行排序。此方法的时间复杂度为 O(n log n)，其中 n 是序列的大小。相比之下，另一种检索前 k 个值的策略是首先使用 np.argpartition 返回无序的前 k 个值，然后使用 np.argsort 对前 k 个值和索引进行排序。由于 np.argpartition 的运行时间复杂度为 O(n) [Harris et al., 2023]，因此总体时间复杂度为 O(n + k log k)，其中 k << n。

```
import numpy as np

def top_k_argpartition(X, k=3):
    """Get top-k values and indices along the last dimension."""
    # Unsorted top k values and indices
    top_indices = np.argpartition(X, -k, axis=-1)[..., -k:]
    top_values = np.take_along_axis(X, top_indices, axis=-1)

    # Sort based on top_values
    indices = np.argsort(top_values, axis=-1)[..., ::-1]
    top_indices = np.take_along_axis(top_indices, indices, axis=-1)
    top_values = np.take_along_axis(top_values, indices, axis=-1)

    return top_values, top_indices

X = np.array([1, 3, 2, 5, 9, 8, 4])
top_values, top_indices = top_k_argpartition(X)
# top_values: array([9, 8, 5])
# top_indices: array([4, 5, 3])
```

- 第 6 行按第 k 大的值对数组进行分区。np.argpartition 将获取分区后数组的索引。这里，我们使用 -k 来指定第 k 大的值，而不是第 k 小的值。有关 np.partition 工作原理的说明，请参见图 10.1（np.argpartition 获取用于分区的索引，而不是分区结果，类似于 np.argsort 获取排序索引而不是排序结果）。然后，我们只切片出前 k 个最大值的索引，[..., -k:]。

![](img/e891acaacd4fb5b80dab2ed824618203_368_0.png)

图 10.1. 数组分区效果的示意图。该算法首先确定指定的第 k 大值，我们将其表示为“主元”（类似于快速排序）。然后，它将任何小于主元的值移到主元左侧，将任何大于主元的值移到主元右侧。结果，主元左侧的所有值都小于主元，而主元右侧的所有值都大于主元。然而，在两个分区内部，这些值并不是有序的。

- 第 7 行从原始输入中获取前 k 个值。此时，top_indices 和 top_values 均未排序。

- 第 10-12 行对 top_values 进行排序，并将排序顺序应用于 top_indices。

我们可以模拟一些数据，比较两个函数 top_k_argsort 与 top_k_argpartition 的性能，以及来自 Tensorflow tf.math.top_k 和 PyTorch torch.topk 的实现。结果在图 10.2 中绘制。

![](img/e891acaacd4fb5b80dab2ed824618203_369_0.png)

图 10.2 在 2021 款 M1 MacBook Pro 上测得的 NumPy、Tensorflow 和 PyTorch 中两个 top-k 函数实现的性能。

```
import numpy as np
import time
import matplotlib.pyplot as plt

batch_size = 32
max_array_length = int(1E6)
lengths = np.concatenate([
    np.geomspace(10, max_array_length, num=100).astype(int)
])

time_taken = {
    "top_k_argsort": [],
    "top_k_argpartition": [],
    "torch_top_k": [],
    "tf_top_k": []
}
for ii, l in enumerate(lengths):
    X = np.random.randint(0, max_array_length+1, size=(batch_size, l))
    # measure top_k_argsort
    tnow = time.time()
    _ = top_k_argsort(X, k=5)
    time_taken["top_k_argsort"].append(time.time() - tnow)
    # measure top_k_argpartition
    tnow = time.time()
    _ = top_k_argpartition(X, k=5)
    time_taken["top_k_argpartition"].append(time.time() - tnow)
    # measure torch
    X_torch = torch.tensor(X)
    tnow = time.time()
    _ = torch.topk(X_torch, k=5)
    time_taken["torch_top_k"].append(time.time() - tnow)
    # measure tf
    tnow = time.time()
    _ = tf.math.top_k(X, k=5)
    time_taken["tf_top_k"].append(time.time() - tnow)

# Plot the results
fig, ax = plt.subplots(1, 1, figsize=(7, 4))
ax.plot(lengths, time_taken["top_k_argsort"], label="np.argsort")
ax.plot(lengths, time_taken["top_k_argpartition"], label="np.argpartition")
ax.plot(lengths, time_taken["torch_top_k"], label="torch.topk")
ax.plot(lengths, time_taken["tf_top_k"], label="tf.math.top_k")
ax.legend()
ax.set_xlabel("Array lengths")
ax.set_ylabel("Time Taken (sec)")
```

## 10.3 案例研究：对矩阵行进行排序

假设我们有一个整数的二维矩阵，我们希望对整数的行进行排序，先按第 1 列排序，然后按第 2 列，然后按第 3 列，以此类推。例如，

```
[
    [3, 2, 1],
    [3, 1, 2],
    [1, 3, 2],
]
```




```python
import torch
data = torch.tensor([1, 2, 3, 2, 5, 4, 7, 2, 8, 3], dtype=float)
offsets = torch.tensor([0, 3, 6, 6, 10])
rea_torch = torch.segment_reduce(data, "sum", offsets=offsets)
# tensor([ 6., 11., 0., 20.], dtype=torch.float64)
```

- length：与其指定起始和结束索引，不如指定序列中每个分段的长度。分段的长度需要是非负的。因此，可以创建长度为零的分段，例如。

```python
import torch
data = torch.tensor([1, 2, 3, 2, 5, 4, 7, 2, 8, 3], dtype=float)
lengths = torch.tensor([3, 3, 0, 4])
rea_torch = torch.segment_reduce(data, "sum", lengths=lengths)
# tensor([ 6., 11., 0., 20.], dtype=torch.float64)
```

编写时，PyTorch 的 torch.segment_reduce 操作仅针对 float dtype 数组实现了。

- 分段 ID：Tensorflow 的分段操作以及 PyTorch 的散射操作均采用此策略。与其根据起始和结束索引之间的间隔显式推断分段，不如分段 ID 明确标记分段所属的组。在这里，segment_id 输入被视为组键。这可能有利之处在于，我们可以在聚合前使用不一定将同一组的所有元素排列在一起的操作。Tensorflow 实现了三种分段聚合操作的变体，它们假设第一个轴(axis=0)是要聚合的分段维度。
  - tf.math.segment_sum：此操作仍然假设相同分段的值彼此相邻。它要求分段 ID 已排序。可以跳过整数值以在分段之间创建长度为零的条目，就像最后的分段可以被跳过以在长度大于 0 的分段之间创建 0 个条目；也可以通过指定 num_segments 参数在最后的分段中创建长度为零的条目。负分段 ID 将被忽略。PyTorch 的 scatter_reduce 操作可以被视为与
  - tf.math.unsorted_segment_sum：此操作不假设相同分段的值彼此相邻。也就是说，每个分段的元素可以分布在各处。可以跳过整数值以在长度大于 0 的分段之间创建 0 个条目；也可以通过指定 num_segments 参数在最后的分段中创建长度为零的条目。负分段 ID 将被忽略。PyTorch 的 scatter_reduce 操作可以被视为与
  - tf.sparse.segment_sum：前两个操作要求分段 ID 的数量等于数据输入第一个维度的元素数量。此操作接受一个额外的参数 indices，该参数与 segment_ids 配对，按组从数据输入中提取元素。假设我们有 data = [1, 2, 3, 4, 5] 和分组 ID [0, 0, 1, 1, 1]。如果我们指定 indices = [0, 1, 2, 3, 4]，则这相当于使用 tf.math.segment_sum 或 tf.math.unsorted_segment_sum，得到 [3, 12]，它来自 [data[0]+data[1], data[2]+data[3]+data[4]]，即 [1+2, 3+4+5]。但是，如果我们指定 indices = [0, 1, 2, 3, 0]，则我们将得到 [3, 8]，它来自 [data[0]+data[1], data[2]+data[3]+data[0]]，即 [1+2, 3+4+1]。与 tf.math.segment_sum 类似，负分段 ID 会引发错误。

## 表 9.2（续）

| 操作 | NumPy | Tensorflow | PyTorch |
| :--- | :--- | :--- | :--- |
| 分组均值<sup>b)</sup> | N/A | tf.math.segment_mean, tf.math.unsorted_segment_mean, tf.sparse.segment_mean | torch.scatter_reduce(..., reduce="mean"), torch.segment_reduce(arr, "mean", offsets) |
| 分组乘积<sup>c)</sup> | np.multiply.reduceat | tf.math.segment_prod, tf.math.unsorted_segment_prod | torch.scatter_reduce(..., reduce="prod"), torch.segment_reduce(arr, "prod", offsets) |

b) NumPy 未实现分组均值函数。这很可能是因为均值操作在技术上不是元素归约操作，因为它不仅需要跟踪总和，还需要跟踪每个组内的元素总数。然而，一个简单的变通方法是利用 `np.add.reduceat` 来实现等效函数，即先计算分组总和，然后通过对全 1 指示数组求和来计算组内的元素数量。实现如下：

```python
import numpy as np
def np_mean_reduceat(arr, indices, **kwargs):
    # Compute groupwise sum
    gsum = np.add.reduceat(arr, indices, **kwargs)
    # Compute groupwise count
    indicator = np.ones_like(arr)
    gcount = np.add.reduceat(indicator, indices, **kwargs)
    # Compute mean
    return gsum / gcount
```

c) Tensorflow 未实现分段乘法操作的 tf.sparse 版本。但可以通过对对数值执行分段求和，然后再提升回指数（会牺牲一些数值精度）来绕过此问题，即：

```python
import tensorflow as tf

def tf_sparse_segment_prod(data, indices, segment_id, num_segments=None) :
    # take log values
    data_out = tf.math.log(tf.cast(data, tf.float32))
    # Segment sum of log
    data_out = tf.sparse.segment_sum(
        data_out, indices, segment_id, num_segments
    )
    # Raise back to exponents
    data_out = tf.exp(data_out)
    if data.dtype in (tf.int32, tf.int64):
        data_out = tf.round(data_out)
    data_out = tf.cast(data_out, data.dtype)
    return data_out

data = tf.constant([1, 2, 3, 2, 3, 6, 3, 4])
indices = tf.constant([0, 1, 2, 3, 4, 5, 6, 7])
segment_id = tf.constant([0, 0, 0, 1, 1, 1, 2, 2])
data_out = tf_sparse_segment_prod(data, indices, segment_id)
# <tf.Tensor: shape=(3,), dtype=int32, numpy=array([ 6, 36, 12], dtype=int32)>
```

## 表 9.2（续）

| 操作 | NumPy | Tensorflow | PyTorch |
|---|---|---|---|
| 除以 sqrt(d) 的分组总和 | N/A | tf.math.unsorted_segment_sqrt_n, tf.sparse.segment_sqrt_n | N/A |
| 分组最大值 | np.maximum.reduceat | tf.math.segment_max, tf.math.unsorted_segment_max | torch.scatter_reduce(..., reduce="amax"), torch.segment_reduce(arr, "max*", offsets) |
| 分组最小值 | np.minimum.reduceat | tf.math.segment_min, tf.math.unsorted_segment_min | torch.scatter_reduce(..., reduce="amin"), torch.segment_reduce(arr, "min*", offsets) |

d) segment_sqrt_n 是一种特殊函数，其灵感来自之前的自然语言建模研究，这些研究试图总结句子中词元的嵌入，即将句子表示为词袋（例如预训练前馈神经网络语言模型，或 NNLM [Bengio et al., 2003]，来自 TFHub [Google, 2023]）。这些研究发现，对嵌入的总和取平方根在表示句子方面比平均词元嵌入更有效。与分组均值归约解决方案类似，这也可以使用 NumPy 中的 np.divide.reduceat 或 PyTorch 中的 torch.scatter_add 来实现。我们在下面的代码块中说明了使用 PyTorch 的实现：

```python
import torch

def torch.scatter_reduce_sqrt_n(arr, segment_ids, **kwargs) :
  # Initialize accumulators
  numerator = torch.zeros(segment_ids.max() + 1)
  denom = torch.zeros_like(numerator)
  # Compute groupswise sum
  gsum = numerator.scatter_add_(0, segment_ids, arr)
  # Compute groupwise count
  indicator = torch.ones_like(arr)
  gcount = denom.scatter_add_(0, segment_ids, indicator)
  # Compute the sum / sqrt_n
  return gsum / torch.sqrt(gcount)
```

e) 这些操作计算分段级最小值和最大值。使用未排序分段 ID 的 Tensorflow 操作（即 tf.math.unsorted_segment_max 和 tf.math.unsorted_segment_min）有一个需要注意的地方：如果我们跳过某些整数 ID 的目的是创建零条目，我们会发现这些跳过的条目将分别填充 -∞（例如 3.4028235e+38）或 +∞（例如 +3.4028235e+38），而不是零。因此，使用这些操作时需要小心。


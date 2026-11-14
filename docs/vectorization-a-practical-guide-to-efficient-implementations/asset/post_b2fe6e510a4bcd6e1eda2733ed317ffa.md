
To illustrate,

```python
import numpy as np
import torch
x = np.arange(10)
buckets = [0, 3, 6, 9]

# Left-inclusive [1, 1, 1, 2, 2, 2, 3, 3, 3, 4]
indices_np_false = np.digitize(x, buckets, right=False)
indices_torch_true = torch.bucketize(
    torch.tensor(x), torch.tensor(buckets), right=True
)
assert np.allclose(indices_np_false, indices_torch_true)

# Left-exclusive [0, 1, 1, 1, 2, 2, 2, 3, 3, 3]
indices_np_true = np.digitize(x, buckets, right=True)
indices_torch_false = torch.bucketize(
    torch.tensor(x), torch.tensor(buckets), right=False
)
assert np.allclose(indices_np_true, indices_torch_false)
```

An alternative operation is `searchsorted` implemented by all three libraries. The following illustrates that these operations are equivalent:

```python
import numpy as np
import tensorflow as tf
import torch

x = np.arange(10)
buckets = np.array([0, 3, 6, 9])
x_t = torch.tensor(x)
buckets_t = torch.tensor(buckets)

# Left inclusive [1, 1, 1, 2, 2, 2, 3, 3, 3, 4]
res = [
    # using digitize/bucketize
    np.digitize(x, buckets, right=False),
    torch.bucketize(x_t, buckets_t, right=True),
    # using searchsorted
    np.searchsorted(buckets, x, side="right"),
    torch.searchsorted(buckets_t, x_t, side="right"),
    tf.searchsorted(buckets, x, side="right")
]

# Pair-wise comparison
assert all(np.allclose(res[ii], res[ii+1]) for ii in range(len(res)-1))

# Left exclusive [0, 1, 1, 1, 2, 2, 2, 3, 3, 3]
res = [
    # using digitize/bucketize
    np.digitize(x, buckets, right=True),
    torch.bucketize(x_t, buckets_t, right=False),
    # using searchsorted
    np.searchsorted(buckets, x, side="left"),
    torch.searchsorted(buckets_t, x_t, side="left"),
    tf.searchsorted(buckets, x, side="left")
]
# Pair-wise comparison
assert all(np.allclose(res[ii], res[ii+1]) for ii in range(len(res)-1))
```

We can also implement bucketization from scratch using masking, though it may not be as efficient as using either `digitize` or `searchsorted`. See Figure 9.11 for an illustration of the masking process.

```python
import numpy as np

def bucketize_via_masking(x, buckets, side="left"):
    """Bucketize values based via broadcasting and
    masking."""
    # keep original shape in case we need to deal
    # with multi-dimensional arrays
    shape = x.shape
    x = x.flatten() # flatten
    # convert to a column vector for subsequent broadcasting
    buckets = buckets[:, None]
    if side == "left":
        mask = x > buckets # left-exclusive
    else:
        mask = x >= buckets # left-inclusive
    # Count the indices
    indices = mask.sum(axis=0)

    # reshape back to the shape of inputs
    indices = indices.reshape(shape)

    return indices
```

- Line 7: Stores the shape of the original input. This is because we will be performing broadcasting on the flattened inputs, but for the mapped bucket indices, we would still like to return the same shape as that of the input.
- Line 8: Flattens the input.
- Line 10: Converts `buckets` into a column vector.
- Lines 11-14: If we follow the `searchsorted` argument `side`, and when `side="left"`, we formulate as left-exclusive, then input values should be strictly greater than the bucket values. Otherwise, to be left-inclusive, the input values are greater than or equal to the bucket values. See Figure 9.11 for illustrations of the resulting masks under the two formulations.

# Figure 9.11 Example illustration of left-inclusive and left-exclusive masking results.

| | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 3 | 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 6 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | 1 |
| 9 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |

| | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 3 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 |
| 6 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 1 |
| 9 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

- Line 17: Here we are counting how many indicators satisfy the formulation condition. Using x=3 as an example (Figure 9.11), if we are formulating as “left-inclusive” (side="right"), then 3 >= 0 -> True -> 1, 3 >= 3 -> True -> 1, 3 >= 6 -> False -> 0, and 3 >= 9 -> False -> 0. The value 3 has indicators [1, 1, 0, 0] along the buckets. Adding the indicators together, we obtain an index value of 2, which corresponds to the bucket range (3,6] (with index 1 being [0, 3], and index 0 being (-inf, 0)). By contrast, if we are formulating as “left-exclusive” (side="left"), then 3 > 0 -> True -> 1, 3 > 3 -> False -> 0, 3 > 6 -> False -> 0, and 3 > 9 -> False -> 0. Now, the value 3 has accumulated indicators as [1, 0, 0, 0] . Adding the indicators together, we obtain an index value of 1, which corresponds to the bucket range (0, 3] (recall the index 0 corresponds to (-inf, 0]).

- Line 20: Reshapes the flattened, mapped indices back to the shape of the input.

There are several applications that need value bucketization. For example, we can engineer a continuous feature as a categorical feature since the model may benefit from learning the features as a group rather than a fine-grained continuous value that may not represent any important aspects of the feature. Consider the user age feature which is typically stored as numerical values in the data. However, when predicting if a user will watch mature content, it may be more beneficial to use a binary feature indicating whether or not the user is an adult, rather than their exact age. Thus, bucketization is a powerful feature engineering technique that helps data scientists and machine learning engineers build more efficient models. In another example, if we would like to plot a histogram given a list of values, we can first assign the continuous values in a predefined list of buckets, and then use `np.unique` to count the number of occurrences of each bin. We can also use bucketization operations to downsample float values into lower-precision integer values to compress the size of the model weights, for example. This is known as **quantization** and is a key technique to speed up model inference by sacrificing output quality due to reduced precision. Both Tensorflow [Abadi et al., 2023] and PyTorch [Paszke et al., 2023] have dedicated operations and quantization integer representations (`qint8`, `qint32`, etc.) to help the parameter quantization and model compression processes.

## 9.5 Segment-wise Aggregation

Although Pandas is the best-known library for the groupby-aggregate-apply pattern, more basic numerical libraries including NumPy as well as deep-learning-oriented ones like Tensorflow and PyTorch also implement operations to facilitate the use of this pattern for data transformation. More specifically, these are called segment operations, where, in general,

- Sequences of elements of variable lengths are arranged along a single dimension.
- An array of integers labels the group identity of the segments.
- Elements within the group are aggregated together by a reduction operation, such as summation.

See Figure 9.12 for an illustration of an example of segment-wise summation operations. Table 9.2 provides a list of segment operations in NumPy, Tensorflow, and PyTorch.

![](img/e891acaacd4fb5b80dab2ed824618203_340_0.png)

**Figure 9.12** Illustration of segment-wise summation operation, with each color indicating a segment/group of values. There are two ways to denote the segment, either through sequence index or segment id.

# **Table 9.2 List of groupwise aggregation operations in NumPy, Tensorflow, and PyTorch.**

| Operation | NumPy | Tensorflow | PyTorch |
|---|---|---|---|
| Groupwise sum<sup>a)</sup> | np.add.reduceat | tf.math.segment_sum, tf.math.unsorted_segment_sum, tf.sparse.segment_sum | torch.scatter_add, torch.scatter_reduce(..., reduce="sum"), torch.segment_reduce(arr, "sum", offsets) |

Notes:
- **Start-end indices**: This is reminiscent of `csr_matrix` `indptr` property from Scipy, where an array of ascending integer indices indicates the starts and ends of each segment along a flattened array. This also assumes the elements of the same group are adjacent to each other. When working with NumPy's groupwise operations `np.ufunc.reduceat`, the value to the indices argument is an array of starting indices of each segment, signifying the slices to aggregate (this means, it does not have to be strictly monotonically increasing). It assumes the last segment starts from the last element of `indices` to the last element of the array, i.e. `data[indices[-1]:]`. `indices` here is also equivalent to `indptr[:-1]` which excludes the last element that denotes the end of the segment. Example usage:

```python
1
import numpy as np
2
data = np.array([1, 2, 3, 2, 3, 4, 5, 4, 7, 2, 8, 31])
3
indices = np.array([0, 3, 6])
4
res_np = np.add.reduceat(data, indices)
5
# sum(data[0:3]), sum(data[3:6]), sum(data[6:])
6
# array([ 6, 11, 20])
7
8
# non-monotonically increasing indices
9
indices = np.array([0, 3, 2, 6])
10
res_np = np.add.reduceat(data, indices)
11
# sum(data[0:3]), sum(data[3]), sum(data[2:6]), sum(data[6:])
12
# array([ 6, 2, 14, 20])
```

In the case of non-monotonically increasing indices, the second slice [3:2] is interpreted as [3], which then takes the element at index 3 only. Therefore, there is no good way to create segments with zero elements. On the other hand, PyTorch's torch.segment_reduce operation has two arguments to indicate the start and end indices: – offsets: Unlike NumPy, the value to this argument needs to include the end index of the last segment, just like the indptr property of csr_matrix. Unlike the indices argument of np.ufunc.reduceat, the offsets property needs to be strictly monotonically increasing, since offsets is being used to compute the length of the segments. Note that it is possible to specify zero-length segments, e.g.(continue on next page)

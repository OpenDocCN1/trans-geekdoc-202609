
# (3, 1) broadcastable to (3, 2)
# this will reuse the value along the rows
values = np.array([[
    [1],
    [2],
    [3],
]])

np.put_along_axis(X, indices, values, axis=1)
# array([[1, 0, 1, 0],
#     [0, 2, 0, 2],
#     [0, 3, 3, 0]])

![](img/e891acaacd4fb5b80dab2ed824618203_122_0.png)

Figure 3.14 Illustrated example of np.put_along_axis.

## 3.6.3 Multi-index Scatter Replacement

Since Tensorflow's tf.Tensor are immutable objects, we need to rely on concrete functions to assign values at indices and return a copy of the modified tensor. Tensorflow does not implement an operation that uses flat index to assign values; i.e. there is not really a function that is the reverse of tf.gather. But Tensorflow does implement the N-dimensional scattering operation tf.scatter_nd which is the opposite operation of tf.gather_nd but with certain limitations (e.g. no support of scattering over a batch). In a subsequent case study below, we will try to implement a version of the batched scattering operation that uses flat indices along an axis. tf.scatter_nd is unique to Tensorflow, as it assumes the target tensor to be modified is always filled with 0s. Therefore, instead of asking for a specific tensor to replace values on, it asks for the shape of the target tensor. For example,

```python
import tensorflow as tf
# [row, col]
indices = tf.constant([
    [0, 2],
    [1, 3],
    [2, 0],
    [3, 1],
    [4, 2],
])
values = tf.constant([1, 3, 5, 7, 9])
shape = (5, 4)
X_tf = tf.scatter_nd(indices, values, shape)
# <tf.Tensor: shape=(5, 4), dtype=int32, numpy=
# array([[0, 0, 0, 0],
# [0, 0, 0, 3],
# [5, 0, 0, 0],
# [0, 7, 0, 0],
# [0, 0, 9, 0]], dtype=int32)>
```

See also Figure 3.15 for an illustration.

Alternatively, we can also use the tensor update operation tf.tensor_scatter_nd_update in Tensorflow, or torch.index_put (and the in-place version, torch.Tensor.index_put_) in PyTorch. For NumPy (as well as PyTorch), the same effect can be achieved via simple indexed assignment,

![](img/e891acaacd4fb5b80dab2ed824618203_123_0.png)

Figure 3.15 Illustration of scattering values over a 2D matrix using multi-index.

```python
import numpy as np
import tensorflow as tf
import torch
# [row, col]
indices = tf.constant([
    [0, 2],
    [1, 3],
    [2, 0],
    [3, 1],
    [4, 2],
])
values = tf.constant([1, 3, 5, 7, 9])
shape = (5, 4)
X_tf = tf.zeros(shape, dtype=values.dtype)
X_tf = tf.tensor_scatter_nd_update(
    X_tf, indices, values
)
# equivalently in NumPy
X_np = np.zeros(shape, dtype=int)
X_np[tuple(indices.numpy().T)] = values
assert np.allclose(X_tf, X_np)
# 2 equivalent operations in PyTorch
# Converting to PyTorch dtypes
indices = indices.to(indices.numpy())
values = torch.tensor(values.numpy(), dtype=int)
# Method 1: Using indexed assignment like NumPy
X_torch = torch.zeros(shape, dtype=int)
X_torch[tuple(indices.T)] = values
assert np.allclose(X_tf, X_torch)
# Method 2: Using torch.index_put
X_torch = torch.zeros(shape, dtype=int)
X_torch = torch.index_put(X_torch, tuple(indices.T), values)
# Method 2 In-place: Using torch.Tensor.index_put_
X_torch = torch.zeros(shape, dtype=int)
# Also returns the modified tensor itself
X_torch.index_put_(tuple(indices.T), values)
```

torch.index_put has two modes, by setting the argument accumulate=False (default) or accumulate=True, respectively. As illustrated in the above example, PyTorch's torch.index_put(..., accumulate=False) is equivalent to Tensorflow's tf.tensor_scatter_nd_update. Just like tf.tensor_scatter_nd_update, the final replaced value of the target tensor is not deterministic on GPU. On the other hand, using torch.index_put(..., accumulate=True) in PyTorch is the same as using tf.tensor_scatter_nd_add in Tensorflow, or using np.add.at in NumPy. The behavior of tf.scatter_nd(indices, values, shape) is also the same as tf.tensor_scatter_nd_add(tf.zeros(shape), indices, values). In these equivalent operations, duplicated indices will be summed together. Suppose the last index is duplicated with a different value to assign:

```python
import numpy as np
import tensorflow as tf
import torch
indices = torch.tensor([
    [0, 2],
    [1, 3],
    [2, 0],
    [3, 1],
    [4, 2],
    [4, 2],
])
values = torch.tensor([1, 3, 5, 7, 9, 11])
shape = (5, 4)

# NumPy:
X_np = np.zeros(shape, dtype=int)
X_np[tuple(indices.T)] = values

# Tensorflow:
X_tf = tf.zeros(shape, dtype=tf.int32)
X_tf = tf.tensor_scatter_nd_update(X_tf, indices, values)

# PyTorch:
X_torch = torch.zeros(shape, dtype=int)
X_torch = torch.index_put(
    X_torch, tuple(indices.T), values, accumulate=False
)

assert np.allclose(X_np, X_tf)
assert np.allclose(X_tf, X_torch)

# On CPU, the last value of the duplicated index is used
# array([[ 0, 0, 1, 0],
#  [ 0, 0, 0, 3],
#  [ 5, 0, 0, 0],
#  [ 0, 7, 0, 0],
#  [ 0, 0, 11, 0]])

# Accumulate via summation
# NumPy:
X_np = np.zeros(shape, dtype=int)
np.add.at(X_np, tuple(indices.T), values) # in-place

# Alternatively,
# X_np[tuple(np.array(indices).T)] += np.array(values)

# Tensorflow:
X_tf = tf.zeros(shape, dtype=tf.int32)
X_tf = tf.tensor_scatter_nd_add(X_tf, indices, values)
X_tf_alt = tf.scatter_nd(indices, values, shape)

# PyTorch:
X_torch = torch.zeros(shape, dtype=int)
X_torch = torch.index_put(
    X_torch, tuple(indices.T), values, accumulate=True
)

assert np.allclose(X_np, X_tf)
assert np.allclose(X_tf, X_tf_alt)
assert np.allclose(X_tf, X_torch)

# array([[ 0, 0, 1, 0],
# [ 0, 0, 0, 3],
# [ 5, 0, 0, 0],
# [ 0, 7, 0, 0],
# [ 0, 0, 20, 0]])
```

NumPy, Tensorflow, and PyTorch also implement other scattering accumulation functions than simple summations, as illustrated in Table 3.5.

```python
import tensorflow as tf
indices = tf.constant([0, 2, 4])
values = tf.constant([1, 3, 5])
shape = (5, )
X = tf.scatter_nd(indices, values, shape)
```

However, this throws the following error:

```
InvalidArgumentError: {{function_node
__wrapped__ScatterNd_device_/job:localhost/replica:0/task:0
/device:CPU:0}} dimensions [3,1] of input [shape=[5]] must
match dimensions [0,1] of updates[shape=[3]]
__ [Op:ScatterNd]
```

Instead, based on the documentation of `tf.scatter_nd` [Abadi et al., 2023d], we need to specify `indices` as a column vector of shape `(n, 1)`, i.e.

```python
import tensorflow as tf
indices = tf.constant([0, 2, 4])[:, None]
values = tf.constant([1, 3, 5])
shape = (5, )
X = tf.scatter_nd(indices, values, shape)
# <tf.Tensor: shape=(5,), dtype=int32, numpy=array([1, 0, 3, 0, 5], dtype=int32)>
```

I found it helpful to understand this as if the target tensor is treated as a column vector as well, and the indices we are specifying are the indices of each row (i.e. first dimension), as illustrated in Figure 3.16. In general, the indices within the dimensions are arranged within a column, and indices of multiple dimensions are horizontally stacked together, which forms

- [dim_0_index_0, dim_1_index_0, ..., dim_d_index_0,
- dim_0_index_1, dim_1_index_1, ..., dim_d_index_1,
- ...
- dim_0_index_n, dim_1_index_n, ..., dim_d_index_n]

PyTorch still requires the indices argument to be a tuple whose number of elements is the same as the number of dimensions, with each element being the 1D array of indices along the dimension:

```python
import torch
indices = torch.tensor([0, 2, 4])
values = torch.tensor([1, 3, 5])
shape = (5, )
X_torch = torch.zeros(shape, dtype=int)
X_torch = torch.index_put(X_torch, (indices, ), values)
# tensor([1, 0, 3, 0, 5])
```

The scattering operations in NumPy, Tensorflow, and PyTorch also allow us to scatter multi-dimensional slices. See also Figure 3.17 for an illustration.

![](img/e891acaacd4fb5b80dab2ed824618203_127_0.png)

Figure 3.16 Illustration of tf.scatter_nd over a 1D target tensor.

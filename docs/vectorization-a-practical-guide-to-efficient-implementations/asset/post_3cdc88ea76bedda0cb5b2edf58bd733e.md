
### Inputs

| | 0 | 1 | 2 | 3 |
|---|---|---|---|---|
| 0 | 1 | 2 | 3 | 4 |
| 1 | 5 | 6 | 7 | 8 |
| 2 | 9 | 10 | 11 | 12 |
| 3 | 13 | 14 | 15 | 16 |
| 4 | 17 | 18 | 19 | 20 |

### Indices

| Block | 0 | 1 | 2 | 3 |
|---|---|---|---|---|
| 1 | 8 | 15 | 20 | 2 |
| 2 | 10 | 8 | 19 | 2 |
| 3 | 5 | 1 | 6 | 2 |
| 4 | 2 | 10 | 13 | 6 |
| 5 | 8 | 15 | 19 | 6 |
| 6 | 7 | 13 | 12 | 2 |

**Figure 3.12** Illustration of tf.gather_nd with nonzero batch_dims argument. The initial two batch dimensions are unfolded into a 2 x 3 grid in this schematic representation.

## 3.5 Assign Values at Index

NumPy's `np.ndarray` and PyTorch's `torch.Tensor` are mutable, which means the values of the object can be updated. This behavior is similar to Python's `list` class. In contrast, Tensorflow's `tf.Tensor` is immutable [Abadi et al., 2023c], which is similar to Python's tuple or set class. This may be tied to Tensorflow's original operating principle which requires series of operations must be compilable into a computational graph before execution (i.e. graph mode), rather than executing as is, in place (i.e. eager mode, which is a more recent development since version 2.0). Both NumPy's `np.ndarray` and PyTorch's `torch.Tensor` can be modified in-place (i.e. without creating a new object) by specifying the indices of the element to change and the values to replace. For examples,

```python
import numpy as np
import tensorflow as tf
import torch

# Python list
X_py = [1, 2, 3, 4]
X_py[3] = 100 # [1, 2, 3, 100]

# NumPy
X_np = np.array([1, 2, 3, 4])
X_np[3] = 100 # array([1, 2, 3, 100])

# PyTorch
X_torch = torch.tensor([1, 2, 3, 4])
X_torch[3] = 100 # tensor([1, 2, 3, 100])

# Tensorflow
X_tf = tf.constant([1, 2, 3, 4])
X_tf[3] = 100 # throws an error
```

The last line, which attempts to assign a value to a Tensorflow `tf.Tensor`, throws the following error:

```
TypeError: 'tensorflow.python.framework.ops.EagerTensor' object does not support item assignment
```

To illustrate that assigning a value at a given index is an in-place operation, let's look at the following example:

```python
import numpy as np
X = np.array([1, 2, 3, 4])
# create a new variable that points to X
Y = X
# modify X
X[3] = 100
# print
print(X) # array([1, 2, 3, 100])
print(Y) # array([1, 2, 3, 100])
```

We will observe that both X and Y are modified, even though we only performed the assignment operation on X.

In addition to modifying values, we can also perform in-place value accumulations using Python's `<operator>=` syntaxes, as listed in Table 3.4:

| Accumulation Operation | In-place Operator | Equivalent Expression |
|---|---|---|
| Addition | += | x[index] += y ⟺ x[index] = x[index] + y |
| Subtraction | -= | x[index] -= y ⟺ x[index] = x[index] - y |
| Multiplication | *= | x[index] *= y ⟺ x[index] = x[index] * y |
| Division | /= | x[index] /= y ⟺ x[index] = x[index] / y |
| Integer division | //= | x[index] //= y ⟺ x[index] = x[index] // y |
| Modulus | %= | x[index] %= y ⟺ x[index] = x[index] % y |
| Exponentiation | **= | x[index] **= y ⟺ x[index] = x[index] ** y |

As a quick example:

```python
import numpy as np
X = np.array([1, 2, 3, 4])
X[3] += 5
print(X) # array([1, 2, 3, 9])
```

For multi-dimensional arrays, we may use multi-index to reference the element and assign the values at the index.

```python
import numpy as np
X = np.arange(20).reshape(4, 5)
X[3, 2] -= 20 # 17 -> -3
print(X)
# array([[ 0, 1, 2, 3, 4],
#     [ 5,  6,  7,  8,  9],
#    [10, 11, 12, 13, 14],
#    [15, 16, -3, 18, 19]])
```

We can also replace the values of a slice with a single value.

```python
import numpy as np
X = np.arange(20).reshape(4, 5)
# replacing the last column with -99
X[:, -1] = -99
print(X)
# array([[ 0,  1,  2,  3, -99],
#        [ 5,  6,  7,  8, -99],
#        [10, 11, 12, 13, -99],
#        [15, 16, 17, 18, -99]])
```

More generally, the values assigned can be broadcasted to the elements of the slice:

```python
import numpy as np
X = np.arange(20).reshape(4, 5)
# replacing the last two columns with -88, -99, respectively
X[:, -2:] = np.array([-88, -99])
# array([[ 0,  1,  2, -88, -99],
#        [ 5,  6,  7, -88, -99],
#        [10, 11, 12, -88, -99],
#        [15, 16, 17, -88, -99]])
```

Lastly, we may also choose to assign different values at multiple indices we choose.

```python
import numpy as np
X = np.arange(20).reshape(4, 5)
# Assign the diagonal entries with different values
rows = np.array([0, 1, 2, 3])
cols = np.array([0, 1, 2, 3])
values = np.array([-1, -2, -3, -4])
X[rows, cols] = values
# array([[ 1,  1,  2,  3,  4],
#        [ 5, -2,  7,  8,  9],
#        [10, 11, -3, 13, 14],
#        [15, 16, 17, -4, 19]])
```

## 3.6 Put and Scatter

Put and scatter operations are the reverse operations of take and gather: instead of retrieving elements from a tensor at certain indices, these operations can replace and aggregate values from a source tensor to a destination tensor. Put and scatter operations are more general operations than in-place value assignment that we discussed in Section 3.5, as they can operate in batches more efficiently. Furthermore, put and scatter operations can be seen as a way to perform group-by and aggregate operations, which we will explore more thoroughly in Chapter 9. Table 3.5 provides a list of equivalent put and scatter operations among NumPy, Tensorflow, and PyTorch.

### 3.6.1 Put

np.put operation is the reverse operation of np.take. Similar to np.take, np.put uses flat indices to put values from a source vector to a destination tensor. The np.put operation is an in-place operation that modifies the input directly without returning a copy.

```python
import numpy as np
X = np.zeros(10, dtype=int)
indices = np.array([2, 4, 6, 8])
values = np.array([1, 2, 3, 4])
# in-place operation modifies X directly
np.put(X, indices, values)
# array([0, 0, 1, 0, 2, 0, 3, 0, 4, 0])
```

Like np.take, multi-dimensional targets are treated as if flattened (in the “C” order); indices are the flat index of the target tensor (see also Figure 3.13 for an illustration).

```python
import numpy as np
X = np.zeros((3, 3), dtype=int)
indices = np.array([1, 2, 5, 8])
values = np.array([1, 2, 3, 4])
np.put(X, indices, values)
# array([[0, 1, 2],
#     [0, 0, 3],
#     [0, 0, 4]])
```

Multidimensional indices may not be utilized as expected, since they are treated as if the indices are flattened. The target’s shape will be retained.

Table 3.5 List of put and scatter operations in NumPy, Tensorflow, and PyTorch.

| Operation | NumPy | Tensorflow | PyTorch |
| :--- | :--- | :--- | :--- |
| Put using flat index | np.put (in-place) | N/A | torch.put (in-place: torch.Tensor.put_) |
| Put along axis | np.put_along_axis (in-place) | N/A | N/A |
| Put to shape using multi-index | N/A | tf.scatter_nd | N/A |
| Scatter with replacement | N/A | tf.tensor_scatter_nd_update | torch.index_put (..., accumulate=False) |
| Scatter with addition | np.add.at | tf.tensor_scatter_nd_add | torch.index_put (..., accumulate=True) |
| Scatter with subtraction | np.subtract.at | tf.tensor_scatter_nd_sub | N/A |
| Scatter with max | np.maximum.at | tf.tensor_scatter_nd_max | a)torch.index_reduce (..., reduce="amax"), torch.scatter_reduce (..., reduce="amax") |
| Scatter with min | np.minimum.at | tf.tensor_scatter_nd_min | a)torch.index_reduce (..., reduce="amin"), torch.scatter_reduce (..., reduce="amin") |
| Scatter with mean | N/A | N/A | a)torch.index_reduce (..., reduce="mean"), torch.scatter_reduce (..., reduce="mean") |
| Scatter with product | np.multiply.at | N/A | a)torch.index_reduce (..., reduce="prod"), torch.scatter_reduce (..., reduce="prod") |

Note: a) The logic of these PyTorch scatter functions is not exactly the same as that of NumPy and Tensorflow. See discussions below.

![](img/e891acaacd4fb5b80dab2ed824618203_121_0.png)

```python
import numpy as np
X = np.zeros((3, 3), dtype=int)
indices = np.array([[1, 2], [5, 8]])
values = np.array([1, 2, 3, 4])
np.put(X, indices, values)
# array([[0, 1, 2],
#     [0, 0, 3],
#     [0, 0, 4]])
```

PyTorch's `torch.put` has identical behavior, but it will return a copy of the modified target tensor. PyTorch has an in-place version of the `put` method, implemented under `torch.Tensor.put_`. To modify the tensor in-place, one can do `X.put_(indices, values)`.

### 3.6.2 Put Along Axis

`np.put_along_axis` is the reverse operation of `np.take_along_axis`. This function is unique to NumPy. Like `np.take_along_axis`, the `axis` argument specified which dimension is the non-batching dimension, while the rest of the dimensions are the batch dimensions. The variable “indices” is indexing the items along the axis, whose value should not exceed `indices.shape[axis]`. The number of dimensions of `indices` must be the same as that of the target, i.e. `indices.ndim == X.ndim`. `values` also need to be broadcastable to `indices`. As illustrated in Figure 3.14, for instance,

```python
import numpy as np
X = np.zeros((3, 4), dtype=int)
indices = np.array([
    [0, 2],
    [1, 3],
    [2, 1]
])
```

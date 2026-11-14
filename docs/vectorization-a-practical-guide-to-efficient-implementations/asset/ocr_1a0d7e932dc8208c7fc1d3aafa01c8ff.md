```
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
y_tf = tf.gather(
    # taking out the singleton dimension
    X, reorder_index[..., 0, :], axis=3, batch_dims=2
)
```

A heuristic on the expected output shape of `tf.gather` can therefore be derived (and also based on [Abadi et al., 2023a]) and implemented as

```
np.concatenate([
    inputs.shape[:axis],
    index.shape[batch_dims:],
    inputs.shape[axis+1:]
]).astype(int)
```

# 3.4.4 N-Dimensional Gather

Both NumPy and PyTorch use arrays of multi-indices to select multiple elements/slices. Tensorflow implements a special operation, `tf.gather_nd` to achieve the same purpose. The `tf.gather_nd` operation uses multi-index to gather elements from multiple index dimensions instead of using flat index to gather from a single dimension like the `tf.gather` operation. As a simple example,

```
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
```
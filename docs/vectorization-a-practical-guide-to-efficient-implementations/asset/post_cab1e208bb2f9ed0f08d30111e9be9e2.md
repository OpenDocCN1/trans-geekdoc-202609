
### 4.2.1 The @ Operator

The @ operator was introduced in Python 3.5 (PEP 465 [Van Rossum and Drake, 2014]). It can help naturally express tensor multiplications, hence, enhancing the readability of the codes that implement certain mathematical operations. It also help simplify calls like np.matmul(np.matmul(np.matmul(a, b), c), d) to a @ b @ c @ d. This operator contrasts the * operator which indicates element-wise multiplication. Its usage rules are the same as matmul operations in each library. Python will assume which library’s matmul operation to call based on the object type of the tensor representations. It is interesting to ask the question of which library’s matmul operation will take priority when there is a mix of variables. We can find out with some experiments, as illustrated in the following code example:

```python
import numpy as np
import tensorflow as tf
import torch

a = np.random.rand(7, 4, 3, 5)
b = np.random.rand(5)
c = np.random.rand(1, 1, 5, 3)
# this is working as expected, returns numpy.ndarray
a @ b
# This throws an error,
# Torch and NumPy is not compatible with @ operator
a @ torch.tensor(b)
# This will throw an error,
# since Tensorflow's matmul is called
a @ tf.constant(b)
# This will pass, returns a tf.Tensor
a @ tf.constant(c)
# This will pass, returns a tf.Tensor
# It does not matter if the first or
# second argument of matmul is tf.Tensor
tf.constant(a) @ c
# This will pass, returns a tf.Tensor
tf.constant(a) @ torch.tensor(c)
```

The conclusions are:

- PyTorch requires the inputs to be both torch.Tensor before executing the operation, so we cannot use NumPy’s np.ndarray and Torch tensors in a mix.
- NumPy and Tensorflow’s tensors can be used in a mix (at least in eager mode). But Tensorflow’s method will take higher priority, and the results returned are cast into a tf.Tensor. Broadcasting also works between NumPy and Tensorflow.
- Torch and Tensorflow's tensors can also be used in a mix. The behavior is the same as if the Torch tensor is a NumPy tensor with respect to broadcasting. Tensorflow's method is taking higher priority and the result is a tf.Tensor.

## 4.3 The tensordot Operation

The tensordot (a.k.a tensor contraction) operation is a generalization of all of the above matrix product operations. It performs dot product (or equivalently, element-wise multiplication followed by summation reduction operation) along certain axes. It takes not only two inputs to be multiplied together but also a third argument axes to indicate how many axes (if integer argument) or along which specific pairs of axes (input a pair of list argument) the multiplication results are summed together. Several mathematical operations we introduced in Section 4.2 can be expressed using tensordot:

- Dot product between vectors, $a \cdot b$, using tensordot(a, b, 1):

```python
a = np.random.rand(5)
b = np.random.rand(5)
np.allclose(
    np.dot(a, b),
    np.tensordot(a, b, 1)
)
```

Note that complex conjugate dot product vdot can be implemented by tensordot using np.tensordot(a, b.conj(), 1)

- Cross (outer) product between vectors, $a \times b$, using tensordot(a, b, 0):

```python
a = np.random.rand(5)
b = np.random.rand(3)
np.allclose(
    np.outer(a, b),
    np.tensordot(a, b, 0)
)
```

- 2D matrix multiplication ab:

```python
a = np.random.rand(5, 3)
b = np.random.rand(3, 5)
np.allclose(
    np.matmul(a, b),
    np.tensordot(a, b, 1)
)
```

A typical usage of tensordot is to implement double matrix/tensor contraction (commonly denoted as a : b = Tr(a · b^T)), using tf.tensordot(a, b, 2), given two matrix inputs:

```python
a = np.random.rand(5, 3)
b = np.random.rand(5, 3)
np.allclose(
    np.tensordot(a, b, 2),
    np.trace(a @ b.T)
)
```

tensordot can be used for even more general tensor multiplications, especially when the axes argument is provided as a pair of lists of indices. Notice that len(axes[0]) == len(axes[1]). Values in the list of dimensions can also be negative. For example, we want to compute the matrix contraction between the combinations of a stack of three matrices and another stack of two matrices of shape (4, 2),

```python
a = np.random.rand(2, 4, 2)
b = np.random.rand(3, 4, 2)
# this results a tensor of shape (2, 3)
np.tensordot(a, b, axes=([1, 2], [1, 2]))
```

The above example is illustrated in Figure 4.1.

![](img/e891acaacd4fb5b80dab2ed824618203_145_0.png)

**Figure 4.1** Illustration of an example tensordot operation between tensors of shape (2, 4, 2) and (3, 4, 2). Notice that the dot products between combinations of the first column vectors result in the upper left corner tiles of the 2 x 2 matrices, while dot products between combinations of the second column vectors result in the lower right tiles in the 2 x 2 matrices. The sum of the values along the diagonal of the 2 x 2 matrices is the values of the final matrix of shape (2, 3).

### 4.3.1 Heuristics of tensordot Operations

Notice from the above examples that the shape of the output tensor from `tensordot` operations varies when the `axes` argument changes. Different integer values of the `axes` argument seem to dictate different tensor multiplication behaviors. But we can derive a general rule of thumb by inductive reasoning.

When `axes=0`, given two vector inputs `(m, )`, and `(n, )`, we have seen that the resulting tensor has shape `(m, n)`, as if an outer product is taken. In general, when given two tensors `a` with shape `(m, n, ...)` and `b` with shape `(p, q, ...)`, the tensordot with `axes=0` has shape of `(m, n, ..., p, q, ...)`. This is as if every single element from tensor `a` is multiplying with every single element from tensor `b` to form the final tensor without summation to reduce any dimensions. Figure 4.2 illustrates this generalization. The following code snippet demonstrates an example of this heuristic:

```python
a = np.random.rand(2, 3, 4, 5)
b = np.random.rand(6, 7, 8)
np.allclose(
    np.tensordot(a, b, 0).shape,
    [2, 3, 4, 5, 6, 7, 8]
)
```

![](img/e891acaacd4fb5b80dab2ed824618203_146_0.png)

**Figure 4.2** Illustration of `tensordot` operations when `axes=0`. (a) For a pair of 1D vectors of shapes `(5, )` and `(4, )`, a combination of each element between the two vectors forms the outer product, having shape `(5, 4)`. (b) Adding one row dimension in the first input, the problem becomes the tensordot operation between a matrix of shape `(2, 5)` and a vector of shape `(4, )`. Hence, the resulting tensor has shape `(2, 5, 4)` (notice that singleton dimensions would be squeezed out). (c) Adding one additional column dimension in the second input forms a problem of tensordot between a matrix of shape `(2, 5)` and one of `(4, 2)`. Then, the resulting tensor has shape `(2, 5, 4, 2)`.

When axes=1, we have seen that when the two inputs are 1D vectors, the dot product (which is a scalar) of the two tensors is returned. In general, given tensors a of shape (m, n, ..., i) and b of shape (i, ..., p, q, ...), the tensor dot product with of the two tensors with axes=1 has shape (m, n, ..., p, q, ...), where the last dimension of a and first dimension of b are reduced together. This is as if we are performing a series of dot products between combinations of two vector batches. Figure 4.3 illustrates examples of this generalization. The following code snippet demonstrates an example of this heuristic:

```python
a = np.random.rand(2, 3, 4, 5)
b = np.random.rand(5, 6, 7)
np.allclose(
    np.tensordot(a, b, 1).shape,
    [2, 3, 4, 6, 7]
)
```

When axes=2, the two input tensors must have at least two dimensions. We have seen that the double tensor contraction operation can be performed when given two matrices. In general, given tensors a of shape (m, n, ..., i, j) and b of shape (i, j, ..., p, q, ...), the tensor dot product between a and b with axes=2 has the shape (m, n, ..., p, q, ...), where the last two dimensions of a and first two dimensions of b are contracted. Figure 4.4 illustrates examples of this generalization. The following code snippet demonstrates an example of this heuristic:

```python
a = np.random.rand(2, 3, 4, 5)
b = np.random.rand(4, 5, 6, 7)
np.allclose(
    np.tensordot(a, b, 2).shape,
    [2, 3, 6, 7]
)
```

After exploring the above heuristics for when axes=0, axes=1 and axes=2, we may derive a more general rule for when axes is an integer argument: given the first input tensor a has shape (m, n, ..., s1, s2, ..., sk), if we would like to perform tensor dot product with axes=k, then it is necessary to make the second input tensor b has the shape (s1, s2, ..., sk, ..., p, q, ...). Each tensor of shape (s1, s2, ..., sk) from the hatched tensor a is multiplied together with the tensor of the same shape from b element-wise and then summed together to form a single scalar. The resulting tensor will then have shape (m, n, ..., p, q, ...), with the last k dimensions of the first input a and first k dimensions of the second input b contracted (i.e. reduced, or summed together).

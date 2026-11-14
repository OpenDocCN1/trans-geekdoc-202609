| Operation | Equation String (Explicit) | Equation String (Implicit) | Equivalent NumPy Operations |
|---|---|---|---|
| Hadamard product<sup>g)</sup> | "ij,ij->ij" | NA | np.multiply |
| Matrix multiplication<sup>h)</sup> | "...ij,...jk->...ik" | "...ij,...jk" | np.matmul |
| Dot product<sup>i)</sup> | "...j,ijk->...ik" | "...j,ijk" | np.dot |

g) The Hadamard multiplication example illustrates the case of element-wise multiplication between a pair of 2D matrices. In general, to construct a Hadamard multiplication using einsum, we can use the format of "ijk...,ijk...->ijk...", in which the corresponding dimensions will be multiplied together. It is also convenient to construct the Hadamard multiplication when one of the tensor's dimensions needs to be swapped or transposed. For example, if we want to perform element-wise multiplication between a tensor of shape (2, 5, 3) and another one of shape (2, 3, 5):

```
```python
X = np.random.rand(2, 5, 3)
Y = np.random.rand(2, 3, 5)
np.allclose(
    X * Y.swapaxes(1, 2),
    np.einsum("ijk,ikj->ijk", X, Y)
)
```
```

h) Multidimensional matrix multiplication requires dimensions other than the last two dimensions broadcastable. The ellipses ... represent the broadcasting dimensions. For example,

```
```python
a = np.random.rand(1, 6, 3)
b = np.random.rand(8, 3, 7)
# shape (8, 6, 7)
np.allclose(
    np.einsum("...ij,...jk", a, b),
    np.matmul(a, b)
)
```
```

i) For multidimensional dot products, the last axis of the first input is multiplied and summed together with the second to last axis of the second input. For the first input, we can omit the indices for all the dimensions other than the last dimension, and replace them with ellipsis .... For the second input, we need to specify all the indices. For example

```
```python
a = np.random.rand(2, 5, 3, 6)
b = np.random.rand(7, 6, 4)
# shape (2, 5, 3, 7, 4)
np.allclose(
    np.einsum("...j,ijk->...ik", a, b),
    np.dot(a, b)
)
```
```
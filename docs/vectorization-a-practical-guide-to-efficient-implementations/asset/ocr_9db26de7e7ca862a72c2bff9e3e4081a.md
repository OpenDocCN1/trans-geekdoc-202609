# Axes = 1

![](bbox=[0.13, 0.16, 0.72, 0.58])

Figure 4.3 Illustration of tensordot operations when axes=1. (a) For a pair of 1D vectors each having a shape of (5,), the tensor dot product along axes=1 is equivalent to simple vector inner dot product, which results in a scalar; (b) adding another vector along the first dimension of a, the operation becomes dot products between two vectors in a (shape (2, 5), each against b (shape (5,). This should yield a resulting vector of shape (2,1). But, since the implicit singleton dimension is squeezed, the resulting vector has shape (2,). (c) Adding an additional column dimension on the second input b, this results in an operation that performs pair-wise dot product between each vector in a (shape (2,5)) and b (shape (5, 2)). The resulting tensor has shape (2, 2), which is equivalent to matrix multiplication ab.

The axes argument can also be specified as a pair of lists of dimensions for contraction. In fact, in some specific cases, integer value arguments for axes can have a corresponding list version. For examples:

+   • np.tensordot (a, b, 0) is equivalent to np.tensordot (a, b, [[]] , [[]] ) where a and b can be any arbitrary tensor.
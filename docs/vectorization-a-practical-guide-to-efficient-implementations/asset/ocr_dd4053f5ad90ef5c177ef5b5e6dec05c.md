# 4.2.1 The @ Operator

The @ operator was introduced in Python 3.5 (PEP465 [Van Rossum and Drake, 2014]). It can help naturally express tensor multiplications, hence, enhancing the readability of the codes that implement certain mathematical operations. It also help simplify calls like np.matmul (np.matmul (np.matmul (a , b) , c) , d) to a @ b @ c @ d. This operator contrasts the * operator which indicates element-wise multiplication. Its usage rules are the same as matmul operations in each library. Python will assume which library’s matmul operation to call based on the object type of the tensor representations. It is interesting to ask the question of which library’s matmul operation will take priority when there is a mix of variables. We can find out with some experiments, as illustrated in the following code example:

```
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

+   * PyTorch requires the inputs to be both torch.Tensor before executing the operation, so we cannot use NumPy’s np.ndarray and Torch tensors in a mix.
+   * NumPy and Tensorflow’s tensors can be used in a mix (at least in eager mode). But Tensorflow’s method will take higher priority, and the results returned are cast into a tf.Tensor. Broadcasting also works between NumPy and Tensorflow.
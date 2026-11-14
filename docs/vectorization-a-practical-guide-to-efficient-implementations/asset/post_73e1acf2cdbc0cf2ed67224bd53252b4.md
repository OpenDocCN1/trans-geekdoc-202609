
Computing, Networking, Storage and Analysis, pages 1–25, Denver, CO, November 2019. ACM. ISBN 978-1-4503-6229-0. doi: 10.1145/3295500.3356216.

Adam Paszke, Sam Gross, Francisco Massa, Adam Lerer, James Bradbury, Gregory Chanan, Trevor Killeen, Zeming Lin, Natalia Gimelshein, Luca Antiga, Alban Desmaison, Andreas Köpf, Edward Yang, Zach DeVito, Martin Raison, Alykhan Tejani, Sasank Chilamkurthy, Benoit Steiner, Lu Fang, Junjie Bai, and Soumith Chintala. PyTorch Sparse Tensors. https://pytorch.org/docs/stable/sparse.html, 2023.

Pauli Virtanen, Ralf Gommers, Travis E. Oliphant, Matt Haberland, Tyler Reddy, David Cournapeau, Evgeni Burovski, Pearu Peterson, Warren Weckesser, Jonathan Bright, Stéfan J. van der Walt, Matthew Brett, Joshua Wilson, K. Jarrod Millman, Nikolay Mayorov, Andrew R. J. Nelson, Eric Jones, Robert Kern, Eric Larson, C. J. Carey, İlhan Polat, Yu Feng, Eric W. Moore, Jake VanderPlas, Denis Laxalde, Josef Perktold, Robert Cimrman, Ian Henriksen, E. A. Quintero, Charles R. Harris, Anne M. Archibald, Antônio H. Ribeiro, Fabian Pedregosa, Paul van Mulbregt, and SciPy 1.0 Contributors. SciPy 1.0: Fundamental algorithms for scientific computing in python. Nature Methods, 17:261–272, 2020. doi: 10.1038/s41592-019-0686-2.

Pauli Virtanen, Ralf Gommers, Travis E. Oliphant, Matt Haberland, Tyler Reddy, David Cournapeau, Evgeni Burovski, Pearu Peterson, Warren Weckesser, Jonathan Bright, Stéfan J. van der Walt, Matthew Brett, Joshua Wilson, K. Jarrod Millman, Nikolay Mayorov, Andrew R. J. Nelson, Eric Jones, Robert Kern, Eric Larson, C. J. Carey, İlhan Polat, Yu Feng, Eric W. Moore, Jake VanderPlas, Denis Laxalde, Josef Perktold, Robert Cimrman, Ian Henriksen, E. A. Quintero, Charles R. Harris, Anne M. Archibald, Antônio H. Ribeiro, Fabian Pedregosa, Paul van Mulbregt, and SciPy 1.0 Contributors. Sparse Matrices (scipy.sparse). https://docs.scipy.org/doc/scipy/reference/sparse.html, 2023.

Wikipedia. Ridge regression. https://en.wikipedia.org/wiki/Ridge_regression, May 2024.

## 8 Jagged Tensors

In various machine learning applications, we may sometimes need to deal with a batch of sequences that vary in length. For example, in natural language processing, sentences, paragraphs, or documents can contain a variable number of tokens. In audio processing, sample clips may come in variable durations. In recommendation systems, users' sequence of catalog interaction events may also vary in size. As we have already seen in Chapter 5, padding with dummy values within a dense tensor is a good way to represent sequences of variable lengths. These tensors still have a typical shape, where each entry along a certain dimension has exactly the same number of elements. For example, a matrix of shape `(4, 5)` has four rows, and each row has uniformly five elements. If we eliminate the padding entries toward the end of the sequence, and then examine the shape of the tensor, we can no longer confidently say that each entry along the dimension has the same number of elements. This tensor without the padding entries has therefore become a so-called **Jagged Tensor** or a **Ragged Tensor**, whose non-uniform dimension is the jagged dimension, and its shape is usually denoted by `None`. For example, a jagged matrix with four rows of data has the shape `(4, None)`.

A jagged tensor differs from a sparse tensor in that the paddings or empty entries of a jagged tensor always occur at the end of the sequence along the jagged dimension, whereas a sparse tensor can have empty entries occurring anywhere within the sequence while having a concrete shape (rather than using `None` to represent the jagged dimension). It can be seen that a sparse tensor is a more general representation of a tensor with padding/filler values. Therefore, we can also use a sparse tensor to represent a jagged tensor. See Figure 8.1 for an illustration of the three ways of representing jagged tensors.

![](img/e891acaacd4fb5b80dab2ed824618203_283_0.png)

Figure 8.1 Comparison of three ways of representing a jagged tensor. (a) A dense tensor with padding. Here, we use 0 as padding values. All padding values are to the right of the valid values. The dense tensor has a fixed shape. (b) A jagged tensor where the second dimension is the jagged dimension whose shape is unknown. The batch dimension has a known size. Notice that at row index 3, there are no elements in this row. It does not mean the batch size is unknown. But rather the row with no values in the list is represented as an empty list (this may be considered a type of padding). (c) Use a left-aligned sparse tensor to represent the jagged tensor. Notice that all valid entries are next to each other along the row. A sparse representation of a jagged tensor still needs to specify the size of the presumed jagged dimension, which is usually the expected maximum sequence length. (d) This is not a jagged tensor representation but rather a generic sparse tensor, since the values are not left-aligned.

Native Python simply represents a jagged tensor as a list of variable-length lists, i.e.

```
jagged_array = [[1, 3], [2, 4, 5], [8], []]
```

In contrast, the main NumPy library does not have a nice representation of a jagged tensor; it treats each list within the list as an object, i.e.

```
import numpy as np
jagged_array_np = np.array(
    [[1, 3], [2, 4, 5], [8], []], dtype=object
)
# array([list([1, 3]), list([2, 4, 5]), list([8]), list([])],
#       dtype=object)
```

But, many vectorization techniques can be applied to an array of objects like such. NumPy/Scipy has an extension library awkward [Pivarski et al., 2018] that can handle jagged arrays and tensors, but to the best of my knowledge, this library is not very well adopted.

The main TensorFlow library implements the tf.ragged module and the tf.RaggedTensor class [Abadi et al., 2023] to represent jagged tensors and allows various vectorizing operations. As we have seen previously, and will see again in this chapter, tf.ragged.range will be a very useful function to implement various sequence and set manipulation operations in TensorFlow.

```python
import tensorflow as tf
jagged_array_tf = tf.ragged.constant(
    [[1, 3], [2, 4, 5], [8], []]
)
# <tf.RaggedTensor [[1, 3], [2, 4, 5], [8], []]>
```

PyTorch implements the torch.nested module and the torch.nested.nested_tensor class to represent jagged tensors. Like TensorFlow's implementation, it eliminates the need to represent a variable-length sequence as a dense tensor with paddings, while allowing efficient operations using vectorization.

```python
import torch
jagged_array_torch = torch.nested.nested_tensor(
    [[1, 3], [2, 4, 5], [8], []]
)
# nested_tensor([
#   tensor([1, 3]),
#   tensor([2, 4, 5]),
#   tensor([8]),
#   tensor([], dtype=torch.int64)
# ])
```

At the time of writing this chapter, the torch.nested module is still in beta (torch==2.1.0). So when calling this module, we will see the following warning message:

> UserWarning: The PyTorch API of nested tensors is in the
> prototype stage and will change in the near future.
> (Triggered internally at
> /Users/runner/work/pytorch/pytorch/pytorch/aten/src/ATen/
> NestedTensorImpl.cpp:180.)

### 8.1 Left Align a Sparse Tensor to Represent Ragged Tensor

As mentioned before, other than padded dense tensors and special data structures such as tf.RaggedTensor, a jagged tensor can be represented using a sparse tensor whose entries are left aligned. For instance, in TensorFlow, we can convert a RaggedTensor to a SparseTensor

```python
import tensorflow
# RaggedTensor
X = tf.ragged.constant([
  [1, 3, 2], [4, 6], [1], [], [9, 3, 5, 8], []
])
# <tf.RaggedTensor [[1, 3, 2], [4, 6], [1], [], [9, 3, 5, 8], []]>
# Convert to SparseTensor
y = X.to_sparse()
# SparseTensor(indices=tf.Tensor(
# [[0 0]
#  [0 1]
#  [0 2]
#  [1 0]
#  [1 1]
#  [2 0]
#  [4 0]
#  [4 1]
#  [4 2]
#  [4 3]], shape=(10, 2), dtype=int64),
# values=tf.Tensor([1 3 2 4 6 1 9 3 5 8],
# shape=(10,), dtype=int32),
# dense_shape=tf.Tensor([6 4], shape=(2,), dtype=int64))
# Display sparse tensor as dense
tf.sparse.to_dense(y)
# <tf.Tensor: shape=(6, 4), dtype=int32, numpy=
# array([[1, 3, 2, 0],
#        [4, 6, 0, 0],
#        [1, 0, 0, 0],
#        [0, 0, 0, 0],
#        [9, 3, 5, 8],
#        [0, 0, 0, 0]], dtype=int32)>
```

We can make several observations of the sparse tensor that we created:

- 1. indices: The first column of the sparse tensor is the batch dimension index or the row index of each variable-length list. Notice that row index 3 is missing while there is no row index for the last row because the 4th and 6th rows of the original input are both empty. Within each row, the array/column index (i.e. the second column of indices) forms 0, 1, 2,

![](bbox=[0.116, 0.107, 0.883, 0.222])

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

The main Tensorflow library implements the tf.ragged module and the tf.RaggedTensor class [Abadi et al., 2023] to represent jagged tensors and allows various vectorizing operations. As we have seen previously, and will see
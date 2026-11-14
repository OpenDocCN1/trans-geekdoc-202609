```
import torch
values = torch.rand((2, 3, 4), dtype=float)
indices = torch.tensor([[3, 0]])
X = torch.zeros((5, 3, 4), dtype=float)
X = torch.index_add(X, 0, indices, values)
```

# ## 3.7 Case Study: Batchwise Scatter Values

As we have seen in Section 3.6, PyTorch implements a version of the scattering operation `torch.scatter` that is the reverse operation of its gather operation `torch.gather`. Tensorflow does not implement `tf.scatter` which allows batched application of scattering by flat indices. However, as we will see in one of the case studies in Chapter 9, batchwise scattering is often needed to implement group by aggregate logic.

Suppose we have the following data (see also Figure 3.20a),

```
import tensorflow as tf
index = tf.constant([
    [1, 3, 6, 2, 4],
    [2, 4, 8, 9, 5],
    [6, 5, 0, 1, 3],
    [3, 7, 2, 5, 4],
], dtype=tf.int64)
inputs = tf.constant([
    [2, 5, 6, 2, 8],
    [6, 1, 7, 0, 4],
    [9, 5, 4, 5, 1],
    [0, 6, 8, 3, 7],
])
```

Figure 30 A step-by-step illustration of the batchwise scattering process using flat indices. We assume the rows are the batch dimension. The first column of matrices is the values whereas the second column of matrices stores the flat indices at the corresponding location. The third column of matrices is the targets, where the numbers in the parentheses are the flat indices. Assuming the tiles only with parenthesized indices are filled with 0 values. (a). Initial set up; (b). Results obtained from the first value (row=0, col=0); (c). Results obtained from the second value (row=0, col=3); (d). Results obtained from the first value of the second row (row=1, col=2); (e). Full results when all steps are completed.
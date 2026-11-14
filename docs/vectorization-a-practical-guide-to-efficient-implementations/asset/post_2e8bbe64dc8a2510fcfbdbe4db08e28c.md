
for n in range(n_items):
    for m in range(n_items):
        if m >= n: # only compute the pair once
            continue

    x, y = set(mat_index[n]), set(mat_index[m])
    sim_loop[n, m] = len(x.intersection(y)) / len(x.union(y))

assert np.allclose(np.tril(sim.A, -1), sim_loop)

## 8.4 Case Study: Batchwise Set Operations

Set operations can be useful for efficiently computing multi-class and multi-label classification metrics. To motivate the current case study, let us consider a typical classification metric, precision, which is defined as

Precision = \frac{\#TruePositive}{\#TruePositive + \#FalsePositive}

where #TruePositive is the number of elements in the intersection between the predicted positive classes and the labeled positive classes; #FalsePositive is the number of elements in the intersection between predicted positive class and negative labels. For binary classification and more generally, multi-class classification, there is only one true label class and one positive prediction for each example. In contrast, for multi-label classification tasks, there can be a variable number of labels and predictions for each example. One way to vectorize the computation of precision metric (or metrics alike) for a batch of examples is to represent the labels and predictions as one-hot as (for binary and multi-class classifications) or binary vectors (for multi-label classifications). In the following code block, let us illustrate an example of computing precision in a multi-label classification task using dense binary representations

```
import numpy as np
predictions = np.array([
    [False, True, True, False, False],
    [True, False, False, False, False],
    [False, False, False, True, True],
    [False, True, True, False, False],
])

labels = np.array([
    [False, True, True, False, False],
    [False, False, True, False, False],
    [False, True, False, True, False],
    [False, True, False, True, False],
])
```

# Compute true positives: prediction and label both need to
be True
tp = np.logical_and(predictions, labels)
tp = np.sum(tp, axis=1) # count
# Compute false positives: prediction is True, label is False
fp = np.logical_and(predictions, ~labels)
fp = np.sum(fp, axis=1) # count
# Compute precision
precision = tp / (tp + fp)
# array([1. , 0. , 0.5, 0.5])

The simple example contains only five classes. However, if the number of classes is large (say 5000), while the number of positive or label classes is small (e.g. 2 or 3), a dense representation such that may not be efficient. Alternatively, we can represent the predictions and labels as only the index of positive classes. Using the same example as above, we can represent the `predictions` and `labels` as

```
predictions = [[1, 2], [0], [3, 4], [1, 2]]
labels = [[1, 2], [2], [0, 3], [1, 3]]
```

It can be seen that `predictions` and `labels` are ragged arrays. Then, to compute precision, we can iterate one example at a time and use Python's `set.intersection` operation to compute true positives and `set.difference` to compute false positives, i.e.

```
precision = []
for pred, lab in zip(predictions, labels):
    # true positives
    tp = set(pred).intersection(set(lab))
    # false positives
    fp = set(pred).difference(set(lab))
    # precision
    p = len(tp) / (len(tp) + len(fp))
    precision.append(p)
# [1.0, 0.0, 0.5, 0.5]
```

But, as we have known since Chapter 1, this can be slow if there are more examples to compute the metric on. How can we vectorize this and compute precision without for-loops? Tensorflow implements the tf.sets module for set operations, where it uses either a dense tf.Tensor or a tf.SparseTensor to represent the set. We can vectorize the above as

```
import tensorflow as tf
# Create the left-aligned ragged sparse tensors
predictions = tf.ragged.constant([[1, 2], [0], [3, 4], [1, 2]]).to_sparse()
labels = tf.ragged.constant([[1, 2], [2], [0, 3], [1, 3]]).to_sparse()
# Compute true positives
tp = tf.sets.intersection(predictions, labels)
tp = tf.sets.size(tp) # count each row
# Compute false positives
fp = tf.sets.difference(predictions, labels)
fp = tf.sets.size(fp) # count each row
# Compute precision
precision = tp / (tp + fp)
# <tf.Tensor: shape=(4,), dtype=float64, numpy=array([1. , 0. , 0.5, 0.5])>
```

To the best of my knowledge, at the time of writing, Tensorflow is the only library that implements batch vectorized set operations. Although PyTorch and Scipy (NumPy) have sparse tensor representations, they do not implement equivalent vectorized set operations like Tensorflow. Operations under the tf.sets module can not only deal with numerical data but also string data, which makes the use of these operations quite convenient when dealing with the evaluation of texts. The following code block illustrates how we can implement batchwise set operations using NumPy and scipy.sparse.

```
import numpy as np
from scipy.sparse import csr_matrix

def set_operation(x, y, pad=None, operation="intersection",
    returns="count"):
    """
    Batch-wise set operations.

    Inputs:
    * x, y: dense 2D np.ndarrays with/without padding values.
    * pad: padding values. Default to None which is no padding.
    * operation: set operation to perform. Valid values are
    ["intersection" (default), "union", "difference"].
    * returns: type of returned outputs, either "count" (default) which
    counts the cardinality of the resulting set operation for each
    row or "matrix" which returns the sparse matrix output from
    the set operations, all values are left aligned.
    """
    # Input shapes
    n_d, m_x = x.shape
    n_d, m_y = y.shape

    # Use np.unique to convert from data -> indices
    # This can appropriately handle all data types, including strings
    unique, indices = np.unique(np.hstack((x, y)), return_inverse=True)
    n_unique = len(unique)

    # From flattened index -> original shape
    indices = indices.reshape(n_d, -1)
    indices_x = indices[:, :m_x]
    indices_y = indices[:, m_x:]

    # which index from unique is the padding of the ragged representation
    pad_index = np.where(unique == pad)[0]
    if len(pad_index) > 0: # found padding
        pad_index = pad_index[0]
    else:
        pad_index = -1

    # Use csr format to create to create binary indicator matrices
    # e.g. index = [1, 3], n_unique = 5 -> [0, 1, 0, 1, 0]
    def _create_csr_indicator(indices, m):
        # create csr
        indptr = np.repeat([m], n_d).cumsum()
        indices = np.concatenate(([0], indptr))
        indices = indices.ravel() # flattened
        data = np.ones_like(indices, dtype=int)
        data[indices == pad_index] = 0 # filter out pad index
        sparse_matrix = csr_matrix(
            (data, indices, indptr), shape=(n_d, n_unique), dtype=int
        )
        # eliminate padding if any
        sparse_matrix.eliminate_zeros()
        return sparse_matrix

    x_hat = _create_csr_indicator(indices_x, m_x)
    y_hat = _create_csr_indicator(indices_y, m_y)

    # set operations using binary arithmetic operation
    if operation == "intersection":
        res = x_hat.multiply(y_hat)
    elif operation == "union":
        res = x_hat + y_hat
        res.data = np.minimum(res.data, 1)
    elif operation == "difference":
        res = x_hat - y_hat
        res.data = np.maximum(res.data, 0)
    else:
        raise ValueError(f"Unrecognized operation {operation}")

    if returns == "count": # return cardinality of set
        return res.sum(axis=1).A.ravel()
    else: # return the actual sparse matrix
        # keep only entries of 1s
        res.eliminate_zeros()
        # replace the indicator back to actual intersected values
        res.data = np.take(unique, res.indices)
        # left align
        l = np.diff(res.indptr) # array lengths
        flat_indices = np.arange(len(res.data))
        offsets = np.repeat(res.indptr[:-1], l)
        res.indices = flat_indices - offsets

        return res
```

- Lines 20 and 21 store the shapes of the inputs which will be used later.
- Line 25 uses np.unique to create the unique vector, which is the set of vocabularies used by both inputs x and y. Recall in Chapter 6 when we used np.unique in a case study to transform string values to integer values, this vector can be seen as the mapping between the original value and the integer representation of the values (corresponding to the indices 0, 1, 2, ...). On the other hand, indices is the set of indices that can be used to recover the original (but flattened) inputs when used together with unique, i.e. unique[indices] = <flattened_inputs>. Note that the use of np.unique allows us to handle both integer and string inputs.
- Line 26 finds the overall vocabulary size of the input values from both x and y, which will be later on by the function _create_csr_indicator.
- Lines 29-31 first reshapes the flattened indices of values from x and y, so that it recovers the shape of the original horizontally stacked matrix hstack((x, y)). Then, it splits the horizontally stacked matrix to recover the respective reverse indices which can recover the original inputs.
- Lines 34-38 attempt to find the index of the padding values from the unique vocabulary vector, using np.where. If we cannot find the padding value from the unique vocabulary vector, then we assume there is no padding. pad_index will be set to -1 which would bypass the padding value filtering steps when it is being used in the subsequent helper function _create_csr_indicator.
- Lines 42-54 is a helper function under the main function to create sparse binary indicator representations of the original input matrices of indices. We can do this efficiently since we assume that we are working with indices of a dense input matrix. Note that it reuses several parameters under the scope of the main function including n_d (batch size), n_unique (vocabulary size of the input value), and pad_index. Figure 8.5 illustrates the process of creating the sparse csr_matrix.
- Lines 44 and 45 create the indptr of the csr_matrix. Since we are creating indptr for a dense matrix, each row has an identical number

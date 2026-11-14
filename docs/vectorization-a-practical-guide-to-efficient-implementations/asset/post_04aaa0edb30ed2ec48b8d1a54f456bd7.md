
```python
Convert sparse tensor of indices to vectors of binary indicators

* X: tf.SparseTensor
  Each row of the sparse matrix is the indices of the indicator
  vector
    vocab_size: int
    This determines the size of the sparse indicator vector
* out_dtype: tf.dtypes.DType
    DType of the values of the output tensor
"""
# create indices of the output sparse tensor
indices = tf.stack([X.indices[:, 0], tf.cast(X.values, tf.int64)])
indices = tf.transpose(indices)
# indicator as ones
values = tf.ones_like(X.values)
values = tf.cast(values, out_dtype)
# (batch_size, vocab_size)
dense_shape = (tf.shape(X)[0], vocab_size)

# Make the sparse tensor
y = tf.SparseTensor(
    indices=indices,
    values=values,
    dense_shape=dense_shape
)
y = tf.sparse.reorder(y)

return y
```

- Lines 19 and 20 create the indices (row and column) of the sparse matrix where the True (dense) values will occupy.
- Lines 22 and 23 create the dummy values of 1s used to occupy the True/dense entries in the sparse matrix. Here, we can dynamically change the dtype of the output sparse matrix, which we currently default to `tf.float32`.
- Line 25 determines the shape of the sparse matrix. The `batch_size` or number of rows can be determined from the original input matrix. The number of columns is specified by `vocab_size`.
- Lines 28–32 create the binary indicator sparse matrix.
- Line 33 makes sure the indices of the new sparse tensor are sorted in ascending order, such that it can be used in subsequent operations such as `tf.sparse.to_dense`.

Figure 8.3 illustrates the process of creating the sparse representation of indicators as well. A similar implementation can be achieved using NumPy with Scipy `coo_matrix`.

![](img/e891acaacd4fb5b80dab2ed824618203_292_0.png)

Figure 8.3 Example illustration of converting a set of variable-length lists of indices to a stack of sparse binary representations. The values in the left-aligned sparse tensor (left) represent several lists of indices for a variable that contains five categories. The same data can be represented by a sparse binary tensor (right) whose values are 1 at those indices.

```python
import numpy as np
from scipy.sparse import coo_matrix

def sparse_to_indicator_scipy(X, vocab_size, out_dtype=np.float32):
    """
    Convert sparse tensor of indices to vectors of binary indicators

    * X:
        Each row of the scipy sparse matrix is the indices of the
        indicator vector
    * vocab_size:
        This determines the size of the sparse indicator vector
    * out_dtype:
        DType of the values of the output tensor
    """

    X = coo_matrix(X) # cast to coo_matrix
    # configure the sparse matrix
    row = np.array(X.row)
    col = np.array(X.col, dtype=row.dtype)
    data = np.ones_like(col)
    shape = (X.shape[0], vocab_size)
    # make the sparse matrix
    y = coo_matrix((data, (row, col)), shape=shape, dtype=out_dtype)

    return y
```

## 8.3 Case Study: Jaccard Similarities Using Sparse Matrix

The Jaccard Similarity metric can be useful when comparing how similar two objects are given their categorical attributes. For example, we can use the Jaccard Similarity score to compare how similar two movies are. If the two movies have many overlapping attributes such as genres and tags, then the movies are similar and should have a high similarity score; otherwise, the movies are different and should have a low similarity score. Jaccard Similarity is defined as

$$
\text{Sim}_{\text{Jaccard}}(X, Y) = \frac{|X \cap Y|}{|X \cup Y|} = \frac{|X \cap Y|}{|X| + |Y| - |X \cap Y|}
\tag{8.1}
$$

where $|\cdot|$ represents the cardinality of the set. In the context of evaluating the performance of object detection algorithms, the Jaccard Similarity metric is also known as the Intersection-Over-Union (IOU) metric. In IOU, X and Y are coordinates of the pixels within the bounding boxes drawn around the object, either by the algorithm prediction or by the label. Jaccard Similarity metric can also be used to search for similar items. In the case where we have a library of movies and each movie's metadata (e.g. tags and genres), we can compute the Jaccard Similarity score between each pair of movies, store the results in a matrix, and then look up the scores to rank the contents whenever a user searches for similar contents to a given title. To build such a matrix, we need to use the knowledge we have gained from Chapter 6 on encoding string values to index representations, and from the previous case study on converting index representations to binary indicator representations. The following code block implements the pairwise computation of Jaccard Similarity given a sparse binary representation of the item attributes, where we assume each item is a row of the sparse matrix, and each value along the column is an attribute of the content.

```python
import numpy as np

def jaccard_similarities(mat):
    """
    Compute pairwise Jaccard similarities
    between rows of a coo sparse matrix
    """
    nnz = mat.getnnz(axis=1)
    # pair-wise binary intersection |X n Y|
    # sparse matrix multiplication
    sim = mat * mat.T
    sim = sim.astype(float)

    # for rows
    xx = np.repeat(nnz, sim.getnnz(axis=1))
    # for columns
    yy = nnz[sim.indices]

    # |X U Y| = |X| + |Y| - |X n Y|
    sim.data /= xx + yy - sim.data

    return sim
```

![](img/e891acaacd4fb5b80dab2ed824618203_294_0.png)

![](img/e891acaacd4fb5b80dab2ed824618203_294_1.png)

![](img/e891acaacd4fb5b80dab2ed824618203_294_2.png)

**Figure 8.4** Illustration of the logic to compute pair-wise Jaccard Similarity scores between rows of a sparse matrix of attributes. (a) Pair-wise binary intersection between rows of the sparse matrix is computed by performing sparse matrix multiplication with its transpose. (b) Broadcasting the cardinality of the first set along rows by using the repeat operation. (c) Broadcasting the cardinality of the second set along columns by using the repeat operation. Once we obtained all 3 matrices, we can apply the Jaccard Similarity formula to compute the final pair-wise distances.

- Line 8 counts the number of attributes for each item.
- Lines 11 and 12 use sparse matrix multiplication to perform pair-wise binary intersection between rows of the input. See Figure 8.4 for an illustration.
- Line 15 computes the flattened cardinality of first set |X| corresponding to each entry of the similarity matrix, i.e. sim.data. This is the same as broadcasting the nnz vector along the column dimension (axis=1) and then flattening the broadcasted matrix, except that we also skip the entries where there is no intersection (empty entries of the sim matrix). This is achieved by repeating nnz for each row by however many elements each row has. See Figure 8.4b for a schematic illustration.
- Line 17 computes the cardinality of the second set |Y| corresponding to each entry of the similarity matrix, i.e. sim.data. This is the same as broadcasting the nnz vector along the row dimension (axis=0) and then flattening the broadcasted matrix, except that we need to skip the entries where there is no intersection. This is achieved by taking elements from nnz at the corresponding column indices of each data entry in sim. See Figure 8.4c for a schematic illustration.
- Line 20 implements the final Jaccard Similarity formula in Equation 8.1. sim.data is the intersection, whereas xx and yy are |X| and |Y|, respectively.

We can test our implementation using the following example:

```python
import numpy as np
from scipy.sparse import coo_matrix

mat_dense = np.array([
    [1, 0, 0, 1, 0,],
    [0, 1, 0, 1, 0,],
    [1, 0, 1, 1, 0,],
    [1, 1, 1, 1, 1,],
    [0, 1, 1, 1, 0,],
    [1, 0, 1, 0, 1],
])

mat = coo_matrix(mat_dense)
# Use our implementation
sim = jaccard_similarities(mat)

# Using for loop and Python native set operations
# Convert binary to indices
mat_index = []
for row in mat_dense:
    indices = np.where(row>0)[0].tolist()
    mat_index.append(indices)
n_items = len(mat_index)

# use set operations to compute jaccard similarity
sim_loop = np.zeros((n_items, n_items))
```

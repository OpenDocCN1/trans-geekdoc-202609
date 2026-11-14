or via the operation dense_to_csr_sparse_matrix

```
```python
# needs the indices of the non-missing values
csr_sparse = sparse_csr_matrix_ops.dense_to_csr_sparse_matrix(
    X, indices=tf.where(X > 0)
)
```
```

To convert from csr to coo, use

```
```python
# Convert from csr to coo
coo_sparse = sparse_csr_matrix_ops.csr_sparse_matrix_to_sparse_tensor(
    csr_sparse, type=tf.float32,
)
# Casting to Sparse Tensor class instead of intermediate
# representation
coo_sparse = tf.SparseTensor(
    coo_sparse.indices, coo_sparse.values, coo_sparse.dense_shape
)
```
```

To convert from coo back into csr matrix, use

```
```python
# Convert from coo to csr
csr_from_coo = sparse_csr_matrix_ops.sparse_tensor_to_csr_sparse_matrix(
    coo_sparse.indices, coo_sparse.values, coo_sparse.dense_shape
)
```
```

This can also be done by directly constructing from the CSRSparseMatrix class [Abadi et al., 2023b],

```
```python
csr_from_coo = sparse_csr_matrix_ops.CSRSparseMatrix(coo_sparse)
```
```

tf.SparseTensor can perform a multiplication between a sparse and a dense tensor using tf.sparse.sparse_dense_matmul. Like tf.SparseTensor, CSRSparseTensor also has an operation sparse_matrix_mat_mul [Abadi et al., 2023a] to multiply a dense vector with the sparse matrix:

```
```python
b_mat = tf.constant([[0, 1, 2, 4, 1]], tf.float32)
w = sparse_csr_matrix_ops.sparse_matrix_mat_mul(
    csr_sparse,
    b_mat,
    transpose_b=True,
)
```
```
```
((0, 2, 0, 1),
(1, 0, 1, 0),
(1, 1, 1, 1),
]
# one array for each dimension
multi_indices = np.array(coordinates).T.tolist()
shape = [2, 3, 3, 2]

# C-order
r_flat_index = np.ravel_multi_index(
    multi_indices, dims=shape, order="C"
)
print(np.concatenate([r_flat_index[:, None], coordinates], axis=1))
# [ [8 0 0 1 0]
# [13 0 2 0 1]
# [20 1 0 1 0]
# [27 1 1 1 1]]

# F-order
c_flat_index = np.ravel_multi_index(
    multi_indices, dims=shape, order="F"
)
print(np.concatenate([c_flat_index[:, None], coordinates], axis=1))
# [ [8 0 0 1 0]
# [22 0 2 0 1]
# [ 7 1 0 1 0]
# [27 1 1 1 1]]
```

We may discover the pattern of conversion like the following:

$$r_j = \sum_d i_d^{(j)} n_d$$ (3.2)

where $n_{d<D-1} = \prod_{i=d+1}^{D-1} n_i, n_{D-1} = 1$ when using row-major ("C") ordering, and $n_{d>0} = \prod_{i=0}^{d-1} n_i, n_0 = 1$ when using column-major ("F") ordering; this is identical to the previous definition in Equation 3.1. We can implement our findings as the following:

```
def sub2ind(multi_index, shape, order="C"):
    """Convert multi-index to flat index."""
    if order == "C": # row-major
        eta = np.cumprod(shape[1:][::-1])
        eta = np.concatenate([[1], eta])[::-1]
    elif order == "F": # column-major
```
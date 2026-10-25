```
sparsity = 1.0 - count_nonzero(A) / A.size
```

Listing 12.3: Example of the manual sparsity calculation.

The example below demonstrates how to calculate the sparsity of an array.

```
# sparsity calculation
from numpy import array
from numpy import count_nonzero
# create dense matrix
A = array([
    [1, 0, 0, 1, 0, 0],
    [0, 0, 2, 0, 0, 1],
    [0, 0, 0, 2, 0, 0]])
print(A)
# calculate sparsity
sparsity = 1.0 - count_nonzero(A) / A.size
print(sparsity)
```

Listing 12.4: Example of calculating sparsity.

Running the example first prints the defined sparse matrix followed by the sparsity of the matrix.

```
[[1 0 0 1 0 0]
 [0 0 2 0 0 1]
 [0 0 0 2 0 0]]
0.7222222222222222
```

Listing 12.5: Sample output from calculating sparsity.

# 12.7 Extensions

This section lists some ideas for extending the tutorial that you may wish to explore.

+   • Develop your own examples for converting a dense array to sparse and calculating sparsity.
+   • Develop an example for the each sparse matrix representation method supported by SciPy.
+   • Select one sparsity representation method and implement it yourself from scratch.

If you explore any of these extensions, I'd love to know.

# 12.8 Further Reading

This section provides more resources on the topic if you are looking to go deeper.
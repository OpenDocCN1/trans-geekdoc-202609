Note, your specific results may vary given differences in floating point precision on different hardware and software versions. Matrix inversion is used as an operation in solving systems of equations framed as matrix equations where we are interested in finding vectors of unknowns. A good example is in finding the vector of coefficient values in linear regression.

# 11.4 Trace

A trace of a square matrix is the sum of the values on the main diagonal of the matrix (top-left to bottom-right).

The trace operator gives the sum of all of the diagonal entries of a matrix

> — Page 46, Deep Learning, 2016.

The operation of calculating a trace on a square matrix is described using the notation tr(A) where A is the square matrix on which the operation is being performed.

```
tr(A)
```

The trace is calculated as the sum of the diagonal values; for example, in the case of a 3 x 3 matrix:

```
tr(A) = a_{1,1} + a_{2,2} + a_{3,3}
```

Or, using array notation:

```
tr(A) = A[0,0] + A[1,1] + A[2,2]
```

We can calculate the trace of a matrix in NumPy using the trace() function.

```
# matrix trace
from numpy import array
from numpy import trace
# define matrix
A = array([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]])
print(A)
# calculate trace
B = trace(A)
print(B)
```

Listing 11.5: Example of creating the trace of a matrix.

First, a 3 x 3 matrix is created and then the trace is calculated. Running the example, first the array is printed and then the trace.

```
[[1 2 3]
 [4 5 6]
 [7 8 9]]
15
```

Listing 11.6: Sample output from creating the trace of a matrix.
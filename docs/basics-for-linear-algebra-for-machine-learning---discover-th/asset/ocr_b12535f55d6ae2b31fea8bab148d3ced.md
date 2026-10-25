We can achieve this by creating a new \(\Sigma\) matrix of all zero values that is \(m \times n\) (e.g. more rows) and populate the first \(n \times n\) part of the matrix with the square diagonal matrix calculated via `diag()`.

```
# reconstruct rectangular matrix from svd
from numpy import array
from numpy import diag
from numpy import zeros
from scipy.linalg import svd
# define matrix
A = array([
    [1, 2],
    [3, 4],
    [5, 6]])
print(A)
# factorize
U, s, V = svd(A)
# create m x n Sigma matrix
Sigma = zeros((A.shape[0], A.shape[1]))
# populate Sigma with n x n diagonal matrix
Sigma[:A.shape[1], :A.shape[1]] = diag(s)
# reconstruct matrix
B = U.dot(Sigma.dot(V))
print(B)
```

Listing 16.3: Example of reconstructing a rectangular matrix from a SVD.

Running the example first prints the original matrix, then the matrix reconstructed from the SVD elements.

```
[[1 2]
 [3 4]
 [5 6]]

[[ 1.  2.]
 [ 3.  4.]
 [ 5.  6.]]
```

Listing 16.4: Sample output from reconstructing a rectangular matrix from a SVD.

The above complication with the \(\Sigma\) diagonal only exists with the case where \(m\) and \(n\) are not equal. The diagonal matrix can be used directly when reconstructing a square matrix, as follows.

```
# reconstruct square matrix from svd
from numpy import array
from numpy import diag
from scipy.linalg import svd
# define matrix
A = array([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]])
print(A)
# factorize
U, s, V = svd(A)
# create n x n Sigma matrix
```
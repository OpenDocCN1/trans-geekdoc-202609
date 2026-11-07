
Symmetric matrices are of fundamental importance in linear algebra and by consequence also form a group of matrices of significant importance in statistics. A symmetric matrix is one for which the *transpose of the matrix is equal to the original matrix*. That is, a symmetric matrix is one for which `A` = `A`^(`T`). Symmetric matrices feature many desirable properties, including the fact that the inverse of a symmetric matrix is also symmetric. Further, if a matrix is not symmetric, there is no guarantee that its eigenvectors will be orthogonal. Hence, when we speak of eigenvectors in general being orthogonal in the context of this book, it is usually implied that we are working with a symmetric matrix.

Two very important classes of symmetric matrices in statistics are those of *covariance* and *correlation* matrices, discussed earlier in our survey of essential probability and statistics.

### 2.37.4 Matrix Addition and Multiplication

For any two matrices of the same dimension, as was the case for vectors, we add and subtract matrices element by element. Consider the following two matrices, `A` and `B`, each of dimension `m` × `n`:

$$A = \\left\\lbrack \\begin{array}{l} {a\_{11}\\,\\,\\,\\,\\, a\_{12}\\,\\,\\,\\,\\, \\cdot \\cdot \\cdot \\,\\,\\,\\,\\, a\_{1n}} \\\\ {a\_{21}\\,\\,\\,\\,\\, a\_{22}\\,\\,\\,\\,\\, \\cdot \\cdot \\cdot \\,\\,\\,\\,\\, a\_{2n}} \\\\ {\\,\\, \\cdot \\,\\,\\,\\,\\,\\,\\,\\,\\,\\, \\cdot \\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, \\cdot} \\\\ {a\_{m1}\\,\\,\\,\\,\\, a\_{m2}\\,\\,\\,\\, \\cdot \\cdot \\cdot \\,\\,\\,\\, a\_{mn}} \\\\ \\end{array} \\right\\rbrack\\,\\,\\,\\,\\, B = \\left\\lbrack \\begin{array}{l} {b\_{11}\\,\\,\\,\\,\\, b\_{12}\\,\\,\\,\\,\\, \\cdot \\cdot \\cdot \\,\\,\\,\\,\\, b\_{1n}} \\\\ {b\_{21}\\,\\,\\,\\,\\, b\_{22}\\,\\,\\,\\,\\, \\cdot \\cdot \\cdot \\,\\,\\,\\,\\, b\_{2n}} \\\\ {\\,\\, \\cdot \\,\\,\\,\\,\\,\\,\\,\\,\\,\\, \\cdot \\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, \\cdot} \\\\ {b\_{m1}\\,\\,\\,\\,\\, b\_{m2}\\,\\,\\,\\, \\cdot \\cdot \\cdot \\,\\,\\,\\, b\_{mn}} \\\\ \\end{array} \\right\\rbrack\\,$$

The addition of matrices `A` and `B` occurs element by element:130

$$A + B = \\left\\lbrack \\begin{array}{l} {a\_{11} + b\_{11}\\,\\,\\,\\,\\, a\_{12} + b\_{12}\\,\\,\\,\\,\\, \\cdot \\cdot \\cdot \\,\\,\\,\\,\\, a\_{1n} + b\_{1n}} \\\\ {a\_{21} + b\_{21}\\,\\,\\,\\,\\, a\_{22} + b\_{22}\\,\\,\\,\\,\\, \\cdot \\cdot \\cdot \\,\\,\\,\\,\\, a\_{2n} + b\_{2n}} \\\\ {\\,\\, \\cdot \\,\\,\\,\\,\\,\\,\\,\\,\\,\\, \\cdot \\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, \\cdot} \\\\ {a\_{m1} + b\_{m1}\\,\\,\\,\\,\\, a\_{m2} + b\_{m2}\\,\\,\\,\\, \\cdot \\cdot \\cdot \\,\\,\\,\\, a\_{mn} + b\_{mn}} \\\\ \\end{array} \\right\\rbrack$$

Note that matrix addition is *commutative*, such that `A` + `B` = `B` + `A`. Note that this parallels scalar algebra in which for two numbers `a` + `b` = `b` + `a`. It is also associative, which means for matrices `A`, `B`, `C`, (`A`+`B`) + `C` = `A` + (`B`+`C`).

We add matrices in Python as follows:

```
a
Out[330]:
array([[1, 2, 3],
  [4, 5, 6]])
b
Out[331]:
array([[1, 2, 3],
  [4, 5, 6]])
a + b
Out[332]:
array([[ 2, 4, 6],
  [ 8, 10, 12]])
```

To multiply matrices `A` `B`, we compute along the first row and down the first column, then the first row, second column, etc., then the second row, first column, then the second row, second column, and so on, as the following example illustrates ([Fox, 2016](#ref.xhtml#re_CIT000106)):

$$\\begin{array}{l} {\\left\\lbrack \\begin{array}{lll} & \\Rightarrow & \\\\ 1 & 2 & 3 \\\\ 4 & 5 & 6 \\\\ \\end{array} \\right\\rbrack\\left\\lbrack \\begin{array}{llll} & 1 & 0 & 0 \\\\ \\Downarrow & 0 & 1 & 0 \\\\ & 0 & 0 & 1 \\\\ \\end{array} \\right\\rbrack} \\\\ {\\,\\,\\,\\,\\,\\,\\left( {2 \\times 3} \\right)\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\left( {3 \\times 3} \\right)} \\\\ {\\,\\,\\,\\,\\,\\,\\,\\, = \\left\\lbrack \\begin{array}{lll} {1\\left\\lbrack 1 \\right\\rbrack + 2\\left\\lbrack 0 \\right\\rbrack + 3\\left\\lbrack 0 \\right\\rbrack,} & {1\\left\\lbrack 0 \\right\\rbrack + 2\\left\\lbrack 1 \\right\\rbrack + 3\\left\\lbrack 0 \\right\\rbrack,} & {1\\left\\lbrack 0 \\right\\rbrack + 2\\left\\lbrack 0 \\right\\rbrack + 3\\left\\lbrack 1 \\right\\rbrack} \\\\ {4\\left\\lbrack 1 \\right\\rbrack + 5\\left\\lbrack 0 \\right\\rbrack + 6\\left\\lbrack 0 \\right\\rbrack} & {4\\left\\lbrack 0 \\right\\rbrack + 5\\left\\lbrack 1 \\right\\rbrack + 6\\left\\lbrack 0 \\right\\rbrack} & {4\\left\\lbrack 0 \\right\\rbrack + 5\\left\\lbrack 0 \\right\\rbrack + 6\\left\\lbrack 1 \\right\\rbrack} \\\\ \\end{array} \\right\\rbrack} \\\\ {\\,\\,\\,\\,\\,\\,\\,\\, = \\left\\lbrack \\begin{array}{lll} 1 & 2 & 3 \\\\ 4 & 5 & 6 \\\\ \\end{array} \\right\\rbrack} \\\\ \\end{array}$$

Recall that in scalar multiplication in basic algebra, `a` ⋅ `b` yields the same product as `b` ⋅ `a`. With matrices, however, `A` `B` does not, in most circumstances, equal `B` `A`. That is, `A` `B` ≠ `B` `A`, which means contrary to scalar addition and subtraction, *matrix multiplication is generally not commutative*. That is, multiplication for matrices is *noncommutative*. What is more, not just any two matrices can be multiplied. For matrices to be conformable for multiplication, the number of *columns* in the first (left) matrix must equal the number of *rows* in the second (right) matrix. For intuition as to why matrix multiplication is the way it is, see [Fox (2016)](#ref.xhtml#re_CIT000106).

### 2.37.5 Meaning of Matrices: Matrices as Data and Transformations

First and foremost, matrices are mathematical objects in and of themselves. The mathematical treatment of matrices is actually quite recent, having their modern origin in the 1800s. When you think about this, realize that in the history of mathematics this is almost like saying that the modern concept of matrices was invented *yesterday* since the history of mathematics is so vast. In pure 131mathematics, matrices are studied for their own sake. It may be challenging for the applied reader to appreciate how one can study them for their own purpose, but this is exactly what motivates pure mathematicians (and philosophers): the study of abstract (but far from arbitrary) objects.

In a more applied context, matrices are generally used to denote two ideas. The first is that of a *transformation*; the second is that of *data*. The transformation idea is closer to pure linear algebra, while the data idea is closer to statistics. In fact, it can be shown that any matrix corresponds to a linear transformation such that

`T`(`v`) = `A` `v`

(2.97)

where `T` is a mapping from ℝ^(`n`) to ℝ^(`m`), `v` is a vector, and `A` is a matrix. The above reads that a linear transformation on the vector `v` is equivalent to pre-multiplying that vector by the matrix `A`. In the simpler case where `v`, in theory, is not a vector but instead a scalar `b` (or simply a vector with a single element), then we would have,

`T`(`b`) = `A` `b`

which as was the case for vectors, communicates that in order to (linearly) transform the scalar `b` we multiply it by the matrix `A`. If `A` is a very simple matrix, say of one element such that we can simply call it a scalar as well, then the above reduces to

`T`(`b`) = `a` `b`

That is, to linearly transform `b`, we multiply it by the scalar `a`.

To appreciate the second interpretation, that of a matrix as a *data matrix*, consider the following matrix, `A`:

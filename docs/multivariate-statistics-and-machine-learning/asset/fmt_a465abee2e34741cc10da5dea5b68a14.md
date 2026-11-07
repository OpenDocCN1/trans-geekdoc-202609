
It is less than full rank because the second column is simply a scalar multiple of the first. That is, the second column is exactly a factor of twice that of the first column. The rank of the matrix is 2 because there are only two linearly independent columns (and rows). Rank is also equal to the dimensionality of the largest submatrix `A` (i.e., deleting certain rows and columns) that has a nonzero determinant ([Izenman, 2008](#ref.xhtml#re_CIT000167)). In an applied sense, the rank of a matrix gives us a sense of how much information is “duplicated” in the matrix. A matrix of full rank tells us that each row (or column) is providing “unique” information. A matrix less than full rank tells us that there is, essentially, “overlap” in the matrix in terms of information. Though this is a nonrigorous way of conceiving rank, it is nonetheless helpful in grasping the concept in an applied sense.

As an example of computing the rank of a matrix in Python, we can use `numpy()`, where in the following the rank of the matrix is equal to 1:

```
np.ones(4)
Out[345]: array([1., 1., 1., 1.])
from numpy.linalg import matrix_rank
matrix_rank(np.ones(4))
Out[347]: 1
```

142

## 2.48 Orthogonal Matrices

Orthogonal matrices are those square matrices for which when we multiply by its transpose, we obtain the identity matrix. As an example, `X X^T = I = X^T X` implies that `X` is an orthogonal matrix. If `X^2 = X`, the matrix is regarded as *idempotent* ([Izenman, 2008](#ref.xhtml#re_CIT000167)). For vectors, we can more simply define orthogonality as when the inner product `x y = 0`. Orthogonality also implies perpendicularity, which is expressed by `x⊥y`. *Orthonormal* vectors are orthogonal and have length equal to 1; hence if `x` is orthonormal to some vector, then it stands that `||x||=1`.

## 2.49 Kernels, the Kernel Trick, and Dual Representations

Kernels play a significant role in machine learning and we see them in techniques such as *neural networks* and *support vector* *machines* (SVMs). Indeed, the “kernel trick” is something that quickly becomes common territory as one studies machine learning. In general, *kernel functions* (as distinct from the kernels featured earlier in relation to matrices) are used to define *similarity* between data objects. Kernels of inner products are often taken to determine the similarity of input data so that a linear classifier can be used to solve what is essentially a nonlinear problem. In support vector machines, the kernel trick was first introduced by Boser et al. ([1992](#ref.xhtml#re_CIT000041)).

Even though much of the emphasis of statistics is on linearity, nonlinear problems pervade scientific practice. Attempting to model such nonlinearity via polynomial transformations, for instance, or other *basis function transformations*, as we will see later, can be complex, timely, and computationally infeasible. By taking kernels of input data, however, what was originally linearly *inseparable* data now becomes *separable* without having to actually mathematically go to those higher dimensions. That is, the kernel trick will allow us to stay in 2-D, for instance, when the data are only separable, for example, in 3-D. Essentially, the *kernel trick* or *kernel substitution* ([Bishop, 2006](#ref.xhtml#re_CIT000032), p. 292) allows one to take an infinite-dimensional problem and reduce it to a finite dimensional problem ([Hastie et al., 2009](#ref.xhtml#re_CIT000145)).

The kernel function `k` is defined by

`k(x,x′) = k(x′,x) = ϕ(x)′ϕ(x′)`  

(2.110)

where the inner product `x, x′` is a measure of *similarity* between two vectors, and hence the kernel function is considered a measure of such “likeness” of data. That is, the kernel function essentially measures how similar observations are to one another. As shown in (2.110), the kernel function here is also symmetric such that `k(x,x′) = k(x′,x)`. Computations of `k(x,x′)` take place in the original data space, but equate to the inner product `ϕ(x)′ϕ(x′)` in the feature space.

Of the only key requirements of kernels is that they be *positive definite* as it can be shown that positive definite kernels induce an inner product in a Hilbert space ([Mohri, 2018](#ref.xhtml#re_CIT000253)). The reader may recall that positive definiteness ensures that the eigenvalues of `K`, the *kernel matrix* in this case, are (strictly) positive. What is more, *for a positive definite kernel, such will always produce (or “associate with”*) *a kernel matrix that is positive semidefinite* ([Mohri et al., 2018](#ref.xhtml#re_CIT000253), p .108). A variety of kernels exist, such as *polynomial kernels*, *Gaussian kernels*, *sigmoid kernels*, and others. Of importance to remember with regard to kernels is that they need not be actually computed as inner products in the original data space `x, x′` for them to imply an inner product `ϕ(x)′ϕ(x′)` in the feature space. *Many other kernels are possible that do not computationally and directly calculate the inner product in data space*. *What is important is that the kernel expresses a degree of similarity in the data space, such that it induces an inner product space in the feature space.*

To better illustrate the kernel trick, consider the data in [Figure 2.14](#c2.xhtml#f2.14) depicting two classes.143

![Figure 2.14 Data on two classes that are clearly not linearly separable.Return to text.⏎](images/fig2.14.jpg)

*Figure 2.14* Data on two classes that are clearly not linearly separable.[Return to text.⏎](#c2.xhtml#re_f2.14)

Of course, the data in [Figure 2.14](#c2.xhtml#f2.14) is not linearly separable; that is, we need a swishy curve to separate the two groups. By computing the *kernel* of the data however, *in its original dimensionality*, we essentially transform this nonlinearity into a linearly separable problem in the feature space. But why should this work? Why does the kernel trick do what it does?

The reason why the kernel trick works is related to *Mercer’s theorem* ([1909](#ref.xhtml#re_CIT000248)), which essentially yields the following very important result:

> *A kernel can be used to approximate a function when it is known that the function exists even if knowledge of what that function is, is incomplete or not known*.

That is, the kernel essentially contains a wealth of information even about higher dimensionalities for which we may be currently unaware. The fact that we can work on the problem in its original configuration or via a kernel is known as *dual representation* ([Bishop, 2006](#ref.xhtml#re_CIT000032)). In words, the so-called “kernel trick” essentially communicates the idea: *You’re working on a complicated problem in higher dimensions, you’re not possibly even aware of what those dimensions are, or even how many there might be, but if you compute the kernel in your existing lower-dimensional space you can learn a lot about those higher dimensions without ever having to go there* ***explicitly*** . By way of fictional analogy, the kernel might allow you to stay and compute in this 3-D spatial universe while potentially learning something about a different one (e.g., a universe possibly in five dimensions).

As stated earlier, the utility of kernels is based on the fact that many data sets that we work with are not linearly separable. *Applying a kernel (hopefully) makes the data linearly separable and also allows for a solution that is convex* ([Goodfellow et al., 2016](#ref.xhtml#re_CIT000131)). Convex solutions (as we will discuss later in more detail) are desirable because they have *global* minima and hence the algorithm will not get “stuck” in *local* minima. That is, an important implication of Mercer’s condition is that it establishes the convexity of the optimization problem for support vector machines and similar algorithms ([Mohri et al., 2018](#ref.xhtml#re_CIT000253)). Hence, a global minimum is assured in optimization.

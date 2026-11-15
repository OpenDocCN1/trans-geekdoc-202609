K(x, y) = (2*3 + 3*4 + 4*5) ^2=(6 + 12 + 20)^2=38*38=1444.

This as we find out, f(x).f(y) and K(x, y) give us the same result, but the former method required a lot of calculations(because of projecting 3 dimensions into 9 dimensions) while using the kernel, it was much easier.

# 3.3.6 Types of Kernel and Methods in SVM

Let us see some of the kernel function or the types that are being used in SVM:

+   1. **Liner Kernel:**- Let us say that we have two vectors with name x1 and Y1, then the linear kernel is defined by the dot product of these two vectors: K(x1, x2) = x1 . x2

+   2. **Polynomial Kernel:**- A polynomial kernel is defined by the following equation: K(x1, x2) = (x1 . x2 + 1)d, Where, d is the degree of the polynomial and x1 and x2 are vectors

+   3. **Gaussian Kernel:**- This kernel is an example of a radial basis function kernel. Below is the equation for this: k(xi,xj) = exp(-γ || xi - xj ||^2) The given sigma plays a very important role in the performance of the Gaussian kernel and should neither be overestimated and nor be underestimated, it should be carefully tuned according to the problem.

+   4. **Exponential Kernel:**- This is in close relation with the previous kernel i.e. the Gaussian kernel with the only difference is – the square of the norm is removed. The function of the exponential function is: k(x,y) = exp( - || x - y || / 2σ^2 ) This is also a radial basis kernel function.

+   5. **Laplacian Kernel:**- This type of kernel is less prone for changes and is totally equal to previously discussed exponential function kernel, the equation of Laplacian kernel is given as:
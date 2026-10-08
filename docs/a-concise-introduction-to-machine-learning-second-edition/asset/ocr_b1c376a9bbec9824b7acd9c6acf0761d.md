# Matern kernel $k(\mathbf{x,y}) = \frac{\sqrt{2
u}^{2
u}}{\Gamma(
u)l^{2
u-1}} K_{\nu}\left(\frac{\sqrt{2
u}}{l}\|\mathbf{x}-\mathbf{y}\|ight)$

where $l$ is again the length scale, $\Gamma(\cdot)$ is the gamma function and $K_{
u}$ is a modified Bessel function. The parameter $
u$ controls the smoothness. The smaller the $
u$, the smoother the function. For $
u = 3/2$, the kernel is once differentiable, and for $
u = 5/2$ it is twice differentiable. For $
u = 1/2$ the Matern kernel becomes:

# Exponential kernel $k(\mathbf{x,y}) = \exp\left(-\frac{\|\mathbf{x}-\mathbf{y}\|}{l}ight)$ which is not differentiable.

# Rational quadratic kernel $k(\mathbf{x,y}) = \left(1+\frac{\|\mathbf{x}-\mathbf{y}\|^2}{2l^2}ight)^{-\alpha}$ uses to be the length scale and $\alpha > 0$ a scale mixture parameter. For $\alpha = 1/2$, this kernel becomes:

# Inverse multiscale kernel $k(\mathbf{x,y}) = \left(1+\frac{\|\mathbf{x}-\mathbf{y}\|^2}{\ell^2}ight)^{-1/2}$.

All kernels also have a multiplicative parameter $	heta$ known as *standard deviation*.

As shown in Section 5.2, the sum, product or exponential of a kernel gives rise to another kernel. Applying a polynomial to a kernel is a kernel. Combinations can be built to suit the use case.

If the kernel contains a positive, additive constant, then the mean of the Gaussian process can be assumed to be zero, a positive bias corresponds to the constant basis function, also known as the *bias* being included in the model.

Listing 8.3 implements six kernel functions and illustrates how to generate draws from a Gaussian process with a given kernel. While a draw from a Gaussian process is a function, the latter generates densely spaced point values. These are draws from the distribution with the required covariance matrix, which is the Gram matrix $\mathbf{K}$ for the given points and kernels $\mathbf{x}_1,\dots,\mathbf{x}_n$. Cholesky factorization $\mathbf{K} = \mathbf{LL}^T$ is calculated. A vector $\mathbf{v}$ of length $n$ is drawn from the standard, multivariate normal distribution. We then draw from the distribution with covariance $\mathbf{K}$. The point values of $\mathbf{f}$ are plotted as functions. Figure 8.12 shows the results of four draws for each of the implemented kernels.

This conclusion of the section concludes the discussion of drawing a function from a Gaussian process. We now turn our attention to drawing a function from the posterior of a Gaussian process, once some pairs $(\mathbf{x}_1, f_1),\dots,(\mathbf{x}_n, f_n)$ have been seen. Let $\mathbf{x}_*$ be arbitrary and distinct from $\mathbf{x}_n$, $n=1,\dots,N$. Recall that the measurements we use have additive normally distributed noise with mean zero and variance $\sigma^2$, that is

$f_* = f(\mathbf{x}_*) + \epsilon_*$.
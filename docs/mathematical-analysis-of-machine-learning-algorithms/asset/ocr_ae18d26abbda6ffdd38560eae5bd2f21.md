Proposition 9.11 establishes a link of kernel methods and Gaussian processes. In the Gaussian process view of kernel methods, the function values defined on a discrete set of $n$ points $\{X_1,\ldots,X_n\}$ is a Gaussian $\mathbf{f}\sim\mathcal{N}(\mathbf{m},K_{n\times n})$, where $\mathbf{m}\in\mathbb{R}^n$ is the mean, and the kernel Gram matrix $K_{n\times n}$ is the covariance matrix. If the mean function is zero, then the density of the Gaussian is $\alpha\exp(-0.5\mathbf{f}^{\mathsf{T}}K_{n\times n}^{-1}\mathbf{f})$, which is closely related to Proposition 9.11. One can also extend Gaussian processes to infinitely many data points, with covariance of any two points given by the kernel function $k(x,x')$. For least squares regression, it can be shown that the posterior mean of the Gaussian process is equivalent to kernel ridge regression. For other loss functions, the inference may be different. Although Gaussian processes and kernel methods are closely related, one interesting fact is that samples from the Gaussian process corresponding to a kernel function $k(x,x')$ do not in general belong to the RKHS of the kernel function. Exercise 9.4 illustrates why this happens, and more discussions can be found in Neal (1998).

The RKHS representation in Proposition 9.11 can be directly used to obtain a semi-supervised formulation of kernel method, defined on both labeled and unlabeled data as follows.

**Corollary 9.12**  *Assume that we have labeled data $X_1,\ldots,X_n$, and unlabeled data $X_{n+1},\ldots,X_{n+m}$. Let $K=K_{(n+m)\times(n+m)}$ be the kernel Gram matrix of a kernel $k$ on these $m+n$ points, and let $\mathcal{H}$ be the corresponding RKHS. Then (9.10) defined on these data points is equivalent to*

$$\hat{f}(\cdot)=\underset{f\in\mathbb{R}^{n+m}}{\arg\min}\left[\frac{1}{n}\sum_{i=1}^{n}L(f(X_i),Y_i)+\frac{\lambda}{2}\mathbf{f}^{\mathsf{T}}K^{+}\mathbf{f}\right],\qquad \mathbf{f}=\begin{bmatrix}f(X_1)\\\vdots\\f(X_{n+m})\end{bmatrix}.$$

A drawback of kernel methods is that the computation requires the full kernel matrix $K_{n\times n}$, and thus it is at least quadratic in $n$. Moreover, the inference time is linear in $n$. Both are rather expensive if $n$ is large.

# 9.2 Universal Approximation

An important question for learning methods is whether the underlying function class (model family) can approximate all measurable functions. A function class that can represent all functions is called a *universal approximator*. Since the set of continuous functions is dense in the set of measurable functions, we only require that all continuous functions can be approximated by the RKHS of a kernel function. The approximation can be measured using different metrics. For simplicity, we consider uniform approximation here.

**Definition 9.13**  A kernel $k(x,x')$ is called a universal kernel on $\mathcal{X}\subset\mathbb{R}^d$ (under the uniform convergence topology) if for any continuous function $f(x)$ on $\mathcal{X}$, and any $\epsilon>0$, there exists $g(x)\in\mathcal{H}$ such that

$$\forall x\in\mathcal{X}:\ |f(x)-g(x)|\leq\epsilon,$$

where $\mathcal{H}$ is the RKHS of kernel $k(\cdot,\cdot)$.
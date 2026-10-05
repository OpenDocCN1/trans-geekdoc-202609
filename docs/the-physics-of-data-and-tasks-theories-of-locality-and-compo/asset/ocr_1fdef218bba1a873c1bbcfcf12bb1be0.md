# 3-4 GENERALIZATION PROPERTIES AND SPATIAL ADAPTIVITY

the decay of an eigenvalue with k is slower than the eigenfunction depends on a few adjacent patches – but not the patches are far apart! This is a property of hierarchical architectures that use nonlinear activation at all layers. Such a feature disappears if all hidden layers apart from the first polynomial [Bie22] or infinitely smooth [AM15; SH21] activation functions or if the kernels are assumed to factor over patches, as in Geifman [Ge+22].

# 3.4 GENERALIZATION PROPERTIES AND SPATIAL ADAPTIVITY

In this section, we study the implications of the peculiar spectra of hierarchical NTKs and RKFs on the generalization properties and prove of adaptivity to the spatial structure of the target function. We follow the classical analysis of Caponetto and De Vito [CD07] for kernel regression see Bach [Bac21] and Bietti [Bie22] for a modern treatment) and employ a spectral bias ansatz for the rideless limit [BCP20; SGW20].

# THEORY OF KERNEL RIDGE REGRESSION AND SOURCE-CAPACITY CONDITIONS

Given a P of training points $\{(x_i, y_i)\}_{i=1}^P$ $p(x)$ for some probability density function $p(x,y)$ and a regularization parameter $\lambda > 0$, the kernel ridge regression estimate of the network function between $x$ and $y's$, or predictor,

```
$f_{\lambda}^P(\mathbf{x}) = \argmin_{f \in \mathcal{H}} \sum_{i=1}^P (f(x_i) - y_i)^2 + \lambda ||f||_{\mathcal{H}}^2,\quad(56)$
```

$\mathcal{H}$ is the Reproducing Kernel Hilbert Space (RKHS) of a (hierarchical) kernel $\mathcal{K}$. If $f(x)$ denotes the model from which the kernel was obtained via Equation 52, the space $\mathcal{H}$ is contained in the span of the network functions $\{f_{	heta\}_p$ in the infinite-width limit. Alternatively, $\mathcal{H}$ can be defined via the kernel's eigenvalues $\Lambda_k$ and eigenfunctions $Y_k$; denoting by $f_k$ the projections of a function $f$ onto the eigenfunctions, $f$ belongs to $\mathcal{H}$ if it is the span of the eigenfunctions

```
$||f_{\lambda}^P||_{\mathcal{H}}^2 = \sum_{k \ge 0} (\Lambda_k)^{-1}|f_k|^2 < +infty.\quad(57)$
```

The performance of the kernel is measured by the generalization error and its expectation over training sets of size $P$ (denoted with $\mathcal{E}_P$)

```
$$\mathcal{E}(f_{\lambda}^P) = \int dx dy p(x,y) (f_{\lambda}^P(\mathbf{x}) - y)^2,\quad(58)$
```

```
$\mathcal{E}(\lambda, P) = \mathcal{E}_P [\mathcal{E}(f_{\lambda}^P)]$,
```

or the excess generalization error, obtained by subtracting from $\mathcal{E}(\lambda, P)$ the error of the optimal predictor $f^*(\mathbf{x}) = \int dy p(x,y)y$. The
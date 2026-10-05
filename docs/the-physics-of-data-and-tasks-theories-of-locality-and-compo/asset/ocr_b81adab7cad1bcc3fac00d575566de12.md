# APPENDIX: THE ROLE OF DEPTH AND SPATIAL ADAPTIVITY

$2s_2 = d$ and $s_1 = p$ (the number of 2-patches). Eigenvalues and eigenfunctions of $T_K$ can be organized into 2 sectors associated with the hidden layers of the kernel/network.

+   i. The first sector consists of local eigenfunctions, which are functions of a single patch $x_i$ for $i=1, \dots, p$. The labels $k_i, \ell$ of local eigenfunctions are such that all the $k_j$'s with $j 
eq i$ are zero (because the eigenfunction is outside $x_i$). The corresponding eigenvalue is degenerate with respect to the location of the patch: we call it $\Lambda_{k_i}$. When $k \to \infty$,

```
$\Lambda_k^{(1)} = C_{2,1} k^{2\ell-1} + o \left(k^{2\ell-1}\right)$,
```

with $v_{NTK} = 1/2, v_{FPK} = 3/2, C_{2,j}$ can take distinct positive values depending on the parity of $k_j$;

+   ii. The second sector consists of global eigenfunctions, which are functions of the whole input $x$. The labels $k, \ell$ of global eigenfunctions are such that at least two of the $k_j$'s are non-zero. We call the corresponding eigenvalue $\Lambda_k^{(2)}$. When $\|k\| \to \infty$, with $k = \|k\|$,

```
$\Lambda_k^{(2)} = C_{2,2} k^{2\ell-p} + o \left(k^{2\ell-p}\right)$,
```

Proof. If we consider binary patches in the first layer, the input space becomes the Cartesian product of two-dimensional unit spheres, i.e., $\mathcal{X} = \prod_{i=1}^p S^1$. Then each $x_i$ corresponds to an angle $	heta_i$ and the spherical harmonics are equivariant to Fourier atoms,

```
$Y_0(\theta_1) = 1, Y_{k_1}(	heta_1) = e^{ik\theta_1}, \quad k \geq 1$.
```

Therefore, solving the eigenvalue problem for a dot-product kernel $\mathcal{K}(x^T y) = \mathcal{K}(\theta_x, \theta_y)$ with $x, y \in S^1$ allows for computing its Fourier transform. With $[S]=2$ and $|S^1|=2\pi$,

```
$\frac{1}{2\pi} \int_{-\pi}^{\pi} d\theta_x \cos(\theta_x - \theta_y) e^{ik\theta_x} = \Lambda_k e^{ik\theta_y} \to \Lambda_k = \frac{1}{2\pi} \int_{-\pi}^{\pi} d\theta \cos(\theta) e^{ik\theta}$,
```

where we denote with $	heta$ the difference between the two angles. Similarly, for a multi-dot product kernel, the eigenvalues coincide with the $p$-dimensional Fourier transform of the kernel, with $p$ is the number of patches,

```
$\Lambda_k = \frac{1}{(2\pi)^p} \int_{-\pi}^{\pi} \left(\prod_{i=1}^p d\theta_i e^{ik\theta_i}\right) \mathcal{K} \left(\{\cos\theta_i\}_{i=1}^p\right) \n = \frac{1}{(2\pi)^p} \int_{-\pi}^{\pi} d^p\theta e^{ik\theta} \mathcal{K} \left(\{\cos\theta_i\}_{i=1}^p\right)$,
```

with $k = (k_1, \dots, k_p)^T$ the vector of the patch wavevectors and $\theta = (	heta_1, \dots, \theta_p)^T$ the vector of the patch angle differences $	heta_i = \theta_{x,i} - \theta_{y,i}$.
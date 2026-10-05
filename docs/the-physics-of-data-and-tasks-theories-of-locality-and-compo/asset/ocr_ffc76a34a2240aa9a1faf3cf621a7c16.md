# B.3 SPECTRA OF DEEP CONVOLUTIONAL KERNELS

where we have introduced $(f_2)_k$ as the projection of $f_2(||theta||)$ on the multi-Legendre polynomial with multi-degree $k$. The asymptotic decay of $(f_2)_k$ is again related to the differentiability of $f_2$, controlled by the action of the multi-sphere Laplace-Beltrami operator $\Delta_{p,s}$ in Equation 197. As $f_2$ depends only on one angle per sphere,

$$(242)$

```
$$\Delta_{p,s}^2(||theta||) = \sum_{i=1}^p (\theta_i^2(||theta||) + (s-2) \frac{\cos(\theta_i)}{\sin(\theta_i)}) \partial_{	heta_i}(f_2(||theta||)) .quad (243)$
```

Further similarities occur since $f_2$ depends only on the norm of $	heta$. In terms of the singular behavior near $||theta||=0, f_2 \sim ||theta||^{2v}$ implies $\Delta_{m,p,s}^2(||v-m)$, thus

```
$$\Delta_{m/p,s}^2||f_2||^2 = \int_{[0,\pi]^p} dp\theta \prod_{i=1}^p (\sin^{s-2}(\theta_i)) f_2(||theta||)\Delta_{m,p,s}^2(||theta||) <+\infty (244)$
```

requires $m < 2v+p(s-1)/2$ with $m < 2v+p(s-1)/2$ for the local contributions. Thereof has

```
$$\Delta_{m/p,s}^2||f_1||^2 = \sum_k \left( \prod_{i=1}^k N_{k,s} \right) \sum_{i=1}^k k_i(k_i+s-2) ||(f_2)_k||^2 <+\infty \quad \forall \quad m < 2v+p(s-1)/2, (245)$
```

while the diverges for $m \geq 2v+p(s-1)/2$. In addition, since $f_2$ is a radial function of $	heta$ which is homogeneous (or scale-invariant) near $||theta||=0, (f_2)_k$ can be factored in the large-$||k||$ limit into a power of the norm $||k||$ and a finite angular part $C(k/||k||)$. By plugging the factorization into Equation 245, we get

```
$$(f_2)_k \sim C(k/||k||)||k||^{-2v-p(s-1)}, \quad \sum_{k,||k||=k} \left(\\prod_{i=1}^k (k_i/||k||)^{-2}\right) C(k/||k||)^2 <+\infty (246)$
```

The projections of all the other terms in $\mathcal{K}$ on multi-Legendre polynomials display a faster decay with $||k||$, therefore the above results imply asymptotic scaling of global eigenvalues.

# n.3.4 General depth

The generalization to arbitrary depth is trivial once the depth-3 case is understood. For global and s1-local eigenvalues, the analysis of the previous section covers them unaltered. All the intermediate sec
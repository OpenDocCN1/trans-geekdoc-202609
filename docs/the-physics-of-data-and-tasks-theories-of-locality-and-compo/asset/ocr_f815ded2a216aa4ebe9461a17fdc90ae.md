# APPENDIX: RACE BETWEEN MEMORIZATION AND GENERALIZATION

LOCAL EIGENFUNCTIONS In the low-noise limit, the score in the vicinity of a data point $x_i$ is dominated by the $i$-th Gaussian component:

```
\nabla_x \log p_e(x) \approx \nabla_x \log \left[ \frac{1}{P} \mathcal{N}(x|x_i, \sigma^2 I_d) \right] = \frac{x-x_i}{\sigma^2}. \quad (410)
```

This shows that the target function is linear and moves our ansatz of approximate eigenfunctions to probe the spectrum of $K$. In particular, we construct a set of vector-valued functions $\{\psi_i\}_{i\in[P]}$ centered at each data point $x_i$;

```
\psi_i(x) \equiv (x-x_i) R \left( \frac{\|x-x_i|}{\}{\sigma} \right), \quad (411)
```

where $R : 0 \to \infty$ is a smooth cutoff function (e.g., $R(r)=e^{-r}$) that decays rapidly for $r \geq 1$. The support of $\psi_i$ is thus concentrated in the ball $B_d(x_i)$. These functions are asymptotically orthogonal $\langle\psi_i, \psi_j\rangle_{L_2(p_e)}=O(e^{-c})$ for $i \neq j$.

EIGENVALUES AND MEMORIZATION TIME We compute the eigenvalue $\lambda_i$ associated with each $\psi_i:

```
\lambda_i = \frac{\langle\psi_i, K\psi_i\rangle_{L_2(p_e)}}{\|\psi_i\|^2_{L_2(p_e)}} \quad (412)
```

The squared norm is dominated by the integral over the $i$-th component of the mixture:

```
\\|\psi_i\|^2_{L_2(p_e)} = \int |\psi_i(x)|^2 p_e(x) d^d x \nsimeq \frac{1}{P} \int \|x-x_i\|^2 R^2 \left( \frac{\|x-x_i|}{\}{\sigma} \right) \mathcal{N}(x|x_i, \sigma^2 I_d) d^d x \quad (413)
```

Changing to local coordinates $u = \frac{x-x_i}{\sigma}$:

```
\\|\psi_i\|^2_{L_2(p_e)} \simeq \frac{\sigma^2}{P} \int \|u\|^2 R^2(\|u\|) \mathcal{N}(u|0, I_d) d^d u \simeq \frac{\sigma^2}{P}, \quad (414)
```

where the proportionality constant depends only on $d$ and the choice of $R$. The numerator is given by the quadratic form

```
\langle\psi_i, K\psi_i\rangle_{L_2(p_e)} = \iint \psi_i(x) \cdot \psi_i(y) K(x,y) p_e(x) p_e(y) d^d x d^d y. \quad (415)
```

Given the localized support of $\psi_i$ and the non-overlapping assumption for the Gaussians, the integral is non-negligible when both $x$ and $y$ are near:

```
\langle\psi_i, K\psi_i\rangle_{L_2(p_e)} \simeq \frac{1}{P^2} \iint \psi_i(x) \cdot \psi_i(y) K(x,y) \mathcal{N}(x|x_i, \sigma^2 I_d) \mathcal{N}(y|x_i, \sigma^2 I_d) d^d x d^d y.
```
# # Appendix F:

# ## Black–Scholes finite-difference schemes

# ### F.1 The general case

In this section we consider the stability of the finite-difference schemes described in Chapter 5. It is assumed that the grid contains $n_s$ asset points, and we will denote the time dependent option values at the $ith$ and $(i+1)$th instances by $X^i$ and $X^{i+1}$ respectively. We can therefore write:

```
$$$T_1 X^i = T_2 X^{i+1}$$
```

where $T_1$ and $T_2$ are $(n_s - 2) 	imes (n_s - 2)$ tridiagonal matrices, and $x'_k, k = 1, \dots, n_s - 2$, will be used to denote the elements of the vector $X^i$.

The option values at the $ith$ time instant are computed from those at the $(i+1)$th time instant using

```
$$$X^i = T_1^{-1} T_2 X^{i+1}$$
```

However, Eq. (F.1.2) is only *stable* if the eigenvalues of the $(n_s - 2) 	imes (n_s - 2)$ matrix $T_1^{-1} T_2$ all have modulus less than one (Smith 1985).

# ### F.2 The log transformation and the implicit difference grid

We will prove that the implicit finite difference method, $	heta_m = 0$, when used on the log transformed Black–Scholes equation with a uniform grid is *unconditionally stable* which means that the stability does not depend on the values of $\sigma, \Delta t, \Delta Z$, etc.

From Chapter 5 the finite-difference scheme is described by the following tridiagonal system:

$$\begin{pmatrix} B & 0 & 0 & 0 & 0 \ A & B & C & 0 & 0 \ 0 & 0 & 0 & 0 & 0 \ 0 & 0 & 0 & 0 & 0 \ 0 & 0 & A & B & C \ 0 & 0 & 0 & A & B \end{pmatrix} egin{pmatrix} x_1^i \ x_2^i \ \vdots \ x_{n_s-1}^i \ x_{n_s-2}^i \end{pmatrix}$
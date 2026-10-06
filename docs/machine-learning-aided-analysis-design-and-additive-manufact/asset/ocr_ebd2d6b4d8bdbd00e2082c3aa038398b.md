where $p_k = n_k + 1$ and the interpolation points $cos\theta_j$ in each dimension are the zeros
of Chebyshev polynomials for orders $p_k$ and reformulated from Eq. (7,37).

```
$x_{jk} = cos\theta_{jk} = cos\left(\frac{2j_k-1}{2p_k}\pi\right), j_k = 1, 2, ..., p_k \quad (7.38)$
```

# 7.6 Results and discussion

In this section, the accuracy and validity of the present methods are evaluated from
both deterministic and nondeterministic ways. For deterministic aspect, results of
present are compared with Kitipnchai et al. [12]. For nondeterministic
alysis, the efficiency and verification of proposed methods are compared to quasi-\nMonte Carlo scheme (QMCS).

# 7.6.1 Validation of deterministic buckling analysis

Kitipnchai et al. [12] and Chen et al. [13] conducted the free vibration, nonlinear
vibration, elastic buckling, and postbuckling analysis. The normalized frequencies
and critical buckling loads are introduced:

```
$\omega = \Omega\sqrt{\frac{T_0}{A_{110}}}, \ N^* = \frac{P_x}{A_{110}} \quad (7.39)$
```

Table 7.1 compare the results of present study with that of Kitipnchai
et al. [12] and the present method, where $n$ is the number of layer. As can be seen,
the present results match well with the open literature for all cases.

Table 7.1 Comparison of the normalized critical buckling loads of nanocomposite beams
for TPI/$L=20$.

| $\Delta_{GL}$ | Method | $n$ | $e_\theta=0$ | $e_\theta=0.2$ | $e_\theta=0.4$ | $e_\theta=0.6$ |
|---|---|---|---|---|---||}{
| 1 wt.% | Kitipnchai et al. [12] | 10000 | 0.01507 | 0.01386 | 0.01265 | 0.01139 |
| | Present / Kitipnchai et al. [12] | 10000 | 0.01506 | 0.01386 | 0.01265 | 0.01139 |
| | Present | / | 0.00799 | 0.00736 | 0.00675 | 0.00613 |
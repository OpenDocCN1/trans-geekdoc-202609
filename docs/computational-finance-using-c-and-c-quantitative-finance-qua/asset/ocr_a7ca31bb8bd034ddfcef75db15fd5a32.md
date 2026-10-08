# Appendix C: Standard statistical results

```
$$\sum_{i=1}^n b_i^2 \text{Var}[X_i] + \sum_{i=1}^n \sum_{j=1(j\neq i)}^n b_i b_j \text{Cov}[X_i, X_j]$
```

As before all the $X$ variables are IID then the covariance terms are zero, and we have:

```
$$\text{Var}[Z] = \sum_{i=1}^n b_i^2 \text{Var}[x_i]$
```

If in addition the $b_i$ terms are one and all the $X$ variable have variance $\sigma^2$ we obtain:

```
$$\text{Var}[Z] = \sum_{i=1}^n \text{Var}[x_i] = n\sigma^2$
```

# C.3.2 Covariance

The covariance between two variables $X$ and $Y$ is defined by:

```
$$\text{Cov}[X, Y] = E[(X - E[X])(Y - E[Y])]$$\n= E[XY] - E[X]Y - XE[Y] + E[X]E[Y]$$\n= E[XY] - E[Y]E[X] - E[X]E[Y] + E[X]E[Y]$\n= E[XY] - E[X]E[Y]$
```

By symmetry it can be seen that $	ext{Cov}[X, Y] = \text{Cov}[Y, X]$.

# Two variables

Let $Z_1 = a + bX$ and $Z_2 = c + dY$, where $a, b, c$ and $d$ are constants. We have:

```
$$\text{Cov}[Z_1, Z_2] = \text{Cov}[a+bX, c+dY] - E[(a+bX)]E[(c+dY)]$\n= E[ac + bcX + adY + bdXY] - \{(a + bE[X])\}(c + dE[Y])\}$$\n= ac + bcE[X] + adE[Y] + bdE[XY]$$\n- ac + bcE[X] - adE[Y] - bdE[X]E[Y]$$\n= bd\{E[XY] - E[X]E[Y]]$
```

.. $\text{Cov}[Z_1, Z_2] = bd \text{Cov}[X, Y]$

# Three variables

Let $Z_1 = a+b_1X_1+b_2X_2$ and $Z_2 = c+dY$, where $a, b_1, b_2, c$ and $d$ are constants.
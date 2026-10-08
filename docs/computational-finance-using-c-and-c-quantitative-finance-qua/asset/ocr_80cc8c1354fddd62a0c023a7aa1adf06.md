# 14 Computational Finance Using C and C#

As in Section 2.3 we need to find the process followed by a function of the stochastic vector X, that the process followed by $\phi(X, t)$. This can be done by applying an $n$-dimensional Taylor expansion, up to second order, in the variables $X$ and $t$ as follows:

```
$$\phi^* = \phi + \frac{\partial\phi}{\partial t}dt + \sum_{i=1}^n \frac{\partial\phi}{\partial X_i}dX_i + \frac{1}{2}E\sum_{i=1}^n\sum_{j=1}^n \frac{\partial^2\phi}{\partial X_i\partial X_j}dX_idX_j$\n$+ \frac{1}{2}\frac{\partial^2\phi}{\partial t^2}dt^2 + \sum_{i=1}^n \frac{\partial^2\phi}{\partial X_i\partial t}dX_idt$ (2.5.3)
```

where $\phi^*$ is used to denote the value $\phi(X+dX, t+dr)$, and $\phi$ denotes the value $\phi(X, t)$. We will now consider the magnitude of the terms $dX_i$, $dX_j$, $dt$ and $dr$ as $dr \to 0$. Expanding the terms $dX_i$, $dX_j$ and $dt$, $dr$ we have:

```
$dX_i dX_j = (a_i+b_i\sqrt{dX_i})(a_j+b_j\sqrt{dX_j})$\n.\ dXd_i = a_ia_jdr^2 + b_id^{5/2}dZ_j + a_jdt^{3/2}dZ_i$\n$+ b_ib_j dr dZ_j$ (2.5.4)\n$dX_i = a_idt^2 + b_idt^{3/2}dZ_i$
```

So as $dr \to 0$, and ignoring all terms in $dt$ of greater than 1, we have:

$dX_t \sim 0$

and

$dX_i dX_j \sim b_ib_j dt dZ_i dZ_j$

Therefore Eq. (2.5.3) can be rewritten as

```
$$\phi = \frac{\partial\phi}{\partial t}dt + \sum_{i=1}^n \frac{\partial\phi}{\partial X_i}dX_i + \frac{1}{2}E\sum_{i=1}^n\sum_{j=1}^n \frac{\partial^2\phi}{\partial X_i\partial X_j}dX_idX_j$ (2.5.5)
```

where $\phi = \phi^* - \phi$$.

Now

```
$E[dX_i dX_j] = E[b_ib_j dt dZ_i dZ_j] = b_ib_j dt \rho_{ij}$
```

where $\rho_{ij}$ is the correlation coefficient between the $i$th and $j$ assets.\nUsing these values in Eq. (2.5.5), and substituting for $dX_i$ from Eq., we obtain:

```
$$\phi = \sum_{i=1}^n \frac{\partial\phi}{\partial X_i}(a_idt + b_idW_i) + \frac{\partial\phi}{\partial t}dt + \frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n b_ib_j \rho_{ij} dt\frac{\partial^2\phi}{\partial X_i\partial X_j}$ (2.5.6)
```

This gives Ito's $n$-dimensional formula:
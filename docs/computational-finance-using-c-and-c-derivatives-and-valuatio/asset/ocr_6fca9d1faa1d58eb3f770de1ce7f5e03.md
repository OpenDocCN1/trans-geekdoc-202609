# 132 CHAPTER 5 Single Asset American Options

$S_j = j\Delta S, j = 0, \dots, n_s-1$, where $\Delta S$ is the spacing between grid points. If $S_{\max}$ is the maximum asset value we want to represent, then the grid spacing, $\Delta S^*$, can be simply calculated as

```
$$\Delta S^* = \frac{S_{\max}}{(n_s-1)} \quad (5.4.2)$
```

However, since we would like to solve the option values and Greeks at the current asset price $S_0$, we would also like an asset grid line to coincide with the current asset price. This leads to the use of interpolation which is necessary when the asset value does not correspond to a grid line. The method by which we achieve this is outlined in Code excerpt 5.12. Here, the user supplies the function `opt_gfd` with values for $S_{\max}$ and $n_s-1$ from which is computed using equation (5.4.2). We then find $n_1$, that is below (or equal) to the value $\frac{S_0}{\Delta S^*}$ and use this to obtain a new grid spacing $\Delta S^*$. This leads to the new price discretization $S_j = j\Delta S, j = 0, \dots, n_s-1$, where we have ensured that $S_{n_1} = S_0$.

The user also supplies the function `opt_gfd` with the number of intervals for the grid. Here $n_t$ time intervals, the grid has $n_t+1$ uniformly spaced time instances, $t_i = i\Delta t, i=0,\dots,n_t$, and the time step is

```
$$\Delta t = \frac{T}{n_t} \quad (5.4.3)$
```

As with the binomial lattice methods, we will solve the equation backwards in time from maturity (at $t+\tau$) to the present (the time $t$). So as we solve the equation, the time index will start at $i=n_t$ (time $t+\tau$) and decrease to $i=0$ (current time $t$).

Here, we discuss the grid method of solving the Black–Scholes equation in terms of the following:

+   - The Finite-difference approximation.
- The boundary conditions.
- Computation of the option values at a given time instant.
- Backwards iteration and early exercise.

Each of these aspects will be considered in turn.

# The Finite-Difference Approximation

The option value corresponding to the grid node at $t_i = i\Delta t$ and $S_j = j\Delta S$ will be denoted by $f_{i,j}$. We will approximate the partial derivative of $f_{i,j}$ with respect to time as

```
$$\frac{\partial f}{\partial t} = \frac{f_{i+1,j}-f_{i,j}}{\Delta t}} \quad (5.4.4)$
```

For the other terms in equation (5.4.1), we will use the weighted, $\Theta_m$, method. This technique involves selecting an appropriate choice for $\Theta_m$ in the range $0 \leq \Theta_m \leq 1$ so that the contribution from node $(i,j)$ is a weighted sum over the values at nodes $(i,j)$ and $(i+1,j)$. For instance, the time $rf_{i,j}$ in equation
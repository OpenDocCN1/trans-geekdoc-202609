(c) Show that

```
$E[S_t] = S_0 \exp\left(\mu t + \frac{\sigma^2}{2}t\right).$$
```

**Problem 11 (Problem 4.3, Øksendal (2003)).** Let $X_t, Y_t$ be stochastic processes. Prove that

```
$d(X_t, Y_t) = X_t dY_t + Y_t dX_t + E[dX_t dY_t].
```

Deduce the following general integration by parts formula:

```
$$\int_{s=0}^t X_s dY_s = X_t Y_t - X_{t_0} Y_{t_0} - \int_{s=0}^t Y_s dX_s - \int_{s=0}^t E[dX_s dY_s].$$
```
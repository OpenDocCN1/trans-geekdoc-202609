# Interest Rate Derivatives | Section | 7.2 219

where $\sigma_x$ is the volatility of the forward foreign exchange rate $X_d^f(t,k)$, $\sigma_f$ is the volatility of the foreign forward rate $F^f(t,t_{k-1},k)$, and $ho_{x,f}$ is the correlation between $dW_x^Q$ and $dW_f^Q$.

Therefore, equation (7.2.86) can be written as

```
$d\left(\frac{X_1}{X_2}\right) = \left(\frac{X_1}{X_2}\right)\{\sigma_x \sigma_f \rho_{x,f}dt + \left(\frac{X_1}{X_2}\right)\{\sigma_1 dW_1^Q - \sigma_2 dW_2^Q\$\}$,$
```

which means that

```
$d\left(F^f(t,t_{k-1},t_k)\right) = -F^f(t,t_{k-1},t_k)\{\sigma_x \sigma_f \rho_{x,f}dt + F^f(t,t_{k-1},t_k)\{\sigma_1 dW_1^Q - \sigma_2 dW_2^Q\$\}$
```

comparing the above equation with equation (7.2.78)

```
$d\left(F^f(t,t_{k-1},t_k)\right) = -F^f(t,t_{k-1},t_k)\{\sigma_x \sigma_f \rho_{x,f}dt + \sigma_f F^f(t,t_{k-1},t_k)dW_t^Q\$\}$ (7.2.89)
```

and so $\alpha = -\sigma_x \sigma_f \rho_{x,f}$.

# Quanto Floorlet

The formula to value a quanto floorlet can be obtained in similar manner to that used for the quanto caplet.

The value at $t_0$ of a standard floorlet that pays at time $t_k$ and extends from time $t_{k-1}$ to $t_k$ is

```
$Floorlet(t_0) = P\tau DF^f(t_0,t_k)E^{Qk} \left[max \left(K - F^f, 0\right)\right],$ (7.2.90)
```

where $P$ is the principal, $K$ is the strike, $	au = t_k-t_{k-1}$, $F_k$ is the domestic forward rate $F(t_0,t_{k-1},t_k)$. Equation (7.2.90) can be evaluated using the Black Schedules formula as follows:

```
$Floorlet(t_0) = P\tau DF^f(t_0,t_k)\{\left\{-F^f(t_0,t_{k-1},t_k)N_1(-d_1) + KN_1(-d_2)\right\},$ (7.2.91)
```

where the symbols have the same meaning as for the corresponding quanto caplet,

```
$d_1 = \frac{\log\left(\frac{DF^f(t_0,t_{k-1},t_k)}{K}\right) + \frac{\sigma_d^2}{2}(t_{k-1}-t_0)}{\sigma_d\sqrt{t_{k-1}-t_0}}\nd_2 = \frac{\log\left(\frac{DF^f(t_0,t_{k-1},t_k)}{K}\right) - \frac{\sigma_d^2}{2}(t_{k-1}-t_0)}{\sigma_d\sqrt{t_{k-1}-t_0}}$$ (7.2.92)
```

In a quanto floorlet instead of using the domestic forward rate $F^d(t_0,t_{k-1},t_k)$,

```
$QFloorlet(t_0) = P\tau DF^d(t_0,t_k) \\times \left\{-F^f(t_0,t_{k-1},t_k)\exp(\alpha(t_{k-1}-t_0))N_1(-d_1) + KN_1(-d_2)\right\\},$ (7.2.93)
```
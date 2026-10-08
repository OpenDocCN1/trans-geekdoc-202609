Other financial derivatives

Using Eq. (7.2.85) we can write Eq. (7.2.87) as:

```
$d(log(	au X_d^f(t, t_k))) = -\frac{\sigma_x^2}{2} dt + \sigma_x dW_x^Q \quad (7.2.88)$
```

Now,

where we have ignored terms in dt with order greater than 1.
In addition

```
$E[d(log(X_2))d(log(X_2)) - d(log(X_1))]$
=-E[d(log(X_2)) d(log(\frac{X_1}{X_2}))]\n=-E[d(log(X_2)) d(F^f(t, t_{k-1}, t_k))]$
=-E[d(log(X_d^f(t, t_k))) d(F^f(t, t_{k-1}, t_k))]$
=-E[d(log(X_d^f(t, t_k))) d(F^f(t, t_{k-1}, t_k))]$
=-\sigma_x\sigma_f \rho_{x,f} dt$
```

where $\sigma_x$ is the volatility of the forward foreign exchange rate $X_d^f(t, t_k)$, $\sigma_f$ is the volatility of the foreign forward rate $F^f(t, t_{k-1}, k)$, and $ho_{x,f}$ is the correlation between $dW_x^Q$ and $dW_f^Q$.
Therefore Eq. (7.2.86) can be written as:

```
$d(\frac{X_1}{X_2}) = -\frac{X_1}{X_2}(\sigma_x\sigma_f \rho_{x,f}) dt + \frac{X_1}{X_2}\{\sigma_1 dW_1^Q - \sigma_2 dW_2^Q\}$
```

which means that

```
$D^f(t, t_{k-1}, t_k)$
=-F^f(t, t_{k-1}, t_k)(\sigma_x\sigma_f \rho_{x,f}) dt + F^f(t, t_{k-1}, t_k)\{\sigma_1 dW_1^Q - \sigma_2 dW_2^Q\}$
```

Comparing the above equation with Eq. (7.2.78):

```
$D^f(t, t_{k-1}, t_k)$
=-F^f(t, t_{k-1}, t_k)(\sigma_x\sigma_f \rho_{x,f}) dt + \sigma_f F^f(t, t_{k-1}, t_k) dW^Q \quad (7.2.89)$
```

and $\alpha = -\sigma_x\sigma_f \rho_{x,f}$.
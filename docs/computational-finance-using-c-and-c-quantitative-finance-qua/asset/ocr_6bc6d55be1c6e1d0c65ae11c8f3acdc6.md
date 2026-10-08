# Other financial derivatives

# FX call

The time t value (in domestic currency) of an FX call to buy one unit of foreign currency can be found from Eq. (4.4.55) and the substitutions given in (7.3.8). We have:

```
$d_1 = \frac{1}{\sigma\sqrt{T-t}}\left\{log\left(\frac{X_d^f(t)}{K}\right) + (r^d - r^f)(T-t) + \frac{1}{2}\sigma^2(T-t)\right\} \quad (7.3.10)\nnd_2 = d_1 - \sigma\sqrt{T-t} \quad (7.3.11)
```

Where $K$ is the strike rate that has been agreed to pay for one unit of foreign currency in units of domestic currency, and $\sigma$ is the implied foreign/domestic currency exchange rate FX volatility, which may depend on effects such as time to maturity, volatility, and scale.

In practice the following, modified version of Eq. (7.3.9) is usually used:

```
$C_d(t) = P^f\{X_d^f(t)\exp(-r^f(T-t))N(d_1) - K\exp(-r^d(T-t))N(d_2)\} \quad (7.3.12)$
```

Where $P^f$ is the number of units of foreign currency and all other symbols have their previous meanings.
The value $C_b(t)$ of the call option in base currency can be found by using $C_b(t) = X_b^fC_d(t)$. From Eq. (7.3.12) we have:

```
$C_b(t) = P^f\{X_b^f(t)N(d_1)DF^f(t, T) - KX_b^f(t)N(d_2)DF^d(t, T)\} \quad (7.3.13)$
```

where we used the fact that $X_d^f(t) = X_b^f(t), DF^f(t, T) = \exp(-r^f(T-t))$ and $DF^d(t, T) = \exp(-r^d(T-t))$. We can also re-express the values for $d_1$ in Eq. (7.3.10) as:

```
$d_1 = \frac{1}{\sigma\sqrt{T-t}}\left\{log\left(\frac{X_b^f(t)}{KX_d^f(t)}ight) +loglog\left(\frac{DF^f(t, T)}{DF^d(t, T)}ight) + \frac{1}{2}\sigma^2(T-t)\right\} \quad (7.3.14)$
```

where we used the fact that

```
$log(DF^f(t, T)) = -r^f(T-t)$,
```

and

```
$log\left(\frac{X_d^f(t)}{K}\right) =log\left(\frac{X_b^f(t)X_d^f(t)}{KX_d^f(t)}ight) =log\left(\frac{X_b^f(t)}{KX_d^f(t)}ight)$
```

We note that the term $KX_d^f$ is the strike in units of base currency—that is, the amount that has been agreed to pay for one unit of foreign currency in units of base currency.
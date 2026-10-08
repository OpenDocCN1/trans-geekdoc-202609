# Put options on the maximum of two assets

It will be shown that the price of a European put option on the maximum of two assets, $p_{\max}(S_1, S_2, E, \tau)$ is:

```
$p_{\max}(S_1, S_2, E, \tau) = E \exp(-r\tau) - c_{\max}(S_1, S_2, 0, \tau) + c_{\max}(S_1, S_2, E, \tau)\n(6.5.9)
```

where, as before, the meaning of the symbols pays has been previously defined. This result can be proved by considering the following two investments:

PORTFOLIO A: Purchase one option on the maximum of $S_1$ and $S_2$ with exercise price $E$.

PORTFOLIO B: Purchase one discount bond which pays $E$ at maturity. Write (that is, sell) one option on the maximum of $S_1$ and $S_2$ with exercise price of zero. Purchase one option on the maximum of $S_1$ and $S_2$ with exercise price $E$.

As before now consider the values of these portfolios at option maturity, $	au$.

```
$If(S_1, S_2) \geq E\nPORTFOLIO A: Pays zero\nPORTFOLIO B: Pays $E - \max(S_1, S_2) + \max(S_1, S_2) - E = 0\nIf(S_1, S_2) = S_1 < E\nPORTFOLIO A: Pays $E - S_1\nPORTFOLIO B: Pays $E - S_1 + 0 = E - S_2\nIf(S_1, S_2) = S_2 < E\nPORTFOLIO A: Pays $E - S_2\nPORTFOLIO B: Pays $E - S_2 + 0 = E - S_2$
```

It follows that, under all possible circumstances, Portfolio A has the same value as Portfolio B, and that Eq. (6.5.9) is true.

# 6.5.3 American options

We assume that the prices of asset 1 and asset 2 follow a lognormal process with drift terms of $\mu_1 = r - \sigma_1^2/2$ and $\mu_2 = r - \sigma_2^2/2$, respectively. As before, $r$ is the riskless interest rate and $\sigma_1$ and $\sigma_2$ are the instantaneous volatilities of asset 1 and asset 2.

If we let $S_{1,t}$ and $S_{2,t}$ denote the respective prices of asset 1 and asset 2 at time $t$, then we can write:

```
$log(S_{1,t+\Delta t}) = \log(S_{1,t}) + \varepsilon_{1,t}\n(6.5.10)
```
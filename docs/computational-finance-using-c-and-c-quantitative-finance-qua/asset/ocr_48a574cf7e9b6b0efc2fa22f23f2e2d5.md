# 196 Computational Finance Using C and C#

and

```
$$\rho_1 = \frac{\sigma_1 - \rho\sigma_2}{\sigma_*}, \quad \rho_2 = \frac{\sigma_2 - \rho\sigma_1}{\sigma_*}$
```

It can also be shown that:

```
$c_{max}(S_1, S_2, E, \tau) + c_{min}(S_1, S_2, E, \tau) = c(S_1, E, \tau) + c(S_2, E, \tau) \quad (6.5.7)$
```

where $c(S_1, E, \tau)$ is the value of a vanilla European call.

We will now derive an expression for the value of the corresponding European put options.

# Put options on the minimum of two assets

It will now be shown that the price of a European option on the minimum of two assets, $p_{min}(S_1, S_2, E, \tau)$ is:

```
$p_{min}(S_1, S_2, E, \tau) = E \exp(-r\tau) - c_{min}(S_1, S_2, 0, \tau) + c_{min}(S_1, S_2, E, \tau) \quad (6.5.8)$
```

where the meaning of the symbols has been previously defined.

This result can be proved by considering the following two investments:

PORTFOLIO A: Purchase one option on the minimum of $S_1$ and $S_2$ with exercise price $E$.

PORTFOLIO B: Purchase one discount bond which pays $E$ at maturity. Write that (is, sell one option on the minimum of $S_1$ and $S_2$ with an exercise price of zero. Purchase one option on the minimum of $S_1$ and $S_2$ with exercise price $E$.

We now consider the values of these portfolios at option maturity, time $\tau$.

```
$If \min(S_1, S_2) \ge E$
```

+   - PORTFOLIO A: pays zero
- PORTFOLIO B: pays $E - \min(S_1, S_2) + \min(S_1, S_2) - E = 0$

```
$If \min(S_1 - 1, S_2) = S_1 < E$
```

+   - PORTFOLIO A: Pays $E - S_1$
- PORTFOLIO B: Pays $E - S_1 + 0 = E - S_1$

```
$If \min(S_1, S_2) = S_2 < E$
```

+   - PORTFOLIO A: Pays $E - S_2$
- PORTFOLIO B: Pays $E - S_2 + 0 = E - S_2$

We have therefore shown that, under all possible circumstances, Portfolio A has the same value as Portfolio B. This means that Eq. (6.5.8) is true.
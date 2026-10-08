PORTFOLIO A: One European call, $c(S, E, 	au)$, and cash of value $E \exp(-r\tau)$.

PORTFOLIO B: One European put, $p(S, E, 	au)$, and one share of value $S$.

At option maturity the value of the call and put are $c(S_T, E, 0)$ and $p(S_T, E, 0)$; respectively; also at time $T$ the value of the dividends paid during the life of the option is $D \exp(r\tau)$.

We now consider the value of both portfolios at time $T$ under all possible conditions.

$If S_T \geq E$

Portfolio A is worth:

$max(S_T - E, 0) + E \exp(r\tau)\{E \exp(-r\tau) + D\} = S_T - E + E + D \exp(r\tau)\n= S_T + D \exp(r\tau)$

Portfolio B is worth:

$max(E - S_T, 0) + S_T + D \exp(r\tau) = 0 + E + D \exp(r\tau)\n= S_T + D \exp(r\tau)$

$If S_T < E$

Portfolio A is worth:

$max(S_T - E, 0) + E \exp(r\tau)\{E \exp(-r\tau) + D\} = 0 + E + D \exp(r\tau)\n= E + D \exp(r\tau)$

Portfolio B is worth:

$max(E - S_T, 0) + S_T + D \exp(r\tau) = E - S_T + S_T + D \exp(r\tau)\n= E + D \exp(r\tau)$

We have therefore shown that under all conditions the value of portfolio A the same as that of portfolio B.

# 4.3.2 Continuous dividends

Here we consider single asset European put and call options, and derive the following relationship:

```
$c(S
```

where $q$ is the asset’s continuous dividend yield that is paid during the life of the option. The result can be proved by considering the following two investments:

PORTFOLIO A: One European call, $c(S, E, \tau)$, and cash of value $E \exp(-r\tau)$.
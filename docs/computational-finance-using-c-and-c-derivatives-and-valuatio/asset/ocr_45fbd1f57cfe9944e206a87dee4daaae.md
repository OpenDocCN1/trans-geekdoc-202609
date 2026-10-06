# Put Call Parity Section | 4.3 59

Portfolio B:

One European put, $p(S, E, 	au)$, and one share of value $S$.

At maturity, the value of the call and put are $c(S_T, E, 0)$ and $p(S_T, E, 0)$ respectively; also at time $T$, the value of dividends paid during the life of the option is $D \exp(r	au)$.

We now consider the value of both portfolios at time $T$ under all possible conditions.

If $S_T \ge E$

Portfolio A is worth,

$$\max(S_T - E, 0) + E \exp(-r	au) + D = S_T - E + E \exp(r	au) = S_T + D \exp(r	au).$$

Portfolio B is worth,

$$\max(E - S_T, 0) + S_T + D \exp(r	au) = 0 + S_T + D \exp(r	au) = S_T + D \exp(r	au).$$

If $S_T < E$

Portfolio A is worth,

$$\max(S_T - E, 0) + \exp(r	au) + D = 0 + E + D \exp(r	au) = E + D \exp(r	au).$$

Portfolio B is worth,

$$\max(E - S_T, 0) + S_T + D \exp(r	au) = E - S_T + S_T + D \exp(r	au) = E + D \exp(r	au).$$

We have shown that under all conditions the value of portfolio A is the same as that of portfolio B.

# 4.3.2 Continuous Dividends

Here, we consider single asset European put and call options, and derive the following relationship:

```
$$$c(S, E, 	au) + E \exp(-r	au) = p(S, E, 	au) + S \exp(-q	au),$$
```

where $q$ is the asset's continuous dividend yield that is paid during the life of the option. The result can be proved by considering the following two investments:

Portfolio A:

One European call, $c(S, E, 	au)$, and cash of value $E \exp(-r	au)$.

Portfolio B:

One European put, $p(S, E, 	au)$, and one share of value $S \exp(-q	au)$.

At expiry, the value of the call and put are $c(S_T, E, 0)$ and $p(S_T, E, 0)$ respectively. Also, if the value of share at time $t$ is denoted by $S$, the combined value of shares and dividends at time $T$ is $S \exp(q	au)$: Note that $q$ is treated in a similar manner to the continuously compounded riskless interest rate $r$.
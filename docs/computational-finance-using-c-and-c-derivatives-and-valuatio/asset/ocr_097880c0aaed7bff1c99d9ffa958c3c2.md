all the asset prices in the economy. So (for example) $S^1$ is a numeraire, then the prices of the other assets denominated in units of $S_1$ are the relative prices $Z'_i=(S_i/S_1),i=2,\dots,n$.

One can find a unique probability measure $Q$ such that the relative prices $Z'_i,i=2,\dots,n$ are martingales. If either is free of arbitrage opportunities, then every payoff pattern $H_T$ can be represented as a linear combination of the asset values $S^T_i,i=1,\dots,n$, and in addition, the relative price process $(H_T/S^T_1)$ is a martingale.

This means we can write

```
$E^Q\frac{H_t}{S^T_t}=E^Q\frac{H_T}{S^T_T}, \quad \text{where } 0 \le t \le T.$
```

The current (time t) value $V_t$ of payoff $H_T$ is this

```
$V_t=S^T_t\frac{H_T}{S^T_T}.$
```

In general for a numeraire $N$ which takes the values $N_t, 0 \le t \le T$, we can write

```
$V_t=N_te^Q\frac{H_T}{N_T}. \quad (4.2.1)
```

Equation (4.2.1) is very important because $V_t$ is the current (time t) price of a financial derivative with maturity $T$ and payoff $H_T$.

It should be mentioned that the price of a financial derivative is independent of the martingale measure under which it is valued, and thus, the same price $V_t$ will be obtained for different numeraires $N$.

# 4.3 PUT CALL PARITY

# 4.3.1 Discrete Dividends

Here, we consider asset European put and call options, and derive the following relationship between their values in the presence of cash dividends:

```
$c(S,E,\tau)+E\exp(-r\tau)+D=p(S,E,\tau)+S. \quad (4.3.1)
```

where $D$ is the *present value* of the dividends that are paid during the life of the option. That is,

```
$D=\sum_{k=1}^n D_k\exp(-r(t_k-t)).$
```

with $D_k$ the cash dividend paid at time $t_k$; the other symbols have already been defined in the Introduction.

This result can be proved by considering the following two investments:

Portfolio A:

One European call, $c(S,E,\tau)$, and cash of value $E\exp(-r\tau)+D.$
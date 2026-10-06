# Credit Derivatives Section | 7.4 **225**

and

```
$$\log\left(\frac{X_d^f(t)}{K}\right) = \log\left(\frac{X_b^f(t)}{K X_b^d(t)}ight) = \log\left(\frac{X_b^f(t)}{K X_d^d(t)}ight)$
```

We note that the term $K_d^X$ is the strike in units of base currency, that is, the amount that has been agreed to pay for one unit of foreign currency in units of base currency.

In the case $N(d1) = N(d2) = 1$ (i.e., there is no uncertainty), equation (7.3.13) becomes

```
$C_b(t) = Pf\X_b^f(t) DF^f(t,T) - K X_d^d(t) DF^d(t,T)$
```

which is the same as already given in equation (7.3.4) for the FX Forward.

# FX Put

The time $t$ value of the corresponding put in units of base currency is

```
$P_b(t) = Pf\{-X_b^f(t) DF^f(t,T) N(-d1) + K X_b^f(t) DF^d(t,T) N(-d2)\\}.$ (7.3.15)
```

where the symbols have the same meanings as the FX call.

# 7.4 CREDIT DERIVATIVES

Credit derivatives take into account the fact that a counterparty may and not honour (or by bankruptcy, etc.) the obligations set out in a given financial contract. In order to obtain the time $t$ value of the probability that the counterparty (and thus the contract) will survive until some time $T > t$. Here we denote the survival probability between times $t$ and $T$ by $S(t,T)$, and we compute value from the hazard rate.

# The Hazard Rate

As previously mentioned, the survival probability between times $t$ and $T$, where $T > t$, is denoted by $S(t,T)$. This means that the probability of default between times $t$ and $T$ is

```
$P_{def}(t,T) = 1 - S(t,T)$
```

and the probability of default, as seen from time $t$, between times $T_1$ and $T_2$ is

```
$P_{def}(t_1,T_2) = S(t,T_1) - S(t,T_2), \quad T_2 > T_1.$$ (7.4.1)
```

The time $t$ discrete hazard rate between times $T$ and $T + \Delta T$, denoted by $H(t,T,T+\Delta T)$, is defined by

```
$H(t,T,T+\Delta T) = \frac{1}{\Delta T} \frac{P_{def}(t,T,T+\Delta T)}{S(t,T+\Delta T)}\\= \frac{1}{\Delta T} \frac{S(t,T) - S(t,T+\Delta T)}{S(t,T+\Delta T)}.$
```
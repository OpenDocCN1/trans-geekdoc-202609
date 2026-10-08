Other financial derivatives 235

so from Eqs. (7.4.18) and (7.4.17):

```
$$\tilde{f}(t, T) - f(t, T) = \frac{\partial}{\partial T}\ln(S(t, T))$ (7.4.19)$
```

Combining Eqs. (7.4.19) and (7.4.4) we have:

```
$h(t, T) = \tilde{f}(t, T) - f(t, T)$ (7.4.20)$
```

This means that we can compute the hazard rate $h(t, T)$ by taking the difference between the instantaneous forward rates computed using defaultable and nondefaultable zero coupon bonds.

# 7.4.1 Defaultable bond

For a defaultable bond we need to take into account the fact that the bond issuer may default, that is cease to make the bond coupon payments. The time $t$ value of a defaultable bond is:

```
$$\tilde{B}(t) = P\tilde{DF}(t, t_m) \quad principal$\n$+ + \sum_{j=1}^{m} C_j\tilde{DF}(t, t_j) \quad coupons$\n$+ PR\sum_{j=1}^{m} DF(t, t_j)\{S(t, t_{j-1}) - S(t, t_j)\} \quad recovery value$
```

where $t_m$ is the maturity of the bond, $P$ is the principal, $C_j$ is the value of the $j$th coupon, $R$ is the recovery rate, $S(t, t_j)$ is the probability that the bond will survive until time $t_j$, and the zero coupon defaultable bond prices are defined by $\tilde{DF}(t, t_m) = S(t, t_m)DF(t, t_m)$ and $\tilde{DF}(t, t_j) = DF(t, t_j)S(t, t_j)$. The term $\{S(t, t_{j-1}) - S(t, t_j)\}$ is the probability that the bond will default between times $t_{j-1}$ and $t$.

# 7.4.2 Credit default swap

A Credit Default Swap (CDS) is a contract between two counterparties in one (party A) makes periodic fixed payments to the other (party B) in order to obtain protection on the default of a reference credit. In the event of default, B pays the default payment of $1 - R$, where $R$ is the recovery rate, and the contract ceases.

The time $t$ value of the credit default swap to $A$, the purchaser of the insurance, is:

```
$CDS(t) = - \sum_{j=1}^{m} C_j\tilde{DF}(t, t_j) \quad coupons$\n$+ P(1 - R)\sum_{j=1}^{m} DF(t, t_j)\{S(t, t_{j-1}) - S(t, t_j)\} \quad recovery value$
```
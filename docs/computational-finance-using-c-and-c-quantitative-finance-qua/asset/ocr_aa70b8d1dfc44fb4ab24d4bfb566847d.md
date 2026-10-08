# Other financial derivatives

```
$ETRS_p(t) = \sum_{m=j+1}^{N_f} S(t)DF(t, t_m) \left[ \frac{DF(t, t_{m-1})}{DF(t, t_m)} - 1 \right] \\n + \sum_{m=j+1}^{N_f} DF(t, t_{m-1})\Phi_f DF(t, t_m) \n + L(t_{j-1})(R(t_{j-1}) + \Phi)\tau_f DF(t, t_j) \n - \sum_{k=i+1}^{N_e} S(t) \left\{ 1 - \frac{DF(t, t_k)}{DF(t, t_{k-1})} \right\ \\n - = \frac{S(t)}{DF(t, t_j)} - L(t_{j-1})\DF(t, t_j) \quad (7.5.6)$
```

If $N_e = N_f = N$, and $	au_e = \tau_f = \tau$, then all the equity and float leg payments coincide and Eq. (7.5.6) simplifies to:

```
$ETRS_p(t) = \sum_{k=j+1}^{N} \frac{DF(t, t_k)}{DF(t, t_{k-1})}\Phi DF(t, t_k) \\n + L(R + \Phi)DF(t, t_j) - \left\{ \frac{S(t)}{DF(t, t_j)} - L \right\DF(t, t_j) \quad (7.5.7)$
```

Thus, if the spread $\Phi$ is the value of the payer equity TRS:

```
$ETRS_p(t) = L(t_{j-1})R(t_{j-1})\tau DF(t, t_j) \\n - \left\ \frac{S(t)}{DF(t, t_j)} - L(t_{j-1}) \right\DF(t, t_j) \quad (7.5.8)$
```

In these circumstances the value of the equity TRS at time $t$ only depends on the current swap, which extends from $t_{j-1}$ to $t_j$, where $t_{j-1} < t < t_j$.

# Equity swap

A special case of an equity TRS is an equity swap. Here one party (say A) pays the returns on a given equity and receives (from party B) returns on another equity, together with the interest on the difference of the reset notion of the two equity assets. An equity swap, ESWP, can be constructed from a structured deal consisting of one equity TRS and a short position in another equity TRS, with the same coupon payment dates and currency. If the individual equity deals are denoted by $ETRS_p^1$ and $ETRS_p^2$, the value of the equity swap at time $t$ is:

```
$ESWP(t) = ETRS_p^1(t) - ETRS_p^2(t) \quad (7.5.9)$
```

Substituting Eq. (7.5.8) into Eq. (7.5.9) we have:
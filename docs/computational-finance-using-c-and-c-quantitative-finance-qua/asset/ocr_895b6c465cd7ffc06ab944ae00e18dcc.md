Other financial derivatives

# Quanto swaplet

A quanto (also known as diff or differential) swaplet is an agreement in which one party makes floating rate payments on the foreign forward rate while the other makes fixed or floating payments based on domestic interest rates.

Here we consider quanto swaplets in which the received floating leg coupons (in domestic currency) are computed using foreign forward rates.

The value of a standard swaplet (in which all the coupons are domestic) can be found using Eqs. (7.20) and (7.274) to write:

Caplet$(t_0)$ - Floorlet$(t_0)$

```
$= P\tau D^F(t_0, t_k) E^Q[max(F_d^F - K, 0) - max(K - F_d^F, 0)]$
```

```
$= P\tau D^F(t_0, t_k) E^Q[F_d^F - K]$
```

```
$= P\tau D^F(t_0, t_k) \{E^Q[F_d^F] - K\}$
```

```
$= P\tau D^F(t_0, t_k) \{F^F(t_0, t_{k-1}, t_k) - K\}$ (7.2.94)
```

From Eq. (7.294) we can see that Quantolet$(t_0)$ - Floorlet$(t_0)$ is the value of a swaplet in which the owner pays the fixed rate K and receives the floating rate $F_d^F(t_0, t_{k-1}, t_k)$.

The value of the floating leg payment can be found by setting $K = 0$ in Eq. (7.294), and is $P\tau D^F(t_0, t_k) F_d^F(t_0, t_{k-1}, t_k)$.

The value of the floating legs in a quanto swap can be found in a similar manner:

Quantolet$(t_0)$ - Floorlet$(t_0)$

```
$= P\tau D^F(t_0, t_k) E^Q[max(F_f^F - K, 0) - max(K - F_f^F, 0)]$
```

Substituting from Eqs. (7.279) and (7.293):

Quantolet$(t_0)$ - Floorlet$(t_0)$

```
$= P\tau D^F(t_0, t_k) \{F^F(t_0, t_{k-1}, t_k) exp(\alpha(t_{k-1} - t_0))N_1(d_1) - K N_1(d_2)$
```

```
$ - F^F(t_0, t_{k-1}, t_k)N_1(-d_1) + K N_1(-d_2)\}$
```

When $K=0$ we have $d_1 = \infty, N_1(d_1) = 1$ and $N_1(-d_1) = 0$, which means that the value of the floating leg payment is:

Floatlet$(t_0)$

```
$= P\tau D^F(t_0, t_k) F^F(t_0, t_{k-1}, t_k) exp(\alpha(t_{k-1} - t_0))$ (7.2.95)
```

where as before $\alphaalpha = -\sigma_f \rho_{s,f}$.

Using Eq. (7.295) the value of a quanto swap with (pay) fixed domestic rate and (receive) foreign rate is:

```
$Qswaplet$(t_0) = P\tau D^F(t_0, t_k) \{F^F(t_0, t_{k-1}, t_k) exp(\alpha(t_{k-1} - t_0)) - K\}$
```
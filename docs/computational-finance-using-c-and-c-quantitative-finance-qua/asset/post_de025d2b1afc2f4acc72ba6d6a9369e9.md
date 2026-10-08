
# Other financial derivatives

$+ R \sum_{t_j=t_m}^{t_R} DF(t_m, t_j) |t\{S(t, t_{j-1}) - S(t_m, t_j)\}|$

All symbols already defined in this chapter have their previous meanings. In addition,

- $P$ - the swap principle
- $C$ - the fixed coupon of the reference bond
- $t_m$ - the swap maturity
- $t_R$ - the maturity of the reference bond $B$
- $B_0$ - the initial price of the reference bond
- $B_{(t_m)}$ - the final price of the reference bond (at swap maturity)
- $C_j$ - the floating coupon payment at time $t_j$. It is computed as:

```
$C_j = P\{F(t, t_{j-1}, t_j) + margin^{TRS}\}\{t_j - t_{j-1}\}
```

$DF(t_1, t_2)|t$ - the discount factor between times $t_1$ and $t_2$ (as seen from time $t$) is:

```
$DF(t_1, t_2)|t = \frac{D(t, t_2)}{D(t, t_1)}$
```

$\overline{DF(t_1, t_2)}|t$ - the defaultable discount factor between times $t_1$ and $t_2$ (as seen from time $t$) is:

```
$$\overline{DF(t_1, t_2)}|t = \frac{\overline{DF(t_1, t_2)} S(t, t_2)}{DF(t_1, t_1) S(t, t_1)}
```

$\overline{DF(t_1, t_1)}$ - the defaultable discount factor between times $t$ and $t_1$ is:

```
$\overline{DF(t_1, t_1)} = DF(t_1, t_1)S(t, t_1)$
```

# 7.5 Equity derivatives

### 7.5.1 Total return swap

An equity return swap consists of an equity leg (whose coupons are determined by the change in value of the equity) and a floating leg which pays according to the forwards of the floating interest rate.

Here we ignore the effect of equity dividends and also assume that the currencies for both the floating and equity legs of the swap are the same.

## Equity leg

Let the equity leg specified by coupon payments at times $t_k, k = 1, \dots, N_e$, where $\tau_e = t_k - t_{k-1}$. If at time $t$ the next coupon payment occurs at $t_j$ then the value of the equity leg is:

```
$V_e(t) = \left\{ \frac{S(t)}{DF(t, t_i)} - L(t, t_{i-1}) \right\} DF(t, t_i)$$
$$\sum_{k=t+1}^{N_t} \left( \frac{S(t)}{DF(t, t_k)} - \frac{S(t)}{DF(t, t_{k-1})} \right) DF(t, t_k) \quad (7.5.1)$$
```

Where $S(t)$ is the value of equity at time $t$, $L(t_{i-1})$ is the reset value of the equity at time $t_{i-1}$, and $DF(t, t_k)$ is the discount factor between times $t$ and $t_k, t_k > t$. It can be seen that the value of the equity $S(t_i)$ at time $t_i > t$ is obtained by inflating the current value, $S(t)$ by the reciprocal of the discount factor, $DF(t, t_i)$; that is, $S(t_i) = S(t)/DF(t, t_i)$.

## Floating leg

Let the floating leg have coupon payments at times $t_m, m = 1, \dots, N_f$, where $\tau_f = t_m - t_{m-1}$. If the next coupon is at time $t_j$, then the value of the floating leg is:

```
$V_f(t) = L(t_{j-1})R(t_{j-1}) + \Phi\tau_f DF(t, t_j)$
$$\sum_{m=j+1}^{N_t} \frac{S(t)}{DF(t, t_m)}F(t, t_{m-1}, t_m) + \Phi\tau_f DF(t, t_m) \quad (7.5.2)$$
```

where $\Phi$ is the margin added to the forward rate to compute coupons, $F(t, t_{m-1}, t_m)$ is the time forward rate between times $t_{m-1}$ and $t_m$, and $R(t_{j-1})$ is the reset rate that is used between times $t_{j-1}$ and $t_j$ to compute the coupon payment at $t_j$.

## Payer equity total return swap

The owner of a payer equity TRS pays the equity leg coupons, and thus at time $t$ the swap has value:

```
$ETRS_p(t) = V_f(t) - V_e(t) \quad (7.5.3)$
```

The owner of a receiver equity TRS receives the equity leg coupons, and the value of the swap is:

```
$ETRS_r(t) = -V_f(t) + V_e(t) \quad (7.5.4)$
```

We will now compute an expression for the value of a payer equity swap. Since

```
$F(t, t_{m-1}, t_m) = \frac{1}{t_m - t_{m-1}} \left( \frac{DF(t, t_{m-1})}{DF(t, t_m)} - 1 \right)$
```

we have:

```
$\tau_f F(t, t_{m-1}, t_m) = \frac{DF(t, t_{m-1})}{DF(t, t_m)} - 1 \quad (7.5.5)$
```

Substituting Eq. (7.5.5) into Eq. (7.5.2) and using Eq. (7.5.3) we obtain:

```
$ETRS_p(t) = \sum_{m=j+1}^{N_f} S(t)DF(t, t_m) \left[ \frac{DF(t, t_{m-1})}{DF(t, t_m)} - 1 \right] + \sum_{m=j+1}^{N_f} DF(t, t_{m-1})\Phi_f DF(t, t_m) + L(t_{j-1})(R(t_{j-1}) + \Phi)\tau_f DF(t, t_j) - \sum_{k=i+1}^{N_e} S(t) \left\{ 1 - \frac{DF(t, t_k)}{DF(t, t_{k-1})} \right\} = \frac{S(t)}{DF(t, t_j)} - L(t_{j-1})DF(t, t_j) \quad (7.5.6)$
```

If $N_e = N_f = N$, and $\tau_e = \tau_f$, then all the equity and float leg coincide and Eq. (7.5.6) simplifies to:

```
$ETRS_p(t) = \sum_{k=j+1}^{N} \frac{DF(t, t_k)}{DF(t, t_{k-1})}\Phi DF(t, t_k) + L(R + \Phi)DF(t, t_j) - \left\{ \frac{S(t)}{DF(t, t_j)} - L \right\} \quad (7.5.7)$
```

Thus, if the spread $\Phi$ is the value of the payer TRS:

```
$ETRS_p(t) = L(t_{j-1})R(t_{j-1})\tau DF(t, t_j) - \left\{ \frac{S(t)}{DF(t, t_j)} - L(t_{j-1}) \right\} \quad (7.5.8)$
```

In these circumstances the value of the equity TRS at time $t$ only depends on the current swap, which extends from $t_{j-1}$ to $t_j$, where $t_{j-1} < t < t_j$.

## Equity swap

A special case of an equity TRS is an equity swap. Here one party (say A) pays the returns on a given equity and receives (from party B) returns on another equity, together with the interest on the difference of the two assets. An equity swap, ESWP, can be constructed from a structured deal consisting of one equity and a short position in another equity, with the same coupon dates and currency. If the individual equity deals are denoted by $ETRS_p^1$ and $ETRS_p^2$, the value of the equity swap at time $t$ is:

```
$ESWP(t) = ETRS_p^1(t) - ETRS_p^2(t) \quad (7.5.9)$
```

Substituting Eq. (7.5.8) into Eq. (7.5.9) we have:

```
$ESWP(t) = L^1(t_{j-1})R(t_{j-1})\tau DF(t, t_j) - \left\{ \frac{S^1(t)}{DF(t, t_j)} - L^1(t_{j-1}) \right\} - \left( L^2(t_{j-1})R(t_{j-1})\tau DF(t, t_j) - \left\{ \frac{S^2(t)}{DF(t, t_j)} - L^2(t_{j-1}) \right\} \right)$
```

so the value of the equity swap paid to A is:

```
$ESWP(t) = \left\{ \frac{S^2(t)}{DF(t, t_j)} - L^2(t_{j-1}) \right\} - \left\{ \frac{S^1(t)}{DF(t, t_j)} - L^1(t_{j-1}) \right\}$
```

## 7.5.2 Black-Scholes

The Black-Scholes equation can also be used to price quanto options (Reiner 1992). We have the following processes:

```
$dS^f = \mu_f S^f dt + \sigma_f S^f dW_f^P$
$dX_s^f = \mu_x X_s^f dt + \sigma_x X_s^f dW_x^P$
$dB^f = r^f B^f dt$
$dB^d = r^d B^d dt$
```

where $S$ is the price (in foreign currency) of the foreign stock. $B^d$ is the domestic money account where money grows at constant free rate $r^d$. $B^f$ is the foreign money account where money grows at constant free rate $r^f$. The tradables for the domestic currency are martingales under the probability measure $\mathbb{Q}$ (the neutral measure measure We also established that under $\mathbb{Q}$ these tradables are GBM with constant drift $r^d$. So the process for the domestic equity $S^d$ is:

```
$dS^d = r^d S^d dt + \sigma_d S^d dW_d^{\mathbb{Q}}$
```

Similarly the process followed by the price of a foreign equity $S^f$ under the foreign neutral measure $\mathbb{F}$ is:

```
$dS^f = r^f S^f dt + \sigma_f S^f dW_f^{\mathbb{F}}$
```

However, the process followed by the price of a foreign equity under the domestic risk neutral measure $\mathbb{Q}$ is:

```
$dS^f = S^f (r^f + \alpha) dt + \sigma_f S^f dW_f^Q$
```

where $\alpha$ (the *quanto adjustment*) is to be determined. We will now derive the value for $\alpha$, and use this to price quanto forwards and quanto options.

## Determining the quantum adjustment, $\alpha$

Since $X_d^B B^f$ and $X_d^B S^f$ are domestic tradables it means the relative prices $X_d^B B^f/X_d^B B^d$ and $X_d^B S^f/X_d^B B^d$ are also martingales under the probability measure $\mathbb{Q}$. Now $X_d^B B^f/X_d^B B^d$ is a martingale:

```
$d\left(\frac{X_{Bd}^B B^f}{X_{Bd}^B B^d}\right) = \sigma_x \frac{X_{Bd}^B B^f}{X_{Bd}^B B^d} dW_Q^x \quad (7.5.14)$
```

We will start by writing $X_d^B B^f/B^d$ as $(S^f/B^f)(X_d^B B^f/X_d^B B^d)$. Using the Ito product rule we have:

```
$d\left(\frac{X_{Bd}^B B^f}{X_{Bd}^B B^d}\right) = d\left(\frac{S^f}{B^f}\right)d\left(\frac{X_{Bd}^B B^f}{X_{Bd}^B B^d}\right) + E\left[d\left(\frac{S^f}{B^f}\right)d\left(\frac{X_{Bd}^B B^f}{X_{Bd}^B B^d}\right)\right] \quad (7.5.15)$
```

Substituting for $d(X_d^B B^f/X_d^B B^d)$ from Eq. (7.5.14) into Eq. (7.5.15) gives:

```
$d\left(\frac{S^f}{B^f}\frac{X_{Bd}^B B^f}{X_{Bd}^B B^d}\right) = d\left(\frac{S^f}{B^f}\right)d\left(\frac{X_{Bd}^B B^f}{X_{Bd}^B B^d}\right) + \sigma_x \frac{S^f}{B^f}\frac{X_{Bd}^B B^f}{X_{Bd}^B B^d} dW_Q^x + E\left[d\left(\frac{S^f}{B^f}\right)d\left(\frac{X_{Bd}^B B^f}{X_{Bd}^B B^d}\right)\right] \quad (7.5.16)$
```

Using one source of randomness, Eqs. (7.5.13) and (7.5.10) yield:

```
$d\left(\frac{S^f}{B^f}\right) = \frac{S^f}{B^f}\alpha dt + \frac{S^f}{B^f}\sigma_x dW_Q^x \quad (7.5.17)$
```

We now consider the $E[d(S^f/B^f)d(X_d^B B^f/X_d^B B^d)]$ in Eq. (7.5.16):

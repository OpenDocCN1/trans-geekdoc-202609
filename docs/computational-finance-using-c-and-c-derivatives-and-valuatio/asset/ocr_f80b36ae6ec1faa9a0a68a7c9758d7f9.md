# 230 CHAPTER |7 Other Financial Derivatives

$P$ – the swap principal.
$	ilde{C}$ – the fixed coupon of the reference bond.
$t_m$ – the swap maturity.
$t_R$ – the maturity of the reference bond.
$B_0$ – the initial price of the reference bond.
$B(t_m)$ – the final price of the reference bond (at swap maturity).
C_j$ – the floating coupon payment at time $t_j$. It is computed as
$C_j = P\{F(t_{j-1}, t_j) + margin^{TRS}\{t_j - t_{j-1}\}$
$DF(t_1, t_2)$ – the discount factor between times $t_1$ and $t_2$ (as seen from time $t_i$) is

```
$DF(t_1, t_2) = \frac{D(t_2)}{D(t_1)}$
```

$\overline{DF(t_1, t_2)}|t$ – the default discount factor between times $t_1$ and $t_2$ (as seen from time $t_i$)

```
$$\overline{DF(t_1, t_2)}|t = \frac{\overline{DF(t_1, t_2)}}{\overline{DF(t_1, t_1)}} = \frac{DF(t_1, t_2) S(t_2)}{DF(t_1, t_1) S(t_1)}$
```

$\overline{DF(t_1, t_1)}$ – the default discount factor between times $t$ and $t_1$ is

```
$DF(t_1, t_1) = DF(t, t_1)S(t, t_1)$
```

# 7.5 EQUITY DERIVATIVES

# 7.5.1 TRS

An equity TRS consists of an equity leg (whose coupons are determined by the change in value of the equity) and a floating leg which pays according to the forwards of the interest rate.
Here, we ignore the effect of equity dividends and also assume that the currencies for both the floating and equity legs of the swap are

# Equity Leg

Let the equity leg be specified by coupon payments at times $t_k, k=1, \dots, N_e$, where $	au_k = t_k - t_{k-1}$. If time $t$ the next coupon payment occurs at $t_i$, then the value of the equity leg is

```
$V_e(t) = \frac{S(t)}{DF(t, t_i)} - L(t_{i-1}) DF(t, t_i) + \sum_{k=i+1}^{N_e} \frac{S(t)}{DF(t, t_k)} \frac{S(t)}{DF(t, t_{k-1})} DF(t, t_k), (7.5.1)$
```

Where $S(t)$ is the equity at current time $t$, $L(t_{i-1})$ is the reset value of the equity at time $t_{i-1}$, and $DF(t, t_k)$ is the discount factor between times $t$ and $t_k, t_k > t$. It can be seen that the value of the equity $S(t_i)$ at time $t_i > t$ is obtained by inflating the current value, and $S(t)$ by the reciprocal of the discount factor, $DF(t, t_i)$, that is, $S(t_i) = S(t)/DF(t, t_i)$
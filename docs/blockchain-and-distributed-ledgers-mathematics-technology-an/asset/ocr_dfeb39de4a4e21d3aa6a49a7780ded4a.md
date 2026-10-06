# 350 | Blockchain Distributed Ledgers: Mathematics, Technology, and Economics

Finally, when

frac{x_0^2}{(1+\varepsilon)} \le P_1 \le (1+\varepsilon)x_0^2, \quad (10.81)$

it is suboptimal to adjust the composition of the pool, so that $(x_t^*, y_t^*) = (x_0, y_0)$.\nEqs (10.78), (10.80), and (10.81) show that for nonzero transaction costs the actual composition of the pool is not only time-dependent, which is, of course, expected, but surprisingly, path-dependent.

Let us study the profitability of a liquidity provider following a constant product rule. Clearly, profitability depends on the behavior of the price $P(t)$. We assume that $P(t)$ is mean-reverting and is driven by Ornstein-Uhlenbeck process:

$P(t) = \exp(p(t)),$$

$dp(t) = -\kappa p(t)dt + \sigma dW(t), \quad p(0)=0. \quad (10.82)$

Here $W(t)$ is the Wiener process driving variations of the log-price, $\kappa$ is mean-reversion rate, and $\sigma$ is volatility; $\kappa$ and $\sigma$ are measured in the units of $[1/\sqrt{T}]$, respectively. For small $\kappa$, the price is only weakly mean-reverting, while for large $\kappa$, it mean-reverts quickly. When $\sigma$ is small, the log-price is almost deterministic, when it is large stochastically. Since small price changes do not result in adjustments of portfolio composition, we can discretize the equation with a time step $\Delta t$, and rewrite it as:

$P(t) = \exp(p(t)),$$

$P_{n+1} = (1-\tilde{\kappa})P_n + \tilde{\sigma}\eta_n, \quad P_0=0. \quad (10.83)$

Here $	ilde{\kappa} = \kappa\Delta t, \tilde{\sigma} = \sigma\sqrt{\Delta t}$, and $\eta_n$ is the normal random variable.\nWe assume that pool's liquidity provider has a time horizon $T=N\Delta t$. The evolution of the system is driven by the following system of nonlinear equations:

$p_{n+1} = (1-\tilde{\kappa})p_n + \tilde{\sigma}\eta_n, \quad p_0=0,\nnx_{n+1}=f(p_{n+1},x_n), \quad x_0=1,\ny_{n+1}=1/x_{n+1},\np_n=\exp(p_n). \quad (10.84)$

> ⁴Of course, since $\kappa$ and $\sigma$ are dimensional quantities, their size should be measured relative to the time period of interest, $T$, and their relative magnitude, $\kappa/\sigma^2$.
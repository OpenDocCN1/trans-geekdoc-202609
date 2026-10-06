# 3. Consider the following GBM process with jumps:

```
$$\frac{dS_t}{S_t} = (\mu - \lambda k)dt + \sigma dW_t + (Y_t - 1)dq_t,$
```

$q_t$ is a Poisson process with intensity $\lambda, Y_t-1$ is the magnitude of the jumps in price returns ($Y_t \geq 0$), and $k$ is the expected jump magnitude of $E(Y_t-1)$. Their symbols have the same distribution. If log $(Y_t) \sim N(\mu,\delta)$ then the value of European put and call options are the same as in Section 4.4.3 but with $r$ replaced by $r-\lambda k+n/r$ and $\sigma$ replaced by $\sqrt{\sigma^2+n\delta^2/r}$

# 4. The Hull and White stochastic differential equation for the short rate

```
$dr_t = (Theta_t - ar_t)dt + \sigma dW_t, \quad dB_t = B_t r_t dt,$
```

where $B$ is the money account, $\alpha > 0$ is the rate of mean reversion, and $\beta$ is the long run mean. Show that the price of a discount bond at time $T$, $P(t,T)$ is given

```
$P(t,T) = exp(A(t,T)-r_t B(t,T)),$
```

where

```
$B(t,T) = \frac{1}{a}\{1-\exp(-a(T-t))\}$
```

and

```
$A(t,T) = \log\frac{P(0,T)}{P(0,t)} - \frac{\log(P(0,t))}{\partial t}B(t,T)-\frac{\sigma^2}{4a}B^2(t,T)(1-\exp(-2at)).$.
```

# 5. The Vasicek Model for the short rate $r$ is defined by where

```
$dr_t = \alpha(\beta-r_t)dt+\sigma dW_t, \quad dB_t = B_tr_t dt,$
```

where $B$ is the money account, $\alpha > 0$ is the rate of mean reversion, and $\Theta_t$ is a time dependent mean. Show that the price of a discount bond at time $T$, $P(t,T)$ is given

```
$P(t,T) = C(t,T)\exp(-r_t A(t,T)),$
```

```
$A(t,T) = \frac{1}{\alpha}\{1-\exp(-\alpha(T-t))\}$
```

and

```
$C(t,T) = exp\left{\frac{\alpha^2\beta-\frac{\sigma^2}{2}}}{\alpha^2}(A(t,T)-T+t)\frac{\sigma^2}{4\alpha}A(t,T)^2\right\}$.
```
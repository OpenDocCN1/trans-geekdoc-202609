# 6(b)

Taking expectations of the expression for $X_t$ derived in part (a)

```
$E[X_t] = m + (X_{t_0} - m) \exp(-t)$
```

where we have used

```
$E[\int_{s=0}^{t} \exp(s) dW_s\] = 0$
```

```
$Var[X_t] = E[(X_t - E[X_t])^2]$
```

```
$= E[\sigma^2 \exp(-2t) {\int_{s=0}^{t} \exp(s) dW_s\}^2]$
```

```
$= \sigma^2 \exp(-2t) E[{\int_{s=0}^{t} \exp(s) dW_s\}^2]$
```

From Ito's isometry

```
$Var[X_t] = \sigma^2 \exp(-2t) {\int_{s=0}^{t} \exp(2s) ds\]$
```

```
$= \sigma^2 \exp(-2t) {\frac{\exp(2s)}{2}}_{s=0}$
```

```
$= \sigma^2 \exp(-2t) {\frac{\exp(2t)}{2} - \frac{1}{2}}$
```

which gives

```
$Var[X_t] = \frac{1}{2\sigma^2} {1 - \exp(-2t)}$
```

# Problem 7

Consider the equation $dS_t = \mu_t S_t dt + \sigma_t S_t dW_t$ where the value of $S_t$ at time $t=0$ is denoted by $S_0$.

+   (a) Show that the mean is

```
$E[log(S_t)] = \log(S_0) + \int_{\tau=0}^{t} {\mu_	au - \frac{\sigma_	au^2}{2}} d\tau$
```

+   (b) Show that the variance is

```
$Var[log(S_t)] = \int_{\tau=0}^{t} \sigma_	au^2 d\tau$
```
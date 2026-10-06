# The Ornstein Uhlenbeck Bridge Section | 2.11 25

The transition density from $X_0$ to $X_t$ is

```
$P(X_t|X_0) = \sqrt{\frac{K}{2\pi(1-y^2)}} \exp\left\{ \frac{K(X_t - X_0) \exp(-\alpha(t-t_0))}{(1-y^2)} ight\} \quad (2.10.14)$
```

where $K = 2\alpha/\sigma^2$ and $y = \exp(-\alpha(t-t_0))$.\nOrnstein Uhlenbeck stochastic paths can be simulated using

```
$X_{t+dt} = X_t \exp(-\alpha dt) + \sigma \sqrt{\frac{1-\exp(-2\alpha dt)}{2\alpha}} dZ. \quad (2.10.15)$
```

From equation (2.10.14), we can write

```
$E[X_{t+dt}|X_t] = X_t \exp(-\alpha dt)\nVar[X_{t+dt}|X_t] = \sigma^2 \left\{ \frac{1-\exp(-2\alpha dt)}{2\alpha} ight\.$
```

We will now show that in the limit $dt \to 0$ equation (2.10.15) reduces to GBM.\n small $dt$, we can take a first order expansion of the exponentials in (2.10.15) to obtain

```
$X_{t+dt} = X_t (1-\alpha dt) + \sigma \sqrt{\frac{1-(1-2\alpha dt)}{2\alpha}} dZ,$
```

```
$X_{t+dt} = X_t - \alpha X_t dt + \sigma \sqrt{\frac{(2\alpha dt)}{2\alpha}} dZ.$
```

so\nTherefore,

```
$X_t - X_t = -\alpha X_t dt + \sigma \sqrt{dt} dZ.$
```

This can be expressed as\nwhich is GBM with drift $-\alpha$ and volatility $\sigma$.

```
$dX_t = -\alpha X_t dt + \sigma dW_t.$
```

# 21.1 THE ORNSTEIN UHLENBEC BRIDGE

Let an Ornstein Uhlenbeck process have value $X_0$, at time $t_0$ and $X_{t_1}$, at time $t_1$. We are interested in the distribution of $X_t$ at an intermediate point, that is, $P(X_t|{X_0, X_{t_1}\})$, where $t_0 < t < t_1$.\We will show that $X_t$ is a Gaussian with conditional mean

```
$\mu_t = X_0 \exp(-\alpha(t-t_0)) \left\ \frac{1-\exp(-2\alpha(t_1-t))}{1-y^2} \right\, \n+ X_{t_1} \exp(-\alpha(t_1-t)) \left\ \frac{1-\exp(-2\alpha(t_1-t))}{1-y^2} \right\. \quad (2.11.1)$
```
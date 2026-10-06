# Two-asset Options Section | 6.5 185

Therefore,

$E^Q[\max(S_T - 1, 0)] = \exp(r	au)SN_1(d_1) - N_1(d_2).$

Using the mapping defined in equation (6.5.4), we have

```
$E^Q\left[\max\left(\frac{S_T^B}{S_T^A}-1, 0\right)\right] = \left\frac{S_T^B}{S_T^A}N_1(d_1) - N_1(d_2)\right]$
```

and so from equation (6.5.1).

```
$V(t_0) = S_{t_0}^B N_1(d_1) - S_{t_0}^A N_1(d_2),$
```

which means that the value of the exchange option at time $t_0$ is

```
$V(t_0) = S_{t_0}^B N_1(d_1) - S_{t_0}^A N_1(d_2),$
```

where

```
$d_1 = \frac{\log(\frac{S_{t_0}^B}{S_{t_0}^A}) + \frac{1}{2}(T-t_0)\sigma^2}{\sigma\sqrt{T-t_0}}
nd_2 = \frac{\log(\frac{S_{t_0}^B}{S_{t_0}^A}) - \frac{1}{2}(T-t_0)\sigma^2}{\sigma\sqrt{T-t_0}}$
```

# 6.5.2 European Options on the Maximum or Minimum

We present the results from Stulz (1982) and Johnson (1987) concerning the value of a European call option on the maximum and minimum of two assets, see Code excerpts 6.2 and 6.3 and results in Tables 6.3 and 6.4.

# Call Options on the Maximum and Minimum of Two Assets

Let the value of a European call option on the minimum of two assets, $S_1$ and $S_2$, with strike price $E$, maturity $	au$, and correlation coefficient $ho$ be denoted by $c_{\min}$. The value of the corresponding call option on the maximum will be represented by $c_{\max}$.

Then, Stulz (1982) and Johnson (1987), we have

```
$c_{max} = S_1 N(d_1(S_1, E, \sigma_1^*)) + S_2 N(d_1(S_2, E, \sigma_2^*)) - E e^{-r\tau}\{N(d_2(S_1, E, \sigma_1^*)) + N(d_2(S_2, E, \sigma_2^*))\}$
```

and

```
$c_{min} = S_1 N(d_1(S_1, E, \sigma_1^*)) + S_2 N(d_1(S_2, E, \sigma_2^*)) - E e^{-r\tau}N_2(d_2(S_1, E, \sigma_1^*), d_2(S_2, E, \sigma_2^*), \rho)$
```

where $N_2(a, b, \rho)$ is the bivariate cumulative distribution. It gives the cumulative probability, in a standardized bivariate normal distribution, that the variables $x_1$
# Table 6.1 The computed values and absolute errors, in brackets, for European options
on the maximum of three assets

| Nsim | Quasi | Put |
|---|---|---|n| 500 | 0.890 ($4.5984 \times 10^{-2}$) | 1.1044 ($1.6839 \times 10^{-1}$) |
| 1000 | 0.924 ($1.1534 \times 10^{-2}$) | 1.0193 ($8.3297 \times 10^{-2}$) |
| 1500 | 0.919 ($2.2954 \times 10^{-2}$) | 0.8957 ($4.0344 \times 10^{-2}$) |
| 2000 | 0.932 ($4.3221 \times 10^{-3}$) | 0.8995 ($3.6488 \times 10^{-2}$) |
| 2500 | 0.932 ($3.5698 \times 10^{-3}$) | 0.8886 ($4.7352 \times 10^{-2}$) |
| 3000 | 0.937 ($1.1376 \times 10^{-3}$) | 0.9025 ($3.3548 \times 10^{-2}$) |

| | Quasi | Put |
|---|---|---|n| 500 | 22.629 ($2.6312 \times 10^{-2}$) | 22.4089 ($2.6312 \times 10^{-1}$) |
| 1000 | 22.683 ($1.1306 \times 10^{-2}$) | 22.3520 ($3.1998 \times 10^{-1}$) |
| 1500 | 22.670 ($2.2954 \times 10^{-3}$) | 22.6346 ($3.7430 \times 10^{-2}$) |
| 2000 | 22.685 ($1.3299 \times 10^{-2}$) | 22.7675 ($9.5491 \times 10^{-2}$) |
| 2500 | 22.670 ($1.6639 \times 10^{-3}$) | 22.9326 ($2.6058 \times 10^{-1}$) |
| 3000 | 22.679 ($7.2766 \times 10^{-3}$) | 22.8050 ($1.3301 \times 10^{-1}$) |

Monte Carlo simulation was used with quasirandom (Sobol) sequences and pseudo-random sequences. The number of paths used from 500 to 3000. Parameters were: $E=100.0, S_1 = S_2 = S_3 = 100.0, r = 0.1, \tau = 1.0, \sigma_1 = \sigma_2 = \sigma_3 = 0.2, \rho_{12} = \rho_{13} = \rho_{23} = 0.5, q_1 = q_2 = q_3 = 0.0$. The *accurate* values were 0.936 for a put and call; see Table 6.7 and Table 2 of Boyle, Evnine, and Gibbs (1989).

where we used the notation $S_{i,t}$ to denote the value of the asset at current time $t$, and $S_{i,t+dt}$ to denote the value of the asset at the future time $t+dt$. Simple rearrangement of the following equations gives:

```
$$\log\left(\frac{S_{i,t+dt}}{S_{i,t}}\right) = \left(r - \frac{\sigma_i^2}{2}\right)dt + \sigma_i dW_i, \quad i = 1, \dots, m$$
```

Taking exponentials of both sides gives:

which is equivalent to:

```
$S_{i,t+dt} = S_{i,t} \exp\left\leftleft(r - \frac{\sigma_i^2}{2}\right)dt + \sigma_i dW_i\right\right), \quad (6.3.1)$
```
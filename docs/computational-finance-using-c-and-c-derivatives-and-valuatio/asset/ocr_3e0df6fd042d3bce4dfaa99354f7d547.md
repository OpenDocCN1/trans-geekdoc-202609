# 190 CHAPTER | 6 Multi-asset Options

**TABLE 6.3** The Computed Values and Absolute Errors for European Put and Call Options on the Maximum of Two Assets. The Results were Obtained using a Binomial Lattice and the Analytic Formula (Johnson (1987) and Stulz (1982). The Time to Maturity of the Option is Varied from 0.1 to 0.8 Years. The Parameters are $\hat{E} = 44.0, S_1 = 40.0, S_2 = 50.0, r = 0.1, \sigma_1 = 0.2, \sigma_2 = 0.2, q_1 = q_2 = 0.0, ho = 0.5,$ and $n_{steps} = 50$

| Time | Analytic | Error | Put | Analytic | Error |
|---|---|---|---|---|---||
| 0.1 | 6.45320 | 6.45245 | $7.4972	imes 10^{-4}$ | 0.01524 | 0.01451 | $7.3344	imes 10^{-4}$ |
| 0.2 | 6.91692 | 6.99593 | $2.3845	imes 10^{-3}$ | 0.08252 | 0.08001 | $2.5106	imes 10^{-3}$ |
| 0.3 | 7.49587 | 7.49376 | $2.1084	imes 10^{-3}$ | 0.15717 | 0.15580 | $2.0675	imes 10^{-3}$ |
| 0.4 | 8.03710 | 8.04022 | $3.1260	imes 10^{-3}$ | 0.22362 | 0.22680 | $3.1678	imes 10^{-3}$ |
| 0.5 | 8.57808 | 8.57916 | $1.0577	imes 10^{-3}$ | 0.27762 | 0.27683 | $7.8867	imes 10^{-4}$ |
| 0.6 | 9.11529 | 9.10810 | $7.2006	imes 10^{-3}$ | 0.32115 | 0.31872 | $2.4328	imes 10^{-3}$ |
| 0.7 | 9.64700 | 9.64388 | $1.3826	imes 10^{-3}$ | 0.35598 | 0.35714 | $1.1548	imes 10^{-3}$ |
| 0.8 | 10.17238 | 10.17663 | $4.2571	imes 10^{-3}$ | 0.38372 | 0.38711 | $3.3891	imes 10^{-3}$ |

In the binomial model, over the interval $\Delta t$, the variate $\log(S_{1,t})$ is only permitted to jump up or down by an variate $v_1 = \sigma_1\sqrt{\Delta t}$, and similarly the variate $\log(S_{2,t})$ is only permitted to jump up and down by the $v_2 = \sigma_2\sqrt{\Delta t}$. We will denote the probability of both $\log(S_{1,t})$ and $\log(S_{2,t})$ having an up-jump over $\Delta t$ by $P_{uu}$, and the probability of $\log(S_{1,t})$ having an up-jump and $\log(S_{2,t})$ having a down-jump by $P_{ud}$, etc. The mean values in equation (6.5.10) and equation (6.5.11) then yields

```
$E[\epsilon_{1,t}] = v_1(P_{uu} + P_{ud} - P_{du}) = \mu_1\Delta t$,n$E[\epsilon_{2,t}] = v_2(P_{uu} + P_{ud} - P_{du}) = \mu_2\Delta t$,
```

and the variance/covariance terms yields

```
$Var[\epsilon_{1,t}] = v_1^2(P_{uu} + P_{ud} + P_{du}) = \sigma_1^2\Delta t$,n$Var[\epsilon_{2,t}] = v_2^2(P_{uu} + P_{ud} + P_{du}) = \sigma_2^2\Delta t$,n$E[\epsilon_{1,t}\epsilon_{2,t}] = v_1v_2(P_{uu} + P_{ud} - P_{du}) = ho\sigma_1\sigma_2\Delta t$,
```

where $ho$ is the correlation coefficient between $\epsilon_{1,t}$ and $\epsilon_{2,t}$.nWe obtain

```
$P_{uu} + P_{ud} - P_{du} = \frac{\mu_1\sqrt{\Delta t}}{\sigma_1}$
```
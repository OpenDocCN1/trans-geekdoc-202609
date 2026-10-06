# Chapter 10 Cryptocurrencies and Quantitative Finance | 309

![](bbox=[0.283, 0.087, 0.715, 0.617])

**Figure 10.9 BTC returns:** (a) one-year risk-neutralized characteristic function; (b) one-year risk-neutralized pdf. Own graphics.

By symmetry, the latter integral is real-valued. It can be computed efficiently by using the Fast Fourier Transform (FFT). We show $f_{Y_{\chi}}(x)$ in Figure 10.8 (b).

It is clear that the expected value of BTC returns is positive, due to its *overall* upward sloping trajectory of the price. The expectation of the generalized hyperbolic distribution is given by

```
$E = \mu + \frac{\delta K_{\lambda+1}(\delta\gamma)}{\gamma K_{\lambda}(\delta\gamma)}.$quad (10.27)
```

For the set of calibrated parameters from Table 10.2, we get $E = 0.0018$.

However, in order to avoid a possible bias, as well as for pricing of options on BTC in the risk-neutral measure, we have to choose $\hat{\mu}$ in such a way that $E=0$. The corresponding $\hat{\mu}=-0.0007$. For the risk neutralized parameter set $(\alpha, \beta, \delta, \hat{\lambda}, \hat{\mu})$ we get $\phi_{\hat{Y}_{\chi}}(x), \f_{\hat{Y}_{\chi}}(x)$ shown in Figure 10.9.
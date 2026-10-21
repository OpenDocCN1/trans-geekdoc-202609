Now combine the two exponents

$$\exp\left\{ -\frac12 t \left[ (K^2 - 2\mu_K K + \mu_K^2 - 2\sigma_K^2 K)/\sigma_K^2 \right] \right\}.$$

Now, multiply and divide this result by $\exp\left(-\frac12 \sigma_K^2 t\right)$ to get

$$\exp\left\{ -\frac12 t \left[ (K^2 - 2\mu_K K + \mu_K^2 - 2\sigma_K^2 K + \sigma_K^4 - \sigma_K^4)/\sigma_K^2 \right] \right\}.$$

Next, rearrange and combine terms to get

$$\exp\left\{\left(-\frac12 t\right)\left[(K - \mu_K - \sigma_K^2)^2 - \sigma_K^4 - 2\mu_K\sigma_K^2\right]/\sigma_K^2\right\}
= \exp\left[(\mu_K + \frac12\sigma_K^2) t\right] \exp\left\{ -\frac12 [K t - (\mu_K + \sigma_K^2) t]^2/\sigma_K^2 t \right\}.$$ 
(27A.8)

In equation (27A.8), $\exp\left[(\mu_K + \frac12\sigma_K^2) t\right] = E(S_t/S)$, the mean of the $t$-period log-normally distributed price ratio $S_t/S$. So, equation (27A.7) becomes

$$S \exp(-r t) E_{x/S}\left(\frac{S_t}{S}\right) = S E\left(\frac{S_t}{S}\right) \exp(-r t) (2\pi\sigma_K^2 t)^{-1/2}
\times \int_{\ln(x/S)}^{\infty} \exp(K t)
\exp\left\{ -\frac12 [K t - (\mu_K + \sigma_K^2) t]^2/\sigma_K^2 t \right\}.$$ 
(27A.9)

Since the equilibrium rate of return in a risk-neutral economy is the riskless rate, $E(S_t/S)$ may be rewritten as $\exp(r t)$

$$S E\left(\frac{S_t}{S}\right) \exp(-r t) = S \exp(r t) \exp(-r t)
= S.$$

So, equation (27A.9) becomes

$$S \exp(-r t) E_{x/S}\left(\frac{S_t}{S}\right)
= S (2\pi\sigma_K^2 t)^{-1/2} \int_{\ln(x/S)}^{\infty} \exp\left\{ -\frac12 [K t - (\mu_K + \sigma_K^2) t]^2/\sigma_K^2 t \right\} t \, dK.$$ 
(27A.10)
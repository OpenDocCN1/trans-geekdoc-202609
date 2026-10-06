# Selected Exercises Section | 4.6 91

Hence, show that the value of a call European option is

$c(S, E, 	au) = SN_1(d_1) - e^{-r	au}EN_1(d_2),$

where

$d_2 = \frac{\log(S/E) + (r - \frac{1}{2}\sigma^2)\tau}{\sigma\sqrt{\tau}} = d_1 - \sigma\sqrt{\tau}$

and

$\hat{\sigma}^2 = \frac{\sigma^2}{2\alpha}(1 - \exp(-2\alpha T)).$

+   4. Let the price of an asset, $S_t$, follow GBM, and also the interest rate be $r = 0$. Show that the conditional variance, $Var(S_t|S_t \geq K)$, when $S_t$ is greater or equal to $K$ is given by

$Var(S_t|S_t \geq K) = S_t^2 \exp(\sigma^2\tau)N(d_3) - 2KN(d_1) + K^2N(d_2) - C(S,K,\tau)^2$,

where $C(S,K,\tau)$ follow a Weibull distribution of a European call option

$d_1 = \frac{\log(S/K) + \frac{1}{2}\sigma^2\tau}{\sigma\sqrt{\tau}}, \quad d_2 = \frac{\log(S/K) - \frac{1}{2}\sigma^2\tau}{\sigma\sqrt{\tau}}$

$d_3 = \frac{\log(S/K) + \frac{3}{2}\sigma^2\tau}{\sigma\sqrt{\tau}}$

+   5. Let the variable $X$ follow a Weibull distribution with density function

$f(X) = \alpha\beta X^{\beta-1} \exp(-\alpha X^{\beta}).$.

The value of a call option $C(X,K)$ is obtained by evaluating the integral $\int_{-\infty}^{\infty} (X-K)^+ \alpha\beta X^{\beta-1} \exp(-\alpha X^{\beta})dX$.

Show that

$C(X,K) = \frac{1}{\alpha^{\beta}} \Gamma(1+\frac{1}{\beta}) \left\{1-P(1+\frac{1}{\beta},\alpha K^{\beta})\right\} - K\exp(-\alpha K^{\beta}),$

where $P(a,b)$ is the incomplete gamma function given by

$P(a,b) = \frac{1}{\Gamma(a)} \int_{0}^{b} \omega^{a-1} \exp(-\omega)dw$,

and $\Gamma(a)$ is the gamma function.
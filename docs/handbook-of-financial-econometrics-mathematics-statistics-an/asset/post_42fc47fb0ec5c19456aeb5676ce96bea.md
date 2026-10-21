
where $h(S_t)$ is the log-normal density function of $S_t$. To evaluate the integral in (27A.2) rewrite it as the difference between two integrals

$$C = \exp(-rt)\left[\int_x^{\infty} S_t h(S_t) dS_t - X \int_x^{\infty} h(S_t) dS_t\right]$$
$$= E_x(S_t) \cdot \exp(-rt) - X \cdot \exp(-rt) \cdot [1 - H(X)],$$ (27A.3)

where $E_x(S_t)$ is the partial expectation of $S_t$, truncated from below at $x$, and $H(X)$ is the probability that $S_t \le X$.

Equation (27A.3) says that the value of the call option is present value of the partial expected stock price (assuming the call expires in the money) minus the present value of the exercise price (adjusted by the probability that the stock’s price will be less than the exercise price at the expiration of the option). The terminal stock price $S_t$, can be rewritten as the product of the current price ($S$) and the $t$-period log-normally distributed price ratio $S_t/S$, so $S_t = S(S_t/S)$. Equation (27A.3) can also be rewritten as:

$$C = \exp(-rt)\left[ S \int_{x/s}^{\infty} \frac{S_t}{S} g\left(\frac{S_t}{S}\right)\left(\frac{dS_t}{S}\right) - X \int_{x/s}^{\infty} g\left(\frac{S_t}{S}\right)\left(\frac{dS_t}{S}\right)\right]$$
$$= S \exp(-rt)E_{x/S}\left(\frac{S_t}{S}\right) - X \exp(-rt)\left[1 - G\left(\frac{X}{S}\right)\right],$$ (27A.4)

where $g(S_t/S)$ is log-normal density function of $S_t/S$; $E_{x/S}(S_t/S)$ is the partial expectation of $S_t/S$, truncated from below at $x/S$; $G(X/S)$ is the probability that $S_t/S \le X/S$.

## Appendix 27A.2: *Present value of the partial expectation of the terminal stock price*

The right-hand side of equation (27A.4) is evaluated by considering the two integrals separately. The first integral, $S \exp(-rt)E_{x/S}(S_t/S)$, can be solved by assuming the return on the underlying stock follows a stationary random walk, that is,

$$\frac{S_t}{S} = \exp(Kt),$$ (27A.5)

where $K$ is the rate of return on the underlying stock per unit of time. Taking the natural logarithm of both sides of equation (27A.5) yields

$$\ln\left(\frac{S_t}{S}\right) = (Kt).$$

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

To complete the simplification of this part of the Black–Scholes formula, define a standard normal random variable $y$

$$y = [Kt - (\mu_K + \sigma_K^2) t]/\sigma_K t^{1/2}.$$

Solving for $Kt$ yields

$$Kt = (\mu_K + \sigma_K^2) t + \sigma_K t^{1/2} y$$

and therefore

$$t\,dK = \sigma_K t^{1/2} dy.$$

By making the transformation from $Kt$ to $y$ the lower limit of integration becomes

$$[\ln(x/S) - (\mu_K + \sigma_K^2) t]/\sigma_K t^{1/2}.$$

Further simplify the integrand by noting that the assumption of a risk-neutral economy implies

$$\exp[(\mu_K + \frac12 \sigma_K^2) t] = \exp(rt).$$

Taking the natural logarithm of both sides yields

$$(\mu_K + \frac12 \sigma_K^2) t = (rt).$$

Hence, $(\mu_K + \frac12 \sigma_K^2) t = (r + \frac12 \sigma_K^2) t.$

The lower limit of integration is now

$$-[\ln(S/x) + (r + \frac12 \sigma_K^2) t]/\sigma_K t^{1/2} = -d_1.$$

Substituting this into equation (27A.10) and making the transformation to $y$ yields

$$S \exp(-rt)E_{x/S}\left(\frac{S_t}{S}\right) = S \int_{-d_1}^{\infty} \exp(-\frac12 y^2)/(2\pi)^{1/2} dy.$$

Since $y$ is a standard normal random variable (distribution is symmetric around zero) the limits of integration can be exchanged

$$S \exp(-rt)E_{x/S}\left(\frac{S_t}{S}\right) = S \int_{\infty}^{-d_1} \exp(-\frac12 y^2)/(2\pi)^{1/2} dy = S N(d_1), \qquad (27A.11)$$

Taking the natural logarithm of both sides yields

(μ_K + ½σ_K²) t = rt

or

μ_K t = (r - ½σ_K²) t.

Therefore, the lower limit of integration becomes

−[ln(S/x) + (r - ½σ_K²) t]/σ_K t^{1/2} = −(d_1 - σ_K t^{1/2})

= −d_2.

Substitution yields

x exp(−rt)[1 − G(X/S)] = x exp(−rt) ∫_{−d_2}^∞ exp[−½ Z²]/(2π)^{1/2} dZ

= x exp(−rt) ∫_{−∞}^{d_2} exp[−½ Z²]/(2π)^{1/2} dZ

= x exp(−rt) N(d_2),

where N(d_2) is the standard normal cumulative distribution function evaluated at Z = d_2.

Substituting equation (27A.11) and (27A.13) into equation (27A.4) completes the derivation of the Black–Scholes formula:

C = S N(d_1) − X exp(−rt) N(d_2). (27A.14)

This appendix provides a simple derivation of the Black–Scholes call-option pricing formula. Under an assumption of risk neutrality, the Black–Scholes formula was derived using only differential and integral calculus and a basic knowledge of normal and log-normal distributions.

> > 合抱之木，生于毫末；九层之台，起于累土；千里之行，始于足下。
> >
> > ——老子

- DWH can also be applied to test alternative theoretical models (e.g., Chermak and Patrick, 2001).
- Incorrect functional form and contemporaneous correlation in the lagged dependent variable — serial correlation model.
- Testing for influential outliers (Dehon et al., 2009).

This chapter presents Durbin, Wu, and Hausman (DWH) specification tests and provides examples of their application. Background literature is briefly discussed in the following section. We then present a general development of the test, discuss implementation of the test in general, computational issues, and provide IV and panel data examples of applications and interpretation of results.

## 28.2 Background

There are two distinct forms of misspecification error:

- 1. the conditional mean E(y|Ω) might not equal βX, which largely concerns bias and inconsistency of parameter estimates, and
- 2. the errors and the constant variance may not be independent (disturbances are non-spherical, i.e., heteroskedastic and/or autocorrelated), affecting efficiency of the standard error estimates.

Since 2 is conditional on 1, the first form of misspecification is a natural starting place in specification testing. DWH tests are used to test for specification errors under 1, they examine possible misspecification errors that lead to a shift in the central tendency of the estimator, i.e., they focus on orthogonality, E(X'e)=0 or, in large samples, plim (X'e / T)=0. So if an estimator were unbiased then the specification error leads to bias. If an estimator were biased but consistent, the error leads to a different bias and inconsistency. For example, the instrumental variables (IV) estimator provides consistent parameter estimates, but with a loss in efficiency. So a natural question arises, is there statistical dependence between explanatory variable(s) and the error? If so, as discussed above, IV will provide consistent parameter estimates while LS estimates will be biased and inconsistent. If not, both LS and IV provide consistent parameter estimates, but LS would be the preferred estimator because it is relatively efficient.

Durbin (1954) developed a specification test comparing LS and IV parameter estimates to address this LS versus IV specification issue. Although not widely applied, Leviatan (1963) and Lee (1973) empirically applied Durbin's specification test.

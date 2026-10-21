
Observe that in equation (27.34),

$$\mu_C C = C_t + C_S \mu S + \tfrac12 C_{SS} \sigma^2 S^2 \tag{27.35}$$
$$\sigma_C C = C_S \sigma S. \tag{27.36}$$

In other words, $\mu_C C$ is the expected change in the call-option price and $\sigma_C^2 C^2$ is the variance of such a change per unit of time. Itô’s lemma simply indicates that if the call-option price is a function of a spot stock price that follows an Itô process, then the call-option price also follows an Itô process with mean and standard deviation parameters that are more complex than those of the stock price. The Itô process for a call is given by equations (27.35) and (27.36).

The infinitesimal change in the value of the portfolio $dP$ is caused by the change in the prices of the assets. This follows from the fact that their respective quantities are rebalanced only after first taking into account the change on the asset prices, in other words the rebalancing strategy is previsible. Mathematically this is expressed as $dN_1 = dN_2 = 0$, which yields

$$dP = N_1 (dS) + N_2 (dC) + dQ$$
$$= (\mu dt + \sigma dZ) N_1 S + (\mu_C dt + \sigma_C dZ) N_2 C + r Q \, dt. \tag{27.37}$$

Let $w_1$ be the fraction invested in stock, $w_2$ be the fraction invested in options, and $w_3$ be the fraction invested in the riskless asset. As before, $w_1 + w_2 + w_3 = 1$, that is, all of the funds available are invested in some type of asset and furthermore the dynamic strategy remains at all times self-financing. Set $w_1 = N_1 S / P$, $w_2 = N_2 C / P$, $w_3 = Q / P = 1 - w_1 - w_2$. Then equation (27.37) becomes

$$\frac{dP}{P} = (\mu dt + \sigma dZ) w_1 + (\mu_C dt + \sigma_C dZ) w_2 + (r \, dt) w_3. \tag{27.38}$$

At this point, the notion of economic equilibrium (also called risk-neutral or preference-free pricing) is introduced in the analysis. This notion plays an important role in modeling financing behavior, and its appropriate formulation is considered to be a major breakthrough in financial analysis.

More specifically, design the proportions $w_1, w_2$ so that the position is riskless for all $t \ge 0$, that is, let $w_1$ and $w_2$ be such that

$$\operatorname{Var}\left(\frac{dP}{P}\right) = \operatorname{Var}(w_1 \sigma dZ + w_2 \sigma_C dZ) = 0. \tag{27.39}$$

Using the same notation as in Section 27.5, equation (27.46) differs from equation (27.33) because the term $Q(t)$ has been deleted. Now concentrating on the two assets of the portfolio, that is, the stock and the call option — and using equations (27.46) and (27.34), the change in the value of the portfolio is given by

$$dP = N_1 dS + N_2 dC = N_1 dS + N_2[(C_t + \frac12 C_{SS}\sigma^2 S^2)dt + C_S dS]. \tag{27.47}$$

Note that $dN_1 = dN_2 = 0$, since at any given point in time the quantities of stock and option are already determined from the last rebalancing. For arbitrary quantities of stock and option, equation (27.47) shows that the change in the nominal value of the portfolio $dP$ is stochastic because $dS$ is a random variable. Suppose the quantities of stock and call option are chosen such that

$$\frac{N_1}{N_2} = -C_S. \tag{27.48}$$

Note that $C_S$ in equation (27.48) denotes a hedge ratio and is called delta. Then, $N_1 dS + N_2 C_S dS = 0$, and inserting equation (27.48) into equation (27.47) yields

$$dP = -N_2 C_S dS + N_2[(C_t + \frac12 C_{SS}\sigma^2 S^2)dt + C_S dS] = N_2(C_t + \frac12 C_{SS}\sigma^2 S^2)dt. \tag{27.49}$$

Let $N_2 = 1$ in equation (27.49) and observe that in equilibrium the rate of return of the riskless portfolio must be the same as the riskless rate $r(t)$, otherwise we would have constructed synthetically a riskless asset that earns more (or less) than the tradable riskless asset. Therefore,

$$\frac{dP}{P} = r \, dt. \tag{27.50}$$

Equation (27.50) can be used to derive the partial differential equation for the value of the option. Making the necessary substitutions in equation (27.49):

$$\frac{(C_t + \frac12 C_{SS}\sigma^2 S^2)dt}{-C_S S + C} = r \, dt,$$

which upon rearrangement gives equation (27.45). Note that the option-pricing equation is a second-order linear partial differential equation of the parabolic type. The boundary conditions of equation (27.45) are determined by the specification of the asset. For the case of an option that can be exercised only at the expiration date $t^*$ with an exercise price $X$, the boundary conditions are

$$C(t, S = 0) = 0, \tag{27.51}$$
$$C(t = t^*, S) = \text{Max}(0, S - X). \tag{27.52}$$

Observe that equation (27.51) says that the call-option price is zero if the stock price is zero at any date $t$; equation (27.52) says that the call-option price at the expiration date $t = t^*$ must equal the maximum of either zero or the difference between the stock price and the exercise price.

The solution of the option-pricing equation subject to the boundary conditions is given, for $T = t^* - t$, as

$$C(T, S, \sigma^2, X, r) = S N(d_1) - \frac{X}{e^{rT}} N(d_2), \tag{27.53}$$

where $N$ denotes the cumulative normal distribution, namely:

$$N(y) = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{y} e^{-x^2/2} dx.$$

In equation (27.53), $T$ is time to expiration (measured in years) and $d_1$ and $d_2$ are given by

$$d_1 = \frac{\ln(S/X) + (r + \frac{1}{2}\sigma^2)T}{\sigma\sqrt{T}} \tag{27.54}$$
$$d_2 = \frac{\ln(S/X) + (r - \frac{1}{2}\sigma^2)T}{\sigma\sqrt{T}} \tag{27.55}$$
$$= d_1 - \sigma\sqrt{T}.$$

It can be shown that

$$\frac{\partial C}{\partial T} > 0, \quad \frac{\partial C}{\partial S} > 0, \quad \frac{\partial C}{\partial \sigma^2} > 0, \quad \frac{\partial C}{\partial X} < 0, \quad \frac{\partial C}{\partial r} > 0. \tag{27.56}$$

These partial derivatives justify the intuitive behavior of the price of an option, as was indicated in the beginning of Section 27.5. More specifically, these partials show the following:

- 1. As the stock price rises, so does the option price. Furthermore, if the stock price rises much higher than the strike of the option then the option starts behaving like the stock itself and its sensitivity relative to the stock price converges to 1, i.e., $\partial C / \partial S \to 1$.
- 2. As the variance rate of the underlying stock rises, so does the option price.
- 3. With a higher exercise price, the expected payoff decreases.
- 4. The value of the option increases as the interest rate rises.
- 5. With a longer time to maturity, the price of the option is greater.

## Itô's Calculus and the Derivation of the Black-Scholes Option-Pricing Model

It is worth observing that two terms of equation (27.53) have economic meaning. The first term, $S N(d_1)$, denotes the present value of receiving the stock provided that $S(t^*) > X$. The second term gives the present value of paying the striking price provided that $S(t^*) > X$. In the special case when there is no uncertainty and $\sigma = 0$, observe that

$$N(d_1) = N(d_2) = N(\infty) = 1,$$
$$C = S(t) - e^{-r(t^* - t)} X,$$

that is, a call is worth the difference between the current value of the stock and the discounted value of the striking price provided $S(t^*) > X$; otherwise, the call price would be zero. When $\sigma \neq 0$, that is, when uncertainty exists and the stock price is volatile — the two terms in equation (27.61) are multiplied by $N(d_1)$ and $N(d_2)$, respectively, to adjust the call price for the prevailing uncertainties. These two probabilities can also be given an economic interpretation. As mentioned earlier, $N(d_1)$ is called delta; it is the partial derivative of the call price with respect to the stock price. $N(d_2)$ gives the probabilities that the call option will be in the money, as equation (27.59) shows.

Assuming that investors in the economy have risk-neutral preferences, it will be possible to derive the Black–Scholes formula without using stochastic differential equations. Garven (1986) has shown that to derive equation (27.53) knowledge is required of normal and log-normal distributions and basic calculus, as presented in Appendix 27A. Sample Problem 27.6.1 provides further illustration.

### Sample Problem 27.6.1

Equation (27.53) indicates that the Black–Scholes option-pricing model is a function of only five variables: $T$, the time to expiration, $S$, the stock price, $\sigma^2$, the instantaneous variance rate on the stock price, $X$, the exercise price, and $r$, the riskless interest rate. Of these five variables, only the variance rate must be estimated; the other four variables are directly observable. A simple example is presented to illustrate the use of equation (27.53). The values of the observable variables are taken from Bloomberg on September 20, 2007.

On Wednesday, September 19, the IBM stock price closed at $116.67. To estimate the price of a call option expiring on Friday, October 19, of the same year with an exercise price of $115, the riskless rate and the instantaneous variance need to be estimated. The riskless rate is estimated either by using

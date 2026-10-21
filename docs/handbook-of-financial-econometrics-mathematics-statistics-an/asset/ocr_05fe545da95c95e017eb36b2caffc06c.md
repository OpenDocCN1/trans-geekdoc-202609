He went through some tedious derivations and simplifications, and finally obtained the formula to compute implied standard deviation:

$$\sigma = \frac{2\sqrt{2}}{\sqrt{T}}z - \frac{1}{\sqrt{T}}\sqrt{8z^2 - \frac{6\alpha}{\sqrt{2}z}},\qquad (106.50)$$

where $\alpha = \frac{\sqrt{2}\pi C}{S}$ and $z = \cos[\frac{1}{3}\cos^{-1}(\frac{3\alpha}{\sqrt{32}})]$.

Since Li included the third-order term in the Taylor expansion on the cumulative normal distribution in his derivation, Li claimed that his formula for ISD provided a consistently more accurate estimate of the true ISD than previous studies.

To sum up, the existing researches mainly follow two different routines to estimate implied volatility. Numerical search methods tried to find an approximate solution for implied volatility which makes the theoretical option value equal to or very close to market observed option price. These methods do not provide closed-form solution for estimated implied volatility, and need iterative algorithms to approximate the ISD. Closed-form derivation approaches took use of either Taylor expansion or inverse function to calculate the analytical solutions for the ISD. First-order, second-order, and third-order Taylor expansions were applied to cumulative normal distribution function respectively to estimate the implied volatility in previous studies. There were also studies using inverse function of normal distribution to derive closed-form solution of the ISD.

An important point to be noted is that some methods rely upon the existence of “at-the-money” options, or at least not too far in- or out-of-the-money options. These approaches include Brenner and Subrahmanyam (1988), Chance (1996), and Li (2005).

Table 106.1 classifies the existing researches of estimating implied volatility accordingly.

# 106.3 MATLAB Approach to Estimate Implied Variance

Usually, implied variance can be obtained from a call or put option model by an optimization technique. For each individual option, the implied variance can be obtained by first choosing an initial estimate $\sigma_0$, and then equation (106.51) is used to iterate towards the correct value:

$$C_{j,t}^M - C_{j,t}^T(\sigma_0) = \left[\left.\frac{\partial C_{j,t}^T}{\partial \sigma}\right|_{\sigma_0}\right](\sigma - \sigma_0) + e_{j,t},\qquad (106.51)$$

where
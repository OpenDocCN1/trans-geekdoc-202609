This partial derivative is also called Vega of the option, denoting the rate of change of the value of the option with respect to the volatility of the underlying asset.

The iteration proceeds by reinitializing σ₀ to equal σ₁ at each successive stage until an acceptable tolerance level is attained. The tolerance level used is

$$\left|\frac{\sigma_1 - \sigma_0}{\sigma_0}\right| < 0.001.\tag{103.8}$$

For each option transaction, the iteration procedure is conducted until the implied volatility has converged, and the predicted option price is finally equal to the observed price.² The detailed estimation procedure using the optimization technique in MATLAB is presented in Appendix B.

# 103.3.4 Momentum factor calculation

For the purpose of confirming the momentum return pattern and investigating the relationship between the stock market momentum and the option prices, we adopt the momentum return, WML, which is defined as the difference between the monthly returns on diversified portfolios of the winners and losers of the last year, as the momentum factor. The momentum factor was originally used in Carhart (1997)'s four-factor model and then commonly used in the empirical application, most notably to detail momentum patterns in average stock returns, such as in Fama and French (2012).

Specifically, WML is calculated for portfolios that are constructed from 2 × 3 sorts on size and momentum (Carhart 1997; Fama and French 2012). First, at the end of December of each year y, the stocks in a region are assigned to two size portfolios based on each stock's market cap. Large stocks are those in the top a% of the market cap, and small stocks are those in the bottom (1 − a)%. The choice for the value of a is flexible. In Fama and French (2012), big stocks are those in the top 90% of market cap for the region, and small stocks are those in the bottom 10%. For North America, 90% of market cap corresponds roughly to the NYSE median, used to define small and big stocks in Fama and French (1993). This description determines the size portfolios in the next year. The same stocks are then allocated in an independent

²The tolerance level is set at 0.001%, which means that we consider the procedure converged if the estimated price is within 0.001% of the observed price. In fact, most options converge finally. A small number of options that did not converge are thus removed from the sample, for instance, options with an observed price dissatisfying the inequalities in terms of the upper and lower bounds.
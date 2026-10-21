the length of each time interval.¹² The mean and standard deviation of the variable Xᵢ are denoted by μ and σ̃, respectively.

In Panel A of Table 42.3, in both the subperiods, the 90% risk-neutral confidence interval from puts is significantly wider than that from calls, indicating that put option traders expect higher volatilities in underlying asset prices compared with call option traders. The skewness coefficients shown in Panel B of Table 42.3 reveal that the risk-neutral distribution from puts is more negatively skewed than the distribution from calls. The implication is that if option traders anticipate a negative jump in underlying asset prices, put option traders tend to expect a larger magnitude relative to call option traders. Panel C of Table 42.3 shows that the risk-neutral distribution derived from puts is more leptokurtic and fat-tailed than the distribution from calls. The evidence suggests that, when option traders are unsure of the size and direction of the jump in underlying asset prices, the uncertainty about market volatility for put option traders is higher than for call option traders.

# 42.4 Sentiment Effect on Call and Put Option Prices

# 42.4.1 Rational and irrational sentiment effects on call and put option prices

Table 42.3 summarizes the significant differences in the shape of risk-neutral distributions separately derived from TAIEX call and put option prices. The previous literature shows that sentiment is related to changes in option prices. To find a potential explanation concerning the diversion between call and put option prices, we examine whether a sentiment effect difference exists between call and put option prices. The sentiment proxies adopted in this chapter are an investor sentiment proxy (LongShort_Futures) and a consumer sentiment proxy (CCI). The relation between sentiment proxies and pre-crisis (crisis) risk-neutral moments is analyzed by running the following regression with daily time-series observations:

Momentₜ = α₀ + α₁ Momentₜ₋₁ + α₂ IXₜ + εₜ, (42.2)

where Moment represents the risk-neutral confidence interval, skewness, and kurtosis and IX denotes the investor sentiment or consumer sentiment proxy.
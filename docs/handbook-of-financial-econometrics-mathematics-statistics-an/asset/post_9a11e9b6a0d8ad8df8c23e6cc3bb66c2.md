
- Grinblatt, M. and Keloharju, M. (2001). How Distance, Language, and Culture Influence Stockholdings and Trades. Journal of Finance 56, 1053–1073.
- Grinblatt, M., Titman, S. and Wermers, R. (1995). Momentum Investment Strategies, Portfolio Performance, and Herding: A Study of Mutual Fund Behavior. American Economic Review 85, 1088–1105.
- Hull, J.C. (2014). Options, Futures and Other Derivatives. Pearson Education, Inc., New Jersey.
- Jegadeesh, N. and Titman, S. (1995). Overreaction, Delayed Reaction, and Contrarian Profits. Review of Financial Studies 8, 973–993.
- Jegadeesh, N. and Titman, S. (1993). Returns to Buying Winners and Selling Losers: Implications for Stock Market Efficiency. Journal of Finance 48, 65–91.
- Jerbi, Y. (2015). A New Closed-Form Solution as an Extension of the Black-Scholes Formula Allowing Smile Curve Plotting. Quantitative Finance 12, 2041–2052.
- Klemkosky, R.C. and Resnick, B.G. (1980). An Ex-Ante Analysis of Put-Call Parity. Journal of Financial Economics 8, 363–378.
- Klemkosky, R.C. and Resnick, B.G. (1979). Put-Call Parity and Market Efficiency. Journal of Finance 34, 1141–1155.
- Kraus, A. and Litzenberger, R.H. (1976). Skewness Preference and Valuation of Risk Assets. Journal of Finance 31, 1085–1100.
- Lai, T.Y., Lee, C.F. and Tucker, A.L. (1992). An Alternative Method for Obtaining the Implied Standard Deviation. Journal of Financial Engineering 1, 369–375.
- Lamont, O. and Thaler, R. (2003). Can the Market Add and Subtract? Mispricing in Tech Stock Carve-Outs. Journal of Political Economy 111, 227–268.
- Latané, H.A. and Rendleman, R.J. (1976). Standard Deviation of Stock Price Ratios Implied by Option Prices. Journal of Finance 31, 369–381.
- Li, S. (2005). A New Formula for Computing Implied Volatility. Applied Mathematics and Computation 170, 611–625.
- Liew, J. and Vassalou, M. (2000). Can Book-to-Market, Size and Momentum be Risk Factors that Predict Economic Growth? Journal of Financial Economics 7, 221–245.
- Lo, A.W. and MacKinlay, A.C. (1988). Stock Market Prices do not Follow Random Walks: Evidence from a Simple Specification Test. Review of Financial Studies 1, 41–66.
- Lo, A.W. and MacKinlay, A.C. (1990). When are Contrarian Profits Due to Stock Market Overreaction? Review of Financial Studies 3, 175–205.
- Lewellen, J. (2002). Momentum and Autocorrelation in Stock Returns. Review of Financial Studies 15, 533–563.
- MacBeth, J.D. and Merville, L.J. (1979). An Empirical Examination of the Black-Scholes Call Option Pricing Model. Journal of Finance 34, 1173–1186.
- Manaster, S. and Koehler, G. (1982). The Calculation of Implied Variances from the Black-Scholes Model: A Note. Journal of Finance 37, 227–230.
- Nisbet, M. (1992). Put-Call Parity Theory and an Empirical Test of the Efficiency of the London Traded Options Market. Journal of Banking and Finance 16, 381–403.
- Ofek, E. and Richardson, M. (2003). Dotcom Mania: The Rise and Fall of Internet Stock Prices. Journal of Finance 58, 1113–1137.
- Ofek, E., Richardson, M. and Whitelaw, R.F. (2004). Limited Arbitrage and Short Sales Restrictions: Evidence from the Options Markets. Journal of Financial Economics 74, 305–342.
- Singleton, J.C. and Wingender, J. (1986). Skewness Persistence in Common Stock Returns. Journal of Financial and Quantitative Analysis 21, 335–341.
- Stoll, H.R. (1969). The Relationship between Put and Call Option Prices. Journal of Finance 24, 801–824.

## Appendix 103A Exact Form of Black–Scholes Option Pricing Model

The well-known Black–Scholes option pricing model was proposed by Black and Scholes (1973) and soon gained large popularity among practitioners and academic researchers. The exact form of the model is provided below:

$c = S_0 N(d_1) - K e^{-rT} N(d_2), \qquad (103A.1)$
$p = K e^{-rT} N(-d_2) - S_0 N(-d_1). \qquad (103A.2)$

where

$d_1 = \frac{\ln(S_0/K) + (r + \frac{1}{2}\sigma^2) T}{\sigma\sqrt{T}},$
$d_2 = d_1 - \sigma\sqrt{T},$

$S_0$ is the current market price of the underlying stock, $K$ the exercise price, $r$ the risk-free interest rate, and $T$ the remaining life of the option.

The implied volatility estimation is based on the B–S pricing model.

## Appendix 103B MATLAB Approach to Estimate Implied Volatility

The MATLAB finance toolbox provides a function *blsimpv* to search for implied volatility. The algorithm used in the *blsimpv* function is Newton’s method, just as the procedure described in equation (103.6). This approach minimizes the difference between the observed market option value and the theoretical value of the B–S model and obtains the implied volatility estimator until the tolerance level is attained.

The complete command of the function *blsimpv* is as follows: Volatility = *blsimpv*(Price, Strike, Rate, Time, Value, Limit, Yield, Tolerance, Class). The command with default setting is as follows:

Volatility = *blsimpv*(Price, Strike, Rate, Time, and Value).

There are nine inputs in total, while the last four are optional. Detailed explanations of all the inputs are as follows:

### Inputs:

- **Price** — Current market price of the underlying asset.
- **Strike** — Strike (i.e., exercise) price of the option.
- **Rate** — Annualized continuously compounded risk-free rate of return over the life of the option, expressed as a positive decimal number.
- **Time** — Time to expiration of the option, expressed in years.
- **Value** — Price (i.e., value) of a European option from which the implied volatility of the underlying asset is derived.

### Optional Inputs:

- **Limit** — Positive scalar representing the upper bound of the implied volatility search interval. If empty or missing, the default is 10, or 1000% per annum.
- **Yield** — Annualized continuously compounded yield of the underlying asset over the life of the option, expressed as a decimal number. For example, this yield could represent the dividend yield and foreign risk-free interest rate for options written on stock indices and currencies, respectively. If empty or missing, the default is zero.
- **Tolerance** — Positive scalar implied volatility termination tolerance. If empty or missing, the default is 1e-6.
- **Class** — Option class (i.e., whether a call or put) indicating the option type from which the implied volatility is derived. This class may be either a logical indicator or a cell array of characters. To specify call options, set Class = true or Class = {'Call'}; to specify put options, set Class = false or Class = {'Put'}. If empty or missing, the default is a call option.

### Output:

- **Volatility** — Implied volatility of the underlying asset derived from European option prices, expressed as a decimal number. If no solution can be found, a NaN (i.e., Not-a-Number) is returned.

### Example:

Consider a European call option trading at \$5 with an exercise price of \$95 and 3 months until expiration. Assume that the underlying stock pays 5% annual dividends and that it is trading at \$90 at this moment; in addition, the risk-free rate is 3% per annum. Under these conditions, the command used in Matlab will be either of the following:

```
Volatility = blsimpv(90, 95, 0.03, 0.25, 5, [], 0.05, [], {'Call'}),
```

```
Volatility = blsimpv(90, 95, 0.03, 0.25, 5, [], 0.05, [], true).
```

Note that this function provided by MATLAB’s toolbox can only estimate the implied volatility from a single option. For more than one option, the user needs to write his/her own programs to estimate the implied variances.

## Appendix 103C Upper and Lower Bounds for European Index Options

The upper and lower bounds for option prices do not rely on any particular assumptions about the factors in the B-S pricing model. If an option price is above the upper bound or below the lower bound, then there are profitable opportunities for arbitrageurs.

Specifically, a European call option provides the holder the right to buy one share of a stock for a certain price. Regardless of what occurs, the option can never be worth more than the stock. Hence, the current stock price should be an upper bound to the call option price:

$c \leq S_0$. (103C.1)

A European put option provides the holder the right to sell one share of a stock for K. Regardless of how low the stock price becomes, we know that, at maturity, the option cannot be worth more than K. It follows that the put cannot be worth more than the present value of K today:

$p \leq K e^{-rT}$. (103C.2)

Regarding the lower bound for the price of a European call option, let us consider the following two portfolios:

- **Portfolio A**: one European call option plus an amount of cash equal to $K e^{-rT}$
- **Portfolio B**: one share

In portfolio A, the cash, if it is invested at the risk-free interest rate, will grow to K in time T. If $S_T > K$, the call option is exercised at maturity, and portfolio A is worth $S_T$. If $S_T < K$, the call option expires worthless and the portfolio is worth K. Hence, at time T, portfolio A is worth:

$\max(S_T, K)$. (103C.3)

Portfolio B is worth $S_T$ at time T. Hence, portfolio A is always worth as much as, and can be worth more than, the value of portfolio B at the option's maturity. It follows that in the absence of arbitrage opportunities, this must also be true today. Hence,

$c \geq S_0 - K e^{-rT}$. (103C.4)

To obtain the lower bound for a European put option, we consider the following two portfolios:

- **Portfolio C**: one European put option plus one share
- **Portfolio D**: an amount of cash equal to $K e^{-rT}$

If $S_T < K$, then the option in portfolio C is exercised at the option maturity, and the portfolio becomes worth K. If $S_T > K$, then the put

The complete command of the function blsimpv is: Volatility = blsimpv(Price, Strike, Rate, Time, Value, Limit, Yield, Tolerance, Class). And the command with default setting is: Volatility = blsimpv(Price, Strike, Rate, Time, Value).

There are nine inputs in total, while the last four of them are optional. Detailed explanations of all the inputs are as follows:

+   - Price — Current price of the underlying asset.
+   - Strike — Strike (i.e., exercise) price of the option.
+   - Rate — Annualized continuously compounded risk-free rate of return over the life of the option, expressed as a positive decimal number.
+   - Time — Time to expiration of the option, expressed in years.
+   - Value — Price (i.e., value) of a European option from which the implied volatility of the underlying asset is derived.

+   - Limit — Positive scalar representing the upper bound of the implied volatility search interval. If empty or missing, the default is 10, or 1000% per annum.
+   - Yield — Annualized continuously compounded yield of the underlying asset over the life of the option, expressed as a decimal number. For example, this could represent the dividend yield and foreign risk-free interest rate for options written on stock indices and currencies, respectively. If empty or missing, the default is zero.
+   - Tolerance — Positive scalar implied volatility termination tolerance. If empty or missing, the default is 1e-6.
+   - Class — Option class (i.e., whether a call or put) indicating the option type from which the implied volatility is derived. This may be either a logical indicator or a cell array of characters. To specify call options, set Class = true or Class = {'Call'}; to specify put options, set Class = false or Class = {'Put'}. If empty or missing, the default is a call option.

Volatility — Implied volatility of the underlying asset derived from European option prices, expressed as a decimal number. If no solution can be found, a NaN (i.e., Not-a-Number) is returned.

Consider a European call option trading at $5 with an exercise price of $95 and 3 months until expiration. Assume the underlying stock pays 5% annual
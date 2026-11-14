5. **Risk-Free Rate (i)**. Use the risk-free rate to calculate the present value of the exercise price. The rate used should be the annualized rate and be adjusted for maturity. The other adjustment is compounding.

# Other Statistical Concepts

It's important to reintroduce some mathematical concepts that are essential for valuing options, including the natural logarithms, probability theory, and normal distribution.

# 1. Compounding Using Exponential (e)

The number **e** is a mathematical constant 2.7182 that is the base of the natural logarithm and is equal to one. The future value calculation is calculated based on the following formula:

$$FV = PV \left(1 + \frac{i}{f}\right)^t$$

where PV is the present value, i is the interest, t is the time, and f is the frequency or compounding payment per year.

As the frequency increases from annually to semi-annually, to quarterly, to monthly, and to infinite, compounding the future value will increase, but it won't get higher than 2.718 times the original present value, as illustrated in Figure 11.16.

The infinite compounding **e** is used in the Black-Scholes model to calculate the present value of the exercise price (X) as $e^{-it}$ and is derived based on the following mathematical calculation:

$$e = PV (1 + i)^t \text{ then } PV = \frac{e}{(1 + i)^t} \text{ then } PV = e^{-it}$$

# 2. Natural Logarithm (ln)

The model assumes spot prices follow a lognormal distribution because asset prices cannot be negative (they are bounded by zero). This is also known as a _Gaussian distribution_. Often, asset prices are observed to have significant right skewness and some degree of kurtosis (fat tails). This means high-risk downward moves happen more often in the market than a normal distribution predicts.

The assumption of lognormal underlying asset prices such as cryptocurrencies should thus show that implied volatilities are similar for each strike price according to the Black-Scholes model.
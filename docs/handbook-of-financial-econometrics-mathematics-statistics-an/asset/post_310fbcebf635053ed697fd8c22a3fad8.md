
Hull, J. and White, A. (1987). The pricing of Options on Assets with Stochastic Volatilities. Journal of Finance, 42, 281–300.
Hull, J. (2006). Options, Futures and Other Derivatives, Sixth Edition, Pearson Prentice Hall.
Ingersoll, J. E. (1976). A Theoretical and Empirical Investigation of the Dual Purpose Funds: An Application of Contingent Claims and Analysis. Journal of Financial Economics, 3, 83–123.
Itô, K. and McKean, H. (1964). Diffusion Processes and Their Simple Paths, Academic Press.
Jarrow, R. and Rudd, A. (1982). Approximate Option Valuation for Arbitrary Stochastic Processes. Journal of Financial Economics, 10, 347–370.
Jarrow, R. and Rudd, A. (1983). Option Pricing, R. D. Irwin.
Jarrow, R., Jin, X. and Madan, D. (1999). The Second Fundamental Theorem of Asset Pricing. Mathematical Finance, 9, 255–273.
Karatzas, I. and Shreve, S. (2005). Brownian Motion and Stochastic Calculus, Corrected Eighth Printing, Springer.
Kreps, D. M. (1981). Arbitrage and Equilibrium in Economics with Infinitely Many Commodities. Journal of Mathematical Economics, 8, 15–35.
Kreps, D. M. (1982). Multiperiod Securities and the Efficient Allocation of Risk: A Comment on the Black-Scholes Option Pricing Model. In The Economics of Information and Uncertainty, ed. J. J. McCall, University of Chicago Press.
Lackner, P. (1993). Martingale Measure for a Class of Right Continuous Processes. Mathematical Finance, 3, 43–53.
Lambertson, D. and Lapeyre, B. (2007). Introduction to Stochastic Calculus Applied to Finance, Chapman & Hall.
Latané, H. A. and Rendleman, R. J. Jr. (1976). Standard Derivations of Stock Price Ratios Implied in Option Prices. Journal of Finance, 31, 369–381.
Lee, C. F., Chen, Y. and Lee, J. (2016). Alternative Methods to Derive Option Pricing Models: Review And Comparison. Review of Quantitative Finance and Accounting, 47(2), 417–451.
Lee, C. F., Chen, H. Y., Lee, A. C. and Lee, J. (2019). Financial Econometrics, Mathematics, Statistics Theory, Method, and Application, Springer, forthcoming.
Leland, H. E. (1985). Option Pricing and Replication with Transaction Costs. Journal of Finance, 40, 1283–1301.
MacBeth, J. D. and Merville, L. J. (1979). An Empirical Examination of the Black-Scholes Call Option Pricing Model. Journal of Finance, 34, 1173–1186.
Malliaris, A. and Brock, W. A. (1982). Stochastic Methods in Economics and Finance, North-Holland.
Malliaris, A. G. (1983). Itô’s Calculus in Financial Decision Making. Society of Industrial and Applied Mathematical Review, 25, 482–496.
McDonald, R. (2005). Derivatives Markets, Pearson Addison Wesley.
Merton, R. C. (1976). Option Pricing When Underlying Stock Returns are Discontinuous, Journal of Financial Economics, 3, 125–144.
Merton, R. C. (1973). The Theory of Rational Option Pricing. Bell Journal of Economics and Management Science, 4, 141–183.
Merton, R. C. (1975). Theory of Finance from the Perspective of Continuous Time. Journal of Financial and Quantitative Analysis, 10, 659–674.
Merton, R. C. (1982). On the Mathematics and Economics Assumptions of Continuous-Time Model. In Financial Economics: Essay in Honor of Paul Cootner, ed. W. F. Sharpe and C. M. Cootner. Prentice-Hall, pp. 19–51.

Merton, R. C. (1992). *Continuous-Time Finance*, Wiley-Blackwell.

Musiela, M. and Rutkowski, M. (1997). *Martingale Methods in Financial Modeling*, Springer Verlag.

Neftci, S. (2000). *Introduction to the Mathematics of Financial Derivatives*, Academic Press.

Oksendal, B. (2007). *Stochastic Differential Equations*, 5th ed. Springer Verlag.

Pliska, S. R. (1997). *Introduction to Mathematical Finance*, Blackwell.

Rebonato, R. (1998). *Interest Rate Option Models*, 2nd ed. John Wiley.

Rebonato, R. (2002). *Modern Pricing of Interest Rate Derivatives*, Princeton University Press.

Rebonato, R. (2004). *Volatility and Correlation: The Perfect Hedger and the Fox*, 2nd ed. Wiley.

Roll, R. (1977). An Analytic Valuation Formula for Unprotected American Call Options on Stocks with Known Dividends. *Journal of Financial Economics*, 5, 251–281.

Rubinstein, M. (1976). The Valuation of Uncertain Income Streams and the Pricing of Options. *Bell Journal of Economics*, 7, 407–425.

Scholes, M. (1976). Taxes and the Pricing of Options. *Journal of Finance*, 31, 319–332.

Schweizer, M. (1992). Martingale Densities for General Asset Prices. *Journal of Mathematical Economics*, 21, 363–378.

Shastri, K. and Tandon, K. (1986). Valuation of Foreign Currency Options: Some Empirical Results. *Journal of Financial and Quantitative Analysis*, 21, 377–392.

Smith, C. W., Jr. (1976). Option Pricing: A Review. *Journal of Financial Economics*, 3, 3–51.

Smith, C. W., Jr. (1979). Applications of Option Pricing Analysis. In *Handbook of Financial Economics*, ed. J. L. Bicksler, North-Holland.

Stricker, C. (1990). Arbitrage et Lois de Martingale. *Ann. Inst. H. Poincaré Probab. Statist.*, 26, 451–460.

Taleb, N. (1997). *Dynamic Hedging*, John Wiley & Sons.

Wilmott, P. (2000). *Paul Wilmott on Quantitative Finance*, John Wiley & Sons.

## Appendix 27A: An Alternative Method to Derive the Black–Scholes Option-Pricing Model

Perhaps it is unclear why it is assumed that investors have risk-neutral preferences when the usual assumption in finance courses is that investors are risk averse. It is feasible to make this simplistic assumption because investors are able to create riskless portfolios by combining call options with their underlying securities. Since the creation of a riskless hedge places no restrictions on investor preferences other than non-satiation, the valuation of the option and its underlying asset will be independent of investor risk preferences. Therefore, a call option will trade at the same price in a risk-neutral economy as it will in a risk-averse or risk-preferent economy.

### Appendix 27A.1: Assumptions and the present value of the expected terminal option price

To derive the Black–Scholes formula it is assumed that there are no transaction costs, no margin requirements, and no taxes; that all shares are infinitely divisible; and that continuous trading can be accomplished. It is also assumed that the economy is risk-neutral.

In the risk-neutral assumptions of Cox and Ross (1976) and Rubinstein (1976), today’s option price can be determined by discounting the expected value of the terminal option price by the riskless rate of interest. As was seen earlier, the terminal call-option price can take on only two values: $S_t - X$ if the call option expires in the money, or 0 if the call expires out of the money. So today’s call option price is

$C = \exp(-rt) \text{Max}(S_t - X, 0),$ (27.A.1)

where $C$ is the market value of the call option, $r$ is the riskless rate of interest, $t$ is the time to expiration, $S_t$ is the market value of the underlying stock at time $t$, and $X$ is the exercise or striking price.

Equation (27.A.1) says that the value of the call option today will be either $S_t - X$ or 0, whichever is greater. If the price of stock at time $t$ is greater than the exercise price, the call option will expire in the money. This simply means that an investor who owns the call option will exercise it. The option will be exercised regardless of whether the option holder would like to take physical possession of the stock. If the investor would like to own the stock, the cheapest way to obtain the stock is by exercising the option. If the investor would not like to own the stock, he or she will still exercise the option and immediately sell the stock in the market. Since the price the investor paid ($X$) is lower than the price he or she can sell the stock for ($S_t$), the investor realizes an immediate profit of $S_t - X$. If the price of the stock ($S_t$) is less than the exercise price ($X$), the option expires out of the money. This occurs because in purchasing shares of the stock the investor will find it cheaper to purchase the stock in the market than to exercise the option.

Assuming that the call option expires in the money, then the present value of the expected terminal option is equal to the present value of the difference between the expected terminal stock price and the exercise price, as indicated in equation (27.A.2):

$C = \exp(-rt) E[\text{Max}(S_t - X, 0)]$
$= \exp(-rt) \int_x^\infty (S_t - X) h(S_t) dS_t ,$ (27.A.2)

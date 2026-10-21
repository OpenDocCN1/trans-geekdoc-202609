
firm has no debt, the decline of the stock price can make it more difficult for the firm to meet its fixed costs and thus increase volatility (Hull, 2002).

The CEV model assumes the diffusion process for the stock is

$$dS = \mu S dt + \delta S^{\beta/2} dz, \tag{51.1}$$

and the instantaneous variance of the percentage price change or return, $\sigma^2$, follows a deterministic relationship:

$$\sigma^2(S,t) = \delta^2 S^{(\beta-2)}, \tag{51.2}$$

where the elasticity of this variance with respect to the stock price equals $\beta$.

If $\beta = 2$, prices are lognormally distributed and the variance of returns is constant, which is the same as the well-known Black–Scholes model. If $\beta < 2$, the stock price is inversely related to the volatility. Cox originally restricted $0 \le \beta < 2$. Emanuel and MacBeth (1982) extended their analysis to the case $\beta > 2$ and discussed its properties. However, Jackwerth and Rubinstein (2001) found that typical values of $\beta$ can fit market option prices well for the post-crash period only when $\beta < 0$, and they called the model with $\beta < 0$ the unrestricted CEV model.$^4$ In their empirical study, the difference of the pricing performance of restricted CEV model ($\beta \ge 0$) and BS model is not significant.

When $\beta < 2$, the non-dividend-paying CEV call pricing formula is as follows:

$$
\begin{aligned}
C &= S \left[ \sum_{n=0}^{\infty} g(S'|n+1) G\left(K'|n+1+\frac{1}{2-\beta}\right) \right] \\
&\quad - K e^{-r\tau} \left[ \sum_{n=0}^{\infty} g\left(S'|n+1+\frac{1}{2-\beta}\right) G(K'|n+1) \right]. \tag{51.3}
\end{aligned}
$$

When $\beta > 2$, the CEV call pricing formula is as follows:

$$
\begin{aligned}
C &= S \left[ 1 - \sum_{n=0}^{\infty} g\left(S'|n+1+\frac{1}{2-\beta}\right) G(K'|n+1) \right] \\
&\quad - K e^{-r\tau} \left[ 1 - \sum_{n=0}^{\infty} g(S'|n+1) G\left(K'|n+1+\frac{1}{2-\beta}\right) \right], \tag{51.4}
\end{aligned}
$$

where

$S' = \left[\frac{2r e^{r\tau(2-\beta)}}{\delta^2(2-\beta)(e^{r\tau(2-\beta)} -1)}\right] S^{2-\beta}, \quad K' = \left[\frac{2r}{\delta^2(2-\beta)(e^{r\tau(2-\beta)} -1)}\right] K^{2-\beta}, \quad g(x|m)=\frac{e^{-x}x^{m-1}}{\Gamma(m)}$

is the gamma density function

$G(x|m)=\int_{x}^{\infty} g(y|m)dy,$

where $C$ is the call price; $S$, the stock price; $\tau$, the time to maturity; $r$, the risk-free rate of interest; $K$, the strike price; and $\beta$ and $\delta$, the parameters of the formula.

### 51.2.1.2 Previous empirical studies

MacBeth and Merville (1980) were the first to empirically test the CEV option model. They tested the CEV model against the Black–Scholes (BS) model using daily closing prices of call options on six companies’ stock from December 31, 1975 to December 31, 1976. Their estimation procedure is as follows:

From (51.1),

$$\frac{(dS - \mu S dt)^2}{S^{\beta} dt} \equiv u_t \propto \chi^2(1), \qquad (51.5)$$

where the constant of proportionality is $1/\delta^2$.

Following (51.5), for some interval of time $dt$,

$$\ln[(dS - \mu S dt)^2] - \ln dt = 2 \ln \delta + \beta \ln S + \ln[\chi^2(1)]. \qquad (51.6)$$

They first estimate $\mu$ from the sample of daily returns. Point estimates of the elasticity parameter $\beta$ can then be obtained using a linear regression since the Chi-square random variables are uncorrelated through time. Note that they only choose the integer value of $\beta$ and fix it the same for all options written on the same stock. The way they choose the integer value is that starting with their point estimate of $\beta$, they use a numerical routine to calculate an implied value of $\delta$ for each observed option price until they have approximately the same value of $\delta$ for each option price. This is done on four arbitrarily selected days during a year. Finally, $\delta$ is deduced from the BS model by taking an at-the-money option on a given day. That is $\delta_t = \sigma_t S_t^{(2-\beta)/2}$, where the variance rate $\sigma_t^2$ is from the BS model.

Their empirical results show that the CEV parameter $\beta$ is generally less than two and ranging from $-4$ for IBM to 1 for Xerox, which explains the empirical evidence for the negative relationship between the sample variance of returns and stock price. Moreover, they demonstrate that under these circumstances, the CEV model generates estimated option prices closer to the market prices than those of the BS models.

Manaster (1980) criticized the approach by MacBeth and Merville (1980) and suggested that:

- (i) the CEV parameter $\beta$ and the volatility parameter $\delta$ should be estimated jointly without using the information (implied parameter $\delta$ of at-the-money option) from the BS model;
- and (ii) post-estimation testing should be conducted to see whether the CEV model continues to fit the observed data better than the BS model for the day or week following the parameter estimation.

In response, Emanuel and MacBeth (1982) tested the post-estimation performance of the CEV model for 1 day, 5 days (a week), and 17 days (a month) including the daily closing prices of call options written on the same six stocks for each day in 1978. To perform the out-of-the-sample test, they select the best value of $\beta$ on each day by searching integer values minimizing the squared deviation between model prices and market prices of option with at least 90 days to expiration. Their results showed that the CEV model yields more accurate predictions of future option prices than the BS model in nearly all cases in the period of less than one month.⁵

Using time series data of underlying assets alone, several empirical studies found that estimates of $\beta$ are confined to 0 and 2 as opposed to the negative estimates. Beckers (1980) estimated the CEV parameters for 47 stocks using the daily stock price data from 1972 to 1977. He found that most return distributions are less positively skewed than the lognormal ($\beta < 2$) and support the significant relationship between the level of the stock price and its volatility. Gibbons and Jacklin (1988) examined stock prices over a longer data sample during 1962 to 1985, and also almost invariably estimated $\beta$ between 0 and 2.

⁵ They also noted that the CEV model works best when $\beta$ is less than two, given the empirical evidence that implied volatility is inversely related to stock price. However, for the period of April to November in 1978, the estimated values of $\beta$ are larger than two. This in turn predicts that volatility and stock price move in the same direction and hence reduces the superior predictive power of option prices of the CEV model compared with the BS model during 1978.

Recently, Lee et al. (2004) took the S&P 500 index options as opposed to stock options to avoid the American option premium biases, and used the non-central Chi-square probability functions proposed by Schroder (1989) to reduce the approximation errors. In addition, they also expanded their analysis into six moneyness and three maturity categories. They employed a similar two-step estimation to obtain the estimated $\beta$ and $\delta$ as MacBeth and Merville (1980), and the difference was that they did not constrain the elasticity value $\beta$ to integer values. Their results still supported the MacBeth and Merville results (1980) although the samples were not subject to the American premium biases. The CEV model in terms of the non-central Chi-square distribution performs better than the BS model in pricing the S&P 500 index call options during January 1, 1992 to June 30, 1997. Furthermore, with the estimates of $\beta < 2$ for the sample period, it is implied that a negative relation exists between the sample index value and its volatility of daily returns.

Also using the S&P 500 index to reduce market imperfections, Jackwerth and Rubinstein (2001) evaluated five kinds of option models with a total of nine models among the deterministic models, the stochastic models and the naïve trader rules. The five categories of models are:

- (i) the Black–Scholes model;
- (ii) two naïve smile-based predictions that use today’s observed smile directly for the prediction;
- (iii) two versions of the CEV models;
- (iv) an implied binomial tree model;
- and (v) three parametric models including displaced diffusion, jump diffusion, and stochastic volatility.

They performed two main types of tests for the following relations:

- (1) Option prices at the same time, with the same underlying asset, and the same strike price, but with different times-to-expiration;
- (2) Option prices with the same underlying asset, the same expiration date, and the same ratio of strike price to underlying asset price, but observed at different times.

Investigating the relation (1) involves the problem of deducing short-term option prices from longer-term option prices. The volatility smile for the longer-term options is assumed known, and the volatility smile for the shorter-term options is unknown. They then fitted the alternative option models to the longer-term option prices, and compared the model values with the observed market prices for the shorter-term options and calculated pricing errors (backward-looking test). To investigate relation (2), they calibrated alternative models on current longer-term option prices, and computed the errors of the forecast prices using the underlying asset price observed 10 and 30 days later (forward-looking test). To decompose the source of any remaining pricing errors, they also conducted related experiments assuming in addition that the at-the-money implied volatility of the

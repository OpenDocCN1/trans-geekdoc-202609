
in terms of higher returns and lower risks across portfolios consisting of currencies, commodities, stocks, bonds, and real estate. Briere, Oosterlinck, and Szafarz (2017) examine correlations between Bitcoin and other asset classes and find evidence that supports diversification benefits. Kajtazi and Moro (2018) use time series data and optimization methods applied to U.S., European, and Chinese portfolios and conclude that Bitcoin has return-enhancement potential but not risk-reduction potential. They acknowledge that Bitcoin's volatility calls into question its risk-reduction efficacy. Using time series modeling, Guesmi et al. (2019) find that Bitcoin reduces the risk in a portfolio of stocks, gold, and Bitcoin. Moreover, selling Bitcoin short can also be an effective hedge. Implementing a new portfolio optimization method, Li, Jiang, Wei, and Wang (2021) show the efficacy of Bitcoin to enhance portfolio return while reducing risk, leading to higher Sharpe ratios.

Collectively, the studies support the efficacy of Bitcoin's diversification potential, signaling opportunities to enhance return-risk performance. When aligned with the evidence supporting return-enhancement potential, especially in instances of inefficient pricing, the motivation for including Bitcoin into investment portfolios is compelling. Again, the issue of the right allocation, however, remains unaddressed.

## Portfolio Analysis and the Black-Litterman Model

Portfolio analysis rests on three fundamental equations, as follows*:

```
E(R_p) = \sum_{i=1}^n w_i E(R_i)
(1)
```

```
\sigma_p^2 = \sum_{i=1}^n \sum_{j=1}^n w_i w_j \sigma_i \sigma_j \rho_{ij}
(2)
```

```
\sum_{i=1}^n w_i = 1,
(3)
```

* Although the equations are in mean-variance form, convention has led to the use of standard deviation in place of variance as a measure of risk, which is frequently referred to as volatility.

where,

\( E(R_p) \) = expected rate of return on a portfolio of securities;

\( \sigma_p^2 \) = variance of the portfolio as a measure of risk;

\( \sigma_i \sigma_j \rho_{ij} \) = covariance of the returns of the securities comprised by the portfolio; and

\( w_i \) = weight assigned to each security.

Because the analysis in this study is restricted to “long-only” portfolios, \( w_i \ge 0 \).
This is to state that “shorting” of securities does not apply. The objective is to minimize portfolio risk subject to an expected return—namely, minimizing equation (2) subject to equation (1). It leads to the positive relationship between expected return and risk. Although this quadratic is relatively easy to optimize, the results are often out of step with reality, as Benninga (2008, 349) expresses:

> It is possible to come away from a standard textbook discussion of portfolio optimization with the impression that a fixed set of mechanical optimization rules, combined with a bit of knowledge about personal preferences, suffices to define an investor’s optimal portfolio. Anyone who has tried to implement portfolio optimization using market data knows that the results are often a nightmare.

Why is this so? Although historical data are useful for estimating portfolio risks, the same does not apply for expected returns. In other words, past results are often not an accurate indicator of future returns, as cogently expressed by Elton (1999). This is the motivation for the model of Black and Litterman (1992). Rather than relying strictly on historical returns, it estimates expected returns from the capital asset pricing model (CAPM), which models expected returns, as follows:

\( E(R_i) = \beta_i [E(R_m) - R_f], \)

(4)

where,

\( E(R_i) \) = expected rate of return on security \( i \);

\( E(R_m) \) = expected rate of return on “the” market;

\( [E(R_m) - R_f] \) = the reward for assuming additional risk, a risk premium;

\( R_f \) = a “risk-free” rate of return; and

\( \beta_i \) = index of systematic, or market, risk normalized around 1.0, defined as the covariance of the rates of return on security \( i \) relative to the variance of the rates of return on “the” market.

The model, which relies on one factor only, is simple, stating that the only variable driving expected return is the beta, with the risk premium measuring the incremental gain per increase in beta.

There is precedent in the literature for the Black-Litterman application, as seen, for example, in Wu and Pandy (2014); Bessler, Opfer, and Wolff (2014); and Loviscek (2021). It has a two-step Bayesian foundation. The first one is the estimation of the CAPM to determine the expected returns. This begins with the estimation of the beta for each security from a simple time series model of volatility, or risk, as follows:

```
(R_{i,t} - R_f) = \beta_i (R_{m,t} - R_f) + e_{i,t} \quad (5)
```

where all terms are defined as before and \( e_{i,t} \) is an error term. In this equation, beta is the coefficient, whereas it is the variable in the CAPM. Again, the beta is the index of systematic risk, and as such, the model is one of risk, where the variance of \( e_{i,t} \) measures idiosyncratic, or unpredictable, risk—that is, risk that is unique to the security (e.g., unexpected death of a CEO, loss of a key patent, underperformance relative to expectations, failed product, etc.). This risk is diversifiable; however, its counterpart, systematic risk, is not diversifiable because it is linked to market conditions. Although multi-factor modeling is often a preferred choice, Frazzini and Pedersen (2014), Cederberg and O'Doherty (2015), and Kolari, Liu, and Huang (2021) support the CAPM when applied within a portfolio framework.

The estimated returns align with equilibrium expected returns that replace the expected returns based exclusively on historical data. After the estimation of the CAPM returns, a “reverse optimization” determines the market-capitalized weights (Idzorek 2011), which lead to the implied returns consistent with portfolio optimization. To explain, after the estimation of the CAPM expected returns, along with the risks and covariances, the model maximizes a reward-to-variability ratio attributed to Sharpe (1994), leading to the respective weights for each security.

To get to the final step—the CAPM equilibrium returns—an investor has two choices: either use CAPM returns in the optimization process or supplement the CAPM returns with additional information in the optimization, such as private information, mean reversion, momentum, or mispricing estimates. This study uses the first choice, effectively assuming that markets are informationally efficient.

These returns are considered to be the “prior” estimates within the Bayesian framework because they do not include the additional information that occurs in the second choice (i.e., the posterior estimates), in which an investor assumes that markets are inefficient by “tilting” the expected return on the portfolio to capture the additional information.

Either way, the optimization process includes an estimate of a risk-aversion coefficient (\(\lambda\)). It can be estimated by the CAPM risk premium, \([E(R_m) - R_f]\), relative to the variance of the portfolio. It represents a return–risk tradeoff that is central to portfolio analysis. During the reverse optimization, it scales the estimates of the variance–covariance matrix. Combined with the capitalized market weights, the result is the implied vector of equilibrium returns, as follows:

```
\(\Pi = \lambda\Sigma w_m\) (6)
```

where,

- \(\Pi\) is the implied excess equilibrium return vector ($N \times 1$ column vector);
- \(\lambda\) is the risk-aversion coefficient, which incorporates the expected return-risk tradeoff;
- \(\Sigma\) is the variance–covariance matrix of excess returns ($N \times N$ matrix); and
- \(w_m\) is the market capitalization weights ($N \times 1$ column vector) of the assets.

The optimization procedure used here is standard, as opposed to those that rely on “shrinkage” of the data or other means of data arrangement (Jorion 1991). Incorporated into the optimization, the estimates from equation (4) embody an exponentially weighted moving average (EWMA) coefficient of 0.97, as reportedly used by major financial institutions (Hoadley 2017). It weighs more recent observations more heavily than older observations, helping to capture any possible momentum effects. It is defined as follows:

```
EWMA_{i,t} = \gamma R_{i,t} + (1-\gamma)EWMA_{i,t-1} (7)
```

where,

- \(EWMA_{i,0} = \) arithmetic average of the historical rates of return;
- \(R_{i,t} = \) rate of return on security \( i \) at time \( t \);
- \(n = \) number of observations, including \(EWMA_{i,0}\); and
- \(\gamma = 0 < \gamma \le 1\), which determines the length of the memory, in this case, 0.97.

* Formally, $N$ assets make up the market, with $M_p$ representing the market portfolio and \(\Sigma\) representing the variance–covariance matrix. The equilibrium expected returns on the securities, in the form of a vector, have a mean of $\mu$, with $\lambda$ reflecting risk tolerance. The equilibrium CAPM expected returns are \(\Pi = \lambda \Sigma P_M\). The optimal portfolio $M_p^* = \Sigma^{-1} \mu / \lambda$.

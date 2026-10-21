
## The Original CAPM
- Sharpe (1964), Lintner (1965), and Mossin (1966)

## The Static CAPM
(single-period)

## Existence of Equilibrium
- Hart (1974)
- Nielsen (1989)

## The Dynamic CAPM
(multi-period)

## Behavioral Finance
- Kahneman and Tversky (1979)
- Tversky and Kahneman (1992)
- Barberis, Huang and Santos (2001)
- Levy, De Giorgi and Hens (2003)
- Lee and Lee (2006)
- Barberis and Huang (2008)
- Levy (2010)

## No Riskless Asset
- Black (1972)

## Dividend and Taxation Effect Models
- Miller and Modigliani (1961)
- Brennan (1970)
- Black and Scholes (1974)
- Sasson and Kolodny (1976)
- Miller and Scholes (1978)
- Litzenberger and Ramaswamy (1979)
- Morgan (1982)
- Litzenberger and Ramaswamy (1982)
- Hagiwara and Herce (1997)

## Equilibrium Models with Heterogeneity Beliefs and Investors
- Constantinides (1982)
- Constantinides and Duffie (1996)
- Brav, Constantinides, and Geczy (2002)
- Basak (2005)
- Levy, Levy, and Benita (2006)
- Yoel (2009)

## Skewness Effect Models
- Borch (1969)
- Feldstein (1969)
- Jean (1971)
- Tsiang (1972)
- Ingersoll (1975)
- Schweser (1978)
- Sears and Wei (1988)
- Harvey and Siddique (2000)

## Equilibrium Models with Heterogeneity Investment Horizon
- Lee (1976)
- Levhari and Levy (1977)
- Lee, Wu, and Wei (1990)

## Liquidity-Based Models
- Pastor and Stambaugh (2003)
- Acharya and Pedersen (2005)

## Intertemporal CAPM—Merton Model
- Merton (1973)

## Supply-Side Effect Models
- Black (1976)
- Grinols (1984)
- Lee, Tsai, and Lee (2009)

## International CAPM
- Stulz (1981a)
- Stulz (1981b)
- Stulz (1982)
- Stulz (1984)
- Chang and Hung (2000)

## Intertemporal CAPM—Consumption-Based Models
- Breeden (1979)
- Campbell (1993)
- Campbell and Cochrane (1999)
- Jagannathan and Wang (1996)
- Lettau and Ludvigson (2001a)
- Lettau and Ludvigson (2001b)
- Lewellen and Nagel (2006)
- Balvers and Huang (2009)

## Intertemporal CAPM—Production-Based Models
- Balvers, Cosimano, and McDonald (1990)
- Cochrane (1991, 1996)
- Balvers and Huang (2007)

Figure 122.1: The evolution of capital asset pricing models.

*the mathematics of the efficient set, no security will have abnormal performance when measured as a departure from the security market line.* Besides, most empirical studies of the static CAPM assume that betas remain constant over time and that the return on the value-weighted portfolio of all stocks is a proxy for the return on aggregate wealth. The general consensus is that the static CAPM is unable to explain satisfactorily the cross-section of average returns on stocks. Therefore, Fama and French (1992, 1996) provide the three-factor model to the cross-section of expected stock returns. So the great factor debate rages on. Sharpe (1998) says, “*I’d be the last to argue that only one factor drives market correlation. There are not as many factors as some people think, but there’s certainly more than one.*”

Thus, in this paper we survey the important literature of CAPM and organize it into the following sections: “Dividend and Taxation Effect Models”, “Equilibrium Models with Heterogeneity Beliefs and Investors”, “Equilibrium Models with Heterogeneity Investment Horizon”, “Skewness Effect Models”, “Liquidity-based Models”, “Intertemporal CAPM-Merton Model”, “Intertemporal CAPM-Consumption-based Model”, “Intertemporal CAPM-Production-based Model”, “Supply-side Effect Model”, “Existence of Equilibrium”, “Behavioral Finance” and “Empirical Tests”. Finally, we draw the evolution of CAPM in Figure 122.1.

## 122.2 The Static CAPM

### 122.2.1 No riskless asset

First, how will CAPM change if investors cannot borrow and lending at the risk-free rate? Black (1972) provides the *minimum-variance zero-beta portfolio* to solve the problem and the model is also called *the Zero-Beta CAPM*.

### 122.2.2 Dividend and taxation effect models

Brennan (1970) first proposes an extended form of the single period CAPM model that accounts for the differential taxation of dividends over capital gains. Litzenberger and Ramaswamy (1979) extend the model of Brennan (1970) to account for restrictions on investors’ borrowing. Both these models assume that dividends and interest are taxed as ordinary income and capital gains are taxed at more favorable rates. Brennan’s model is under the assumption of proportional individual tax rate (not a function of income), certain dividends, and unlimited borrowing at the riskless rate of interest as

$$E(R_i) - r_f = b^* \beta_i + \tau(d_i - r_f) \tag{122.1}$$

where $E(R_i)$ is the before tax expected return to security $i$, $\beta_i$ is the covariance of asset $i$'s return with the market divided by the variance of the market, $b^* = [E(R_m) - r_f - \tau(d_m - r_f)]$ is the after-tax excess return of the market portfolio, $r_f$ is the return on a riskless asset, $d_i$ and $d_m$ is the dividend yield on security $i$ and the market portfolio, and $\tau$ represents a tax differential between dividends and capital gains.

Litzenberger and Ramaswamy (1979) extend this model by assuming both margin and income constraints on borrowing. Their model is

$$E(R_i) - r_f = a + b \beta_i + c(d_i - r_f) \tag{122.2}$$

where $a = E(R_{z^*}) - r_f$, $b = E(R_m) - E(R_{z^*}) - c(d_m - r_f)$, $c$ is a tax differential reduced by a shadow price that reflects increases in investors' ability to borrow from an additional dollar of dividends, and $E(R_{z^*})$ is the expected return on a zero-beta portfolio with a dividend yield equal to the taxable riskless rate. These models are the standard two-parameter pricing models adjusted for differential taxation of dividends and interest income relative to capital gains. Besides the differential taxation of dividends over capital gains, Black and Scholes (1974) examine the effects of dividend yield and policy on common stock prices and returns. Their paper suggests that it is not possible to demonstrate, using the best available empirical methods, that the expected returns on high-yield common stock differ from the expected returns on low-yield common stocks either before or after taxes. After Black and Scholes (1974), Sasson and Kolodny (1976) also examine the relationship between the CAPM and the question of dividend relevance. They argue that once a security's beta coefficient is given, the CAPM implies that knowledge of a firm's dividend policy is of no use in assessing the security's return, or correspondingly, its market value. However, they provide evidence in their paper against this premise. In the tests they perform, knowledge of a firm's dividend policy makes a significant contribution to explaining the return received on the firm's security. In particular, the results support the position that investors have a net preference for receiving their return in the form of dividends to receiving it in the form of capital gains. Therefore the results of their research suggest that if, as shown, firms having greater payouts on average have less market risk and offer the investor smaller risk-adjusted returns, the results of tests that classify firms according to risk class would contain an underlying bias in favor of greater risk firms. These firms would exhibit a greater risk-adjusted return than others because of the omitted dividend policy variable. In such a situation, the CAPM should be modified or an alternative model used to eliminate the bias. Morgan (1982) summarizes three distinct views of the importance of dividends to investors have received support at one time or another. According to the two most important views, dividends have a neutral and a negative effect on security prices respectively. Miller and Modigliani (1961) and Miller and Scholes (1978) favor complete substitutability of dividends and capital gain. Brennan (1970) and Litzenberger and Ramaswamy (1979) have developed models that incorporate differential taxation of income and capital gain. In these models, the tax disadvantage of income changes the investor’s portfolio problem from one of optimization of mean and variance of portfolio before-tax return to optimization in after-tax terms. Stocks with relatively large dividend yields should provide high expected returns (and so sell for low prices) to compensate the investor for the tax. Litzenberger and Ramaswamy (1982) present some new empirical results to show that a positive and nonlinear relationship between common stock returns and expected dividend yield. The prediction rule for expected dividends is based solely on information that would have been available to the investor ex ante. Hagiwara and Herce (1997) consider dividend-based and consumption-based CAPMs. Their estimation results suggest that the dividend asset pricing model provides a better explanation of the data than the consumption asset pricing model.

### 122.2.3 Equilibrium models with heterogeneity

One of the fundamental assumptions that all of the above-mentioned models share, which is considered as the most critical drawback of CAPM, is that all investors have homogeneous beliefs regarding the expected returns and the variance–covariance matrix. In the consumption-based CAPM we need to assume that assets can be priced if there is a representative agent who consumes aggregate consumption. Therefore, in this section we will introduce the model of heterogeneous beliefs, agents, and investment horizon.

### 122.2.3.1 Heterogeneous beliefs and investors

Basak (2005) provides a continuous-time pure-exchange framework to study asset pricing implication of the presence of heterogeneous beliefs, within a rational Bayesian setting. Equilibrium is determined in terms of a representative investor’s utility function with stochastic weighting driven by the investor’s disagreement about the aggregate growth. In addition, Levy et al. (2006) relax the homogeneous beliefs assumption of CAPM, which can be derived under various sets of assumptions. Under the homogeneous beliefs

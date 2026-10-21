
Like Meyer et al. (2012), we do not account for autocorrelation for two reasons. First, the majority of rolling window regressions do not report autocorrelation at the conventional significance level using the Breusch–Godfrey test. Second, it has the advantage of enhancing comparability between simulated and actual t-statistics through a uniform test specification. This is because the bootstrap simulations consist of random drawings of individual daily returns with replacements, which means the time-series drawn cannot contain any true underlying autocorrelation by design. We thus employ the robust standard errors that control for the autoregressive conditional heteroscedastic (ARCH) effect (see Appendix 55B).

### 55.3.3.2 Procedure II: Jointly resampling both the residuals and common risk factors

Motivated by Fama and French (2010), we repeat Procedure I by jointly resampling both the residuals and common risk factors in Step (iii), ceteris paribus. Specifically, in Step (iii), we generate two time-series of pseudo residuals {ε_t^b = T_1^b, ..., T_{252}^b} and risk factors {(R_{m,t} − R_{f,t})^b, SMB_t^b, HML_t^b} jointly by randomly drawing residuals and risk factors from the original residual vector {ε_t} and risk factor vector {(R_{m,t} − R_{f,t}), SMB_t, HML_t} with replacements, respectively. The major difference between the two bootstrapping procedures is that Procedure II considers the distribution of the residuals conditional on the realization of the systematic risk factors (see, Fama and French, 2010), while Procedure I employs the unconditional distribution of the residuals and assumes the influence of the common risk factors is not fixed at their historical realizations (see, Kosowski et al., 2006).

## 55.4 Results

In this section, we first report the results for the average daily abnormal returns to the long and short portfolios, followed by the simulated results. The abnormal returns to the long and short portfolios are calculated as the gross abnormal returns less the estimated transaction costs multiplied by the corresponding daily portfolio turnover in each rolling window. We employ a relatively cautious estimate of the average round-trip transaction costs in the UK for purchasing stocks at 1.5% and for short selling stocks at 3.0% (see, e.g., Hudson et al., 1996; Su et al., 2019).

### 55.4.1 Time-varying performance of the long and short portfolios

Throughout this section, we present the results under the Fama and French (1993) three-factor model, while our results remain qualitatively the same under the CAPM and the Carhart (1997) four-factor model, ruling out the concern on a poor model of asset pricing raised by Barber et al. (2001). Our empirical and simulated results under the CAPM and the Carhart (1997) four-factor model are not presented for the sake of brevity, but are available on request from the authors.

Figure 55.1A (B) shows the time-varying average daily abnormal returns to the long (short) portfolio and the corresponding t-statistics. Overall, we find that the abnormal returns to the long and short portfolios fluctuate over time during the whole sample period, while these positive or negative abnormal returns are not statistically significant at the conventional level. Specifically, the abnormal returns to the long portfolio range from −2.38 basis points (t-stat = −1.23) to 1.48 basis points (t-stat = 0.70), while the abnormal returns to the short portfolio range from −1.34 basis points (t-stat = −0.91) to 1.95 basis points (t-stat = 0.80). Our rolling window analysis results suggest that it is unlikely for investors to make profits either by purchasing stocks with positive revisions or by short selling stocks with negative revisions during any period of time.

Although a number of investment strategies based on analyst recommendation revisions fail to generate significant abnormal returns, Barber et al. (2001, p. 537) point out that “it remains an open question whether other types of trading strategies could be profitable”. A growing body of evidence shows that more prestigious brokerage houses have superior access to company managers and information; thus, their stock recommendations are supposed to be more readily available to investors (see, Stickel, 1995; Womack, 1996; Barber et al., 2001; Hong and Kubik, 2003; Green, 2006; Jegadeesh and Kim, 2006; Fang and Yasuda, 2014). For the robustness purposes, we construct two alternative long and short portfolios, based on a subsample of 55,092 analyst recommendation revisions made exclusively by top-5 brokerage houses, identified by their three year moving average (t − 3, t − 2, t − 1) of positions on the annual All-Europe Research Team published by Institutional Investor. For example, the ranking of each brokerage house in the calendar year of 1998 is determined based on its average position in the years of 1997, 1996, and 1995.7 Replicating all analyses in Figures 55.1A and 55.1B, we find that our results remain qualitatively the same (see Figures 55.2A and 55.2B). That is, investment strategies following UK sell-side analyst recommendation revisions could not generate significant abnormal returns, irrespective of whether these stock recommendations are made by sell-side analysts working for more or less prestigious brokerage houses.

(A)

The average daily abnormal returns to the long portfolio

(a)

t-statistics of the average daily abnormal returns to the long portfolio

(b)

(B)

The average daily abnormal returns to the short portfolio

(a)

t-statistics of the average daily abnormal returns to the short portfolio

(b)

Figure 55.1: (A). The time-varying average daily abnormal returns to the long portfolio and the corresponding t-statistics under the Fama and French (1993) three-factor model, based on the whole sample of UK sell-side analyst recommendations. (B). The time-varying average daily abnormal returns to the short portfolio and the corresponding t-statistics under the Fama and French (1993) three-factor model, based on the whole sample of UK sell-side analyst recommendations.

Notes: Figure 55.1A (B) here illustrates the time-varying average daily abnormal returns to the long (short) portfolio using the whole sample of UK sell-side analyst recommendations over the period January 1997 to June 2013. The long portfolio includes all upgrades to Strong Buy or Buy from previous Strong Sell, Sell, or Hold, while the short portfolio includes all downgrades to Strong Sell, Sell, or Hold from previous Strong Buy or Buy. For each analyst recommendation made by a brokerage house, the recommended stock enters the long or short portfolio at the close of trading on the day the recommendation is released, and remains in the portfolio until the close of trading on the day the recommendation expires. The abnormal return is estimated as the intercept term derived from the Fama and French (1993) three-factor model on a one-year window length rolling one trading day forward. The reported abnormal returns in this section are the abnormal net returns adjusted by the round-trip transaction costs in the UK, i.e., 1.5% for purchasing stocks and 3.0% for short selling stocks.

![](img/31ee7e6fa5107b22bbf7960ec96106a1_2116_0.png)

![](img/31ee7e6fa5107b22bbf7960ec96106a1_2116_1.png)

![](img/31ee7e6fa5107b22bbf7960ec96106a1_2116_2.png)

![](img/31ee7e6fa5107b22bbf7960ec96106a1_2116_3.png)

### 55.4.2 Bootstrapping simulations

As our results suggest that sell-side analysts cannot provide valuable stock recommendation revisions, we further examine whether the observed insignificant abnormal returns are simply as a result of these analysts’ bad luck or their inferior skill (Fama, 1998; Barber et al., 2001). We compare any actual t-statistic of alpha with its appropriate luck distribution to distinguish whether sell-side analysts have sufficient skill in making valuable stock recommendations. Like, Kosowski et al. (2006), Barras et al. (2010), and Fama and French (2010), we focus on the distribution of the t-statistic of alpha rather than the actual alpha, as the t-statistic has superior statistical properties (see, Brown et al., 1992). Specifically, the t-statistic accounts for differences in the precision of alpha. Consider, for example, an investor who takes high risks or who only has a short time-series of portfolio returns. That investor can more easily exhibit extreme estimated alphas, which, however, are likely to be spurious outliers. The t-statistic corrects for that by scaling the alphas by its standard errors. Through this rescaling, the t-statistic accounts even more generally for the differences in risk-taking and number of observations in the whole rolling windows. The time-series distribution of the t-statistic of alpha, therefore, has the statistically preferable attribute of being closer to a normal distributed than the time-series distribution of alpha. Therefore, we compare the t-statistics of alphas at selected percentiles of the CDF of the actual t-statistics of alphas with the average of the 10,000 simulated t-statistics at the same percentiles. For the outperforming sub-samples, if the simulated t-statistic is higher than the actual t-statistic in

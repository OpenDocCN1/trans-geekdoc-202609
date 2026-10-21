
implications of earnings information. Some investors may be unable to form an unbiased expectation of future earnings immediately upon revelation of current earnings, with some portion of the response not occurring until analyst’s forecasts are revised or future earnings are realized. Kormendi and Lipe (1987) and Freeman and Tse (1989) also provide little evidence to indicate that responses to current earnings reflect at least some of the implications for future earnings. Empirical evidence provided in recent studies generally concluded that the market does not fully understand the implication of current earnings for future earnings. For example, Maines and Hand (1996) suggest that individuals do not fully understand the implications of current earnings for future earnings for a quarterly earnings time-series process as simple as a seasonal random walk. Rangan and Sloan (1998) show that the stock market appears to ignore the variation of the auto-regressive coefficients of quarterly earnings. In their study, Lys and Soffer (1999) and Brown and Han (2000) provide evidence that is consistent with the view that the market is unaware of autocorrelation in quarterly earnings. However, the evidence regarding the post-earnings-announcement drifts provided by FOS and Bernard and Thomas is challenged by Beneish et al. (1994). They contend that both research designs are subject to Ball’s proxy critique. When they control these research design problems through portfolio formation on a daily basis and the use of financial analysts’ forecast as proxy for earnings expectation, the PEAD no longer exists.

In summary, the question as to whether the PEAD arises from market inefficiency or inappropriate empirical design remains unanswered. Commonly used in the event studies, the capital asset pricing model explicitly assumes the variances of abnormal returns to be constant. This assumption implies that the market does not revise its assessment of risk in the presence of new information about firm’s operating performance. Although BKW’s findings are consistent with the hypothesis that risk shifts occur as a function of changes in earnings, they have not yet been able to develop an appropriate approach that captures the instability of the systematic risk for the investigation of the information content hypothesis of accounting earnings. BKW’s findings might not hold when more sample firms and the shorter post-announcement periods are involved as well. Since most of the drift occurs within three months of the earnings announcement, quarter-return periods should provide a more powerful test.

This chapter proposes an alternative method that uses quarterly earnings and daily stock returns to investigate how the market revises its assessment of the systematic risk on earnings announcement. This research is motivated by the findings of previous studies that large and small fluctuation of economic series tend to cluster together in continuous time periods. Engle (1982) proposes the autoregressive conditional heteroscedasticity (ARCH) model to describe the aforementioned phenomena, particularly in the fluctuation of foreign exchange rates. Diebold et al. (1993) also provide evidence that the monthly stock returns of the NYSE firms have a rather common ARCH effect during the 1939–1983 period. They found that about 25% of NYSE firms have significant ARCH effects at the 10% level. This phenomenon raises the concerns of the test methodology of event studies that assumes homoscedasticity in residual returns. The sample average abnormal return is an efficient estimator of the expected abnormal return in the presence of heteroscedasticity. They therefore suggest that the identification of a well-defined variance structure such as ARCH can be used to improve research design.

Specifically, we develop a time-varying systematic risk model with return to normality by employing the theoretical framework in Bollerslev et al. (1988) who cast the ARCH model into the CAPM.¹ We expect that the market would revise their assessment of systematic risks once the accounting earnings have been announced. We use Kalman filter to estimate how the market revises the systematic risks subsequent to the announcement of accounting earnings. We then examine the cumulative abnormal returns (CARs) estimated from both the conventional as well as the time-varying systematic market models to see if the PEADs can be attributed to the misspecification of CAPM.

Our empirical analysis is based on a sample of US publicly held companies during the five-fiscal year sample period, 2010–2014. Controlling for misspecification and other potential confounding effects, we document that the phenomenon of PEADs are economically insignificant for investment decision making.

This chapter adds to the literature in two ways. First, we provide empirical evidence on how the revision of systematic risk affects the phenomenon of PEADs. Secondly, we provide an alternative approach for reducing the misspecification of CAPM. More specifically, we show that incorporating Kalman filter and ARCH into the conventional CAPM helps reduce the conditional heteroscedasticity subsequent to earnings announcement.

> Bollerslev et al. (1992) cite over 200 articles using ARCH techniques in a wide variety of finance applications. However, this technique has not yet become popular in accounting literature.

## The Revision of Systematic Risk on Earnings Announcement in the Presence

The following section provides model development. Section 53.3 discusses the empirical design and data. Section 53.4 provides the empirical results. Section 53.5 provides the conclusion.

Whether the conditional variances of monthly returns have been smoothed through the aggregation of daily returns or not is an empirical issue. However, the daily returns, which are critical for investigating the phenomenon of PEADs, have much higher percentage of showing ARCH than the monthly returns used in Diebold et al. (1993).²

These tentative results provide us with the incentive to investigate the impact of ARCH effect on the conventional CAPM. More specifically, we illustrate that the systematic risk is no longer constant as the conventional CAPM states. The investors will revise their assessment of systematic risk continuously as the new information comes in.

Following Bollerslev et al. (1988), the market with ARCH can be represented as

```
Y_{i,t} = Y_{m,t}β_t + ε_{i,t} ; ε_{i,t} ~ N(0, H_{i,t}), (53.1)
```

where Y_{i,t} represents the excess return of security i at time t, which is defined as R_{i,t}−R_{f,t}. R_{i,t} is a N∗1 vector of return of risky security i at time t; R_{f,t} is a N∗1 vector of return of riskless security at time t. Y_{m,t} represents the excess return of market portfolio at time t and is defined as Y_{i,t}^′W_{i,t−1}. W_{i,t−1} is the proportion of wealth invested in risky asset at time t−1. Y_{i,t}|Ω_{i,t−1} is normally distributed with mean Y_{m,t}β_t and conditional variance H_{i,t}. Ω_{i,t−1} is the information set available at time t−1. H_{i,t} is the conditional variance.

The conditional mean and variance of Y_{i,t} is defined as

```
U_{i,t} = E_{t−1}(Y_{i,t}), (53.2a)
```

```
H_{i,t} = E_{t−1}(Y_{i,t}Y_{i,t}^′), (53.2b)
```

respectively, where H_{i,t} follows the ARCH process as suggested in Engle (1982).

The CAPM developed by Jensen et al. (1972) can be written as

```
E(R_i − R_f) = δCov(R_i − R_m), (53.3)
```

> ²See Judge et al. (1985, pp. 809-811).

where
δ = [E(R_m) - R_f]/Var(R_m) is the price per unit of risk and is invariant over firms.

The traditional CAPM is stated in the form of unconditional expectation. Let us assume that prior information will affect current expectation of security return; then the CAPM in the form of conditional expectation is

E_{t-1}(R_{i,t} - R_{f,t}) = δ Cov_{t-1}(R_{i,t} - R_{m,t}). (53.4)

The conditional covariance matrix of risky assets and market portfolio and the conditional variance of market portfolio can be written as

E_{t-1}(Y_{i,t}Y_{m,t}) = H_{i,t}W_{i,t-1}, (53.5)

and

E_{t-1}(Y'_{m,t}Y_{m,t}) = W'_{i,t-1}H_{i,t}W_{i,t-1} (53.6)

respectively,

Substituting equation (53.5) into equation (53.4) yields

U_{i,t} = δ H_{i,t}W_{i,t-1}. (53.7)

The conditional expected return of market portfolio can be written as

U_{m,t} = W'_{i,t}U_{i,t}. (53.8)

Substituting equation (53.7) into equation (53.8) and applying the result of equation (53.6) yields

U_{m,t} = δ σ_{m,t}^2. (53.9)

By definition the systematic risk β_{i,t} is

β_{i,t} = H_{i,t}W_{i,t-1}/σ_{m,t}^2. (53.10)

Therefore,

σ_{m,t}^2 = H_{i,t}W_{i,t-1}/β_{i,t}. (53.11)

Substituting equations (53.11) and (53.7) into (53.9) yields

U_{m,t} = U_{i,t}/β_{i,t}. (53.12)

Finally, the traditional CAPM with ARCH can be expressed as

U_{i,t} = β_{i,t}U_{m,t}, (53.13)

which is equivalent to

E_{t-1}(R_{i,t}) = R_{f,t} + β_{i,t}[E(R_{m,t}) - R_{f,t}]. (53.14)

Equation (53.14) indicates that the systematic risk is time-variant. However, equation (53.14) is an ex ante model with unobservable components: conditional expected return of risky assets and market portfolio. In practice, the

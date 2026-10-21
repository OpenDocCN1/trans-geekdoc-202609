
demonstrates that not only does using the AAF methodology improve the accuracy of the risk prediction, it also moves the ex post frontier upwards, thereby giving ex post performance improvements. In other words, the AAF approach recognizes the possibility of missing systematic risk factors and makes amends to the greatest extent that is possible without a complete recalibration of the risk model that accounts for the latent systematic risk in alpha factors explicitly. In the process of doing so, AAF approach not only improves the accuracy of risk prediction, but also makes up for the lack of efficiency in the optimal portfolios.19 Saxena and Stubbs (2015) extended their 2012 Journal of Investing research and reported positive frontier spreads.

Guerard et al. (2015) tested CTEF and a 10-factor regression-based model of global expected returns, GLER, during the 1997-2011 time period. The authors reported that the geometric means and Sharpe ratios increase with the targeted tracking errors; however, the information ratios are higher in the lower tracking error range of 3-6%, with at least 200 stocks, on average, in the optimal portfolios. They reported that statistically-based risk models using principal components, such as SunGard APT and Axioma, produce more efficient trade-off curves than fundamentally-based risk model using our variables. Risk was underestimated substantially at higher targeted tracking errors, with the AAF producing higher Sharpe ratios and information ratios in both Fundamental and Statistical risk model tests, particularly in the 7-10% targeted tracking error range. The Axioma Statistical Risk Model was sufficient for CTEF whereas the Axioma Statistical Model with AAF of 20% was optimal for the GLER Model.

The Markowitz (1952, 1959) portfolio construction approach seeks to identify the efficient frontier, the point at which returns are maximized for a given level of risk, or risk is minimized for a given level of return. The portfolio expected return, E(Rp), is calculated by taking the sum of the security weights multiplied by their respective expected returns. The portfolio standard deviation is the sum of the weighted covariances.

```
E(R_p) = \sum_{i=1}^N x_i E(R_i) = \sum_{i=1}^N x_i \mu_i, 
 \sigma_p^2 = \sum_{i=1}^N \sum_{j=1}^N x_i x_j c_{ij},
```

where μ is the expected return vector, C is the variance–covariance matrix, x is the portfolio weights. The efficient frontier can be traced out by

```
minimize_{x_i \ge 0, x_i \le \bar u} x^T C x - \lambda \mu^T x,
```

where λ is the risk-return tradeoff parameter and ū is the fixed upper bound.

However, as the number of securities, N, increases, the number of variance-covariances increases faster, at being N × (N + 1)/2. This leads to estimate C by a factor model, in which the individual stock return R_j of security j at time t, dropping the subscript t for time, may be written like this:

```
R_j = \sum_{k=1}^K \beta_{jk} \tilde f_k + \tilde e_j.
```

The non-factor, or asset-specific, return on security j, \tilde e_j, is the residual risk of the security after removing the estimated impacts of the K factors. The term f_k is the rate of return on factor k. The factor model simplifies the C as the sum of the systematic risk covariance and diagonal specific variances,

```
C = \beta C_{f,f'} \beta' + \Sigma.
```

If the investor is more concerned about tracking a particular benchmark, the mean-variance optimization in equation (30.17) can be reformulated as a mean-variance tracking error at risk (MVTaR) optimization:

minimize(x − x_b)^T C(x − x_b) − λμ^T(x − x_b), (30.20)

where x_b is the weight vector of the benchmark.

One can enhance the tracking by adding equal active weighing constraints (EAW):

|x_j − (x_b)_j| ≤ y, for all j. (30.21)

The MVTA with constraints in equation (30.21) will be referred to as EAW-TaR. The EAWTaR optimization technique enhances Information Ratios, relative to MVTA, because it lowers realized tracking errors.21 We believe that the EAWTaR optimization techniques creates portfolio that are consistent with the semi-variance and skewness applications.

## 30.5 Has the Financial World Changed from 2003 (or 2010)? Empirical Results

Global modeling for a “global growth specialist”, such as McKinley Capital Management, LLC (2006a, b), involves the use of larger weighting of momentum and forecasted earnings acceleration factors. In this analysis, we report results for two universes: Russell 3000 Index stocks for US stocks; and (2) the index constituents of the MSCI All Country World ex USA (ACWexUS) and EAFE Universes for international stocks. Our data source is the FactSet Worldscope database. The REG8, REG9CTEF, and REG10 models are estimated using the FactSet database for US and All Country World Investable ex US and EAFE stocks for the 1997–2016 time period and subperiods. Moreover, we use the Beaton–Tukey bisquare procedure to estimate robust regression estimates of the models. We use latent root regression to address the issue of multicollinearity. The WLRR analysis is very similar to the Leamer Bayesian analysis of multicollinearity (1973, 1978) and Lin et al. (2011).

We create forecasted earnings acceleration growth variable and corporate exports variables. Our analysis is developed for the December 1996–November 2016 period. Our simulation conditions assume 8% monthly turnover, 35 basis point threshold positions, an upper bound in

21 Markowitz reminds researchers that Chapter 9 of his seminal Portfolio Selection (1959) introduced the semi-variance to portfolio construction. Financial researchers, such as Konno et al. (1993), Konno et al. (1993), King (1993), and Kijima and Ohnishi (1993), examined alternative risk modeling techniques, including the semi-variance, to enhance the risk–return trade-off.

mean–variance (MV) optimization of 4% on security weights, and ITG transactions costs.22

Guerard et al. (2015) reported three levels of testing investment strategies.23 In this analysis we restrict ourselves to levels I and II tests of Information Coefficients, ICs, Efficient Frontiers. We seek to maximize the Geometric Mean (GM), Information Ratios (IRs), and Sharpe Ratios (ShRs). In Sections 30.2 and 30.3, we traced the model development of CTEF, REG8, REG9CTEF, and REG10. We rank these variables, low to high, 99 is preferred, and we refer to ranked CTEF as CTEF (RCTEF). In the US universe, using Russell 3000 stocks, we estimate REG10, known also as US Expected Returns, or USER, see Guerard, Xu, and Gultekin (2012) and Guerard, Markowitz, and Xu (2014). If we examine the ICs over the December 1996–November 2016, and its 15, 10, 5, 3, and 1-year time sub-periods, we report in Table 30.3 that ranked CTEF has the highest Information Coefficient among US financial variables, in the 20-year time period as well as the 15-year, 10-year, five-year, three-year time periods, and is statistically significant in these time periods. The ranked CTEF is generally followed by REG9CTEF in most time periods which is almost always statistically significant. REG10 is most often third and REG8 is fourth in the US. The RCTEF, REG9CTEF, and USER quintile spreads approach 15–17%, annually, for 20 years. The ranked earnings-to-price, REP, and ranked book value-to-price, RBP, are included and are not generally statistically significant, see Table 30.3. In terms of the top decile minus bottom decile spreads, REG10, REG9CTEF, and RCTEF, lead the variables, see Table 30.3. How often should portfolios turnover? Bloch et al. (1993) argued for lower turnover to maximize the Geometric Mean. We agree! We report in Table 30.4, that monthly turnover of 10 and 20% maximizes the Geometric Mean. TO (10) means 5% buys and 5% sells (or both way, round-trip turnover). Turnover exceeding 10% buys

22 ITG estimate our transactions costs to be about 60 basis points, each-way, for 2011-2015.

23 The first level is the information coefficient, IC, of a strategy in which the subsequent ranked returns are regressed as a function of the ranked financial strategy. The regression coefficient is the IC which is a randomly distributed variable to test the statistical significant of the individual variable or composite model strategies. The second level of investment testing is to estimate, with transactions costs, the Markowitz efficient frontier, by varying either the lambda or the targeted tracking error. The third level of testing is to apply the Markowitz and Xu (1994) Data Mining Corrections, DMC, to test whether the strategy is statistically different from any model that could have been used. Moreover, the regression coefficient of the DMC test indicates how much excess returns could be continued into the future, holding everything else constant.

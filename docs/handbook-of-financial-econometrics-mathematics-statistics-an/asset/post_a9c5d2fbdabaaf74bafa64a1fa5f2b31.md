
the importance scores for i and adjacency matrix A = [a_ij]. The solution is represented by the eigenvector corresponding to the eigenvalue 1.

PageRank is a version of the eigenvector centrality measure. There are different versions of the measure. In one version, the value of a network node centrality is calculated by the following formula

```
PR(i) = (1 - α) + α · ∑_j PR(j → i) / |N_j(g)| , (9C.4)
```

where PR(i) is the value of the node centrality i, α is the so-called damping factor (usually set at 0.85), PR(j → i) is the value of the central node j, which has a direct link with the node i, N_j(g) is the number of links of node j. In other words, PageRank for node i is determined by the PageRank of each node j, which has a direct link with the node i.

## Chapter 10: Application of the Multivariate Average *F*-Test to Examine Relative Performance of Asset Pricing Models with Individual Security Returns

Shafiqur Rahman and Matthew J. Schneider

## Contents

- 10.1 Introduction ... 392
- 10.2 Multi-Factor Models ... 396
- 10.3 Data and Research Methodology ... 401
  - 10.3.1 Data description ... 401
  - 10.3.2 Balanced versus unbalanced data panel ... 402
  - 10.3.3 The average *F*-test ... 402
  - 10.3.4 Simulation analysis ... 405
- 10.4 Empirical Analysis ... 407
  - 10.4.1 Summary statistics for individual security returns ... 407
  - 10.4.2 Model performance measures ... 408
  - 10.4.3 Results from the average *F*-test and pricing errors ... 409
  - 10.4.4 Relative performance of models ... 414
  - 10.4.5 Variance inflation factor analysis ... 418
  - 10.4.6 Factor loadings and forces behind model performance ... 420
  - 10.4.7 GRS test of intra-industry securities ... 423
- 10.5 Conclusions ... 425
- Bibliography ... 427

## Abstract

The standard multivariate test of Gibbons et al. (1989) used in studies examining relative performance of alternative asset pricing models requires the number of stocks to be less than the number of time-series observations, which requires stocks to be grouped into portfolios. This results in a loss of disaggregate stock information. We apply a new statistical test to get around this problem. We find that the multivariate average F-test developed by Hwang and Satchell (2014) has superior power to discriminate among competing models and does not reject tested models altogether, unlike the standard multivariate test. Application of the multivariate average F-test for examination of relative performance of asset pricing models demonstrate that a parsimonious 6-factor model with the market, size, orthogonal value, profitability, investment, and momentum factors outperforms all other models.

## Keywords

Multivariate F-test ● Asset pricing ● Factor models ● Market portfolio ● Size ● Book-to-market ● Momentum ● Investment ● Profitability ● Liquidity risk ● Factor loadings ● GRS test.

### 10.1 Introduction

Over the past 50 years, much work has been done on examining the relationship of the variation in asset returns to the variation in factor returns. Competitive models of asset pricing first started with the capital asset pricing model (CAPM) of Sharpe (1964), Lintner (1965), and Mossin (1966) and the arbitrage pricing theory (APT) formulated by Ross (1976, 1977) and later refined by Huberman (1982), Chamberlain and Rothschild (1983), Chen and Ingersoll (1983), Connor (1984), and Ingersoll (1984). These are ex ante models to explain the cross-sectional variation in asset returns.

Having recognized the apparent inability of CAPM to explain cross-sectional variation in asset returns, Fama and French (1993, 2015) took a different approach. Using the relationship between asset prices and observed variables representing firm-level characteristics and associated risks, the authors developed multi-factor models to explain cross-sectional variation in asset returns. These latter models are ex post or empirical models that look at the behavior of stock prices and reverse-engineer them to identify which factors explain and predict variation in stock returns.[^1] Fama and French (1993, 2015) examine the explanatory power of their models by applying the respective models to hypothetical portfolios formed on size, book-to-market (B/M) ratio, and other relevant financial variables.[^2] However, returns on these innovative but imaginative portfolios are not directly observed in the marketplace. Moreover, individual as well as institutional investors, except for specialized mutual or exchange traded funds, seldom form portfolios based on market cap, B/M, price-earnings (P/E) ratio, or any combination thereof. Investors form portfolios by bundling securities across markets, sectors, industries, etc., to achieve maximum diversification. From a practical standpoint, it is almost impossible to replicate investors’ (individual as well as institutional) portfolios. Tests of asset pricing models should preferably be applied to directly observed individual security returns. This will help investors select securities based on the exposure of securities to the factor(s) in a model.

Primary reason for grouping securities into portfolios is to employ a conventional multivariate *F*-test proposed by Gibbons *et al.* (1989), popularly known as the GRS test. The GRS test requires that the number of assets (*N*) does not exceed the number of time-series observations (*T*). This is because when *N* > *T*, the sample variance-covariance matrix of asset returns becomes singular and is not invertible (Knight and Satchell, 2005). To get around this restriction, portfolios are formed from securities, thereby ensuring that *N* < *T*. Grouping securities into portfolios to satisfy the conditions of the GRS test does not always serve this purpose well. The GRS test easily rejected all models tested in Fama and French (2015, 2016).

Another motivation for grouping stocks into portfolios is to reduce the errors-in-variables (EIV) problem inherent in estimating betas. Since measurement errors in betas across securities are not perfectly correlated, grouping would likely decrease the asymptotic bias in OLS estimators (Litzenberger and Ramaswamy, 1979). Errors-in-variable bias would be reduced and should approach zero as the number of securities (*N*) grows without bound, since portfolios would have less idiosyncratic risk (Jegadeesh *et al.*, 2015). However, forming portfolios by grouping stocks results in a reduction of efficiency caused by the loss of information regarding the cross-sectional behavior of individual stocks unrelated to portfolio groupings. Portfolios diversify away and mask the relevant risk and return features of individual stocks. Connor and Korajczyk (1988) point out that such a grouping procedure may conceal important deviations from the model under review if the deviations are related to the attributes used to assign assets into portfolios.

While creating portfolios reduces the sampling variability of the estimates of factor loadings, the standard errors of factor risk premia actually increase (see Roll, 1977; Ang et al., 2009, 2010; Hwang and Satchell, 2014). Ang et al. (2010) show analytically and demonstrate empirically that the smaller standard errors of beta estimates from creating portfolios do not lead to smaller standard errors of cross-sectional coefficient estimates. The standard errors of factor risk premia estimates are determined by the cross-sectional distributions of factor loadings and residual risk. Creating portfolios destroys information by shrinking the cross-sectional dispersion of betas and inflates the standard errors of estimated coefficients (Ang et al., 2010). Furthermore, Lo and MacKinlay (1990) note that tests of asset pricing models may yield misleading inferences when tests are based on returns to portfolios constructed by sorting on empirically motivated characteristics such as size, beta, or book-to-market. They argue that these are examples of “data-snooping,” and this kind of data-snooping could lead to rejection of the null hypothesis too often, an increase in type I error. Kim (1995) notes that the formation of portfolios might cause a loss of valuable information about cross-sectional behavior among individual assets, since cross-sectional variations would be smoothed out. He considers using all available individual stocks (without forming portfolios) in the estimation process as an efficient way to avoid loss of information. Ferson et al. (1999) point out that many empirical studies use the returns of attribute-sorted portfolios of common stocks to represent risk factors in tests of asset pricing models, where the attributes are selected on the basis of empirically observed relationships to the cross-section of stock returns. They argue that such attribute-sorted portfolios may present useful risk factors even when the attributes are completely unrelated to risk exposure. Jegadeesh et al. (2015) point out that when using portfolios, rather than individual assets, there is an immediate issue of test power since dimensionality is reduced, i.e., there are unavoidably fewer explanatory variables with portfolios than with individual assets. Berk (2000) shows that the standard practice of grouping stocks into portfolios to test asset pricing inferences introduces a bias in rejecting the model under consideration. A direct and more effective method to deal with these problems is to use individual stocks instead of characteristics- or attribute-sorted portfolios in testing asset pricing models (Hwang and Lu, 2007).

This study is an attempt to empirically explore the explanatory power of Fama and French’s (2015) 5-factor model, an extended version of the 4-factor

[^1]: DeMuth (2014) compared this approach to building a transcontinental railroad starting from the final destination, San Francisco, and working backwards.

[^2]: Researchers have used hundreds of factors to explain the cross-sectional variation of expected returns. See Harvey *et al.* (2016) for further details on the factors used and a survey of related literature.

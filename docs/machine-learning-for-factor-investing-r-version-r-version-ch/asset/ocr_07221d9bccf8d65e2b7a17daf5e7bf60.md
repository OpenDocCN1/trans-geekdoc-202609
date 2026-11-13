# 3.2.4 Fama-Macbeth regressions

Another detection method was proposed by Fama and MacBeth (1973) through a two-stage regression analysis of risk premia. The first stage is a simple estimation of the relationship (3.1): the regressions are run on a stock-by-stock basis over the corresponding time series. The resulting estimates \(\hat{\beta}_{i,k}\) are then plugged into a second series of regressions:

\(r_{t,n} = \gamma_{t,0} + \sum_{k=1}^K \gamma_{t,k}\hat{\beta}_{n,k} + \varepsilon_{t,n},\) (3.4)

which are run date-by-date on the cross-section of assets.¹ Theoretically, the betas would be known and the regression would be run on the \(\beta_{n,k}\) instead of their estimated values. The \(\hat{\gamma}_{t,k}\) estimate the premia of factor \(k\) at time \(t\). Under suitable distributional assumptions on the \(\varepsilon_{t,n}\), statistical tests can be performed to determine whether these premia are significant or not. Typically, the statistic on the time-aggregated (average) premia \(\hat{\gamma}_k = \frac{1}{T} \sum_{t=1}^T \hat{\gamma}_{t,k}\) :

\(t_k = \frac{\hat{\gamma}_k}{\hat{\sigma}_k / \sqrt{T}}\)

is often used in pure Gaussian contexts to assess whether or not the factor is significant (\(\hat{\sigma}_k\) is the standard deviation of the \(\hat{\gamma}_{t,k}\) ).

We refer to Jagannathan and Wang (1998) and Petersen (2009) for technical discussions on the biases and losses in accuracy that can be induced by standard ordinary least squares (OLS) estimations. Moreover, as the \(\hat{\beta}_{i,k}\) in the second-pass regression are *estimates*, a second level of errors can arise (the so-called errors in variables). The interested reader will find some extensions and solutions in Shanken (1992), Ang et al. (2018) and Jegadeesh et al. (2019).

Below, we perform Fama and MacBeth (1973) regressions on our sample. We start by the first pass: individual estimation of betas. We build a dedicated function below and use some functional programming to automate the process.

```
```r
nb_factors <- 5
 data_FM <- left_join(data_ml %>%
   dplyr::select(date, stock_id, R1M_Usd) %>%
   filter(stock_id %in% stock_ids_short),
   FF_factors,
   by = "date") %>%
 mutate(R1M_Usd = lag(R1M_Usd)) %>%
 na.omit() %>%
 spread(key = stock_id, value = R1M_Usd)
models <- lapply(paste0("'", stock_ids_short,
         ~ MKT_RF + SMB + HML + RMW + CMA'),   # Model spec
```
```

¹Originally, Fama and MacBeth (1973) work with the market beta only: \(r_{t,n} = \alpha_n + \beta_{n,t_M} + \epsilon_{t,n}\) and the second pass included nonlinear terms: \(r_{t,n} = \gamma_{n,0} + \gamma_{t,1}\hat{\beta}_n + \gamma_{t,2}\hat{\beta}_n^2 + \gamma_{t,3}\hat{s}_n + \eta_{t,n}\), where the \(\hat{s}_n\) are risk estimates for the assets that are not related to the betas. It is then possible to perform asset pricing tests to infer some properties. For instance, test whether betas have a linear influence on returns or not (\(\mathbb{E}[\gamma_{t,2}] = 0\)), or test the validity of the CAPM (which implies \(\mathbb{E}[\gamma_{t,0}] = 0\)).
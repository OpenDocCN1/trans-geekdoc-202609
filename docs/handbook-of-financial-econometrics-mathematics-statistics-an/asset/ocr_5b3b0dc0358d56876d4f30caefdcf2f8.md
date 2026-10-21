according to the cointegration theory proposed by Engle and Granger (1987) and Johansen (1988). According to Johansen cointegration test results, various time-series, such as the TAIEX, INDU, exchange rate, and consumer price index, have cointegration. In other words, the test results suggest that the relationships among the time-series are not caused by spurious regression. Based on the relationships among the time-series, this study has established the ECM and transfer function prediction models for the TAIEX.

# 6.3.2 Integration of the intervention analysis into ARIMA-GARCH model

When establishing the ARIMA process model, the researchers first determined the order of the series: ARIMA(p,1,q)p < 5, q < 5. According to the selection standards for Akaike Information Criterion (AIC) and Schwartz Information Criterion (SIC), ARIMA (0,1,1) achieved the minimum AIC and SIC. In the Ljung-Box Q test, the residuals had no autocorrelation, but the Ljung-Box Q² test showed that the residuals were inconsistent; in other words, the residuals demonstrated the problem of heteroskedasticity. The researchers used ARIMA (0,1,1)-GARCH(1,1) to modify the model, but the residual problem had not been solved completely. According to the outlier detection results shown in Table 6.3, the model detected the temporary changes (TC) in July 1997, July 2007, and additive outliers (AO) in November 1993, and November 2001.

According to Box and Tiao (1975), when affected by external events at a specific point in time, intervention analysis should be incorporated in the model establishment process. The detected external events of July 1997, July 2007, November 1993, and November 2001 are, therefore, incorporated into the model analysis to construct the model for the TAIEX, which can be

Table 6.3: Outlier detection results.

| Year | Month | Coef. | t-value | Outlier types |
|------|-------|-------|---------|---------------|
| 1993 | 11 | 0.329 | 5.05*** | AO |
| 1997 | 7 | -0.151 | -3.37*** | TC |
| 2001 | 11 | 0.329 | 5.05*** | AO |
| 2007 | 7 | -0.151 | -3.37*** | TC |

Note: ***Coefficients indicate that they are significantly different from zero at the 1% significance level.
Source: Compiled by the researchers.
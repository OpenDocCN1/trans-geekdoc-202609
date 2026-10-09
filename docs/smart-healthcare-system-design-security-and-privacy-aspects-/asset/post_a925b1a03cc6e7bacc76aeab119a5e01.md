
## **Table 14.2** Partial auto correlation of second differenced daily new cases.

| **Lag** | **Partial autocorrelation** | **Std. error** |
|---|---|---|
| 1 | −0.297 | 0.088 |
| 2 | −0.196 | 0.088 |
| 3 | −0.197 | 0.088 |
| 4 | −0.219 | 0.088 |
| 5 | −0.407 | 0.088 |
| 6 | −0.344 | 0.088 |
| 7 | −0.024 | 0.088 |
| 8 | 0.049 | 0.088 |
| 9 | 0.19 | 0.088 |
| 10 | −0.055 | 0.088 |
| 11 | −0.012 | 0.088 |
| 12 | −0.143 | 0.088 |
| 13 | −0.155 | 0.088 |
| 14 | 0.136 | 0.088 |
| 15 | 0.147 | 0.088 |
| 16 | 0.086 | 0.088 |

The ARIMA model ARIMA (2, 2, 2) and ARIMA (0, 2, 1) is fitted to the second difference series of daily new cases and daily new deaths respectively. The adequacy of this model is also studied on the analysis of residuals.

From the normal P–P plot (Figures 14.21 and 14.22) for estimated residuals; we infer that the distribution of residuals may be normal. Therefore, the given model may be used for forecasting purpose [3, 4, 6, 12].

Figures 14.19 and 14.20 show that maximum values of ACF and PACF are lying within the confidence limit. Hence, from all the studies, the estimated ARIMA model ARIMA (2,2,2) and ARIMA (0,2,1) are found to be adequate and therefore model can be used for forecasting reason of daily COVID-19 new cases in the world and COVID-19 new deaths in the world. Forecasting values are given in Tables 14.11 and 14.12. These values are presented diagrammatically in Figures 14.23 and 14.24.

## **Table 14.3** Autocorrelation with second differenced values are obtained by transforming non stationary to stationary with respect to daily new deaths using Box Ljung Statistic.

| **Lag** | **Autocorrelation** | **Std. error**$^{a}$ | **Box-Ljung statistic Value** | **df** | **Sig.**$^{b}$ |
|---|---|---|---|---|---|
| 1 | −0.353 | 0.087 | 16.45 | 1 | 0 |
| 2 | −0.224 | 0.087 | 23.12 | 2 | 0 |
| 3 | 0.099 | 0.086 | 24.43 | 3 | 0 |
| 4 | 0.016 | 0.086 | 24.47 | 4 | 0 |
| 5 | −0.19 | 0.086 | 29.38 | 5 | 0 |
| 6 | −0.094 | 0.085 | 30.58 | 6 | 0 |
| 7 | 0.388 | 0.085 | 51.42 | 7 | 0 |
| 8 | 0.19 | 0.085 | 56.45 | 8 | 0 |
| 9 | −0.472 | 0.084 | 87.84 | 9 | 0 |
| 10 | 0.134 | 0.084 | 90.38 | 10 | 0 |
| 11 | 0.119 | 0.084 | 92.4 | 11 | 0 |
| 12 | −0.285 | 0.083 | 104.2 | 12 | 0 |
| 13 | −0.047 | 0.083 | 104.5 | 13 | 0 |
| 14 | 0.36 | 0.082 | 123.6 | 14 | 0 |
| 15 | 0.097 | 0.082 | 125 | 15 | 0 |
| 16 | −0.278 | 0.082 | 136.5 | 16 | 0 |

$^{a}$Standard error analysis
$^{b}$Significance in second differenced values

## **Table 14.4** Partial auto correlation of second differenced daily new deaths.

| **Lag** | **Partial autocorrelation** | **Std. error** |
|---|---|---|
| 1 | −0.353 | 0.088 |
| 2 | −0.398 | 0.088 |
| 3 | −0.206 | 0.088 |
| 4 | −0.158 | 0.088 |
| 5 | −0.357 | 0.088 |
| 6 | −0.614 | 0.088 |
| 7 | −0.44 | 0.088 |
| 8 | 0.177 | 0.088 |
| 9 | −0.063 | 0.088 |
| 10 | −0.051 | 0.088 |
| 11 | 0.132 | 0.088 |
| 12 | 0.032 | 0.088 |
| 13 | −0.149 | 0.088 |
| 14 | −0.002 | 0.088 |
| 15 | 0.057 | 0.088 |
| 16 | −0.027 | 0.088 |

# 14.4.2 Regression Model for Daily New Cases and New Deaths

A simple linear regression model is fitted by considering daily new deaths as the response variable and daily new cases as the predictor variable [2, 5].

The scatter plot for daily new cases against daily new deaths is given in Figure 14.25. It shows the linear relationships between the daily new cases and daily new deaths. Hence, a LR model is an appropriate to find out the relationship between daily new cases and daily new deaths which is highly significant. The output presented in Table 14.13 shows the appropriate LR model. The fitted model is as

## **Table 14.5** ARIMA models and normalized BIC value for daily new cases in the world.

| ARIMA(p,d,q) model | Normalized BIC value |
| :--- | :--- |
| (0,2,0) | 18.120 |
| (1,2,0) | 17.980 |
| (0,2,1) | 17.618 |
| (1,2,0) | 17.610 |
| (0,2,2) | 17.612 |
| (2,2,0) | 17.980 |
| **(2,2,2)** | **17.467** |
| (1,2,2) | 17.663 |
| (2,2,1) | 17.614 |

## **Table 14.6** ARIMA models and normalized BIC value for daily COVID-19 new deaths in the world.

| ARIMA(p,d,q) model | Normalized BIC value |
| :--- | :--- |
| (0,2,0) | 14.105 |
| (1,2,0) | 14.017 |
| **(0,2,1)** | **13.543** |
| (1,2,1) | 13.683 |
| (0,2,2) | 13.668 |
| (2,2,0) | 13.888 |
| (2,2,2) | 13.822 |
| (1,2,2) | 13.615 |
| (2,2,1) | 13.564 |

## **Table 14.7** Model statistics of daily new cases in the globe.

| Description | Predictors count | Statistics analysis R-squared (STS) | Statistics analysis R-squared | Statistics analysis Bayesian information criterian-normalized |
|---|---|---|---|---|
| Daily new cases- Model_1 | 1 | 0.525 | 0.983 | 17.467 |

## **Table 14.8** Model statistics of daily new deaths in the globe.

| Description | Predictors count | Statistics analysis R-squared (STS) | Statistics analysis R-squared | Statistics analysis Bayesian information criterian-normalized |
|---|---|---|---|---|
| Daily new deaths- Model_1 | 1 | 0.455 | 0.908 | 13.543 |

Y = 78.818 + 0.058X

which is simple linear regression model for daily COVID-19 new deaths on daily COVID-19 new cases.

The standardised and unstandardized coefficient values along with errors are displayed in Table 14.14. This reveals the fact that it is highly significant with the rejection of Null hypothesis.

The significant probability 0.000, calculated in testing the nullity of the coefficient of daily COVID-19 new cases indicates the significant presence of daily new cases. Rises of daily new cases makes 0.058 changes in the daily new deaths. The value of coefficient of determination, $R^{2}=0.801$, shows the relevance of this linear relationship. The adequacy of the model can be analyzed from the residuals. From Table 14.15, it is found that the mean residual is zero. The value of Durbin-Watson test statistic d is 0.34. Since this value is less than the $\mathrm{d}_{\mathrm{L}}$ value it is observed that there is +ve autocorrelation in the errors. The other model assumptions can be verified using the residual plots. The

## **Table 14.9** ARIMA model parameters of daily new cases in the world.

| Daily new cases-Model_1 | Daily new cases | No transformation | Constant | Estimate | SE | t | Sig. |
| --- | --- | --- | --- | --- | --- | --- | --- |
| | | | | -119.031 | 294.8675 | 0 | 1 |
| | | AR | Lag 1 | 0.898 | 0.09 | 9.959 | 0 |
| | | | Lag 2 | -0.489 | 0.086 | -5.681 | 0 |
| | | Difference | 2 | | | | |
| | | MA | Lag 1 | 1.805 | 0.057 | 31.752 | 0 |
| | | | Lag 2 | -0.887 | 0.054 | -16.285 | 0 |
| | Date | No transformation | Numerator | Lag 0 | 9.53E-09 | 2.14E-05 | 0 | 1 |

## **Table 14.10** ARIMA model parameters of daily new deaths in the world.

| Daily new deaths model_1 | Daily new deaths | No transformation | | | | |
| --- | --- | --- | --- | --- | --- | --- |
| | | | Constant | -7.031 | 36400.68 | 0 | 1 |
| | Date | No transformation | Difference | MA | Lag 1 | 0.912 | 0.077 | 11.785 | 0 |
| | | | | Lag 0 | 4.28E-10 | 2.64E-06 | | 1 |

![](img/bb4a43d3cc1537c84f048d14c493ee68_350_0.png)

**Figure 14.19** Plotting of ACF and PACF values for estimated residuals of daily new cases in the world.

![](img/bb4a43d3cc1537c84f048d14c493ee68_350_1.png)

**Figure 14.20** Plotting of ACF and PACF values for estimated residuals of daily new deaths in the world.

![](img/bb4a43d3cc1537c84f048d14c493ee68_351_0.png)

**Figure 14.21** Normal P–P plot of estimated residual daily new cases.

![](img/bb4a43d3cc1537c84f048d14c493ee68_351_1.png)

**Figure 14.22** Normal P–P plot of estimated of residuals of daily new deaths.

## **Table 14.11** Forecasting values of daily new cases in the world (June 2020–August 2020).

| **Date** | **Predicted daily COVID 19 new cases** | **LCL** | **UCL** | **Date** | **Predicted daily COVID 19 new cases** | **LCL** | **UCL** |
|---|---|---|---|---|---|---|---|
| 01-Jun-2020 | 105,530 | 94,563 | 116,497 | 17-Jul-2020 | 211,130 | -82,020 | 504,281 |
| 02-Jun-2020 | 110,995 | 94,748 | 127,242 | 18-Jul-2020 | 213,494 | -88,840 | 515,828 |
| 03-Jun-2020 | 118,649 | 100,340 | 136,959 | 19-Jul-2020 | 215,870 | -95,742 | 527,482 |
| 04-Jun-2020 | 123,919 | 104,754 | 143,083 | 20-Jul-2020 | 218,259 | -102,726 | 539,243 |
| 05-Jun-2020 | 125,982 | 105,961 | 146,003 | 21-Jul-2020 | 220,660 | -109,790 | 551,110 |
| 06-Jun-2020 | 126,341 | 104,714 | 147,967 | 22-Jul-2020 | 223,074 | -116,933 | 563,081 |
| 07-Jun-2020 | 126,742 | 102,410 | 151,075 | 23-Jul-2020 | 225,501 | -124,154 | 575,156 |
| 08-Jun-2020 | 128,025 | 100,169 | 155,880 | 24-Jul-2020 | 227,940 | -131,453 | 587,334 |
| 09-Jun-2020 | 130,084 | 98,366 | 161,802 | 25-Jul-2020 | 230,392 | -138,829 | 599,614 |
| 10-Jun-2020 | 132,419 | 96,741 | 168,096 | 26-Jul-2020 | 232,857 | -146,281 | 611,995 |
| 11-Jun-2020 | 134,627 | 94,889 | 174,365 | 27-Jul-2020 | 235,334 | -153,808 | 624,477 |
| 12-Jun-2020 | 136,596 | 92,604 | 180,588 | 28-Jul-2020 | 237,824 | -161,409 | 637,058 |
| 13-Jun-2020 | 138,418 | 89,909 | 186,926 | 29-Jul-2020 | 240,327 | -169,084 | 649,738 |

(Continued)

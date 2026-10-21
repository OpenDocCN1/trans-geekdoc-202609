
as follows.

```
XR_{i,j,t} = α₀ + α₁ Hole_{i,t-1} + α₂ SUE_{i,j,t} + α₃ Hole_{i,t-1} * SUE_{i,j,t}
+ α₄ degree_{i,t-1} + α₅ degree_{i,t-1} * SUE_{i,j,t} + α₆ X_{j,t-1}^k + e_t.
(31.8)
```

In the model specification (31.8), the dependent variable XR represents excess stock return (adjusted by market return) at the forecast date t, the day t + 1, two days after t + 2, as well as the cumulative excess return of the 3-day period, respectively. Constraint and rankings based on constraint are used to measure structural hole (Hole). Degree is the number of direct connections a given analyst has with other peer analysts. We control for the degree of network here to rule out the possibility that analysts occupying more structural hole have impact on stock return by covering more firms than others. X_{j,t-1}^k denotes a set of control variables, which includes the market to book ratio (MTB), financial leverage (leverage), return of asset (ROA), logarithm of firm assets, percentage of shares traded (turnover) in the regression. The component of surprise in an announced earnings forecast, SUE, is calculated following the procedure in (Cooper et al., 2001):

```
SUE = (FEPS_{it} - CF_{t-1}) / σ(CF_{t-1}),
(31.9)
```

where FEPS_{it} is analyst i's FY1 forecast on earnings per share at date t. CF_{t-1} is the consensus forecast, calculated as the average of all FY1 forecasts on a given firm in the previous 90 days. The variable σ(CF_{t-1}) is the standard deviation of the analyst earnings forecasts at date t.

In all of the regressions, we also control year, analyst, and firm fixed effect, and calculate standard error clustered by firms. If the coefficient on the interaction term of Hole and SUE is significantly negative, it will be consistent with Hypothesis 1 that analysts occupying more structural holes have greater ability to move stock price, and thus structural hole measures can be used to rank analysts.

Table 31.6 reports the results of the regressions with constraint as the structural hole measure. In column 1, the coefficient of constraint*SUE is −0.069998 with a t-statistic of −3.48. The coefficients of this interaction are also significant in columns 2 and 3, but they are much smaller than the coefficient in column 1, indicating that the information of the new earnings forecasts by analysts occupying more structural holes is mostly incorporated by investors in the day of announcement, with the impact on stock prices decreasing rapidly in subsequent days. Moreover, we use the rank of

## Table 31.6: Regression analysis: Excess stock return and analyst structural hole.

|  | **XR_t** | **XR_{t+1}** | **XR_{t+2}** | **Car** |
|---|---|---|---|---|
| **Intercept** | -0.005939***<br>(-12.91) | -0.0003620*<br>(-1.90) | -0.0005077***<br>(-3.10) | -0.006810***<br>(-11.54) |
| **Hole** | -0.001480***<br>(-4.49) | -0.0005987***<br>(-4.17) | -0.0001851*<br>(-1.71) | -0.002263***<br>(-5.11) |
| **SUE** | 0.013370<br>(1.46) | 0.0019304<br>(1.27) | 0.0004319<br>(1.37) | 0.015732<br>(1.45) |
| **Hole*SUE** | -0.069998***<br>(-3.48) | -0.0144061***<br>(-2.93) | -0.0012878**<br>(-2.11) | -0.085691***<br>(-3.44) |
| **Degree** | 8.2987950***<br>(3.87) | 2.15651994**<br>(2.06) | -3.2041466<br>(-0.38) | 1.029***<br>(3.37) |
| **Degree*SUE** | -4.1404636**<br>(-2.43) | -6.9785802**<br>(-2.33) | -9.864686*<br>(-1.71) | -4.936**<br>(-2.43) |
| **MTB** | -0.004385**<br>(-1.96) | -0.0012184<br>(-0.80) | -0.0035713***<br>(-3.44) | -0.009176***<br>(-2.90) |
| **Leverage** | -0.306859***<br>(-5.91) | -0.1562119***<br>(-6.54) | -0.0605591***<br>(-3.46) | -0.523557***<br>(-7.29) |
| **ROE** | -0.008344<br>(-0.09) | -0.00768906<br>(-1.19) | -0.0133697<br>(-0.25) | -0.098620<br>(-0.51) |
| **Size** | 0.081163***<br>(13.53) | 0.0157146***<br>(6.34) | 0.0114410***<br>(5.48) | 0.108333***<br>(13.79) |
| **Turnover** | 0.000652<br>(0.87) | 0.0004414<br>(0.88) | 0.0001589<br>(0.47) | 0.001252<br>(1.27) |
| **R square** | 0.003996 | 0.000517 | 0.000069 | 0.003763 |
| **Adjusted R square** | 0.003992 | 0.000513 | 0.000065 | 0.003759 |
| **Obs.** | 2526937 | 2526937 | 2526937 | 2526937 |

Notes: This table reports the result of regressing the announcement date excess stock returns on analyst structure hole. The dependent variables XR_t, XR_{t+1}, XR_{t+2} are the excess stock return (adjusted by market return) at the forecast date t, the day t + 1, two days after t + 2, as well as the cumulative excess return of the 3-day period, respectively. The variable of constraint is used as the structural hole measure (Hole). The component of surprise in an announced earnings forecast, SUE, is calculated as in equation (31.9). Degree is the number of direct connections a given analyst has with other peer analysts. Other control variables include the market to book ratio (MTB), financial leverage (leverage), return of asset (ROA), logarithm of firm assets, and percentage of shares traded (turnover). The t statistics are presented in parenthesis, with ***, **, and * indicating a 1%, 5% and 10% level of significance respectively.

constraint to conduct regression analysis. Table 31.7 reports similar results using the rank variable of constraint in the regression analysis, which are in support of Hypothesis 1.

In addition to the variable of constraint, we also use effective size and betweenness centrality as alternative measures of structural hole. Tables 31.8 and 31.9 present the regression results using effective size and betweenness

## Table 31.7: Regression analysis: Excess stock return and ranked structure hole.

|  | $XR_t$ | $XR_{t+1}$ | $XR_{t+2}$ | Car |
|---|---|---|---|---|
| Intercept | 0.032**<br>(15.38) | 0.011***<br>(9.14) | -0.00059***<br>(5.98) | -0.00021**<br>(-2.05) |
| Hole | -0.0061<br>(-0.27) | 0.0024<br>(0.18) | -0.020<br>(-1.56) | 0.0036<br>(0.26) |
| SUE | 0.092***<br>(3.13) | 0.021***<br>(4.11) | 0.018***<br>(2.8) | 0.022<br>(1.27) |
| Hole*SUE | -0.2602***<br>(-3.12) | -0.850**<br>(-2.35) | -0.32*<br>(-1.98) | -0.3832**<br>(-2.19) |
| Degree | -0.36**<br>(-2.1) | -0.0042<br>(-0.04) | 0.13<br>(1.45) | -0.034<br>(-0.32) |
| Degree*SUE | -31.94***<br>(-4.35) | -7.95*<br>(-1.80) | -2.20<br>(-0.54) | -7.27<br>(-1.64) |
| MTB | -1.04<br>(-1.01) | 8.47<br>(0.14) | -3.14*<br>(-1.81) | -9.52<br>(-0.79) |
| Leverage | 1.37*<br>(1.86) | -1.56***<br>(-3.53) | 1.21**<br>(2.53) | -1.92<br>(-0.22) |
| ROE | 1.97***<br>(2.74) | 8.94***<br>(3.15) | 2.47***<br>(51.33) | 2.86***<br>(33.17) |
| Size | -2.07***<br>(-3.70) | -1.36***<br>(-4.06) | 1.53***<br>(5.66) | -3.44***<br>(-5.24) |
| Turnover | -2.02***<br>(-8.57) | -4.95***<br>(-3.48) | -1.37***<br>(-15) | -2.52***<br>(-9.10) |
| Year | YES | YES | YES | YES |
| Analyst | YES | YES | YES | YES |
| Firm | YES | YES | YES | YES |
| Clustered by firm | YES | YES | YES | YES |
| R square | 0.00072 | 0.000452 | 0.000064 | 0.003825 |
| Adjusted R square | 0.00072 | 0.000448 | 0.000063 | 0.003817 |
| Obs. | 2526937 | 2526937 | 2526937 | 2526937 |

Notes: This table reports the result of regressing the announcement date excess stock returns on analyst structure hole. The dependent variables XR_t, XR_{t+1}, XR_{t+2} are the excess stock return (adjusted by market return) at the forecast date t, the day t + 1, two days after t + 2, as well as the cumulative excess return of the 3-day period, respectively. The variable of constraint ranking is used as the structural hole measure (Hole). The component of surprise in an announced earnings forecast, SUE, is calculated as in equation (31.9). Degree is the number of direct connections a given analyst has with other peer analysts. Other control variables include the market to book ratio (MTB), financial leverage (leverage), return of asset (ROA), logarithm of firm assets, and percentage of shares traded (turnover). The t statistics are presented in parenthesis, with ***, **, and * indicating a 1%, 5% and 10% level of significance respectively.

centrality, respectively. The coefficients of interaction terms Hole *SUE are all significantly positive in all regressions. Again, results are in support for Hypothesis 1 that analysts occupying more structural holes have greater impact on stock prices.

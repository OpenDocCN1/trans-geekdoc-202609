
### Table 31.8: Regression analysis: Excess stock return and effective size.

|  | **XR_t** | **XR_{t+1}** | **XR_{t+2}** | **CAR** |
|---|---|---|---|---|
| **Intercept** | -0.006567*** (-13.67) | -0.006529*** (-3.35) | -0.000561*** (-3.31) | -0.007782*** (-12.67) |
| **Hole** | -0.00232*** (-3.63) | -0.0013805*** (-4.27) | -0.000032 (-0.11) | -0.00373*** (-4.48) |
| **SUE** | 0.026758** (2.23) | 0.0042372** (2.52) | 0.000869* (1.93) | 0.031864** (2.29) |
| **Hole\*SUE** | 0.000365** (2.26) | 0.000601** (2.53) | 0.000013** (2.28) | 0.000438** (2.32) |
| **Degree** | 26.890179* (1.79) | 1.1961435 (0.15) | -12.482467** (-2.00) | 15.576398 (0.73) |
| **Degree\*SUE** | -22.884809 (-1.55) | -2.7492632 (-1.26) | -0.824258 (-1.54) | -26.45691 (-1.53) |
| **Financial variables** | YES | YES | YES | YES |
| **Year** | YES | YES | YES | YES |
| **Analyst** | YES | YES | YES | YES |
| **Firm** | YES | YES | YES | YES |
| **Clustered by firm** | YES | YES | YES | YES |
| **R square** | 0.00072 | 0.000452 | 0.000064 | 0.003825 |
| **Adjusted R square** | 0.00072 | 0.000448 | 0.000063 | 0.003817 |
| **Obs.** | 2526937 | 2526937 | 2526937 | 2526937 |

Notes: This table reports the result of regressing the announcement date excess stock returns on analyst structural hole. The dependent variables XR_t, XR_{t+1}, XR_{t+2} are the excess stock return (adjusted by market return) at the forecast date t, the day t + 1, the day t + 2, as well as the cumulative excess return of the 3-day period, respectively. The variable of effective size is used as the structural hole measure (Hole). The component of surprise in an announced earnings forecast, SUE, is calculated as in equation (31.9). Degree is the number of direct connections a given analyst has with other peer analysts. Other control variables include the market to book ratio (MTB), financial leverage (leverage), return on assets (ROA), logarithm of firm assets, and percentage of shares traded (turnover). The t-statistics are presented in parentheses, with ***, **, and * indicating 1%, 5%, and 10% levels of significance, respectively.

As discussed in Section 31.4.3, more experienced analysts are more likely to occupy more structural holes in our sample period. It is unclear whether the effect on stock return in Tables 31.7-31.9 can be driven by analyst attributes occupying network structural holes. To exclude the possibility, we include experience and the interaction terms of experience and structural hole measure in the regression. Experience is calculated by the year of a given earnings forecast minus the year of the analyst’s first earnings forecast release. Results in Table 31.10 indicate that the coefficients of experience\*SUE are significantly positive, indicating a significant effect of analyst’s experience on impacting stock return. The coefficients of Hole\*SUE continue to be significantly negative, providing further support that structural hole can be used to rank analysts. We also use rank of constraint to measure structural hole. The results remain significant.

### Table 31.9: Regression analysis: Excess stock return and betweenness centrality.

|  | **XR_t** | **XR_{t+1}** | **XR_{t+2}** | **CAR** |
|---|---|---|---|---|
| **Intercept** | -0.006332*** (-13.49) | -0.000527*** (-2.75) | -0.000554*** (-3.35) | -0.007413*** (-12.32) |
| **Hole** | -0.016599* (-1.66) | 0.004573 (0.79) | -0.008440* (-1.7) | -0.020507 (-1.48) |
| **SUE** | 0.015540** (2.18) | 0.002381** (2.31) | 0.000465 (1.49) | 0.018385** (2.20) |
| **Hole\*SUE** | 3.8989*** (2.65) | 0.76439563* (1.85) | 0.1565532*** (3.11) | 4.81984948** (2.56) |
| **Degree** | 11.873416 (0.74) | -10.72118 (-1.28) | -10.287473 (-1.58) | -9.132958 (-0.39) |
| **Degree\*SUE** | -15.411652 (-1.43) | -1.605838 (-0.92) | -0.566681 (-1.3) | -17.582875 (-1.38) |
| **Financial variables** | YES | YES | YES | YES |
| **Year** | YES | YES | YES | YES |
| **Analyst** | YES | YES | YES | YES |
| **Firm** | YES | YES | YES | YES |
| **Clustered by firm** | YES | YES | YES | YES |
| **R square** | 0.002371 | 0.000319 | 0.000068 | 0.003763 |
| **Adjusted R square** | 0.002366 | 0.000313 | 0.000063 | 0.003759 |
| **Obs.** | 2526937 | 2526937 | 2526937 | 2526937 |

Notes: This table reports the result of regressing the announcement date excess stock returns on analyst structural hole. The dependent variables XR_t, XR_{t+1}, XR_{t+2} are the excess stock return (adjusted by market return) at the forecast date t, the day t + 1, the day t + 2, as well as the cumulative excess return of the 3-day period, respectively. The variable of betweenness centrality is used as the structural hole measure (Hole). The component of surprise in an announced earnings forecast, SUE, is calculated as in equation (31.9). Degree is the number of direct connections a given analyst has with other peer analysts. Other control variables include the market to book ratio (MTB), financial leverage (leverage), return on assets (ROA), logarithm of firm assets, and percentage of shares traded (turnover). The t-statistics are presented in parentheses, with ***, **, and * indicating 1%, 5%, and 10% levels of significance, respectively.

As discussed earlier in Section 31.4.3, analysts working at large brokerages are more likely to have resources and support to process the rich and diverse information received when occupying the structural holes. As a result, the position of structural hole may play a bigger role when analysts work at large brokerages. We construct a dummy variable “brokerage” with a value of one for analysts working at large brokerages and zero otherwise.

### Table 31.10: Regression analysis: Excess stock return, constraint, experience and brokerage size.

|  | **XR_t** | **XR_{t+1}** | **XR_{t+2}** | **CAR** |
|---|---|---|---|---|
| **Intercept** | -0.0064*** (-10.77) | -0.0004 (-1.54) | -0.0009723 (-4.00) | -0.0082*** (-10.45) |
| **Hole** | -0.0015*** (-4.48) | -0.0006*** (-4.13) | -0.0002065* (-1.90) | -0.0208 (-1.50) |
| **SUE** | -0.016 (-1.23) | -0.0086** (-2.15) | 0.0004058 (0.25) | -0.024111 (-1.43) |
| **Hole\*SUE** | -0.06114*** (-3.12) | -0.01124** (-2.3) | -0.0012798 (-1.57) | -0.073658*** (-3.02) |
| **Degree** | 79.1936*** (3.70) | 20.6632* (1.96) | -5.5922413 (-0.67) | -15.052 (-0.64) |
| **Degree\*SUE** | -36.559** (-2.30) | -5.2451* (-1.87) | -0.9830981 (-1.72) | -17.585 (-1.38) |
| **Experience** | 0.0063 (1.29) | 0.000115 (0.39) | 0.0000620*** (2.73) | 0.00011** (2.08) |
| **Experience\*SUE** | 0.00392* (1.75) | 0.0014** (2.29) | 0.0000036 (0.02) | 0.005330* (1.85) |
| **SUE\*brokerage** | -0.091593*** (-7.57) | -0.0156600*** (-5.26) | -0.0045429*** (-2.59) | -0.118836*** (-7.81) |
| **Constraint\*SUE** | -0.042568 (-1.26) | -0.0063805 (-1.21) | -0.0028873 (-1.18) | -0.051885 (-1.32) |
| **Constraint\*SUE\*brokerage** | -0.0113213*** (-3.07) | -0.0211458*** (-3.05) | -0.0040018* (-1.71) | -0.138407*** (-3.16) |
| **Financial variables** | YES | YES | YES | YES |
| **Year** | YES | YES | YES | YES |
| **Analyst** | YES | YES | YES | YES |
| **Firm** | YES | YES | YES | YES |
| **Clustered by firm** | YES | YES | YES | YES |
| **R square** | 0.004058 | 0.000538 | 0.000076 | 0.002297 |
| **Adjusted R square** | 0.004053 | 0.000533 | 0.000070 | 0.002292 |
| **Obs.** | 2526937 | 2526937 | 2526937 | 2526937 |

Notes: This table reports the result of regressing the announcement date excess stock returns on analyst structural hole. The dependent variables XR_t, XR_{t+1}, XR_{t+2} are the excess stock return (adjusted by market return) at the forecast date t, the day t + 1, the day t + 2, as well as the cumulative excess return of the 3-day period, respectively. The variable of constraint is used as the structural hole measure (Hole). The component of surprise in an announced earnings forecast, SUE, is calculated as in equation (31.9). Degree is the number of direct connections a given analyst has with other peer analysts. Other control variables include the market to book ratio (MTB), financial leverage (leverage), return on assets (ROA), logarithm of firm assets, and percentage of shares traded (turnover). Experience and brokerage size (brokerage) are as defined in Tables 31.2 and 31.3. The t-statistics are presented in parentheses, with ***, **, and * indicating 1%, 5%, and 10% levels of significance, respectively.

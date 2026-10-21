that the unconditional distribution of excess log returns has heavier tails than the normal distribution for all countries. Furthermore, the Bera–Jarque statistics also show that the hypothesis of normality is rejected in our sample. Hence, we incorporate the heteroscedastic property when we estimate the asset pricing model.

Descriptive statistics for the state variables are reported in the second panel of Table 12.1. We select a set of state variables that have been widely used in the literature. These instruments include the logarithm of the monthly MSCI world dividend yield (DIV) and the 1-month US T-bill rate (TB) both in excess of the monthly Eurodollar rate. These variables have been found to measure the information that investors use to set prices in the market. For example, Campbell (1996) finds that the dividend yield has some predictive power for future stock returns. Similarly, Fama and Schwert (1977), Ferson (1989), and Ferson and Harvey (1991) find that the short-term T-bill rate (TB) is capable of predicting monthly returns of stocks and bonds.

We first construct the dynamic behavior of state variables. Table 12.2 reports the estimates of the coefficients in the one-lag VAR. The first row

# Table 12.2: VAR summary: Dynamics of risk factor.

| Dependent regressors variables | World(-1) | £(-1) | DM(-1) | Y(-1) | TB(-1) | DIV(-1) | R² |
|---|---|---|---|---|---|---|---|
| World | 0.0088<br>(0.0740) | -0.1758<br>(0.1198) | 0.1488<br>(0.1288) | 0.1207<br>(0.1099) | -1.4335<br>(3.6347) | 0.0100<br>(0.0053) | 0.0234 |
| £ | -0.0730<br>(0.0612) | 0.1345<br>(0.0990) | -0.0352<br>(0.1064) | 0.0034<br>(0.0908) | 3.2940<br>(3.0035) | -0.0045<br>(0.0044) | 0.0216 |
| DM | -0.1467<br>(0.0613) | 0.0439<br>(0.0993) | 0.0475<br>(0.1067) | 0.0178<br>(0.0911) | 3.0623<br>(3.0114) | -0.0015<br>(0.0044) | 0.0374 |
| Y | -0.0030<br>(0.0626) | -0.0347<br>(0.1013) | 0.0951<br>(0.1088) | 0.0599<br>(0.0929) | -1.4571<br>(3.0719) | 0.0029<br>(0.0045) | 0.0166 |
| TB | 0.0011<br>(0.0009) | -0.0018<br>(0.0015) | 0.0023<br>(0.0016) | -0.0018<br>(0.0013) | 0.7481<br>(0.0460) | 0.0002<br>(0.0001) | 0.8584 |
| DIV | -0.2714<br>(0.1469) | 0.1034<br>(0.2378) | 0.1212<br>(0.2556) | -0.1537<br>(0.2181) | -13.6528<br>(7.2113) | 0.9928<br>(0.0106) | 0.9924 |

Notes: Standard errors are in parentheses.

We adopt the Vector Auto-Regressive (VAR) approach from Campbell (1991). We assume that the real market index return and currency portfolio return are the first and second elements of the state variable vector z_t. The other elements of z_t are variables that are known to the market at the end of the period t and are related to forecasting future market returns. In addition, we assume that the vector z_t follows a first-order VAR

z_{t+1} = Φ z_t + u_{t+1}.
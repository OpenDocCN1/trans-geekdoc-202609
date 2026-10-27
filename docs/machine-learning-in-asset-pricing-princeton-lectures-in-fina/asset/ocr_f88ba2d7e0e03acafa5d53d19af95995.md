# TABLE 3.2
Return prediction with a polynomial of lagged returns

| Method | Scaling | CV criterion | γ (i) | IS R² (ii) | CV R² (iii) | Mean (iv) | S.D. (v) | Sharpe Ratio (vi) |
|---|---|---|---|---|---|---|---|---|
| OLS | Equal | n/a | 0 | 5.22 | −1.18 | 4.12 | 11.60 | 0.35 |
| Ridge | Equal | R² | 2.25 | 2.63 | 0.84 | 4.20 | 13.85 | 0.30 |
| Ridge | Unequal | R² | 1.40 | 2.69 | 1.18 | 4.55 | 12.47 | 0.37 |
| Ridge | Unequal | E[r_p] | 3.11 | 1.75 | 0.89 | 4.58 | 12.94 | 0.35 |
| Lasso | Unequal | R² | 0.00028 | 3.55 | 0.84 | 4.25 | 11.79 | 0.36 |

move in lagged 12-month returns is small relative to the typical annualized standard deviation of market-adjusted individual stock returns in the ballpark of 40% or more. Second, nonlinearities are subtle. While the inclusion of second and third powers of past returns is a crude way of dealing with nonlinearities and there are many other types of potentially relevant nonlinearity, such as interactions between covariates, that we have not explored here, strongly nonlinear effects do not jump out of the data in an obvious way. To the extent they exist, one has to look for them with more sophisticated tools in order to find them.

Table 3.2 presents information on the predictive performance of the model. All numbers are annualized.¹ The second row presents the estimates for the ridge regression. For comparison, the first row shows the same statistics for an OLS regression. For now, we focus on the R² measures in columns (ii) and (iii). We will discuss the other columns later in this chapter. Column (ii) shows the in-sample (IS) R² in the training data. The IS R² of ridge regression is just about half as big as the IS R² of OLS. However, the cross-validated R² from leave-one-year-out cross-validation (CV) in column (iii) shows that much of the seemingly good in-sample fit of the OLS regression is in fact coming from overfitting noise: the CV R² of OLS takes a negative value of −1.18%. In contrast, the ridge regression produces a positive CV R² of 0.84%. This illustrates that regularization is important for achieving good predictive performance.

¹The R² numbers are annualized by multiplying the monthly numbers by 12, which is a good approximation as long as the predictable component is a small portion of total return variance.
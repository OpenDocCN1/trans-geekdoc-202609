To test CAPM, we first use market model to estimate beta for each security.

$R_{i,t} = \alpha_i + \beta_i R_{m,t} + e_{i,t}. \tag{37.64}$

To reduce the impact of the measurement error problem, Black et al. (1972) use the grouping method in the capital asset pricing model test. Black et al. (1972) use the previous five-year monthly returns for each security to obtain pre-ranking beta from the market model in the January of each year. Securities are then sorted on their pre-ranking beta and divided into 10 portfolios. The subsequent 12 monthly returns of each portfolio are equal-weighted. The next 12 monthly portfolio returns are again calculated by the pre-ranking beta in the following year. This process is then repeated from January 1931 to January 1965. The post-ranking beta for each of the 10 portfolios is estimated by the market model using its corresponding 420 monthly portfolio returns.

In the second step, the estimated post-ranking betas are used in testing the linear relationship between betas and expected returns. Then the second-step regression in testing CAPM can be written as

$R_i - R_f = \gamma_0 + \gamma_1 \hat{\beta}_i + \varepsilon_i. \tag{37.65}$

Black et al. (1972) regress the average 35-years monthly returns of 10 portfolios on the post-ranking betas of 10 portfolios. Their cross-sectional regression results show that the estimated intercept term ($\hat{\gamma}_0$) is significantly different from zero and the estimated slope term ($\hat{\gamma}_1$) is significantly different from the average market premium during the estimation period. Although the results support the linear relationship between the systematic risk and expected return, CAPM cannot hold because of the non-zero intercept term and the lower market premium in the cross-sectional regression.

+   - the estimated betas for portfolios have substantially smaller measurement errors
+   - the variance of the measurement errors for portfolios will be much smaller than the variance of the measurement errors for individual securities
+   - the use of grouping method can adjust for survival bias problems

To cope with the measurement error problem, Blume and Friend (1973) also use the grouping method in testing the capital asset pricing model. The advantages of the grouping method are that (1) the estimated betas for portfolios have substantially smaller measurement errors, (2) the variance of the measurement errors for portfolios will be much smaller than the variance of the measurement errors for individual securities, and (3) the use of grouping method can adjust for survival bias problems. Different from the grouping method used by Black et al. (1972), Blume and Friend's (1973) grouping method in testing CAPM uses only a five year period in the second step. The pre-ranking beta of each security is obtained by the market model using previous five year monthly data. Securities are then assigned into 12 portfolios based upon their pre-ranking betas. The post-ranking beta for

In this depiction of the MIM, $I_j^*$ is the actual level of index $j$, while $b_{ij}^*$ is the actual responsiveness of security $i$ to index $j$. If the component of the security return is not related to any of the indexes, then this index model can be divided into two parts: (1) $a_i$, the expected value of the unique return, and (2) $c_i$ which represents the distribution of the random effect; $c_i$ has a mean effect of zero and a variance of $\sigma_{c_i}^2$.

This model can be utilized with multiple regression techniques, but if the indexes are unrelated to each other, the calculations would be made much simpler. This assumption reduces the number of calculations, as compared with the Markowitz full variance–covariance model, but is obviously more complex than the single-index model. To assure that the indexes are unrelated, the index variables can be orthogonalized (made uncorrelated) by completing inter-regressions on the indexes themselves.

Assume there is a hypothetical model that deals with two indexes:

$R_i = a_i^* + b_{i1}^* I_1^* + b_{i2}^* I_2^* + c_i.$  (81.22)

Suppose the indexes are the market index and an index of wholesale prices. If these two indexes are correlated, the correlation may be removed from either index.

To remove the relation between $I_1^*$ and $I_2^*$, the coefficients of the following equation can be derived by regression analysis:

$I_2^* = e_0 + e_1 I_1^* + d_i,$

where $e_0$ and $e_1$ are the regression coefficients, and $d_i$ is the random error term.

By the assumptions of regression analysis, $d_i$ is uncorrelated with $I_1$. Therefore,

$\hat{d}_i = I_2^* - (\hat{e}_0 + \hat{e}_1 I_1^*),$

which is an index of the performance of the sector index without the effect of $I_1$ (the market removed). Defining

$I_2 = \hat{d}_i = I_2^* - \hat{e}_0 - \hat{e}_1 I_1^*,$

an index is obtained that is uncorrelated with the market. By solving for $I_2^*$ and substituting into equation (81.22),

$R_i = a_i^* + b_{i1}^* I_1^* + b_{i2}^* I_2 - b_{i2}^* \hat{e}_0 - b_{i2}^* \hat{e}_1 I_1^* + c_i.$

Rearranging,

$R_i = (a_i^* - b_{i2}^* \hat{e}_0) + (b_{i1}^* - b_{i2}^* \hat{e}_1) I_1^* + b_{i2}^* I_2 + c_i.$

If the first set of terms in the brackets are defined as $a_i$ and the second set of terms are defined as $b_{i1}, b_{i2}^* = b_{i2}, I_1^* = I_1,$ and $c_i = e_i,$ the equation can be expressed as

$R_i = a_i + b_{i1} I_1 + b_{i2} I_2 + e_i,$ (81.23)

in which $I_1$ and $I_2$ are totally uncorrelated: the goal has been achieved. As will be seen later, these simplifying calculations will make the job of determining variance and covariance much simpler.

The expected return can be expressed as:

$E(R_{it}) = E(a_i + b_{i1} I_{1t} + b_{i2} I_{2t} + e_{it})$ $= E(a_i) + E(b_{i1} I_{1t}) + E(b_{i2} I_{2t}) + E(e_{it})$ $= a_i + b_{i1} \bar{I}_1 + b_{i2} \bar{I}_2.$ (81.24)

Since $a_i$, $b_{i1}$ and $b_{i2}$ are constants, $E(e_i) = 0$ by assumption, where $\bar{I}_1 = E(I_{1t})$ and $\bar{I}_2 = E(I_{2t})$.

Variance can be expressed as follows:

$\sigma^2 = E(R_{it} - R_i)^2 \quad \text{where } R_i = E(R_{it})$ $= E[(a_i + b_{i1} I_1 + b_{i2} I_2 + e_{it}) - (a_i + b_{i1} \bar{I}_1 + b_{i2} \bar{I}_2)]^2$ $= E[(a_1 + a_i) + b_{i1}(I_{1t} + \bar{I}_1) + b_{i2}(I_{2t} + \bar{I}_2) + e_{it}]^2$ $= E[b_{i1}^2 (I_{1t} + \bar{I}_1)^2 + 2b_{i1}b_{i2}(I_{1t} + \bar{I}_1)(I_{2t} + \bar{I}_2) + b_{i2}^2 (I_{2t} + \bar{I}_2)^2 + 2b_{i1}(I_{1t} + \bar{I}_1)e_{it} + 2b_{i2}(I_{2t} + \bar{I}_2)e_{it} + e_{it}^2]$ $= b_{i1}^2 E(I_{1t} + \bar{I}_1)^2 + b_{i1}b_{i2}E[(I_{1t} + \bar{I}_1)(I_{2t} + \bar{I}_2)] + b_{i2}^2 E(I_{2t} + \bar{I}_2) + b_{i1}E[(I_{1t} + \bar{I}_1)e_i] + b_{i2}E[(I_{2t} + \bar{I}_2)e_i] + E(e_i^2).$

But by assumption,

$E[(I_{1t} + \bar{I}_1)(I_{2t} + \bar{I}_2)] = 0,$ $E[(I_{1t} + \bar{I}_1)e_i] = 0,$ $E[(I_{2t} + \bar{I}_2)e_i] = 0,$

be accomplished by examining the mean square error for the forecast of the actual historic values. Although not within the scope of this text, the ability to judge the accuracy of a forecast is essential and can be acquired from any good statistical forecasting text. Example 81.3 provides further illustration of the single-index model.

## 81.4 Summary

This chapter has discussed the essentials of single- and multiple-index models. The theoretical underpinnings of the theories have been explored and numerical examples have been provided. An efficient boundary has been derived under the guidelines of the model and the quantitative analysis of the related parameters has been studied. It has been shown that both single-index and multi-index models can be used to simplify the Markowitz model for portfolio selection; remember, however, that the MIM is much more complicated than the single-index model.

## Bibliography

- W. Beaver, P. Kettler, and M. Scholes (1970). The Association between Market Determined and Accounting Determined Risk Measures. *The Accounting Review*, 45, 654-682.
- M. Blume (1975). Betas and Their Regression Tendencies. *Journal of Finance*, 20, 785-795.
- M. Brenner (1974). On the Stability of the Distribution of the Market Component in Stock Price Changes. *Journal of Financial and Quantitative Analysis*, 9, 945-961.
- E. J. Elton, M. J. Gruber, and T. Urich (1978). Are Betas Best? *Journal of Finance*, 23, 1375-1384.
- E. J. Elton, M. J. Gruber, S. J. Brown, and W. N. Goetzmann (2014). *Modern Portfolio Theory and Investment Analysis*, 9th ed. New York: John Wiley & Sons.
- W. Fouse, W. Jahnke, and B. Rosenberg (1974). Is Beta Phlogiston? *Financial Analysts Journal*, 30, 70-80.
- J. C. Francis and D. Kim (2013). *Modern Portfolio Theory: Foundations, Analysis, and New Developments*, 1st ed. New York: John Wiley and Sons, Inc.
- G. Frankfurter and H. Phillips (1977). Alpha-Beta Theory: A Word of Caution. *Journal of Financial Management*, 3, 35-40.
- G. Frankfurter and J. Seagle (1976). Performance of the Sharpe Portfolio Selection Model: A Comparison. *Journal of Financial and Quantitative Analysis*, 11, 195-204.
- M. R. Gibbons (1982). Multivariate Tests of Financial Models, a New Approach. *Journal of Financial Economics*, 81, 3-27.
- J. B. Guerard (2018). *Handbook of Portfolio and Construction: Contemporary Applications of Markowitz Techniques*. New York: Springer.
- R. Haugen and D. Wichern (1975). The Intricate Relationship between Financial Leverage and the Stability of Stock Prices. *Journal of Finance*, 20, 1283-1292.
- N. Jacob (1974). A Limited-Diversification Portfolio Selection Model for the Small Investor. *Journal of Finance*, 19, 847-856.
- B. King (1966). Market and Industry Factors in Stock Price Behavior. *Journal of Business*, 39, 139-140.

Sharpe approaches the problem of capturing the essence of mean–variance portfolio selection in an LP formulation by

- (1) making a diagonal transformation of the variables that will convert the problem into a diagonal form, and
- (2) using a piecewise linear approximation for each of the terms for variance.

The LP that results from the use of market responsiveness as the risk measure and the imposition of an upper limit on investment in each security is

MaxP = λ [∑_{i=1}^{n} x_i E(R_i)] − (1 − λ) [∑_{i=1}^{n} x_i β_i], (81A.1)

subject to

∑_{i=1}^{n} x_i = 1,
0 ≤ x_i ≤ U,

where x_i is the fraction of the portfolio invested in security i, E(R_i) is the expected returns of security i, β_i is the beta coefficient of security i, U is the maximum fraction of the portfolio that may be held in any one security, and λ is a parameter reflecting the degree of risk aversion.

λ is used in generating the efficient frontier. The value of λ corresponds to the rate of substitution of return for risk measured by the individual security β, while the U maximum percentage to be invested in any one security greatly reduces the number of securities that will be needed for diversification.

Building on this framework, Jacob derives an LP model that allows the small investor explicit control over the number of securities held. Jacob's LP model incorporates the effects of unsystematic risk as well as systematic risk, the beta in the Sharpe LP. Jacob's model is to minimize

Systematic risk Unsystematic risk
σ²(R_p) = 1/K (∑_{i=1}^{n} x_i β_i)² σ²(R_m) + (1/K)² ∑_{i=1}^{n} x_i² σ²(e_i), (81A.2)

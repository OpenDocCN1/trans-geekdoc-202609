
### 4.2.2 *Sparsity*

The method that we have presented so far deals with the high-dimensionality challenge by shrinking SDF coefficients toward zero, but none of the coefficients are set to exactly zero. In other words, the solution we obtain is not sparse. As we have argued in Section 4.1, the economic case for extreme sparsity with characteristics-based factors is weak. However, it may be useful to allow for the possibility that some factors are truly redundant in terms of their contribution to the SDF. Moreover, as we have discussed, there are economic reasons to expect that a representation of the SDF that is sparse in terms of PCs could provide a good approximation. Sparsity could therefore be useful when we consider PCs as factors.

For these reasons, we now introduce an additional $L^1$ penalty $\gamma_1\sum_{j=1}^{H}|b_j|$ in the penalized regression problem given by (4.21). The approach is motivated by lasso regression and elastic net and it leads to some elements of $\hat{b}$ being set to zero. Combining both $L^1$ and $L^2$ penalties, our estimator solves the problem.$^{1}$

$$\hat{b}=\arg\min_b\; (\bar{\mu}-\Sigma b)'\Sigma^{-1}(\bar{\mu}-\Sigma b)+\gamma_2 b'b+\gamma_1\sum_{j=1}^{H}|b_j|. \qquad (4.22)$$

This dual-penalty method enjoys much of the economic motivation behind the $L^2$-penalty-only method with an added benefit of potentially delivering sparse SDF representations. We can control the degree of sparsity by varying the strength of the $L^1$ penalty and the degree of economic shrinkage by varying the $L^2$ penalty.

While we will ultimately let the data speak about the optimal values of the penalties $\gamma_1$ and $\gamma_2$, there is reason to believe that completely switching off the $L^2$ penalty and focusing purely on lasso-style estimation would not work well in this asset pricing setting. Lasso is known to suffer from relatively poor performance compared with ridge and elastic net when regressors are correlated (Tibshirani 1996, Zou and Hastie 2005). As we discussed in Section 2.2.1, the tendency of $L^1$-penalized estimation to pick one of two correlated variables, rather than averaging them, hurts predictive performance if correlated covariates each contain a common signal and uncorrelated noise. For instance, rather than picking book-to-market as the only characteristic to represent the value effect in an SDF, it may be advantageous to consider a weighted average of multiple measures of value, such as book-to-market, price-dividend, and cash flow-to-price ratios. This reasoning also suggests that an L^1-only penalty may work better when we first transform the characteristics-based factors into their PCs before estimation. We examine this question in our empirical work below.

¹To solve the optimization problem in (4.22), we use the LARS-EN algorithm in Zou and Hastie (2005).

### 4.2.3 Data-Driven Penalty Choice

To implement the estimators (4.17) and (4.22), we need to set the values of the penalty parameters γ, γ1, and γ2. In the L^2-only penalty specification, the penalty parameter γ = τ/(κ^2 T) following from the prior (4.13) has an economic interpretation. The root expected maximum squared Sharpe ratio under the prior is

𝔼[μ′ Σ^{-1} μ]^{1/2} = κ. (4.23)

This means that γ = τ/(κ^2 T) implicitly represents views about the maximum squared Sharpe ratio. For example, an expectation that the maximum Sharpe ratio cannot be very high, i.e., low κ, would imply high γ and hence a high degree of shrinkage imposed on the estimation. Some researchers pick a prior belief based on intuitive reasoning about the likely relationship between the maximum squared Sharpe ratio and the historical squared Sharpe ratio of a market index.² However, these are intuitive guesses. It would be difficult to go further and ground beliefs about κ in deeper economic analyses of plausible degrees of risk aversion, risk-bearing capacity of arbitrageurs, and degree of mispricing. For this reason, we prefer a data-driven approach. But we will make use of (4.23) to express the magnitude of the L^2-penalty that we apply in estimation in terms of an economically interpretable root expected maximum squared Sharpe ratio.

We use a data-driven approach that involves estimation of γ via k-fold cross-validation (CV). We divide the historic data into k equal subsamples. Then, for each possible γ (or each possible pair of γ1, γ2 in the dual-penalty specification), we compute \hat{b} by applying (4.17) to k − 1 of these subsamples. We evaluate the OOS fit of the resulting model on the single withheld subsample. Consistent with the penalized objective, (4.20), we compute the OOS R-squared as

R^2_{OOS} = 1 - \frac{(\bar{μ}_2 - \bar{Σ}_2 \hat{b})' (\bar{μ}_2 - \bar{Σ}_2 \hat{b})}{\bar{μ}_2' \bar{μ}_2}, (4.24)

where the subscript 2 indicates an OOS sample moment from the withheld sample. We repeat this procedure \(k\) times, each time treating a different subsample as the OOS data. We then average the \(R^2\) across these \(k\) estimates, yielding the cross-validated \(R^2_{\mathrm{oos}}\). Finally, we choose \(\gamma\) (or \(\gamma_1, \gamma_2\)) that generates the highest \(R^2_{\mathrm{oos}}\).

²Barillas and Shanken (2018) is a recent example. See also MacKinlay (1995) and Ross (1976) for similar arguments.

We chose \(k = 3\) as a compromise between estimation uncertainty in \(\hat{b}\) and estimation uncertainty in the OOS covariance matrix \(\hat{\Sigma}_2\). The latter type of uncertainty increases with \(k\). With high \(k\), the withheld sample becomes too short for \(\hat{\Sigma}_2\) to be well behaved, which distorts the fitted factor mean returns \(\hat{\Sigma}_2\hat{b}\). However, our results are robust to using moderately higher \(k\).

This penalty choice procedure uses information from the whole sample to find the penalty parameters that minimize the \(R^2\) based on Eq. (30). The cross-validated OOS \(R^2\) at the optimal values of the penalty parameters is therefore typically an upward-biased estimate of the true OOS \(R^2\) that one would obtain in a new data set that has not been used for penalty parameter estimation (Varma and Simon (2006), Tibshirani and Tibshirani (2009)). Our interest centers on the optimal strength of regularization and we therefore are only concerned about the relative performance of models at various degrees of regularization, not the level of the OOS \(R^2\). In a subsequent step, in Section 4.4, we also evaluate the penalty parameter choice OOS by applying the estimated SDF on a part of the sample that has not been used to estimate the penalty parameters.

## 4.3 EMPIRICAL ANALYSIS

We start with the universe of US firms in the CRSP database. We construct two independent sets of characteristics. The first set relies on characteristics underlying common “anomalies” in the literature. We follow standard anomaly definitions in Novy-Marx and Velikov (2016), McLean and Pontiff (2016), Kogan and Tian (2015), and Hou, Xue, and Zhang (2015) and compile our own set of 50 such characteristics. The second set of characteristics is based on 70 financial ratios as defined by Wharton Research Data Services (WRDS): the WRDS Industry Financial Ratios (WFR), a collection of over 70 financial ratios grouped into the following seven categories: capitalization, efficiency, financial soundness/solvency, liquidity, profitability, valuation, and others. We supplement this data set with 12 portfolios sorted on past monthly returns in months \(t - 1\) through \(t - 12\). The combined data set contains 80 managed portfolios (we drop two variables due to their short time series and end up with 68 WRDS ratios in the final data set). The Internet Appendix of Kozak,

![](img/d6b658bf753df69fb65789651dc4a65e_88_0.png)

![](img/d6b658bf753df69fb65789651dc4a65e_88_1.png)

(a) Raw 50 anomaly portfolios

(b) PCs of 50 anomaly portfolios

Figure 4.1. OOS R^2 from dual-penalty specification (50 anomaly portfolios).
OOS cross-sectional R^2 for families of models that employ both L^1 and L^2 penalties simultaneously using 50 anomaly portfolios (Panel a) and 50 PCs based on anomaly portfolios (Panel b). We quantify the strength of the L^2 penalty by prior root expected squared Sharpe ratio on the x-axis. We show the number of retained variables in the SDF, which quantifies the strength of the L^1 penalty, on the y-axis. Both axes are plotted on logarithmic scale.

Using daily data allows us to estimate second moments much more precisely than with monthly data and focus on uncertainty in means while largely ignoring uncertainty in covariance estimates (with exceptions as noted below). We adjust daily portfolio weights on individual stocks within each month to correspond to a monthly rebalanced buy-and-hold strategy during that month. Finally, we orthogonalize all portfolio returns with respect to the CRSP value-weighted index return using market factor loadings estimated in the full sample.

### 4.3.1 Fifty Anomaly Characteristics

We start with the data set of 50 portfolios based on anomaly characteristics. The sample is daily from November 1973 to December 2017. Figure 4.1 presents the OOS R^2 from our dual-penalty specification as a function of κ (on the x-axis) and the number of nonzero SDF coefficients (on the y-axis). Focusing on the left-hand part of Figure 4.1 based on raw returns of the 50 anomaly portfolios, unregularized models (top-right corner) demonstrate extremely poor performance with OOS R^2 substantially below zero. Hence, substantial regularization is needed to get good OOS performance. Moreover, there is not much substitutability between

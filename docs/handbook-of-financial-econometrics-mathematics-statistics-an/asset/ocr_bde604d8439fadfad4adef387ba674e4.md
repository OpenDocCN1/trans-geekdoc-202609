+   14.5 Conclusion ........................................ 579
+   Bibliography ........................................... 580

# Abstract

The modern portfolio theory in Markowitz (1952) is a cornerstone for investment management, but its implementations are challenging in that the optimal portfolio weight is extremely sensitive to the estimation for the mean and covariance of the asset returns. As a sophisticated modification, the Black–Litterman portfolio model allows the optimal portfolio’s weight to rely on a combination of the implied market equilibrium returns and investors’ views (Black and Litterman, 1991). However, the performance of a Black–Litterman model is closely related to investors’ views and the estimated covariance matrix. To overcome these problems, we first propose a predictive regression to form investors’ views, where asset returns are regressed against their lagged values and the market return. Second, motivated by stylized features of volatility clustering, heavy-tailed distribution, and leverage effects, we estimate the covariance of asset returns via heteroscedastic models. Empirical analysis using five industry indexes in the Taiwan stock market shows that the proposed portfolio outperforms existing ones in terms of cumulative returns.

**Keywords**

Markowitz modern portfolio theory • Black–Litterman model • GARCH model • EGARCH model • The investor’s views • Volatility clustering.

# 14.1 Introduction

Markowitz (1952) provided a framework for modern portfolio theory, in which the asset returns can be assumed as identical and independently distributed multivariate normal vector with mean μ and covariance Σ. In practice, investment theory seeks portfolios to diversify risk. However, a direct implementation of the Markowitz model is challenging as the optimal weight is extremely sensitive to the estimation of the assets means and covariances and may be a corner solution, which is however against the intuition about portfolio diversification. For example, Chopra et al. (1993) and Brianton (1998) have revealed that estimation errors in the parameters severely affect the optimized portfolio and efficiency frontier. In addition, Michaud (1989) points out that Markowitz model may lead to maximize the effect of errors in the input parameters assumptions.

Black and Litterman (1991) improve the Markowitz model by combining the implied market equilibrium return and investors’ views, so that the estimated means and covariances are adjusted to reflect the market behavior more realistically. Using a Bayes’ formula, the return given investors’ views
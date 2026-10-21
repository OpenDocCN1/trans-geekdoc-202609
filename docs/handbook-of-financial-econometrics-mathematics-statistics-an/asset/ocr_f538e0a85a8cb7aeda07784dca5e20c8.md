# Keywords

Measurement error • Probability limit for regression coefficient • Decomposition of estimated regression coefficient • Performance measure • Systematic risk.

# 62.1 Introduction

In this chapter, we examine the effects of errors in measurement of the two independent variables, return on market ($R_m$) and return on risk-free assets ($R_f$), in the traditional one-factor capital asset pricing model (CAPM). After discussing Sharpe–Lintner’s CAPM and both Jensen and Fama’s specifications thereof, we review briefly the recent results of Friend and Blume (1970), hereafter FB; Black, Jensen and Scholes (1972), hereafter BJS; and Miller and Scholes (1972), hereafter MS. In Section 2, we first explore possible sources of measurement errors for both $R_m$ and $R_f$; then we specify these errors mathematically and derive analytically their effects on estimates of systematic risk of a security or portfolio, $\widehat{\beta}_j''$, and the Jensen’s measure of performance, $\widehat{\alpha}_j''$. In Section 3, we derive an analytical expression for the regression coefficients of estimated $b$’s where we estimate the equation $\widehat{\alpha}_j'' = a + b\widehat{\beta}_j''$. The result is then examined to find the conditions under which errors in measurement of $R_m$ and $R_f$ can cause $b$ to have a positive or negative value even if the true $b$ is zero. The conditions are then used to examine FB’s results and their interpretation. In Section 4, an alternative hypothesis testing procedure for the CAPM is examined. We show that the empirical results so derived are also affected by the measurement errors and the sample variation of the systematic risk. The relative advantage between the two different testing hypotheses is then explored. Finally, we comment on the relevance of the results to popular zero = beta model and indicate areas for further research.

The Sharpe–Lintner form a single-period capital assets pricing model can be theoretically written as¹

$E(\tilde{R}_j) - R_f = \beta_j[E(\tilde{R}_m) - R_f]$  (62.1)

where $\tilde{R}_j$, $R_f$ and $\tilde{R}_m$ are the rates of return for the $j$th asset, the risk-free asset and the market portfolio respectively, $\beta_j$ is the measure of systematic risk for the $j$th asset and $E$ if the expectation operator.
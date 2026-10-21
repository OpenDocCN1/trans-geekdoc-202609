Merton, R. C. (1974). On the Pricing of Corporate Debt: The Risk Structure of Interest Rates. *Journal of Finance*, 29, 449–70.

Ng, S. and Perron, P. (2001). Lag Length Selection and The Construction of Unit Root Tests with Good Size and Power. *Econometrica*, 69, 1519–1554.

Rajan, G. (2006). Has Finance made the World Riskier? *Journal of European Financial Management*, 12(4). 499–533.

Raunig, B. and Scheicher, M. (2009). Are Banks Different? Evidence from the CDS Market. OeNB Working paper 152.

Sabkha, S., de Peretti, C. and Hmaied, D. (2018). *Review of Quantitative Finance and Accounting*. https://doi.org/10.1007/s11156-018-0741-6.

Sims, C. A. (1980). “Macroeconomics and Reality,” *Econometrica, Econometric Society*, 48(1), 1–48.

Tang, D. Y. and Yan, H. (2006). Macroeconomic Conditions, Firm Characteristics, and Credit Spreads, *Journal of Financial Services Research*, 29(3), 177–210.

# Appendix 60A: Estimation of Panel Vector Autoregressive Models

# Appendix 60A.1: *The model*

Time-series vector autoregression (VAR) models are originated in the macro-econometrics literature as an alternative to multivariate simultaneous equation models (Sims, 1980). All variables in a VAR system are typically treated as endogenous, although identifying restrictions based on theoretical models or on statistical procedures can be allowed as well. We give a brief overview of the panel VAR model and the Generalized Method of Moments (GMM) estimating framework. We consider a k-variate homogeneous panel VAR of order *p* with *N* unit-specific fixed effects represented by the following system of linear equations

$$Y_{it}=Y_{it-1}A_1+Y_{it-2}A_2+\cdots+Y_{it-p+1}A_{p-1}+Y_{it-p}A_p+X_{it}B+u_i+e_{it}$$

$$i\in\{1,2,\ldots,N\},\ t\in\{1,2,\ldots,T\},\qquad (60A.1)$$

where $Y_{it}$ is a $(1\times k)$ vector of dependent variables; $X_{it}$ is a $(1\times l)$ vector of exogenous covariates; $u_i$ and $e_{it}$ are $(1\times k)$ vectors of dependent variable, unit specific fixed-effects and idiosyncratic errors, respectively. The $(k\times k)$ matrices $A_1,A_2,\ldots,A_{p-1},A_p$ and the $(l\times k)$ matrix $B$ are parameters to be estimated and are restricted to be the same for all units. Therefore, we do not allow for cross-sectional heterogeneities or for dynamic interdependencies. We assume that the innovations have the following characteristics: $E[e_{it}]=0$, $E[e_{it}e'_{it}]=\Sigma$ and $E[e'_{it}e_{is}]=0$ for all $t>s$ which implies that we do not allow for static interdependencies among units as well. All of the parameters are suggested to be estimated jointly with fixed effects.
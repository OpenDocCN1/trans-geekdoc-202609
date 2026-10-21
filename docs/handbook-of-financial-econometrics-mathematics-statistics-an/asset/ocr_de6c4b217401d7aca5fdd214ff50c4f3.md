frequencies, Leland instead chooses common inputs across models to observe how well they match observed default statistics.

Wei and Guo (1997) use an approach similar to that often used when calibrating models of the risk-free yield curve. For data on the spread between the credit term structures of the studied security (Eurodollar in their study) and the term structure of US Treasury (T-bills in their study), they choose parameters that minimize the squared fitting error for each time period they have observations. This enables them to back out the asset value, implied volatility as well as other model parameters.

Some studies even employ a simple proxy approach to calculate asset values. They typically approximate market value of corporate assets by the sum of the market value of equity and the book value of liabilities. For instance, Brockman and Turtle (2003) simply measure the market value of a firm’s assets as the book value of assets less the book value of shareholders’ equity, plus the market value of equity. Asset volatility is then calculated directly from returns of the estimated asset value. Eom et al. (2004) add the book value of debt and the observed market value of equity to estimate the asset value. Then they use a refining approach to calculate the asset volatility estimate using the relation σ_S = ∂S_t/∂V_t σ_v, given historical equity return volatility σ_S and ∂S_t/∂V_t = N(d1(K_t, t)).

Finally, Hsu et al. (2003) employ the Generalized Method of Moment (GMM) to illustrate their model with selected exchange traded bond data. They impose the moment restriction on bond yield, and the log-solvency ratio associated with the conditional mean, variance, and covariance. Then the parameter estimates can be obtained by minimizing the objective function containing the time t vector of sample moments corresponding to these restrictions.

# 50.3.2 Comparison of alternative estimation approaches

In this section, we summarize the problems of the existing estimation approaches that have been pointed out in the literature. In the end of this section, we present in Table 50.2 a summary of the main drawbacks of these estimation methods adopted in previous empirical studies.

# 50.3.2.1 Problems of volatility restriction approach

Duan (1994) addresses that the shortcoming of the volatility restriction method by Ronn and Verma (1986) can be seen as follows: Under their model specification, the asset price follows a log-normal process, and equity
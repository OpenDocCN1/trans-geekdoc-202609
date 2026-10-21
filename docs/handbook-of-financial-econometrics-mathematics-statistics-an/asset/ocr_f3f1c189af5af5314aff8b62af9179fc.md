Z. -R. Wang, X. -H. Chen, Y. -B. Jin, and Y. -J. Zhou (2010). Estimating risk of foreign exchange portfolio: Using VaR and CVaR based on GARCH-EVT-Copula model. Physica A, 389, 4918-4928. https://doi.org/10.1016/j.physa.2010.07.012.

G. Weiss (2013). Copula-GARCH versus dynamic conditional correlation: an empirical study on VaR and ES forecasting accuracy. Review of Quantitative Finance and Accounting, 41(2), 179-202. https://doi.org/10.1007/s11156-012-0311-2.

G. Weiss and H. Supper (2013). Forecasting liquidity-adjusted intraday Value-at-Risk with vine copulas. Journal of Banking and Finance, 37(9), 3334-3350. https://doi.org/10.1016/j.jbankfin.2013.05.013.

# Appendix 73A: Standardized Student’s t-Distribution

Let T be a continuous variable with domain D(-∞,∞), while its distribution function F is given by F(t) = P(T ≤ t). If T follows a Student’s t-distribution with v degrees of freedom, its density function is

f_v(t) = (vπ)^(-1/2) · Γ(v/2)^-1 Γ((v+1)/2) · (1 + t²/v)^(-(v+1)/2)

where Γ is the gamma function. If we define X = μ + σT, then X has a generalized t-distribution with density function as follows:

f_v(x|μ,β) = (βvπ)^(-1/2) · Γ(v/2)^-1 Γ((v+1)/2) · (1 + (x-μ)²/(βv))^(-(v+1)/2)

where the expectation of X is μ, and the variance of X is σ² = βv(v-2)^-1. If μ = 0 and βv = v-2 (so that σ² = 1), then X ∼ t_v(0,1), and the density function for the standardized Student’s t-distribution is as follows:

f_v(x) = (π(v-2))^(-1/2) · Γ(v/2)^-1 Γ((v+1)/2) · (1 + x²/(v-2))^(-(v+1)/2)

If the degree of freedom is small, the distribution will have a lower peak and longer tails compared to a normal distribution. As ν → ∞, the distribution approaches the normal distribution with mean 0 and variance 1.

# Appendix 73B: Density Functions for Elliptical Copulas

The Gaussian copula distribution cannot be written in a simple closed form, and it can only be expressed as an integral. When n = 2, the bivariate
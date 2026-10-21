![](bbox=[0.06, 0.1, 0.95, 0.45])

# Figure 108.1: Hypothetical distributions of alpha t-ratio for three subpopulations of funds.

The t-ratios for the three subpopulations are centered around a negative value (bad funds), zero, and a positive value (good funds), respectively. t_g and t_b are two critical values for the t-ratios corresponding to a test size of 10%, from a simulation under the null that the alpha is zero. The parameters β_g and β_b denote the power of the tests for good and bad funds, respectively, from the simulations where the alphas are at the good or bad values. The parameter δ_g (δ_b) captures the confusion, the probability that a bad (good) fund is mistaken for a good (bad) fund.

The stylized structure of the probability model is illustrated in Figure 108.1 for hypothetical densities. There are three subpopulations of funds whose alphas are centered around the values [α_b < 0, 0, α_g > 0]. A fraction of the funds belongs to each subpopulation. The fractions, which sum to 1.0, are [π_b, π_0, π_g]. The unconditional distribution of funds’ alphas is a mixture of the three distributions.

# 108.2.1 Estimation by simulation

The set of unknown parameters is θ = [π_g, π_b, α_g, α_b, β_g, β_b, δ_g, δ_b], where the last four are the power and confusion parameters of the tests. The parameters are estimated in three stages as follows. In the first stage, for given values of [α_b, α_g] we use three simulations to estimate the parameters [β_b, β_g, δ_b, δ_g]. We set the size of the tests, (γ/2), say to 10% in each tail.

The first simulation of the cross-section of fund alphas, imposing the null hypothesis that all of the alphas are zero, produces two critical values for the t-statistics, t_g and t_b. The critical value t_g is the t-ratio above which 10% of
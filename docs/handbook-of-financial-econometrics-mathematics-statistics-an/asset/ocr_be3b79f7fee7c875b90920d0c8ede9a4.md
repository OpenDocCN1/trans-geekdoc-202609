# Table 38.5: Best fitting distributions for credit, market and operational risks.

| Risk type | Distribution | Estimated parameters | D value | P value |
|---|---|---|---|---|
| Credit risk | SGED | σ = 0.57, μ = −6.11, k = 0.96, λ = 0.90 | 0.04 | 0.83 |
| Market risk | t | ν = 2 | 0.04 | 0.83 |
| Operational risk | Lognormal | μ̃ = −10.08, σ̃ = 0.90 | 0.05 | 0.62 |

Note: See Appendix 38B for specific mathematical expressions and parameter definitions of the three distributions. All parameters are estimated by maximum likelihood estimation.

space considerations. For the KS test, the larger the P value is, the better the theoretical distribution is able to fit the empirical data, and 0.05 is generally set as the threshold. Table 38.5 shows that P values of SGED, t distribution and lognormal distribution are 0.83, 0.83 and 0.62, respectively. All of them are much larger than 0.05, indicating that these distributions fit the three risk types very well. Figure 38.4 presents the histograms of credit risk, market risk and operational risk and their best fitting distributions in Table 38.5. In Figure 38.4, the shapes of the fitting distributions are very similar to the corresponding histograms, which further demonstrates that SGED, the t distribution and the lognormal distribution indeed fit the three risk types very well.

The second step is using the proper mixture copula to model the dependence between credit, market and operational risks. The analysis in Section 38.3 infers that the mixture of the t copula and Gumbel copula can best capture the dependence between bank risks, so the t-Gumbel copula is used to model the dependence between the three risk types of Chinese banks. The estimation results are shown in Table 38.6. The estimated parameters include weight parameters of the two copula components and their respective association parameters. In contrast with the results of several studies, such as Hu (2006), weights of the t copula and Gumbel copula are 0.42 and 0.58, respectively, which are relatively balanced; their association parameters are not close to that implying independence. This indicates that both copulas play an important role in modeling the dependence structure and none of them can be eliminated.

After the marginal distributions of the three risk types are determined and the mixture copula is estimated, the total risk distribution can be derived by Monte Carlo simulation with Steps 3-6 (Section 38.3.3). Finally, VaR of the total risk can be calculated by using Step 7. For an overall comparison,
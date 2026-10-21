E(x_ib) = (γ/2)π0 + δ_b π_g + β_b π_b, and similarly for E(F_g) = E(x_ig). We estimate Var(x_ib) = E(x_ib){1 − E(x_ib)} and use the correlation, ρ, described above to approximate Cov(x_ib, x_jg) and Cov(x_ib, x_jb) as the correlation times the product of the standard deviations. However, when we simulate the simulations to evaluate the finite sample performance of this version of the standard errors, we find that they perform much worse.

In the two-distribution example for mutual funds, the standard errors of π0 and π_b are equal. The standard errors follow from equation (108A.4) with Var(F_b) = Var(x_ib)[(1/N) − ρ(1 − 1/N)], Var(x_ib) = E(x_ib)[1 − E(x_ib)] and E(x_ib) = π0 CDFN(t_b) + CDFN(t_b − μ_b) (1 − π0), where CDFN(·) is the standard normal cumulative distribution function.

These expressions for the variances of the pie fractions hold when the constraints that the fractions are positive and sum to less than 1.0 are not binding. When the constraints are binding the distribution of the estimators is complicated by the truncation, and it involves the sampling variance of the Lagrange multipliers. We do not report standard errors when the constraints are binding.

The standard errors in BSW are based on equation (108A.1), which implies

Var(π0,C) = Var(F)/(1 − γ)^2,  (108A.5)

where Var(F) is computed as the sum of Bernoulli random variables, specialized to the case of a two-sided test, with F = F_g + F_b, and ignoring dependence across the tests (ρ = 0). Thus, BSW use Var(F) = γ(1 − γ)/N when computing their standard errors. Similarly, their estimate of π_g is F_g − (γ/2)π0,BSW, and they use Var(π_g,C) = Var(F_g) + Var(π0,C) * (γ/2)^2 − 2(γ/2)Cov(F_g, π0,C), with Var(F_g) = F_g(1 − F_g)/N and Cov(F_g, π0,C) = F_g(1 − F)/[N(1 − γ)]. It follows that Var(π_b,C) = Var(F_g) + Var(π0,C)(1 − γ/2)^2 + (1 − γ/2)Cov(F_g, π0,C).

The BSW calculations do not use the asymptotic normal approximations that we employ, and they do not arrive at the unconditional expectations by averaging over the conditional expectations given each fund group, weighted by the estimated fractions in each group, as in our standard error estimators.

# Appendix 108B  More on the Relation to Previous Approaches

This appendix describes in more detail than in the main text how our approach modifies the framework of BSW (2010) and Storey (2002). Consider the case of a two-tailed test with size γ and power β < 1, and let
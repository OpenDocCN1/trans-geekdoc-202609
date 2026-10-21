
deviations and factor model R-squares. Either method closely reproduces the statistical properties of the original data.

In Panel B of Table 108H.1, the values at each fractile of the cross-sectional distributions of mutual funds’ alphas and alpha t-ratios are shown for the two simulation methods. These are the averages across 100 simulation trials, thus estimating the expected outcomes. Alpha is the average alpha value at each fractile of the cross-sectional fund distribution of alphas. T-ratio is the heteroscedasticity-consistent t-ratio for alpha at each fractile of the cross-section of alpha t-ratios. Alphas are in percent per month. The results show that the cross-sectional distributions of alphas and alpha t-ratios that is produced by the two simulation methods are very similar.

## Appendix 108I Analysis of the Impact of Variation in the δ and β Parameters on the Simulations

Our standard error calculations assume that the δ and β parameters are estimated without error. As the number of simulation trials gets large, these errors should be negligible, but it is useful to evaluate their impact when we use 1000 simulation trials.

Consider the estimated fractions π = π(φ,F) as a function of φ = (δ_g, δ_b, β_g, β_b) and the fractions rejected, F. Note that we report and use the average values of the φ parameters over 1000 simulation trials, so it is the variance of the mean value that we are concerned with here. Our current estimate for the variance of π may be written as Q Vf Q′, where the Q = Q(φ) is defined by equation (108A.4). Vf is the variance matrix of the fractions rejected, F. To consider the impact of variation in the φ parameters, we expand π = π(φ,F) using the delta method and assume that the covariance matrix of (φ,F) is block diagonal. The standard errors in the main paper include the part due to Vf, but not the part due to V(φ). Equivalently, we can assume that our current estimate is the expected value of the conditional variance of π given φ, and that we are missing the variance of the conditional mean, taken with respect to the variation in φ. Either approach leads to the same missing term due to variation in φ:

E(∂π/∂φ) V(φ̂ − φ) E(∂π/∂φ)′. (108I.1)

The analytical derivatives are evaluated at the average parameter values across the 1000 simulation trials, and the variance matrix V(φ̂ − φ) is estimated from the covariances of the (δ,β) estimates across the 1000 trials. These covariances are estimated assuming independent simulation trials.

The results for hedge fund data and 1000 simulation trials, with (γ/2) = 0.10, and evaluated at the best fitting alpha values are:

$Q\,Vf\,Q' = \begin{bmatrix} 0.0327520 & -0.0175781 \\ -0.0175781 & 0.0488524 \end{bmatrix}$

$\mathrm{E}(\partial\pi/\partial\phi)V(\phi^\wedge - \phi)\mathrm{E}(\partial\pi/\partial\phi)' = \begin{bmatrix} 0.000831679 & 0.000259822 \\ 0.000259822 & 9.87724e-005 \end{bmatrix}.$

We conclude that the variation in the δ and β parameters has a trivial impact on our results. Even if the covariance of (φ, F) is not block diagonal, the cross terms should be small compared with the included Q Vf Q' terms.

## Appendix 108J Alternative Goodness of Fit Measures

The alternative goodness-of-fit measures are the two-sample, Kolmogorov–Smirnov distance: KS = Sup_x |F1(x) − F2(x)|, where F1(·) and F2(·) are the two empirical cumulative distribution functions (CDFs) of alpha t-ratios; one from the data and one from the model. This measure looks at the maximum vertical distance between the CDFs. The second alternative measure is the Cramer–von Mises distance: CvM = E_x {[F1(x)−F2(x)]^2}, which looks at the mean squared distance. To implement the alternative measures we combine the observations of the alpha t-ratios from the original data and from a model, rank the values and calculate the two CDFs at each of the discrete points.

Table 108J.1 presents the analysis. The first row replicates the Pearson Chi-square case, because these exercises are based on 100 simulation trials at each point in the grid, whereas the results in the main text use 1000 trials. The difference between 100 and 1000 here is a maximum difference of two basis points per month in the alpha parameters. The difference across the goodness-of-fit measures is less than eight basis points per month in the alpha parameters, 7% in the power parameters, less than one percent in the confusions and within about one standard error on the π parameters. While the alternative measures find a few more zero-alpha hedge funds, the results are otherwise very similar. We conclude that results are robust to the use of the different goodness-of-fit measures.

## Table 108J.1: Joint estimation of alphas and fractions in the populations with alternative goodness-of-fit measures.

| Alphas (%) | Power | Confusions | Fractions |
| Good α_g | Bad α_b | Measure | β_g | β_b | δ_g | δ_b | π_0 | π_g |
| Unconstrained Alpha Domains, 3-Group Model |  |  |  |  |  |  |  |  |
| 0.237 | -0.128 | Pearson | 30.7 | 19.5 | 6.6 | 4.9 | 7.3 | 63.2 (20.6) (20.1) |
| 0.227 | -0.148 | KS | 29.7 | 21.7 | 6.2 | 5.1 | 10.0 | 65.9 (20.3) (21.3) |
| 0.307 | -0.113 | CvM | 37.5 | 18.3 | 6.9 | 4.3 | 26.5 | 46.0 (19.9) (14.3) |

Notes: All tests are conducted using a size of γ/2 = 0.10. Simulations use 100 trials at each point in the grid search of the good and bad alpha values. Given those alpha values, simulations use 1000 trials to estimate the other model parameters. The standard errors in parentheses are the asymptotic standard errors. Pearson denotes the Pearson Chi-square goodness-of-fit measure, KS denotes the Kolmogorov–Smirnov distance and CvM denotes the Cramer–von Mises distance.

This page intentionally left blank

## Chapter 109

## Constant Elasticity of Variance Option Pricing Model: Integration and Detailed Derivation*

Y. L. Hsu, T. L. Lin and Cheng Few Lee

## Contents

- 109.1 Introduction . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 3830
- 109.2 The CEV Diffusion and its Transition Probability Density Function . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 3830
- 109.3 Review of Noncentral Chi-Square Distribution . . . . . . . . . . 3834
- 109.4 The Noncentral Chi-Square Approach to Option Pricing Model . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 3836
  - 109.4.1 Detailed derivations of C1 and C2 . . . . . . . . . . . . 3836
- 109.5 Some Computational Considerations . . . . . . . . . . . . . . . 3842
- 109.6 Conclusions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 3844
- Acknowledgments . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 3844
- Bibliography . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 3844
- Appendix 109A Proof of Feller’s Lemma . . . . . . . . . . . . . . . . 3845

Y. L. Hsu
National Chung Hsin University
e-mail: ylhsu@amath.nchu.edu.tw
T. L. Lin
National Chao-Tung University
Cheng Few Lee
Rutgers University
e-mail: cflee@business.rutgers.edu

*This chapter draws upon the paper, “Constant elasticity of variance (CEV) option pricing model: Integration and detailed derivation,” which was published in Mathematics and Computers in Simulation, Vol. 79, 1, pp. 60–71, 2008.

## Constant Elasticity of Variance Option Pricing Model

In this chapter, we will focus on the case β < 2 since many empirical evidences (see Campbell (1987), Glosten et al. 1993, Brandt and Kang 2004) have shown that the relationship between the stock price and its return volatility is negative. The transition density for β > 2 is given by Emanuel and Macbeth (1982) and the corresponding CEV option pricing formula can be derived through a similar strategy. For more details, see Chen and Lee (1993).

In order to derive the CEV option pricing model, we need the transition probability density function f(ST|St, T > t) of the stock price at time T given the current stock price St. For the transition probability density function f(ST|St), we will start with the Kolmogorov forward and backward equations.

Assume Xt follows the diffusion process

dX = μ(X,t)dt + σ(X,t)dZ, (109.2)

and P = P(Xt,t) is the function of Xt and t, then P satisfies the partial differential equations of motion. From equation (109.2), we have the Kolmogorov backward equation,

1/2 σ²(X₀,t₀) ∂²P/∂X₀² + μ(X₀,t₀) ∂P/∂X₀ + ∂P/∂t₀ = 0, (109.3)

and the Kolmogorov forward (or Fokker–Planck) equation

1/2 ∂/∂Xt [σ²(Xt,t) P] - ∂/∂Xt [μ(Xt,t) P] - ∂P/∂t = 0. (109.4)

Consider the following parabolic equation:

(P)t = (axP)xx - ((bx + h)P)x , 0 < x < ∞, (109.5)

where P = P(x,t) are constants with a > 0, (P)t is the partial derivative of P with respect to t, ( )x and ( )xx are the first and second partial derivatives of ( ) with respect to x. This can be interpreted as the Fokker–Planck equation of a diffusion problem in which bx + h represents the drift, ax represents the diffusion coefficient.

Lemma 1 (Feller (1951)). Let x f(x,t|x0) be the probability density function for x and t conditional on x0. The explicit form of the fundamental

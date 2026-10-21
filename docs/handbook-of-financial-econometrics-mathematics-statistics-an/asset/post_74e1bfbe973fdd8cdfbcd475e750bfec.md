
where the coefficients are D = (−δ_b + γ/2)/G, E = (β_g − γ/2)/G, B = (β_b−γ/2)/G, C = (−δ_g+γ/2)/G, with G = −(δ_g−γ/2)(δ_b−γ/2)+(β_b−γ/2)(β_g − γ/2). Our estimator for π0 derives from (108A.4) as 1 − π_b − π_g.

Setting the β parameters equal to 1.0 and the δ parameters equal to 0.0, then 1 − π_b − π_g in (108B.4) is equal to the classical FDR estimator π0,C. At these parameter values, assuming F_b > γ/2 and F_g > γ/2, we find that ∂π0/∂δ_b > 0 and ∂π0/∂δ_g > 0. Setting the δ-parameters to zero biases the estimator of π0 towards zero. There are two offsetting biases. Setting the β-parameters to 1.0 creates an upward bias in the estimator, while setting the δ-parameters to 0.0 creates a downward bias in the estimator.

In the BSW analysis, a central focus is estimating the fractions of skilled and unskilled managers, π_g and π_b. We would call this high and low-performance funds, acknowledging that the after-cost alphas used in both of our studies are better measures of the performance available to investors than they are measures of fund skill. BSW estimate the fractions by subtracting the expected fraction of “lucky” funds, P(reject at t_g|H0)π0 = (γ/2)π0, from the observed fraction of funds where the null hypothesis of zero alpha is rejected in favor of the alternative of a positive alpha. In our notation the classical estimator for π_g is F_g − (γ/2)π0,C, where π0,C.

The classical estimator separates skill from luck by subtracting from F_g, the fraction of “lucky” funds, that the test says have positive alphas but which actually have zero alphas, (γ/2)π0,C. Our approach can better separate skill from luck, because we also consider the expected fraction of “extremely lucky” bad funds, where the test is confused and indicates that the fund is good.

## Appendix 108C A Two-Distribution Model

With two distributions we use two-sided tests of the null hypothesis. Solving the probability model for an estimator of π0 in the two-distribution model with only a zero alpha and a positive alpha, the parameters β_b, δ_b and δ_g are no longer relevant and we obtain:

π0 = [β_g − E(F_g)]/(β_g − γ), (108C.1)

where γ is the size of the one-tailed test of the null of zero alpha against the alternative of a positive alpha. We use this version of the model in our simulations that examine the discovery rates in the main paper. The two-distribution model with only a zero and a bad alpha modifies (108C.1) in the obvious way. The standard error of the estimator follows from (108C.1) and the variance of F_b.

## Appendix 108D Kernel Smoothing

We employ a kernel smoothing function to estimate the simulation-generated empirical densities of the alphas, conditional on each subpopulation of funds. Let the sample of the relevant cross-section of funds’ alpha estimates be {x_i}_{i=1,…,n}. The estimator for the density function evaluated at some particular value, x, is:

f(x) = (1/nh) ∑_{i} K((x - x_i)/h), (108D.1)

where the kernel function K(·) must be strictly positive and integrate to 1.0. The symbol h denotes the bandwidth parameter and n is the number of observations. We choose the Epanechnikov optimal kernel function:

K(u) = (3/4)(1 - u^2) I(|u| < 1), (108D.2)

with the bandwidth parameter that approximately minimizes the mean integrated squared error of the kernel approximation for second-order kernels (see Hansen (2009, Section 2.7)), which is 0.374 in our application when the number of funds in the sample is 3865.

When the conditional distributions are estimated from simulations and there are 1000 trials, there are 3,865,000 observations of the x_i, which is unwieldy. To keep the problem of manageable size, we use the 3865 observations from the first simulation trial. We experiment with concatenating the observations from the first k simulation runs, and adjust the bandwidth of the kernel according to Silverman’s rule of thumb, multiplying it by k^{(-1/5)}. We also experiment with using the means of the simulated alphas for each fund taken across the simulation trials to characterize the conditional distributions. Neither of these alternatives changes the results much in the full sample. In the rolling, 60-month analysis, k = 1 produces some instability across simulation trials. We find that recursive estimation with k = 2 produces more stable results, so we use recursive estimation with k = 2.

## Appendix 108E Robustness Results Details

Tables 108E.1–108E.5 present ancillary results described in the main text. This section provides additional information for interpreting these tables. Table 108E.1 presents summary statistics for the hedge fund returns, comparing the effects of different benchmarks, different numbers of required observations and the effects of return smoothing. In the main text, Table 108.1, the minimum number of observations is 8, while here it is 12. The summary statistics show that the cross-sectional distributions of

### Table 108E.1: Summary statistics with alternative benchmarks.

Hedge fund returns: January 1994-March 2012 (219 months)

| Fractile SW | Nobs | Mean | Std | Rho1 | α Estimates (%) 3-fac | α Estimates (%) 7-fac | α t-ratios 3-fac | α t-ratios 7-fac | α t-ratios 7-fac SW |
|---|---|---|---|---|---|---|---|---|---|
| 0.010 | 208 | 2.52 | 14.31 | 0.61 | 2.147 | 2.200 | 6.395 | 6.787 | 7.326 |
| 0.050 | 154 | 1.46 | 8.57 | 0.50 | 1.042 | 1.140 | 3.369 | 3.380 | 3.932 |
| 0.100 | 125 | 1.15 | 6.65 | 0.43 | 0.736 | 0.811 | 2.485 | 2.959 | 2.919 |
| 0.250 | 83 | 0.75 | 4.21 | 0.30 | 0.342 | 0.431 | 1.287 | 1.598 | 1.682 |
| Median | 48 | 0.38 | 2.63 | 0.17 | 0.030 | 0.119 | 0.110 | 0.456 | 0.504 |
| 0.750 | 28 | -0.01 | 1.74 | 0.03 | -0.307 | -0.186 | -0.931 | -0.605 | -0.668 |
| 0.900 | 18 | -0.56 | 1.23 | -0.11 | -0.813 | -0.672 | -1.850 | -1.642 | -1.806 |
| 0.950 | 15 | -1.07 | 0.97 | -0.20 | -1.296 | -1.079 | -2.436 | -2.248 | -2.486 |
| 0.990 | 12 | -2.61 | 0.58 | -0.33 | -2.626 | -2.786 | -4.031 | -3.742 | -4.012 |

Notes: Monthly returns are summarized for hedge funds, stated in monthly percentage units. The values at the cutoff points for various fractiles of the cross-sectional distributions of the sample of funds are reported. Each column is sorted on the statistic shown. Nobs is the number of available monthly returns, where a minimum of 12 are required. Mean is the sample mean return, Std is the sample standard deviation of return, reported as monthly percentages, and Rho1 is the first-order sample autocorrelation in raw units. The alpha (α) estimates and their t-ratios are based on OLS regressions using the Fama-French three factors (denoted 3-fac) or the Fung and Hsieh seven factors (denoted 7-fac) and heteroskedasticity-consistent standard errors for the hedge funds. The t-ratios denoted 7-fac SW use Scholes Williams betas, and increase the minimum number of required observations to 19.

### Table 108E.2: Estimated fractions of funds with various alpha values.

Panel A: Mutual Funds

| Monthly Alphas (%) Good α_g | Monthly Alphas (%) Bad α_b | Size γ/2 | FDR Calcs: π0 | FDR Calcs: π_g | Powers β_g | Powers β_b | Confusions δ_g | Confusions δ_b | Fractions π0 | Fractions π_g |
|---|---|---|---|---|---|---|---|---|---|---|
| Estimates for Given Test Sizes and Various Alpha Values | | | | | | | | | | |
| -0.084 | -0.104 | * | 72.6 | -4.6 | 4.1 | 29.5 | 3.3 | 25.6 | 0.0 | 0.0 |
|  |  |  |  |  |  |  |  |  | (na) | (na) |
| 0.031 | -0.234 | * | 72.4 | -4.5 | 14.3 | 57.9 | 1.1 | 7.3 | 63.2 | 0.0 |
|  |  |  |  |  |  |  |  |  | (34.1) | (na) |
| 0.170 | -0.415 | * | 71.7 | -4.3 | 45.2 | 81.5 | 0.4 | 1.8 | 75.9 | 0.0 |
|  |  |  |  |  |  |  |  | (6.1) | (na) |
| 0.270 | -0.573 | * | 72.7 | -4.5 | 64.6 | 91.1 | 0.2 | 0.9 | 77.7 | 0.0 |
|  |  |  |  |  |  | (4.1) | (na) |

### Table 108E.2: (Continued)

Alphas (%)
Good α_g  Bad α_b  Fit  Size γ/2  Powers β_g β_b  Confusions δ_g δ_b  Fractions π_0 π_g

Joint Estimation of Alphas and Fractions in the Populations

Unconstrained Alpha Domains, 3-Group Model
-0.087  -0.305  2509  0.05  2.1  58.7  0.4  15.6  38.9 (14.6)  4.4 (22.1)
-0.034  -0.204  2155  0.10  6.9  52.4  1.5  15.4  50.7 (26.7)  6.9 (37.2)

Constrained Alpha Domains (α_g ≥ 0, α_b ≤ 0), 3-Group Model
0.004  -0.162  3925  0.05  5.6  30.0  1.0  4.8  33.4 (28.3)  12.2 (35.3)
0.001  -0.173  3816  0.10  10.3  45.7  1.8  10.3  0.0 (na)  55.2 (44.5)

2-Group Model
0.00  -0.139  4694  0.05  na  24.0  na  na  29.3 (23.2)  0.0 (na)
0.0  -0.172  3862  0.10  na  45.5  na  na  48.4 (37.8)  0.0 (na)

Single-Alpha Model
na  -0.220  3431  0.05  na  na  na  na  0.0 (na)  0.0 (na)
na  -0.205  3401  0.10  na  na  na  na  0.0 (na)  0.0 (na)

Panel B: Hedge Funds

Monthly Alphas (%)
Good α_g  Bad α_b  Size γ/2  FDR Calcs: π_0 π_g  Powers β_g β_b  Confusions δ_g δ_b  Fractions π_0 π_g

Estimates for Given Test Sizes and Various Alpha Values
0.040  0.020  *  75.8  22.3  12.8  9.4  11.6  8.7  0.0 (na)  100 (na)
0.342  -0.307  *  76.6  21.8  40.4  39.2  4.2  4.1  53.3 (18.8)  39.8 (13.7)
0.736  -0.813  *  75.0  22.6  68.2  73.5  2.1  2.4  77.6 (9.1)  20.6 (7.2)
1.042  -1.296  *  76.5  22.1  80.0  85.8  1.4  1.8  81.5 (6.4)  17.1 (4.7)

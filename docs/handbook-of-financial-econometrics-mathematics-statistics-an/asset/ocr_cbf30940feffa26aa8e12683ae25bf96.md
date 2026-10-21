Kroner and Sultan (1993) combine the error-correction model with the GARCH model considered by Cecchetti et al. (1988) and Baillie and Myers (1991) in order to estimate the optimum hedge ratio. Specifically, they use the following model:

```
\[\begin{bmatrix} \Delta \log_e (S_t) \\ \Delta \log_e (F_t) \end{bmatrix} = \begin{bmatrix} \mu_1 \\ \mu_2 \end{bmatrix} + \begin{bmatrix} \alpha_s (\log_e (S_{t-1}) - \log_e (F_{t-1})) \\ \alpha_f (\log_e (S_{t-1}) - \log_e (F_{t-1})) \end{bmatrix} + \begin{bmatrix} e_{1t} \\ e_{2t} \end{bmatrix}, (11.28)\]
```

# 11.3.2 Estimation of the optimum mean-variance and Sharpe hedge ratios

The optimum mean-variance and Sharpe hedge ratios are given by equations (11.4) and (11.7), respectively. These hedge ratios can be estimated simply by replacing the theoretical moments by their sample moments. For example, the expected returns can be replaced by sample average returns, the standard deviations can be replaced by the sample standard deviations, and the correlation can be replaced by sample correlation.

# 11.3.3 Estimation of the maximum expected utility hedge ratio

The maximum expected utility hedge ratio involves the maximization of the expected utility. This requires the estimation of distributions of the changes in spot and futures prices. Once the distributions are estimated, one needs to use a numerical technique to get the optimum hedge ratio. One such method is described in Cecchetti et al. (1988) where an ARCH model is used to estimate the required distributions.

# 11.3.4 Estimation of mean extended-gini (MEG) coefficient based hedge ratios

The MEG hedge ratio involves the minimization of the following MEG coefficient:

```
\[\Gamma_v(R_h) = -v \Cov[R_h, (1 - G(R_h))^{v-1}].\]
```

In order to estimate the MEG coefficient, we need to estimate the cumulative probability density function G(R_h). The cumulative probability density function is usually estimated by ranking the observed return on the hedged
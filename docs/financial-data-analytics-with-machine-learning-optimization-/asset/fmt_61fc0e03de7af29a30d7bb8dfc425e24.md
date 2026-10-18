
where `D_t := diag(σ_1t, ..., σ_pt)` and `R_t` is the conditional time-varying correlation matrix given `σ_it`'s. The variance `σ_it^2` in `D_t` for each security `i = 1, 2, ..., p` can be modelled by an independent GARCH(1, 1) process. Denote the marginally standardized innovation vector by `η_t = D_t^{-1} r_t`, where `r_it` is the return of security `i` at time `t`. The DCC-GARCH(1, 1) model incorporates time-varying conditional correlations through the evolutionary covariance matrix, denoted by `Q_t`. This covariance matrix is recursively modeled as:

(7.26) `Q_t = (1 - θ_1 - θ_2) Q̄ + θ_1 η_{t-1} η_{t-1}^⊤ + θ_2 Q_{t-1}, for t = n, n + 1, ...`

where `Q̄` is the unconditional covariance matrix of `η_t`. The positive coefficients `θ_1` and `θ_2` are constrained by `θ_1 + θ_2 < 1`, determining the impact of past innovations on the current covariance matrix. To obtain the evolutionary correlation matrix `R_t` at time `t`, we standardize the covariance matrix `Q_t` with the following formula:

(7.27) `R_t = diag(Q_t)^{-1/2} Q_t diag(Q_t)^{-1/2}.`

After obtaining `R_t`, we can estimate the conditional covariance matrix from ([7.25](#c07.xhtml#c07-disp-0044)).

Under the multivariate normal assumption `u_t ~ N_k(0, H_t)` given `H_t`, the logarithmic likelihood function is given by:

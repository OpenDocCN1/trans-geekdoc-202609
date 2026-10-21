The equality of (40.24) indicates that the spread of GVIX and VIX (GV-Spread) is determined by the ex ante mean return of the underlying asset as well as the ex ante high moments of the return distribution.

In practice, the calculation of our generalized volatility index is as simple as that of VIX (equation (40.17)). No additional information is necessary, and one is able to compute the GVIX based on three aspects: option prices (Q_K), arbitrage-free forward price of the underlying asset (F0 = S0 e^{rT}) and risk-free rate of interest (r) such that

mu_T hat = [ln(K0/S0) + (F0/K0 -1)] - e^{rT} sum_i 1/K_i^2 Q(K_i) Delta K, (40.25)

V_T hat = [ln^2(K0/S0) +2 ln(K0/S0)(F0/K0 -1)] +2 e^{rT} sum_i 1/K_i^2 [1+ln(S0/K_i)] Q(K_i) Delta K_i, (40.26)

GVIX = 1/sqrt(T) sqrt(V_T hat - (mu_T hat)^2). (40.27)

Furthermore, to be consistent with CBOE's VIX estimation, we adjust the GVIX index on a 30-day basis. Following the same interpolation procedures as VIX estimation (see equation (40.18)), we first identify option contracts of the near-term and next-term, denoted by T1 and T2, accordingly. Then, one calculates two GVIX indexes according to T1 and T2, respectively. Finally, by taking a weighted average, one could calculate the annualized GVIX index based on 30-day market returns as follows:

GVIX_a = sqrt( { [N(T2)-N(30)]/[N(T2)-N(T1)] (T1 * GVIX1^2) + [N(30)-N(T1)]/[N(T2)-N(T1)] (T2 * GVIX2^2) } (N(365)/N(30)) ). (40.28)

Having mathematically explained the bias of the VIX formulation and proposed an alternative volatility measure in theory, we now pursue our empirical investigation in the Section 40.5.

# 40.5 Empirical Investigation

We empirically examine our theoretical arguments using the S&P500 index (SPX) options data during the 2362-daily period between January 2005 and
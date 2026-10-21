(x_{i,t} = 1 for a stock recommended on date t − 1); R_{i,t} represents the daily return for the recommended stock i on date t.

The abnormal return is estimated using the intercept term, α_p, derived from the Fama and French (1993) three-factor model⁵:

$R_{p,t} - R_{f,t} = \alpha_p + \beta_p(R_{m,t} - R_{f,t}) + s_p SMB_t + h_p HML_t + \varepsilon_{p,t}, \quad (55.2)$

where R_{p,t} and R_{m,t} are the daily return on the portfolio and the FTSE All-Share Index, respectively, R_{f,t} represents the three month UK T-bill rate, SMB_t and HML_t represent the daily returns on zero-investment factor-mimicking portfolios for size and book-to-market (B/M), respectively, ε_{p,t} represents the error term. We obtain the daily (R_{m,t}−R_{f,t}), SMB_t, and HML_t in the UK stock market from the Xfi Centre for Finance and Investment at the University of Exeter (see, Gregory et al., 2013).

We estimate equation (55.2) on a rolling window basis, i.e., a one year window length rolling one trading day forward, to track the performance of the underlying variables over time. For example, the first rolling window is from January 2, 1997 to December 31, 1997, which covers 253 trading days. The chosen length of a rolling window is one year in this study as average investors generally evaluate their portfolios on an annual basis (see, Benartzi and Thaler, 1995).Then the return for the first trading day is dropped and the return for a new trading day is added, meaning that the return for January 2, 1997 is dropped and the return for January 2, 1998 is added. This process continues so that we estimate a total of 3,912 rolling windows over the whole sample period. In each rolling window, the three-factor regression yields parameter estimates of α_p, β_p, s_p, and h_p; a significantly positive (negative) α_p indicates that the long (short) portfolio is profitable after controlling for the risk factors of market, size, and value. This calculation, therefore, generates a time-series of daily abnormal returns for the long or short portfolio.

# 55.3.3 Time-series bootstrapping simulation methods

To study whether the time-varying abnormal returns to the long and short portfolios are due to random chance (i.e., sell-side analysts’ luck), we propose a time-series bootstrapping simulation method in the spirit of Kosowski et al. (2006) and Fama and French (2010). In particular,
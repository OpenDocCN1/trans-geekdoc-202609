the proposal transition density

$$f \propto \prod_{t=1}^{T} \exp\left(-\kappa g_t + (\nu_t - 1.5)\log(g_t)\right). \quad (70.17)$$

The steps of the Metropolis chain algorithm are outlined as follows:

+   (a) For $n = 1$ to $L$,  
+     (a.1) A random sample $\boldsymbol{g} = (g_1, \dots, g_T)'$ is drawn from the proposal transition density $\boldsymbol{f}$,  
+     (a.2) A random variate $U \sim Uniform(0,1)$ is generated, if $U < b$, then $\boldsymbol{g}_n = \boldsymbol{g}$, otherwise, $\boldsymbol{g}_n = \boldsymbol{g}_{n-1}$, where  
+     $$b = \min\left\{\exp\left(-\sum_{t=1}^{T}\left(\frac{\delta_t}{g_t} - \frac{\delta_t}{g_{t,n-1}}\right)\right),1\right\}. \quad (70.18)$$  
+   (b) $\boldsymbol{g}_L$ is one realization from the target distribution $p(\boldsymbol{g}|\boldsymbol{Y}; \Theta)$.

# 70.4 Empirical Analysis

This chapter considers price dynamics of financial firms with capitalization exceeding US$500 billion belonging to the S&P 500 index during January 3, 2006 to December 31, 2009. Table 70.1 lists a representative sample of eight S&P 500 financial firms. Daily adjusted close price data are collected from January 3, 2006 to December 31, 2009. Table 70.2 lists the correlation coefficients among the eight financial companies. Price movements are closely correlated for the four commercial banks, namely, the Bank of America (BAC), Wells Fargo (WF), J.P. Morgan Chase (JPM), and CitiGroup (CITI), with

Table 70.1: S&P 500 financial companies with assets exceeding $500 billions.

| Name | Total stockholders' equity | Total liabilities and stockholders' equity |
|---|---|---|
| Goldman Sachs Group Inc. | 64.369 billion | 849 billion |
| J.P. Morgan Chase & Co. | 170.19 billion | 2.07 trillion |
| Wells Fargo & Co. | 99.08 billion | 1.284 trillion |
| State Street Corporation | 125.19 billion | 1.7 trillion |
| Morgan Stanley | 50.831 billion | 659.035 billion |
| CitiGroup Inc. | 125.19 billion | 1.93 trillion |
| Bank of America Corporation | 177.052 billion | 2.25 trillion |
| American International Group, Inc | 52.710 billion | 860.418 billion |
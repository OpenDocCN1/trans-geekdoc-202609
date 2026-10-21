
applying it to the empirical estimations. As a result, we anticipated that the intertemporal relation between VaR_t and the excess return, R_{t+1}, in the market is positive and statistically significant as predicted by the tradeoff hypothesis. Figure 58.1 depicts the autocorrelation functions up to lag 40 for the weekly downside risk of nine markets. Evidently, the autocorrelations of these series have been persistent and significantly stretched out for a long period of lags. The time series plots suggest that VaR exhibits a long memory phenomenon, although the patterns may differ from each other in different markets. In addition, the Ljung-Box test statistics for examining the null hypothesis of the independence of the autocorrelation of the VaR time series for each market up to 40 lags have significantly rejected its null.⁶

Table 58.1 presents the summary statistics of stock returns and downside risk for Asian markets. The weekly excess returns are in the range of -0.019% (Taiwan) to 0.138% (S. Korea). These numbers translated to an annual basis are -0.988% to 7.176%. The evidence suggests that the VaR for all of the markets shows the presence of an AR(1) process and Indonesia has the highest standard deviations on both stock returns and VaR. The augmented Dickey-Fuller (ADF) tests indicate that the null hypothesis of a unit root is rejected uniformly and is significant at the 1% level for all markets. Rejecting the null indicates that the returns and VaR do not have a unit root, indicating that d in the (1 − L)^d VaR_t process may lie between zero and one, characterizing a long memory process.

## 58.3 VAR Process for Risk–Return Dynamics

### 58.3.1 Elements of VAR process

To allow for more flexible interaction between returns and risks with different lagged lengths, we consider a VAR system that jointly analyzes both the downside risk and excess returns as given by

$A_i(L)\mathbf{X}_{i,t} = \mathbf{u}_{i,t},\quad (58.1)$

## Table 58.1: Descriptive statistics of downside risk and stock returns.

| Country | Series | Mean | Std | Skewness | Kurtosis | AR(1) | ADF test |
|---|---|---:|---:|---:|---:|---:|---:|
| Korea | Return | 0.138% | 5.680% | −0.536 | 5.120 | −0.057 | −8.585* |
|  | VaR | 2.209% | 2.038% | 2.303 | 9.190 | 0.365* | −5.820* |
| Hong Kong | Return | 0.039% | 3.715% | −0.294 | 1.380 | −0.003 | −8.092* |
|  | VaR | 1.559% | 1.304% | 2.323 | 10.984 | 0.364* | −5.811* |
| Indonesia | Return | −0.004% | 6.287% | −0.628 | 5.667 | −0.010 | −8.877* |
|  | VaR | 2.227% | 2.562% | 3.676 | 20.743 | 0.444* | −6.728* |
| Thailand | Return | 0.006% | 5.168% | −0.061 | 2.396 | 0.009 | −9.035* |
|  | VaR | 1.860% | 1.590% | 1.929 | 6.226 | 0.323* | −5.975* |
| Singapore | Return | 0.053% | 3.266% | −0.243 | 1.701 | 0.054 | −7.972* |
|  | VaR | 1.293% | 1.044% | 1.764 | 5.775 | 0.303* | −6.262* |
| Taiwan | Return | −0.019% | 4.144% | −0.087 | 1.213 | 0.003 | −7.975* |
|  | VaR | 1.635% | 1.208% | 1.359 | 3.531 | 0.293* | −6.255* |
| Malaysia | Return | 0.001% | 4.327% | −0.841 | 14.890 | 0.034 | −8.024* |
|  | VaR | 1.371% | 1.863% | 6.915 | 76.354 | 0.470* | −5.080* |
| US | Return | 0.071% | 2.913% | −0.510 | 2.263 | −0.069 | −8.660* |
|  | VaR | 1.319% | 1.070% | 1.920 | 6.154 | 0.329* | −4.934* |
| China | Return | 0.104% | 3.803% | 0.007 | 1.069 | −0.033 | −7.617* |
|  | VaR | 1.567% | 1.213% | 1.545 | 3.482 | 0.236* | −6.439* |

*Notes:* The data cover seven Asian markets: Korea, Hong Kong, Indonesia, Thailand, Singapore, Taiwan and Malaysia. Both the United States and China are viewed as the dominating countries. The entire sample spans the period 1997–2011. Both excess return and the VaR are calculated on a weekly basis by taking the log-difference between the daily stock prices on Wednesday. The VaR is defined as the minimum daily return from Wednesday of weekₜ₋₁ to Wednesday of weekₜ, and has been multiplied by −1. ADF is the augmented Dickey–Fuller test (1981). * indicates that the coefficient is significant at the 1% level. The ADF tests together with the critical values reported by Fuller (1976) indicate that the null hypothesis of a unit root is rejected uniformly. Rejecting the null indicates that the returns and VaR do not have a unit root, indicating that \(d(1-L)^dV_t\) may lie between zero and one, characterizing a long memory process.

where \(X_{i,t}=(R_{i,t},V_{i,t})'\) is a vector containing the excess return \(R_{i,t}\) and the downside risk \(V_{i,t}\) is measured by VaR in country \(i\) at time \(t\). \(A_i(L)\) is a lag polynomial and \(u_{i,t}\) is a system error vector. Both \(R_{i,t}\) and \(V_{i,t}\) are demeaned values, in the sense that the values of returns and downside risk are subtracted from the corresponding unconditional means, respectively.

To specify a valid dynamic VaR system involving excess returns and risk, it is necessary to deal with the persistent impact of risk on excess returns. This can be done by applying long memory models to address the degree of persistence in time series data. Granger and Ding (1996) and Chen et al. (2018) note that a long memory series is characterized by a slowly declining autocorrelation structure such that the process depends strongly upon values of the time series in the distant past. This specification is consistent with the risk aversion behavior of investors: it takes a long time for fear to subside once an investor suffers a big loss in the equity market.

To address the impact of a long memory on the risk–return relation, we adopt the following procedures. First, to examine the effect of the long memory property embodied in downside risk, we begin with a short-memory specification of a VaR process and then refine it by using an appropriate fractionally integrated process. Second, we incorporate the leverage effect into this dynamic VAR system. The leverage effect depicts a negative relation between the lagged return and the risk resulting from bad news that causes higher volatility. This increase in VaR produces a forward-looking effect on the demand for higher future returns, giving rise to a VaR feedback effect. A bivariate VAR system that consists of return and downside risk adjusted for long memory will give us a flexible and more comprehensive approach for dealing with risk–return dynamics.

Merton’s (1973) intertemporal capital asset pricing theory postulates that there is a positive and linear relation between the expected return and conditional variance. Using the conditional downside risk (Bali and Cakici, 2004; Bali et al., 2009), rather than the conditional variance, to measure risk, we can express Merton’s (1973) notion as:

$E_t[R_{i,t+1}] = \gamma_{ii} \cdot E_t[V_{i,t+1}], \quad (58.2)$

where $R_{i,t+1}$ is the excess return of country $i$ at time $t+1$; $E_t[\cdot]$ is an expectation operator at time $t$; $\gamma_{ii}$ is the relative downside risk aversion parameter of country $i$; and $E_t[V_{i,t+1}]$ is the conditional VaR of country $i$. Following Bali et al. (2009), we model the VaR process as an AR(1) given by

$V_{i,t+1} = a_i + \phi_i V_{i,t} + v_{i,t+1}. \quad (58.3)$

By substituting equation (58.3) into equation (58.2) and using rational expectations, $R_{i,t+1} = E_t[R_{i,t+1}] + \varepsilon_{i,t+1}$, we obtain:

$R_{i,t+1} = \gamma_{ii}\phi_i V_{i,t} + \varepsilon_{i,t+1}. \quad (58.4)$

Equation (58.4) provides a functional relationship between VaR and the next period’s excess return. A system of excess returns and conditional downside

⁸Equation (58.2) has been widely used to examine the intertemporal relation between risk and return for the aggregate stock market. For instance, Bali and Peng (2006) find that there is a significantly positive relation between the GARCH variance of the S&P 500 index and excess return in the market. The estimated coefficients on the daily GARCH variance correspond to a relative risk aversion parameter of 11.25 for the S&P 500 index and 9.79 for the CRSP value-weighted index. This evidence, along with the study by Ghysels et al. (2005), supports the risk–return tradeoff hypothesis.


the daily data of stocks in the S&P 500 index, we document strong evidence of persistent dynamic correlations among the returns of the index component stocks. Conditional correlations between S&P 500 index and the component stocks increase substantially during the period of sub-prime crisis, showing strong evidence of contagion. In addition, stock return variance is time-varying and peaks at the crest of financial crisis. The results show that the DCC-GARCH model is a powerful tool for forecasting return correlations and performing value-at-risk portfolio analysis.

## Keywords

Dynamic conditional correlation • Multivariate GARCH • DCC-MVGARCH • Contagion • Risk management.

## 129.1 Introduction

In portfolio and risk management, it is a common practice to pick stocks in different categories (styles) and evaluate their correlation with a benchmark. For portfolio managers, they need to divide his/her portfolio into a number of different industries, such as banking and real-estate industries, to manage risk. This provides asset diversity within each industry and diversification across industries. In order to manage portfolio risk, managers need to know the relations of the assets in the portfolio. Thus, it is imperative for them to estimate the correlation of a selection of firms or companies within each industry and of different industry index. Although the prevailing diversification strategies typically assume that correlations are constant, it has been known that for some time that individual stocks and overall market return correlations do not remain constant (see, for example, Giorgio, 2016; Mollah, Quoreshi, and Zafirov, 2016; Horváth, Lyócsa, and Baumöhl, 2018). Moreover, it is widely recognized that the correlations among equity returns tend to increase during bear markets, and decrease during periods of strong stock market growth (see Santis and Gerard, 1997; Bekaert and Ang, 1999). Especially, in times of financial crisis, such as stock market crash in October 1987, Asian crisis in the late 1990's, and the subprime crisis in 2007-2009, stock market correlations increased. In this chapter, in order to assess the contagious effect during the subprime crisis, we employ a dynamic variance–covariance model to ascertain time-varying correlations and volatility of stock returns.

We first examine the statistical properties of daily stock returns. The daily stock returns during the period from January 2006 to October 2008 are random, which approaches to normal distribution by Jarque-Bera test. This finding justify the use of the DCC-GARCH model introduced by Engle (2001), which is based on the multivariate normal distribution, to calculate the correlations of stock returns.

Univariate GARCH models have widespread applications in estimating and forecasting equity return variances. But a major challenge in estimating the multivariate GARCH models with time-varying correlations is the substantial computing requirement, which constraints researchers to estimating models with either a limited scope or considerable restrictions (see Engle and Sheppard, 2001). For example, the full unrestricted multivariate GARCH model, originally proposed by Bollerslev, Engle and Wooldridge (1998), requires O(k^4) parameters to be estimated by maximum likelihood, where k is the number of time series being modeled. Even for a simpler model, the diagonal vech, which allows for non-zero coefficients only on own lagged effects and cross products, the number of parameters estimated is O(k^2). To overcome these computational burden, Engle (2002), and Engle and Sheppard (2001) have proposed a more efficient model, the DCC-GARCH model, to deal with the time-series behavior of large correlation matrices by adopting a two-step procedure. In the first step, a set of univariate GARCH models is estimated for each asset return. In the second stage, they used residuals, transformed by the standard deviation estimated during the first stage, to estimate the parameters of the dynamic correlation.

In the past two decades, there has been a considerable interest in the return correlation issue between different markets. For instance, Breen, Glosten and Jagannathan (1989) document a negative correlation between the short-term interest rate and the stock index future returns in the United States. As mentioned by Kearney and Poti (2003), an extensive analysis of long-term trends at the firm level and market volatility in United States stock markets from 1962 to 1997 is provided by Campbell, Lettau, Malkiel and Xu (abbreviated by CLMX) (2001). They document the evidence that a decline in overall market correlations has been accompanied by a parallel increase in average firm-level volatility by using daily data of all stocks traded over their sample period on three stock markets (AMEX, NASDAQ and NYSE).

In this chapter, we apply the dynamic conditional correlation GARCH model of Engle (2002) and Engle and Sheppard (2001) to capture the behavior of three kinds of firm-level correlations with S&P 500 index and three kinds of intercorrelations in the same index over the period from January 2006 to October 2008. Our major findings can be summarized as follows. First, from the simple average correlations, we find that the trends of firm-level correlations increase from February 2007 to October 2008, which covers

part of the subprime crisis period. Second, the variance of each time series of returns becomes much larger starting from July 2007 than before. Moreover, we discover that the variance has three different stages for each time series of asset returns. In the first stage, before July 2007, the variance is very flat. In the second stage, from July 2007 to September 2008, it becomes much bigger. In the third stage, from September 2008 to October 2008, the variance reaches a peak value. The results show that both correlations and variance of returns increase substantially over our sample period.

This chapter is structured as follows. In Section 129.2, we discuss the DCC-MVGARCH model and its implementation. In Section 129.3, we introduce a multiple structural change model proposed by Bai and Perron (1998). This model is used to test the structural change for the correlations that we estimate. In Section 129.4, we present our results of estimated coefficients and tests and present time series of correlations. These graphs are related to three simple average correlations of firms in the same industry, correlations among firms and with the S&P500 index, and variance for some selected return time series. Finally, Section 129.6 summarizes the results and concludes the paper.

## 129.2 Model and Estimation

The dynamic conditional correlation (DCC) GARCH model proposed by Engle (2002) is used in empirical estimation. The DCC-GARCH model can be estimated in two stages. In the first stage, the mean return of each stock in the sample nested in a univariate GARCH model is estimated. We use the variance estimate to standardize the zero-mean return for each stock. In the second stage, the parameters of the dynamic correlation are estimated using the residuals from the first stage.

Assume that the returns r_t from k assets are either the residuals from a filtered time series or conditionally multivariate normal with zero expected value and covariance matrix H_t. Let D_t be the k × k diagonal matrix of time varying standard deviations from univariate GARCH models, and R_t be the time varying correlation matrix. Then, the generalized DCC-MVGARCH model can be written as follows:

r_t|F_{t-1} ~ N(0, H_t), (129.1)

and

H_t = D_t R_t D_t, (129.2)

where

D_t = diag{h_it}, (129.3)

and

R_t = Q_t^{*-1} Q_t Q_t^{*-1} = {q_{ij,t}/ sqrt(q_{ii,t} q_{jj,t})}, (129.4)

where {rho_ij}_t = q_{ij,t}/ sqrt(q_{ii,t} q_{jj,t}) is a correlation matrix containing the conditional correlation coefficients.

From above, h_it represents the variance of r_t, which follow the univariate GARCH(p, q) process:

h_it = omega_i + sum_{p=1}^{P_i} alpha_{ip} r_{it-p}^2 + sum_{q=1}^{Q_i} beta_{iq} h_{it-q}. (129.5)

In Engle's (2002), DCC(M, N) structure can be given as

Q_t = (1 - sum_{m=1}^{M} alpha_m - sum_{n=1}^{N} beta_n) bar Q + sum_{m=1}^{M} alpha_m (epsilon_{t-m} epsilon'_{t-m}) + sum_{n=1}^{N} beta_n Q_{t-n}, (129.6)

Q_t^* = diag{ sqrt(q_ii) }, (129.7)

where Q_t = {q_{ij,t}} is the conditional variance-covariance matrix of standardized errors, epsilon_t = D_t^{-1} r_t = {epsilon_{it}/ sqrt(h_{it})} is a vector containing the standardized errors, and bar Q is the unconditional covariance of the standardized residuals resulting from the first stage estimation.

The DCC-GARCH model can be estimated using the maximum likelihood method, in which the log-likelihood function for the model can be written as

L = -1/2 sum_{t=1}^{T} (k log(2pi) + log(|H_t|) + r_t' H_t^{-1} r_t) = -1/2 sum_{t=1}^{T} (k log(2pi) + 2 log(|D_t|) + log(|R_t|) + epsilon_t' R_t^{-1} epsilon_t). (129.8)

This estimation process includes two stages. In the first stage, R_t is replaced by a k x k identity matrix, which reduces the equation above to the sum of log-likelihood of the univariate GARCH equations in (129.5). Let phi_i = (omega, alpha_{1i}, ..., alpha_{P i}, beta_{1i}, ..., beta_{Q i}) be the parameters of the univariate GARCH

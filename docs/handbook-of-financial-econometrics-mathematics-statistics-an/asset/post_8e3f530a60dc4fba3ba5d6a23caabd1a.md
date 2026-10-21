
specification of a particular underlying stochastic process of returns. Without any diffusion assumption, VIX theoretically characterizes not the fair value of volatility but that of a linear combination of ex ante distributional return-moments. Particularly, the VIX index constitutes additionally one-third of the value of the ex ante third return-moment (skewness). This highlights a potentially significant bias for VIX to serve as a volatility index because skewness continues to occupy a prominent role in financial markets. Intuitively, during a period when asset price-movement experiences downtrend momentum, demand for puts increases relatively to calls as investors seek protection, and put options become relatively more expensive than call options. The value of volatility, which is extractable from the market price of a long option portfolio, increases as put premiums increase. Simultaneously, the price of the third-moment (skewness) is replicable by a long position of OTM calls and a short position of OTM puts, on the other hand, becomes largely negative. Consequently, even when the VIX (fear gauge) value increases, the index still understates the true value of volatility due to the impact of a negative third-moment.

To avoid the impact of high moments on the volatility index as well as to retain the same economic merit as the VIX’s conceptualization, we propose an alternative approach, named generalized VIX (GVIX). GVIX is generic because it is based on the direct definition of log-return variance with an option formulation extended from Bakshi et al. (2003). Neither modeling specification nor diffusion assumption is necessary to be imposed on the underlying asset’s return generating process. Further, we prove that VIX is a special case of GVIX.

We empirically investigate estimation errors of VIX and their relationship with ex ante return-moments of the underlying asset (S&P 500 index) over a period from January 2005 to May 2014. In general, the empirical findings are consistent with our theoretical argument in that VIX statistically and significantly underestimates the true volatility. The VIX-bias dramatically increases as market volatility rises due to the impact of substantially negative third return-moment. In short, the larger the VIX, the higher the downward biases, and these errors could be as much as 559 index basis points.

Finally, we examine time series properties of VIX, GVIX, and especially, the difference between GVIX and VIX (GV-Spread). The individual dynamic process of both VIX and GVIX generally follows a random walk. However, the time variation of GV-Spread over our sample period follows a mean-reversion with a break of the stationary trend dated by September 8, 2008. The co-existence of the stationarity of GV-Spread as well as the non-stationarity of VIX and GVIX implies that the time series of VIX and that of GVIX are co-integrated. The movement of the GV-Spread quantifies the shift of distributional asymmetry of return expectations, as well as the change of market sentiments.

Du and Kapadia (2012) is the closest to the current paper. Du and Kapadia (2012) derive a jump and tail index, JTIX, and uses 22-day moving average of JTIX in their empirical estimation. This chapter differentiates itself from Du and Kapadia (2012) in important ways. First, we provide the discrete approximation procedure following VIX index methodology, this makes the application of our GVIX index more broadly available. Second, in our empirical estimation, we use the daily GVIX and GV-Spread (the difference between VIX and the “true” volatility index) estimates instead of moving averages. Third, we examine the mean-reverting property of GV-Spread and the possibility in terms of spread trading.

The chapter proceeds as follows. Section 40.2 demonstrates the related literature. Section 40.3 presents an important theoretical relationship between option premiums and an ex ante moment-combination of returns to the underlying asset. Section 40.4 reviews the derivation of VIX and explicitly proves the equivalence between VIX and a moment-combination. An alternative model-free expression of the ex ante volatility valuation is also proposed in Section 40.4. Section 40.5 empirically investigates our theoretical arguments, and Section 40.6 contains brief concluding remarks.

## 40.2 Related Literature

A pioneer work by Breeden and Litzenberger (1978) set the foundation of research on extracting risk-neutral distribution and model-free volatility from option market prices. The concept of model-free implied volatility later arose from the research and development of variance-swaps, for example, see Dupire (1994), Neuberger (1994), Carr and Madan (1998), and Bakshi et al. (2003).

Jiang and Tian (2005) extend Britten-Jones and Neuberger (2000) model-free-implied volatility framework to asset prices processes with jumps. They state this model-free-implied volatility provides a more efficient forecast than Black–Scholes-implied volatility for future-realized volatility and is more efficient than the historical variance allowing that the underlying asset price process has jumps.

Carr and Wu (2006) describe the major differences between the old and the new volatility indexes of CBOE, they also derive the theoretical underpinnings for the two indexes. They conclude that the switch is due to the fact that the new VIX has a better known and more robust economic interpretation. Additionally, the variance swap underlying the new VIX formulation has a robust replicating portfolio whose option component is static.

Furthermore, in addition to Du and Kapadia (2012) discussed previously, several other papers are close to ours. Bakshi et al. (2003) theoretically derive risk-neutral skewness and kurtosis for asset returns. This chapter adopts similar approach but applies to asset return volatility instead of centralized higher moments of returns and subsequently provides estimation details. Jiang and Tian (2007) examine the mispricing of VIX index and propose a simple smoothing method instead of VIX formula to estimate model-free return volatility. Comparatively, the GVIX volatility measure in this chapter is less restricted to interpolation choices and is based on the straightforward variance concept. Martin (2011) develops a volatility index, named SVIX, based on the simple variance swaps. However, Martin (2011) does not provide the empirical estimation methodology nor examine the empirical trend of SVIX.

Internationally, Zheng et al. (2017) devise an improved model-free-implied variation index (AVIX) based on a generalized semi-martingale process with stochastic interest rates and applies it to China 50 ETF option markets. They conclude that AVIX is a better measure of investor sentiment compared to iVIX in Chinese market.

## 40.3 Ex ante Moment-Combination and Option Prices

This section demonstrates a generalized relation between option prices and a distributional moments’ combination of log-returns without imposing any structure on the underlying focusing process. We begin conventionally with a simple holding-period return denoted by a capital $R_T$ and a continuously compounded rate of return (or log-return) denoted by a lower case $r_T$, respectively. These are written as:

$R_T = \frac{S_T - S_0}{S_0}, \qquad (40.1)$

$r_T = [\ln(S_T) - \ln(S_0)] = \ln\left(\frac{S_T}{S_0}\right), \qquad (40.2)$

where $S_0$ and $S_T$ are the price of the asset at time 0 and $T$, accordingly. Consider the Taylor expansion with the remainder of $\ln(S_T)$ centered at $S_0$,

we have

$$\ln(S_T)=\ln(S_0)+\frac{S_T-S_0}{S_0}+\int_{S_0}^{\infty}\frac{-1}{K^{2}}(S_T-K)^{+}dK$$

$$+\int_{0}^{S_0}\frac{-1}{K^{2}}(K-S_T)^{+}dK.\tag{40.3}$$

Equivalently, using our return notations in (40.1) and (40.2), equation (40.3) can be rewritten as:

$$R_T-r_T=\left[\int_{S_0}^{\infty}\frac{1}{K^{2}}(S_T-K)^{+}dK+\int_{0}^{S_0}\frac{1}{K^{2}}(K-S_T)^{+}dK\right]\ge 0.\tag{40.4}$$

That is, the return of a long position in a contract that pays a holding-period return ($R_T$) and a short position in the contract that pays the logarithm of a total return at time $T$ ($r_T$) can be replicated by payoffs of a long position in $(1/K^2)$ call option struck at $K$ for all strikes above the current asset price and these of a similar long position in $(1/K^2)$ put option struck at $K$ for all strikes below the current asset price, where all option contracts have $T$ period of time to expiration. Notably, the non-negative option payoffs ensures that $R_T \ge r_T.$

Consider that under the no-arbitrage condition, a currently fair price of an asset can be extracted from the put-call parity of European options so that $S_0 = C_T(K_A) - P_T(K_A) + K_A e^{-rT}$, where $C_T(K_A)$ and $P_T(K_A)$ are the current premiums of call and put option contracts with an at-the-money (ATM) strike $K_A$ and expiration $T$, respectively. $r$ is the annualized risk-free rate corresponding to expiration date $T$. The forward asset price and expected return can then be determined in a risk-neutral framework in that $E(S_T)= e^{rT}[C_T(K_A)-P_T(K_A)]+K_A = S_0 e^{rT}$, and importantly $E(R_T)= \frac{E(S_T)-S_0}{S_0}= e^{rT}-1$, where $E(\cdot)$ represents the expectation operator. This implies that the fair value of the expected return-difference in (40.4) can also be drawn from the risk-neutral forward value of the replicated option portfolio:

$$E(R_T)-E(r_T)=e^{rT}\left\{\int_{S_0}^{\infty}\frac{1}{K^{2}}C_T(K)dK+\int_{0}^{S_0}\frac{1}{K^{2}}P_T(K)dK\right\}.\tag{40.5}$$

For connecting equation (40.5) to the expression of moment-combination, we apply Taylor series to an exponential function of $r_T$ as follows:

$$(1+R_T)=\frac{S_T}{S_0}=\exp\left[\ln\left(\frac{S_T}{S_0}\right)\right]$$

$$=1+\sum_{\kappa=1}^{N}\frac{1}{\kappa!}\left[\ln\left(\frac{S_T}{S_0}\right)\right]^{\kappa}+o\left[\ln\left(\frac{S_T}{S_0}\right)\right]^{N}.\tag{40.6}$$

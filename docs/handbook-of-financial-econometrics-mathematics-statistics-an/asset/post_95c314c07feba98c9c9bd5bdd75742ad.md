
Then, taking the expected value of both sides of equation (40.6) with some rearrangement, the expected value of return difference between $R_T$ and $r_T$ is equal to a linear combination of distributional moments:

$E(R_T) - E(r_T) = \frac{1}{2}E(r_T^2) + \frac{1}{6}E(r_T^3) + \frac{1}{24}E(r_T^4) + o[E(r_T^4)]. \quad (40.7)$

Interestingly, equation (40.7) shows that the expected holding-period return is the moment generating function of the log-returns. Consequently, when we incorporate (40.5) with (40.7), the forward value of an OTM option portfolio represents an *ex ante* moment-combination of log-returns. We demonstrate formally this important result in the following theorem:

### Theorem 40.1.

Let $C_T(K)$ and $P_T(K)$ be the European call and put options with an exercise price of $K$ and expiration date at $T$, respectively. Without imposing any structure on the underlying focusing process, the fair value of *ex ante* moment-combination of log-returns can be extracted from the market price of an OTM option portfolio with weight inversely proportional to square value of the strike price in that

$\left[\frac{1}{2}E(r_T^2) + \frac{1}{6}E(r_T^3) + \frac{1}{24}E(r_T^4) + o[E(r_T^4)]\right]$ 
$= e^{rT}\left[\int_{S_0}^{\infty} \frac{1}{K^2}C_T(K)dK + \int_{0}^{S_0} \frac{1}{K^2}P_T(K)dK\right]. \quad (40.8)$

Theorem 40.1 highlights an essential connection between option premiums and market expectations about future return-moments. Specifically, the market price of a $(1/K^2)$ weighted OTM put/call option portfolio extracts the fair value of a linear combination of *ex ante* moments (e.g., variance, skewness, kurtosis, etc.). Next, we note that the VIX index was derived based on the concept of fair value of *future* variance and used *forward* price instead of current price of the underlying asset as a reference point to determine future OTM option payoffs of calls and puts. In addition, since it is almost certain, in practice, no option contract has a strike price exactly equal to the forward price, one could select the first strike price below the forward price as the reference price. In the next corollary, we adjust the fair value of the option portfolio by taking the forward price into consideration.

### Corollary 40.1.

Let $S_0$ be the current fair price of the underlying asset determined from ATM Put-Call parity, and the forward price ($F_0$) at time $T$ is then equal to $S_0 e^{rT}$ where $r$ is the annualized risk-free rate of interest. Further, let $K_0$ be the first strike price below the forward price ($K_0 \le F_0$). The forward value of the options portfolio in Theorem 40.1. has the following equality:

$e^{rT}\left[\int_{S_0}^{\infty}\frac{1}{K^2}C_T(K)dK + \int_{0}^{S_0}\frac{1}{K^2}P_T(K)dK\right]$
$=\left[(e^{rT}-1)-\left(\frac{F_0}{K_0}-1\right)-\ln\left(\frac{K_0}{S_0}\right)\right]$
$+ e^{rT}\left[\int_{K_0}^{\infty}\frac{1}{K^2}C_T(K)dK + \int_{0}^{K_0}\frac{1}{K^2}P_T(K)dK\right]. \quad (40.9)$

The proof of Corollary 40.1 is straightforward. By employing Taylor expansion with the remainder of ln(S_T) about the point K_0 we have

ln(S_T)=ln(K_0)+\frac{S_T-K_0}{K_0}+\int_{K_0}^{\infty}\frac{-1}{K^2}(S_T-K)^+dK
+\int_{0}^{K_0}\frac{-1}{K^2}(K-S_T)^+dK. \quad (40.10)

Substituting (40.3) into (40.10), take the risk-neutral expectation, and realize that E(R_T)=e^{rT}-1, we have equation (40.9). The first term of the right-hand side of equation (40.9) represents the adjustment between F_0, S_0 and K_0.

In summary, from mathematical applications to the relationship between a holding-period return (R_T) and log-return (r_T), we illustrate that without any diffusion assumption and model-specification, a portfolio of OTM options weighted inversely proportional to the square value of the strike price extracts the fair value of a linear combination of ex ante return-moments. Since the CBOE volatility index is calculated from the price of the identical option portfolio as (40.9), we explicitly prove, in the following section, that the VIX formulation is actually a moment-combination not a volatility measure in general. A generalized model-free volatility index is also proposed in Section 40.4.

## 40.4 The VIX and GVIX Indexes

This section reviews briefly the derivation of the CBOE volatility index, illustrates the validity problem of the VIX to serve as a volatility index, and develops a generic method to estimate ex ante volatility. We first note that although the revamped VIX index on September 2003 no longer relies on any option pricing model, as shown by Demeterfi et al. (1999), the derivation of the index still assumes that the stochastic process of returns to assets follows a specification of Geometric Brownian Motion (GBM) and Ito’s Lemma (IL):

$$\begin{cases} \frac{dS_t}{S_t} = \mu dt + \sigma dZ_t, \quad \text{and} \\
 d[\ln(S_t)] = \left(\mu - \frac{1}{2}\sigma^2\right) dt + \sigma dZ_t,\end{cases}$$ (40.11) (40.12)

where $Z_t$ is a Wiener process or Brownian motion, $\mu$ is a fixed drift, and $\sigma$ is a constant volatility, accordingly.¹ GBM and IL assume asset returns to be continuous and symmetrically distributed. Thus, higher orders of moments than the variance neither exist nor have impact on the return generating process. Since the log-return over a period of $T$ and its variance can be expressed by $r_T = \int_0^T d[\ln(S_t)]$ and $\int_0^T \sigma^2 dt$, respectively, the instantaneous volatility (variance) can then be calculated directly from simultaneous equations (40.11) and (40.12) as follows:

$$\mathbf{v} = \frac{1}{T} \int_0^T \sigma^2 dt = \frac{2}{T}\left[\int_0^T \frac{dS_t}{S_t} - r_T\right].$$ (40.13)

As also illustrated by Demeterfi et al. (1999), equation (40.13) indicates that the ex ante volatility is replicated by a portfolio of two positions: (1) a continuous rebalanced position of instantaneously long $\frac{1}{S_t}$ shares of the underlying asset worth one dollar, and (2) a short position in a contract that pays the logarithm of the total return at time $T$. Under the risk-neutral framework, $E\left(\int_0^T \frac{dS_t}{S_t}\right) = rT$, and $E(R_T) = e^{rT} - 1$, according to (40.5) and (40.13), the expected volatility can be expressed as

$$E(\mathbf{v}) = \sigma^2 = \frac{2}{T} \left\{ e^{rT} \left[\int_{S_0}^{\infty} \frac{1}{K^2} C_T(K) dK + \int_{0}^{S_0} \frac{1}{K^2} P_T(K) dK\right] - \left[(e^{rT} - 1) - rT\right]\right\}.$$ (40.14)

Consequently, the expected value of return-volatility, under the assumptions (40.11) and (40.12), can be extracted from the market price of a portfolio of out-of-the money options weighted inversely proportional to the square value of the strike prices. The third term of equation (40.14), expressed by $(e^{rT} - 1) - rT$, captures the difference between continuously compounding return and single compounding return over a period of $T$. This difference approaches zero, when $T$ is small.

By applying the results of Corollary 40.1 to equation (40.14), we have the VIX formulation, which is identical to that in Demeterfi et al. (1999), as follows:

$$VIX^2 = E(\mathbf{v}) = \frac{2}{T}\Big\{ rT - \Big(\frac{F_0}{K_0} -1\Big) - \ln\Big(\frac{K_0}{S_0}\Big) + e^{rT}\Big[ \int_{K_0}^{\infty} \frac{1}{K^2} C_T(K) dK + \int_{0}^{K_0} \frac{1}{K^2} P_T(K) dK \Big] \Big\}. \tag{40.15}$$

Therefore, independent of any option pricing model, the implied volatility is calculated explicitly from a set of out-of-the money option prices, current asset price, and risk-free rate of interest. Furthermore, applying Taylor's expansion of log function and ignoring terms higher than the second order, the terms preceding the integrals in (40.15) can be restated as

$$\Big[ rT - \Big(\frac{F_0}{K_0} -1\Big) - \ln\Big(\frac{K_0}{S_0}\Big) \Big] = \Big[ \ln\Big(\frac{F_0}{K_0}\Big) - \Big(\frac{F_0}{K_0} -1\Big) \Big] \approx -\frac{1}{2}\Big(\frac{F_0}{K_0} -1\Big)^2. \tag{40.16}$$

Consequently, identical to that shown in CBOE's VIX whitepaper, the volatility index can be calculated under the discrete framework as follows:

$$VIX^2 = \frac{2 e^{rT}}{T} \sum_i \frac{1}{K_i^2} Q(K_i) \Delta K_i - \frac{1}{T} \Big(\frac{F_0}{K_0} -1\Big)^2, \tag{40.17}$$

where $Q(K_i)$ is the midpoint of the bid-ask spread for the option (a call if $K_i > K_0$, a put if $K_i < K_0$, both call and put if $K_i = K_0$), and $\Delta K_i = \tfrac12(K_{i+1} - K_{i-1})$. The forward price is calculated from at-the-money options using put-call parity so that $F_0 = K_A + e^{rT}[C_T(K_A) - P_T(K_A)]$. Furthermore, CBOE calculates the VIX from an interpolation of two volatility indexes with respect to two expiration dates: the near-term $(T_1)$ and next-term $(T_2)$, respectively. Finally, by taking a weighted average of these two VIX measures, one obtains an annualized index (denoted as $\widehat{VIX_a}$) as follows:

$$VIX_a = \sqrt{\Big\{ \Big[ \frac{N(T_2)-N(30)}{N(T_2)-N(T_1)} \Big](T_1 \cdot VIX_1^2) + \Big[ \frac{N(30)-N(T_1)}{N(T_2)-N(T_1)} \Big](T_2 \cdot VIX_2^2) \Big\} \Big( \frac{N(365)}{N(30)} \Big)}, \tag{40.18}$$

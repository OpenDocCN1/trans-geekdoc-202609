Then, taking the expected value of both sides of equation (40.6) with some rearrangement, the expected value of return difference between $R_T$ and $r_T$ is equal to a linear combination of distributional moments:

$E(R_T) - E(r_T) = \frac{1}{2}E(r_T^2) + \frac{1}{6}E(r_T^3) + \frac{1}{24}E(r_T^4) + o[E(r_T^4)]. \quad (40.7)$

Interestingly, equation (40.7) shows that the expected holding-period return is the moment generating function of the log-returns. Consequently, when we incorporate (40.5) with (40.7), the forward value of an OTM option portfolio represents an *ex ante* moment-combination of log-returns. We demonstrate formally this important result in the following theorem:

# Theorem 40.1.

Let $C_T(K)$ and $P_T(K)$ be the European call and put options with an exercise price of $K$ and expiration date at $T$, respectively. Without imposing any structure on the underlying focusing process, the fair value of *ex ante* moment-combination of log-returns can be extracted from the market price of an OTM option portfolio with weight inversely proportional to square value of the strike price in that

$\left[\frac{1}{2}E(r_T^2) + \frac{1}{6}E(r_T^3) + \frac{1}{24}(r_T^4) + o[E(r_T^4)]\right]$ 
$= e^{rT}\left[\int_{S_0}^{\infty} \frac{1}{K^2}C_T(K)dK + \int_{0}^{S_0} \frac{1}{K^2}P_T(K)dK\right]. \quad (40.8)$

Theorem 40.1 highlights an essential connection between option premiums and market expectations about future return-moments. Specifically, the market price of a $(1/K^2)$ weighted OTM put/call option portfolio extracts the fair value of a linear combination of *ex ante* moments (e.g., variance, skewness, kurtosis, etc.). Next, we note that the VIX index was derived based on the concept of fair value of *future* variance and used *forward* price instead of current price of the underlying asset as a reference point to determine future OTM option payoffs of calls and puts. In addition, since it is almost certain, in practice, no option contract has a strike price exactly equal to the forward price, one could select the first strike price below the forward price as the reference price. In the next corollary, we adjust the fair value of the option portfolio by taking the forward price into consideration.

# Corollary 40.1.

Let $S_0$ be the current fair price of the underlying asset determined from ATM Put-Call parity, and the forward price ($F_0$) at time $T$ is then equal to $S_0 e^{rT}$ where $r$ is the annualized risk-free rate of interest. Further, let $K_0$ be the first strike price below the forward price ($K_0 \le F_0$). The forward value of the options portfolio in Theorem 40.1. has the following
bound of an European call option, $C_{\max}^E$, can be written as

$C_{\max}^E = \begin{cases} \dfrac{\mu^2(\mu-K)+\mu\sigma^2}{\mu^2+\sigma^2} & \text{if } K \le \dfrac{\mu^2+\sigma^2}{2\mu} \\ \dfrac12\left[\mu - K + \sqrt{(\mu - K)^2 + \sigma^2}\right] & \text{if } K > \dfrac{\mu^2+\sigma^2}{2\mu}. \end{cases}$ (24.19)

The important feature of this equation is that the upper bound of the call option depends only on the first two moments of the price distribution.

Zhang (1994) sharpens Lo (1987)'s bounds by using the assumption that the underlying stock price is continuously distributed. Assume the terminal stock price $S_T$ with cumulative distribution $F(S_T)$ satisfying the moment conditions

$\int_0^{\infty} dF(S_T)=1,\ \int_0^{\infty} S_T dF(S_T)=\mu,\ \int_0^{\infty} S_T^2 dF(S_T)=\mu^2+\sigma^2.$ (24.20)

Based on these constraints, the upper bound, $C_{\max}^E$, and lower bound, $C_{\min}^E$, of a European call option can be obtained as

$C_{\max}^E = \dfrac12\left[\mu - K + \sqrt{(\mu - K)^2 + \sigma^2}\right],$ 
$C_{\min}^E = \begin{cases} \mu - \dfrac{K\mu^2}{\mu^2+\sigma^2} & \text{if } K \le \mu + \dfrac{\sigma^2}{\mu} \\ 0 & \text{if } K > \mu + \dfrac{\sigma^2}{\mu}. \end{cases}$ (24.21)

Lee et al. (2002) further extend Zhang (1994)'s moments conditions by incorporating third and fourth moments to capture skewness and kurtosis characteristics of the underlying stock price since most empirical findings indicate that the distribution of stock return is often fat-tailed and excess kurtosis. The results for the upper bounds of a European call option of Lee et al. (2002) can be categorized into three parts

$C_{\max}^E = \begin{cases} \sigma\left(\dfrac{\eta\left(F_{S_T}(K)\right)^3}{a}\right)^{1/4} & \text{when } \mu = K \\ \kappa_4(\mu - K) & \text{when } \mu > K \\ \varpi_4(K - \mu) & \text{when } \mu < K, \end{cases}$ (24.22)

where $a = 1+\left(\dfrac{F_{S_T}(K)}{1-F_{S_T}(K)}\right)^3$ and $\eta$ is the kurtosis of the underlying asset price distribution. $F_{S_T}(K)$ denotes the cumulative function of any distribution for the underlying asset when $S_T$ equals the strike price $K$ at maturity; $\kappa_4$ the largest real root of the quadratic equation: the largest real root of
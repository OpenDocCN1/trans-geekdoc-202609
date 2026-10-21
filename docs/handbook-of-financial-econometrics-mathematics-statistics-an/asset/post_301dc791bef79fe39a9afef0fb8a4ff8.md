
Adding both sides of equations (7A.4) and (7A.5) using equation (7A.1) yields

$$
\frac{(R_C)^4}{(1-s)^3} + \frac{(R_P)^4}{s^3} \le \int_0^1 (x-K)^4 dF = \int_0^1 [(x-\mu)+(\mu-K)]^4 dF. \qquad(7A.6)
$$

Expanding equation (7A.6) and using equation (7A.1) yields

$$
\frac{(R_C)^4}{(1-s)^3} + \frac{(R_P)^4}{s^3} \le \eta\sigma^4 + 4k\sigma^3(\mu - K) + 6\sigma^2 (\mu - K)^2 + (\mu - K)^4. \qquad(7A.7)
$$

Taking expectation to both sides of equation (7A.7) yields

$$
R_P = R_C - (\mu - K). \qquad(7A.8)
$$

Multiplying both sides of equation (7A.7) by \(s^3 > 0\) and substituting equation (7A.8) into equation (7A.7) yields the following inequality

$$
a(R_C)^4 - 4(\mu - K)(R_C)^3 + 6(\mu - K)^2(R_C)^2 - 4(\mu - K)^3 R_C + (\mu - K)^4 \le s^3[\eta\sigma^4 + 4k\sigma^3(\mu - K) + 6\sigma^2(\mu - K)^2 + (\mu - K)^4], \qquad(7A.9)
$$

When \(\mu = K\), equation (7A.9) becomes \(a(R_C)^4 \le \eta s^3 \sigma^4\), which yields Proposition 1 immediately. When \(\mu > K\), multiplying both sides of equation (7A.9) by \(1/(K-\mu)^4\) and letting \(x = R_C/(\mu - K)\) yield

$$
a x^4 - 4x^3 + 6x^2 - 4x + b \le 0. \qquad(7A.10)
$$

When \(\mu < K\), multiplying both sides of equation (7A.9) by \(1/(K-\mu)^4\) and letting \(y = R_C/(K-\mu)\) yield

$$
a y^4 + 4y^3 + 6y^2 - 4y + b \le 0. \qquad(7A.11)
$$

As \(a > 1\) for all \(F(K)\), the polynomial \(a x^4 - 4x^3 + 6x^2 - 4x + b\) must have positive derivative at the largest root \(x_4\). Therefore, in order for \(a x^4 - 4x^3 + 6x^2 - 4x + b\) to be nonpositive, \(x\) must be smaller than \(x_4\), or \(x_4\) is the maximum \(x\) satisfying equation (7A.10). The same argument can be made for equation (7A.11).

### Proof of Proposition 7.4

Let \(P(x) = a x^4 - 4x^3 + 6x^2 - 4x + b\). Since \(x_4\) is the largest root of \(P(x)=0\) and \(a>1\) for all \(F(K)>0\), the polynomial \(P(x)\) must be positively sloped at \(x_4\); thus

$$
P'(x_4) = 4(ax_4^3 - 3x_4^2 + 3x_4 - 1) > 0. \qquad(7A.12)
$$

Let \(x_4 = \alpha(s)\) stand for the implicit function determined by \(P(x_4)=0\). Taking the derivative of both sides of \(P(x_4)=0\) with respect to \(s\) yields

$$
\frac{\partial\alpha(s)}{\partial s} = \frac{3s^2}{P'(x_4)}\left[\phi - \left(\frac{x_4}{1-s}\right)^4\right]. \qquad(7A.13)
$$

Letting the right-hand side of equation (7A.13) equal zero yields

$$
\alpha(s) = (1-s)\phi^{1/4}. \qquad(7A.14)
$$

Taking the derivative of both sides of equation (7A.13) and using equation (7A.14) yields

$$
\frac{\partial^2\alpha(s)}{\partial s^2} = -\frac{12s^2\phi}{(1-s)P'(x_4)}. \qquad(7A.15)
$$

Equation (7A.15) implies that the necessary and sufficient condition for \(x_4 = \alpha(s)\) to have a maximum (\(\bar R_{4C2}\) reaches maximum simultaneously as \(x_4 = \alpha(s)\) reaches maximum) is \(\phi > 0\). For positively skewed asset prices, \(\kappa > 0\), and \(\kappa > 0\) is sufficient for \(\phi > 0\) but not necessary. When \(\phi > 0\), the negativity of equation (7A.15) shows that \(x_4 = \alpha(s)\) reaches its maximum at the \(s\) that is determined by equation (7A.14). Equation (7A.14) is a function of \(s = F(K)\), it determines \(s\) as a function of \(\phi\), therefore, the optimal \(s = F(K)\) which yields the maximum \(x_4\) can be written as \(F(K) = G(\mu, \sigma, \eta, K)\).

$$
\begin{aligned}
E(Y^4;v,\lambda) ={}& (v+\lambda)^6 + 18(v+\lambda)^4(v+2\lambda)
 + 4(v+\lambda)^3[16(v+3\lambda)+3(v+2\lambda)]\\
&+(v+\lambda)^2[432(v+4\lambda)+96(v+3\lambda)+12(v+2\lambda)+48(v+2\lambda)^2]\\
&+640[(v+3\lambda)^2+(v+2\lambda)^2]+1440(v+\lambda)(v+4\lambda)\\
&+288(v+\lambda)(v+2\lambda)(v+3\lambda)+48(v+\lambda)(v+3\lambda)\\
&+2304(v+\lambda)(v+5\lambda)+288(v+2\lambda)(v+3\lambda)\\
&+288(v+\lambda)(v+4\lambda)+72(v+\lambda)(v+2\lambda)^2+3840(v+6\lambda).
\end{aligned}
$$

constructed by dichotomizing pairwise correlations. While the number of stocks becomes very large, the network can be approximated by an exponential random graph model under which the clustering coefficient of the market network is a natural candidate for measuring the collective correlation of the stock market. With a sample of S&P 500 components in the period from January 1996 to August 2009, we show that the clustering coefficient can be used as an alternative risk measure in addition to volatility. Furthermore, investigations on higher-order statistics also reveal the distinctions on the clustering effect between bear markets and bull markets.

## Keywords

- Collective correlation
- Correlation breakdown
- Dimension reduction
- Partition function
- Random graph

## 8.1 Introduction

It is relatively easy to measure the volatility of a stock market, and developments in volatility modeling have made significant progress in the past decades. In contrast to volatility, relatively few stylized facts about correlation have been commonly recognized. Especially, when a large number of assets are considered, it seems hard to give a description regarding their correlation structure. This paper proposes a network-based approach to measure the collective correlation of the market. The measure is statistically stable and incorporates the clustering effect in the market. Empirical investigation shows its potential to be used as a risk measure like the volatility index.

The most important feature about correlation is that it increases during crisis, usually referred to as correlation breakdown. In the past years, many articles have tried to address this issue, for example Karolyi and Stulz (1996), Longin and Solnik (2001), Forbes and Rigobon (2002), Ang and Chen (2002), Campbell et al. (2002), Dungey and Martin (2007). However, recent research by Campbell et al. (2007) attributes the phenomenon to be caused by fat tails. Beyond the bull/bear market scheme, Becker and Schmidt (2010) investigated some stock pairs and showed that the correlations are either constant or increasing in bull markets. In fact, correlations of asset prices have been known to be time-varying for a long time. The Dynamic Conditional Correlation (DCC) model proposed by Engle (2002) and many of its variants are commonly used in academia and industries for forecasting and filtering correlations. So it does not seem so ambitious to ask questions like: Is there some functional relation between correlations and volatility in a stock market? To answer such a question, a measure for the collective correlation should be built first. But what should it be?

The relation between correlations and market crash provides the key. Some researchers had suggested that large market crashes could be explained by the behavior of large participants, for example Gabaix et al. (2003) and Khandani and Lo (2007). That is, position changes of large participants may trigger a large market crash if all stocks are tightly bound. Under this context, tight integration of the market should be observed prior to the crash. On the other hand, recent theoretical developments for the mechanism of market crash have been concentrated on the role of liquidity (Brunnermeier and Pedersen, 2009; Huang and Wang, 2009). Especially, Brunnermeier and Pedersen analyzed the links between an asset’s market liquidity and traders’ funding liquidity, and they suggested that liquidity provider’s funding ability would be a critical driving force for all the effect of liquidity. Since liquidity providers basically execute contrarian trading strategies, their profitability and risk quite depend on the distribution of returns of assets (Conrad and Kaul, 1998). So the degree of integration of the market is closely related to the liquidity provider’s funding and thus the possibility of market crash.

Thus simply summarizing pairwise correlations is not enough for a collective correlation measure. Basically, the measure should be statistically stable even with a large number of stocks and short time series. And most importantly, it should be able to provide information about the tightness of the market or the deviation of the correlations from their “usual” level. In addition, it better be able to address the clustering effect that commonly exists in the financial markets.

Intuitively, analyzing the correlation matrix will help in gathering certain information. However, as pointed out by Laloux et al. (1999), the correlation matrices calculated with a large number of asset price returns are mainly composed of noises. Thus, dimension reduction is essential in dealing with the correlations. Araújo and Louçã (2007) proposed a procedure to denoise, determine the number of effective dimensions, and then compute the eigenvalues in the projected space as an index for market integration. They found that unusually high levels of the market structure index generally corresponded to major market crashes.

The eigenvalue approach over the (denoised) correlation matrix provides a macroscopic view of the stock market. It indexes simultaneously the extent and the amplitude of correlations for a large amount of stocks. However, it provides fewer insights for the microscopic phenomenon — how stocks interact with each other as they get closer toward a market crash.

An alternative approach is to dichotomize all the correlations with respect to some thresholds, then a network or an undirected graph can be obtained.

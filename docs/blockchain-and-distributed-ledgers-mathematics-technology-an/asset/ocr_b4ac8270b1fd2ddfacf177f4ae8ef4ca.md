# Chapter 10 Cryptocurrencies and Quantitative Finance | 295

![](bbox=[0.082, 0.093, 0.467, 0.313])

![](bbox=[0.503, 0.093, 0.918, 0.313])

![](bbox=[0.082, 0.331, 0.467, 0.553])

![](bbox=[0.503, 0.331, 0.918, 0.553])

Figure 10.1 BTC, ETH, XRP, and MRKT price series. Own graphics. Source: coinmarket-cap.com.

returns on cryptocurrencies, such as Bitcoin, Ethereum, XRP, and others, is particularly pronounced.

This section discusses possible candidate distributions for BTC; ETH, XRP, and MRKT returns are analyzed in Section 10.6. We study several distributions, starting with the standard normal distribution and going all the way to the generalized hyperbolic distribution, initially introduced by Ole Eilorf-Nielsen to describe various phenomena; we use Barackdorf-Nielsen (1997). We show that the latter distribution provides an adequate, if not perfect, fit to empirical data. Several papers discuss fitting of BTC and other crypto returns as well as their qualitative behavior; see Chan et al. (2017); Chu et al. (2015); Scaillet et al. (2020), among others.

We use kernel distribution as a nonparametric representation of a random variable's pdf to avoid making any a priori assumptions. A kernel distribution depends on random samples from an unknown distribution, a smoothing function, and a bandwidth value, which controls the output curve smoothness.
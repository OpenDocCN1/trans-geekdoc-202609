+   103.4.2 Implied volatility spread and past stock returns ........ 3633
+   103.4.3 Source of price pressure ................................. 3638
+   103.5 Conclusions ................................................ 3641
+   Bibliography ..................................................... 3642
+   Appendix 103A Exact Form of Black–Scholes Option Pricing Model ... 3644
+   Appendix 103B MATLAB Approach to Estimate Implied Volatility ..... 3644
+   Appendix 103C Upper and Lower Bounds for European Index Options .. 3645

# Abstract

Option prices tend to be correlated to past stock market returns due to market imperfections. This chapter discuss this issue in Chinese derivative market. Implied volatility spread based on pairs of options is constructed to measure the price pressure in the option market. By regressing the implied volatility spread on past stock returns, we find that past stock returns exert a strong influence on the pricing of index options. Specifically, the SSE 50 ETF calls are significantly overvalued relative to SSE 50 ETF puts after stock price increases, and vice versa. Moreover, we empirically validate that momentum effects in the underlying stock market are responsible for the price pressure. These findings are both economically and statistically significant and have important implications.

+   **Keywords**
+   Option price • Implied volatility spread • Past stock returns • Stock market momentum • Price pressure • Momentum factor.

# 103.1 Introduction

Providing a frictionless market free of arbitrage, the standard and celebrated option pricing model, the Black–Scholes model (hereafter B–S model, see Appendix A) proposed by Black and Scholes (1973), has gained wide popularity among market participants. As tested by a spectrum of empirical studies on the option pricing model (Cox and Ross 1976; Galai 1977; MacBeth and Merville 1979; Jerbi 2015), options are priced by disallowing arbitrage opportunities. When pricing a European option, only the following five factors are needed: the strike price, the current market price of the underlying stock, the risk-free interest rate, the remaining life of the option, and the volatility. In addition, no relation should exist between option prices and the past stock market momentum. However, due to market imperfections, including indivisibilities of securities, the unknown volatility, the existence of transaction costs and the rebalancing only at discrete intervals, additional factors such as investors’ risk aversion and perceptions about the fluctuation
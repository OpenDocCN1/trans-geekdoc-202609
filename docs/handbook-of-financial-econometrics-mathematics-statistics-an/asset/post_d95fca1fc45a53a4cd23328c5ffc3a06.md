
### Table 106.2 Details of sample companies.

| Security ID | Ticker | Company name | SIC code | Industry |
|-------------|--------|--------------|----------|----------|
| 101594 | AAPL | Apple Inc. | 3571 | Electronic Computers |
| 104533 | XOM | Exxon Mobil Corporation | 2911 | Petroleum Refining |
| 121812 | GOOGL | Google Inc. | 7370 | Computer Program |
| 107525 | MSFT | Microsoft Corporation | 7372 | Prepackaged Software |
| 106566 | JNJ | Johnson & Johnson | 2834 | Pharmaceutical Preparations |
| 111953 | WFC | Wells Fargo & Company | 6021 | National Commercial Banks |
| 105169 | GE | General Electric Company | 3600 | Electronic Equipment |
| 111860 | WMT | Wal-Mart Stores Inc. | 5331 | Variety Stores |
| 102968 | CVX | Chevron Corporation | 2911 | Petroleum Refining |
| 109224 | PG | The Procter & Gamble Company | 2840 | Cosmetics |
| 102936 | JPM | JP Morgan Chase & Co. | 6021 | National Commercial Banks |
| 111668 | VZ | Verizon Communications Inc. | 4813 | Radiotelephone Communications |
| 108948 | PFE | Pfizer Inc. | 2834 | Pharmaceutical Preparations |
| 106276 | IBM | International Business Machines Corporation | 3570 | Computer/Office Equipment |
| 109775 | T | AT&T, Inc. | 4813 | Radiotelephone Communications |

Note: Sample time spans from May, 2018 to June, 2018. 10-year Treasury rate is used as the risk-free rate. We calculated the continuously compounded annual risk-free interest rate accordingly, as the parameter r. We select actively traded option pairs to estimate implied volatility.

## 106.5.2 Cases from China — 50 ETF options

In Chinese financial market, there were no stock options in the exchange until February, 2015. Now, 50 ETF options are still the only traded options in Chinese market (Li et al., 2018). We choose the options which were traded actively on June 29, 2018 as our samples to compare the alternative methods of implied volatility estimation. (There were 120 call options trading on that day. We choose the most actively traded 10% options for implied volatility estimation.) The underlying asset price, i.e., 50 ETF was traded at 2.495 on June 29, 2018.

### Table 106.3: Implied volatility estimation for individual stock options: Comparison of alternative estimation methods.

| Ticker | IV-matlab | IV-approximation | IV-regression |
|---|---|---|---|
| AAPL | 0.357 | 0.320 | 0.426 |
| XOM | 0.196 | 0.178 | 0.124 |
| GOOGL | 0.369 | 0.378 | 0.315 |
| MSFT | 0.341 | 0.325 | 0.298 |
| JNJ | 0.206 | 0.198 | No positive solution |
| WFC | 0.287 | 0.269 | No positive solution |
| GE | 0.156 | 0.154 | 0.184 |
| WMT | 0.142 | 0.132 | 0.156 |
| CVX | 0.312 | 0.296 | 0.339 |
| PG | 0.186 | 0.172 | No positive solution |
| JPM | 0.175 | 0.186 | 0.169 |
| VZ | 0.182 | 0.190 | 0.232 |
| PFE | 0.202 | 0.197 | 0.167 |
| IBM | 0.433 | 0.428 | No positive solution |
| T | 0.192 | 0.186 | No positive solution |

### Table 106.4: Implied volatility estimation from ETF 50 call options.

| Option ticker | Exercise price | Expiration date | IV-matlab | IV-approximation |
|---|---|---|---|---|
| 10001361.SH | 2.9 | 2018/7/25 | 0.452 | 0.462 |
| 10001217.SH | 3.4 | 2018/9/26 | 0.463 | 0.478 |
| 10001216.SH | 3.3 | 2018/9/26 | 0.416 | 0.406 |
| 10001218.SH | 3.5 | 2018/9/26 | 0.427 | 0.415 |
| 10001219.SH | 3.6 | 2018/9/26 | 0.452 | 0.447 |
| 10001343.SH | 2.85 | 2018/7/25 | 0.406 | 0.429 |
| 10001215.SH | 3.2 | 2018/9/26 | 0.414 | 0.428 |
| 10001214.SH | 3.1 | 2018/9/26 | 0.392 | 0.406 |
| 10001213.SH | 3 | 2018/9/26 | 0.401 | 0.415 |
| 10001320.SH | 2.85 | 2018/12/26 | 0.422 | 0.429 |
| 10001342.SH | 2.8 | 2018/7/25 | 0.418 | 0.422 |
| 10001334.SH | 2.95 | 2018/12/26 | 0.372 | 0.388 |
| 10001321.SH | 2.9 | 2018/12/26 | 0.422 | 0.409 |
| 10001212.SH | 2.95 | 2018/9/26 | 0.398 | 0.402 |
| 10001225.SH | 3.3 | 2018/9/26 | 0.420 | 0.413 |
| 10001211.SH | 2.9 | 2018/9/26 | 0.376 | 0.399 |
| 10001395.SH | 2.3 | 2018/8/22 | 0.401 | 0.412 |
| 10001333.SH | 2.95 | 2018/12/26 | 0.388 | 0.396 |
| 10001316.SH | 2.65 | 2018/12/26 | 0.401 | 0.398 |
| 10001341.SH | 2.75 | 2018/7/25 | 0.387 | 0.397 |

## 106.6 Implied Volatility in Terms of CEV Model and Related Excel Program

One alternative to Black–Scholes is the constant elasticity of variance (CEV) model. In this section, we discuss how to use CEV model to forecast implied volatility and show related EXCEL program of this approach. Cox (1975) and Cox and Ross (1976) developed the “constant elasticity of variance (CEV) model” which incorporates an observed market phenomenon that the underlying asset variance tends to fall as the asset price increases (and vice versa). Schroder (1989) derives computation formula for CEV model. Schroder’s (1989) CEV formula is generally used to do empirically computation of either option value or implied variance. The advantage of CEV model is that it can describe the interrelationship between stock prices and its volatility.

```
dS = (r - q)S dt + δ S^α dZ
(106.83)
```

where r is the risk-free rate, q is the dividend yield, dZ is a Wiener process, δ is a volatility parameter, and α is a positive constant. The relationship between the instantaneous volatility of the asset return, σ(S, t), and parameters in CEV model can be represented as σ(S, t) = δ S^{α-1}. (106.84)

When α = 1, the CEV model is the geometric Brownian motion model we have been using up to now. When α < 1 , the volatility increases as the stock price decreases. This creates a probability distribution similar to that observed for equities with a heavy left tail and a less heavy right tail. When α > 1, the volatility increases as the stock price increases, giving a probability distribution with a heavy right tail and a less left tail. This corresponds to a volatility smile where the implied volatility is an increasing function of the strike price. This type of volatility smile is sometimes observed for options on futures.

```
C_t = \left\{ \begin{array}{ll} S_t e^{-q\tau}[1 - \chi^2(a, b + 2, c)] - K e^{-r\tau} \chi^2(c, b, a) & \text{when } \alpha < 1, \\ S_t e^{-q\tau}[1 - \chi^2(c, -b, a)] - K e^{-r\tau} \chi^2(a, 2 - b, c) & \text{when } \alpha > 1, \end{array} \right.
(106.85)
```

### Implied Variance Estimates for Black-Scholes and CEV OPM

where a = \frac{[Ke^{-(r-q)\tau}]^{2(1-\alpha)}}{(1-\alpha)^2 v^2}, b = \frac{1}{1-\alpha}, c = \frac{S_t^{2(1-\alpha)}}{(1-\alpha)^2 v^2}, v = \frac{\delta^2}{2(r-q)(\alpha-1)} and \chi^2(z,k,v) is the cumulative probability that a variable with a non-central \chi^2 distribution with non-centrality parameter v and k degrees of freedom is less than z. Hsu, Lin and Lee (2008) provided the detailed derivation of approximate formula for CEV model. Based on the approximated formula, CEV model can reduce computational and implementation costs rather than the complex models such as jump-diffusion stochastic volatility model. Therefore, CEV model with one more parameter than Black–Scholes–Merton Option Pricing Model (BSM) can be a better choice to improve the performance of predicting implied volatilities of index options (Singh and Ahmad 2011). The calculation process of \chi^2(z, k, v) value can be referred to Ding (1992). The complementary non-central chi-square distribution function can be expressed as an infinite double sum of gamma function, which can be referred to Benton and Krishnamoorthy (2003).

In order to price a European option under a CEV model, we need a non-central chi-square distribution. The following figure shows the charts of the non-central chi-square distribution with 5 degrees of freedom for non-central parameter \delta = 0,2,4,6.

![](img/31ee7e6fa5107b22bbf7960ec96106a1_3897_0.png)

Under the theoretical foundation of the CEV model in this chapter, we can write a call option price under CEV model. Following is the figure to do this:

![](img/31ee7e6fa5107b22bbf7960ec96106a1_3898_0.png)

Hence, the formula for CEV call option in B14 is

= IF(B9 < 1, B3 * EXP(-B6 * B8) * (1 − ncdchi(B11, B12 + 2, B13))
    − B4 * EXP(-B5 * B8) * ncdchi(B13, B12, B11),
    B3 * EXP(-B6 * B8) * (1 − ncdchi(B13, −B12, B11))
    − B4 * EXP(-B5 * B8) * ncdchi(B11, 2 − B12, B13)).

The ncdchi is the non-central chi-square cumulative distribution function. The function, IF, is used to separate the two conditions for this formula, 0 < α < 1 and α > 1.

We can write a function to price the call option under CEV model. Below is the code to accomplish this:

```
' CEV Call Option Value
Function CEVCall(S, X, r, q, T,sigma,alpha)
Dim v As Double
Dim aa As Double
Dim bb As Double
Dim cc As Double
```

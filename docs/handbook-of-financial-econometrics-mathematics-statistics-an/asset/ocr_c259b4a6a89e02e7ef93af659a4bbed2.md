+   (1) current price of the firm’s common stock ($S$);
+   (2) exercise price (or strike price) of the option ($X$);
+   (3) term to maturity in years ($T$);
+   (4) variance of the stock’s price ($\sigma^2$); and
+   (5) risk-free rate of interest ($r$).

The binomial option pricing model defined in equation (85.22) can be written as

$$C = S\left[ \sum_{k=m}^{T} \frac{T!}{k!(T-k)!} p'^k (1-p')^{T-k} \right]$$
$$- \frac{X}{(1+r)^T}\left[ \sum_{k=m}^{T} \frac{T!}{k!(T-k)!} p^k (1-p)^{T-k} \right] \tag{85.47}$$
$$= SB(T,p',m) - \frac{X}{(1+r)^T} B(T,p,m),$$
and $C = 0$ if $m > T$,

where $S$ is the Current price of the stock, $T$ is the term to maturity in years, $m$ is the minimum number of upward movements in stock price that is necessary for the option to terminate “in the money,” $p$ is the $\frac{R-d}{u-d}$ and $1-p = \frac{u-R}{u-d}$, $X$ is the option exercise price (or strike price), $R$ is the $1 + r = 1+$ risk-free rate of return, $u$ is the $1+$ percentage of price increase, $d$ is the $1+$ percentage of price decrease, $p' = (\frac{u}{R})p$, $B(n,p,m) = \sum_{k=m}^n C_k^n p^k (1-p)^{n-k}$.

By a form of the central limit theorem, we showed in Section 85.7 as $T \to \infty$, the option price $C$ converges to $C$ as

$$C = S N(d_1) - X R^{-T} N(d_2), \tag{85.48}$$

where

+   $C =$ Price of the call option,
+   $d_1 = \frac{\log\left(\frac{S}{X R^{-\tau}}\right)}{\sigma \sqrt{t}} + \frac{1}{2}\sqrt{t}$,
+   $d_2 = d_1 - \sigma \sqrt{t}$
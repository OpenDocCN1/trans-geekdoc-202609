firm has no debt, the decline of the stock price can make it more difficult for the firm to meet its fixed costs and thus increase volatility (Hull, 2002).

The CEV model assumes the diffusion process for the stock is

$$dS = \mu S dt + \delta S^{\beta/2} dz, \tag{51.1}$$

and the instantaneous variance of the percentage price change or return, $\sigma^2$, follows a deterministic relationship:

$$\sigma^2(S,t) = \delta^2 S^{(\beta-2)}, \tag{51.2}$$

where the elasticity of this variance with respect to the stock price equals $\beta$.

If $\beta = 2$, prices are lognormally distributed and the variance of returns is constant, which is the same as the well-known Black–Scholes model. If $\beta < 2$, the stock price is inversely related to the volatility. Cox originally restricted $0 \le \beta < 2$. Emanuel and MacBeth (1982) extended their analysis to the case $\beta > 2$ and discussed its properties. However, Jackwerth and Rubinstein (2001) found that typical values of the $\beta$ can fit market option prices well for the post-crash period only when $\beta < 0$, and they called the model with $\beta < 0$ the unrestricted CEV model.$^4$ In their empirical study, the difference of the pricing performance of restricted CEV model ($\beta \ge 0$) and BS model is not significant.

When $\beta < 2$, the non-dividend-paying CEV call pricing formula is as follows:

$$C = S \left[ \sum_{n=0}^{\infty} g(S'|n+1) G\left(K'|n+1+\frac{1}{2-\beta}\right) \right]$$

$$- K e^{-r\tau} \left[ \sum_{n=0}^{\infty} g\left(S'|n+1+\frac{1}{2-\beta}\right) G(K'|n+1) \right]. \tag{51.3}$$

When $\beta > 2$, the CEV call pricing formula is as follows:

$$C = S \left[ 1 - \sum_{n=0}^{\infty} g\left(S'|n+1+\frac{1}{2-\beta}\right) G(K'|n+1) \right]$$

$$- K e^{-r\tau} \left[ 1 - \sum_{n=0}^{\infty} g(S'|n+1) G\left(K'|n+1+\frac{1}{2-\beta}\right) \right], \tag{51.4}$$
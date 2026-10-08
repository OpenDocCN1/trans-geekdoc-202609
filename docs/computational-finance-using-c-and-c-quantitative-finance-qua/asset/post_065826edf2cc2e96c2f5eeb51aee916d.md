
# Problem 10

Let $S_t = S_0 \exp(\mu t + \sigma W_t)$ where $\mu$ and $\sigma$ are constants.

- (a) Show by Ito's lemma that

```
$dS_t = \left(\mu + \frac{\sigma^2}{2}\right)S_t dt + \sigma S_t dW_t$
```

- (b) Show that

```
$E[S_t] - E[S_0] = \left(\mu + \frac{\sigma^2}{2}\right) \int_{\tau=0}^t E[S(\tau)] d\tau$
```

- (c) Show that

```
$E[S_t] = S_0 \exp(\mu t + \frac{\sigma^2}{2}t)$
```

## 10(a)

Let $\phi = S_0 \exp(\mu t + \sigma W_t)$. Using Ito's formula:

```
$d\phi = \frac{\partial\phi}{\partial t}dt + \frac{\partial\phi}{\partial W_t}dW_t + \frac{1}{2}\frac{\partial^2\phi}{\partial W_t^2}E[(dW_t)^2]$
```

So

```
$d\phi = \mu \phi dt + \sigma \phi dW_t + \frac{1}{2}\phi \sigma^2 dt$
```

where we have used $\frac{\partial^2\phi}{\partial W_t^2} = \phi \sigma^2$ and $E[(dW_t)^2] = dt$.

Therefore

```
$dS_t = \left(\mu + \frac{1}{2}\sigma^2\right)S_t dt + \sigma S_t dW_t$
```

## 10(b)

From part (a) we have

```
$\int_{\tau=0}^t dS_\tau = \left(\mu + \frac{1}{2}\sigma^2\right) \int_{\tau=0}^t S_\tau d\tau + \int_{\tau=0}^t \sigma S_\tau dW_\tau$
```

Therefore

```
$S_t - S_0 = \left(\mu + \frac{1}{2}\sigma^2\right) \int_{\tau=0}^t S_\tau d\tau + \sigma \int_{\tau=0}^t S_\tau dW_\tau$
```

Taking expectations we have

```
$E[S_t] - E[S_0] = \left(\mu + \frac{1}{2}\sigma^2\right) E\left[\int_{\tau=0}^t S_\tau d\tau\right] + \sigma E\left[\int_{\tau=0}^t S_\tau dW_\tau\right]$
```

Using the fact that:

```
$E\left[\int_{\tau=0}^{t'} f(\tau) dW_{\tau}\right] = 0$
```

and Fubini's theorem:

```
$E\left[\int_{\tau}^{t'} S(\tau) d\tau\right] = \int_{\tau}^{t'} E[S(\tau)] d\tau$
```

we thus finally obtain:

```
$E[S_t] - E[S_0] = \left(\mu + \frac{1}{2}\sigma^2\right)\int_{\tau=0}^{t'} E[S_{\tau}] d\tau$
```

## 10(c)

From part (a) we know:

```
$dS_t = \left(\mu + \frac{1}{2}\sigma^2\right)S_t dt + S_t\sigma dW_t$
```

Therefore

```
$d(\log(S_t)) = \left(\mu + \frac{1}{2}\sigma^2\right)dt + \sigma dW_t$
```

```
$\int_{\tau=0}^{t} d(\log(S_{\tau})) = \left(\mu + \frac{1}{2}\sigma^2\right)\int_{\tau=0}^{t} + \sigma\int_{\tau=0}^{t} dW_{\tau}$
```

So

```
$$\log(S_t) - \log(S_0) = \left(\mu + \frac{1}{2}\sigma^2\right)t + \sigma\int_{\tau=0}^{t} dW_{\tau}$$
```

Taking expectations we obtain:

```
$E[\log(S_t)] - E[\log(S_0)] = \left(\mu + \frac{1}{2}\sigma^2\right)t + E\left[\int_{\tau=0}^{t} dW_{\tau}\right]$
```

Since

```
$E[\int_{\tau=0}^{t} dW_{\tau}] = 0 \quad \text{and} \quad E[S_0] = S_0$
```

we have:

```
$$\log\left(\frac{E[S_t]}{S_0}\right) = \left(\mu + \frac{1}{2}\sigma^2\right)t$$
```

which yields:

```
$E[S_t] = S_0 \exp\left(\mu + \frac{1}{2}\sigma^2\right)t$$
```

## Problem 11

$\Phi = X_t Y_t$. From Ito's formula we obtain:

```
$d\Phi = \frac{\partial\Phi}{\partial X_t} dX_t + \frac{\partial\Phi}{\partial Y_t} dY_t + \frac{1}{2}\frac{\partial^2\Phi}{\partial X_t^2}(dX_t)^2 + \frac{1}{2}\frac{\partial^2\Phi}{\partial Y_t^2}(dY_t)^2 + \frac{\partial^2\Phi}{\partial X_t \partial Y_t}dX_t dY_t$
```

Now

$\frac{\partial\Phi}{\partial X_t} = Y_t$, $\frac{\partial\Phi}{\partial Y_t} = X_t$, $\frac{\partial^2\Phi}{\partial X_t^2} = 0$, and $\frac{\partial^2\Phi}{\partial Y_t^2} = 0$, $\frac{\partial^2\Phi}{\partial X_t \partial Y_t} = 1$. We thus obtain:

```
$d\Phi = Y_t dX_t + X_t dY_t + dX_t dY_t$
```

Using

```
$\int_{\tau=0}^t d(X_\tau Y_\tau) = \int_{\tau=0}^t Y_\tau dX_\tau + \int_{\tau=0}^t X_\tau dY_\tau + \int_{\tau=0}^t dX_\tau dY_\tau$
```

have

```
$X_t Y_t - X_0 Y_0 = \int_{\tau=0}^t Y_\tau dX_\tau + \int_{\tau=0}^t X_\tau dY_\tau + \int_{\tau=0}^t dX_\tau dY_\tau$
```

## References

- Abramowitz, M., and Stegun, I.A. (1968). *Handbook of Mathematical Functions*. Dover Publications.
- Bachelier, L. (1900). Théorie de la finance. *Annales scientifiques de l'École Normale Supérieure*, 17:1–86.
- Barone, J., and Whaley, R.E. (1987). Efficient Approximation of Option Values. *Journal of Finance*, 42(2):301–320.
- Barra, J., and Martineau, D. (1995). Numerical Valuation of High Dimensional Securities. *Journal of Quantitative Analysis*, 30:383–405.
- Baxter, M., and Rennie, A. (1996). *Financial Calculus: An Introduction to Derivative Pricing*. Cambridge University Press.
- Black, F. (1973). Fact in the Use of Options. *Journal of Political Economy*, 81:637–657.
- Boyle, P.E., and Tian, Y. (1998). An Explicit Finite Difference Approach to the Pricing of Barrier Options. *Applied Mathematics*, 5:17–43.
- Boyle, G.P., and Miller, H.D. (1958). A Note on the Generation of Normal Deviates. *Annals of Mathematics*, 29:610–611.
- Boyle, P.E., Evnine, J., and Gibbs, S. (1989). Numerical Evaluation of Multivariate Contingent Claims. *Journal of Management Studies*, 2(2):241–250.
- Boyle, P.P., Brodie, M., and Glasserman, P. (1997). Monte Carlo Methods for Pricing. *Journal of Economic Dynamics and Control*, 21:1267–1321.
- Big, D., and Mercurio, F. (2001). Interest Rate Models – Theory and Practice: With Inflation and Credit. Springer-Verlag.
- Broadie, M., and DeTemple, J. (1996). American Option Valuation: New Bounds, and a Comparison of Existing Methods. *Review of Financial Studies*, 9(4):1211–1250.
- Broadie, M., and Glasserman, P. (1997). Pricing American-Style Simulation. *Journal of Economic Dynamics and Control*, 21:1323–1352.
- Brotcher-Ratcliffe, R. (1994). Monte Carlo Pricing. *Risk*, 7(12):53–58.
- Callisish, R.E., Morokoff, W., and Owen, A. (1997). Valuation of Mortgage-Backed Securities with Brownian Bridges to Reduce Effective Dimension. *The Journal of Computational Finance*, 1(1):27–46.
- Cox, D.R., and Miller, H.D. (1965). *The Theory of Stochastic Processes*. Methuen & Co Ltd.
- Cox, J.C., Ross, S.A., and Rubinstein, M. (1979). Option Pricing: A Simplified Approach. *Journal of Financial Economics*, 7:229–263.
- Crank, J., and Nicolson, P. (1947). A Practical Method for Numerical Evaluation of Partial Differential Equations of the Heat Type. *Proceedings of the Cambridge Philosophical Society*, 43:50–67.
- Einstein, A. (1905). On the Movement of Small Particles Suspended in a Stationary Fluid by the Molecular-Kinetic Theory of Heat. Annalen der Physik, 17.
- Evans, M., Hastings, N., and Peacock, B. (2000). Statistical Distributions, Third Edition. Wiley.
- Garman, M.B., and Kohlhagen, S.W. (1983). Foreign Currency Option Values. *Journal of International Finance and Money*, 2:231–237.
- Geske, R. (1979). A Note on an Analytic Valuation Formula for Unprotected American Options on Stocks with Known Dividends. *Journal of Econometrics*, 7:375–380.
- Geske, R., and Johnson, H.E. (1984). The American Put Valued Analytically. *Journal of Finance*, 39:1511–1524.
- Golub, G.H., and Van Loan, C.F. (1988). Computing the Nearest Correlation Matrix. Springer-Verlag.
- Grimmett, G., and Welsh, D. (1996). Probability: An Introduction. Oxford Science.
- Higham, N.J. (2002). Matrix Computation – A Problem from *IMA Journal of Numerical Analysis*, 22:329–343.
- Karrad, B., and Ritchen, P. (1991). Multinomial Approximating Models for State Variables. *Management Science*, 37:1640–1652.

exploits cross-sectional differences in expected returns. We consider a portfolio with weights as in (3.3), but with a different scaling factor:

```
\hat{\omega} = \frac{1}{\sqrt{\hat{\mu}' \hat{\mu}}} \hat{\mu}. \tag{3.8}
```

Multiplying estimated expected returns with the ratio 1/\sqrt{\hat{\mu}' \hat{\mu}} ensures that the weights have an interpretable scale by fixing the sum of squared weights to 1. For the calculations we do here, this is more convenient than scaling by the sum of absolute portfolio weights, although the portfolio then does not have the interpretation of being exactly half a dollar long and half a dollar short.

Given our assumption here that returns are cross-sectionally uncorrelated, the weights of the mean-variance efficient portfolio—i.e., the portfolio that maximizes the Sharpe ratio of mean return to return standard deviation—are proportional to the vector of expected returns.³ Therefore, in this special case, the weights \hat{\omega} also represent the (estimated) weights of the mean-variance efficient portfolio.

The portfolio with weights \hat{\omega} earns a per-period return out-of-sample (i.e., for periods t > \tau) with expected value and variance of

```
\mathbb{E}[\hat{\omega}' \hat{r}_v | \hat{\omega}] \approx \frac{\mu' \mu}{\sqrt{\mu' \mu + \frac{N}{\tau}\sigma^2}}, \quad \text{var}(\hat{\omega}' \hat{r}_v | \hat{\omega}) = \frac{1}{T - \tau} \sigma^2. \tag{3.9}
```

Therefore, the squared Sharpe ratio in the validation period is

```
\frac{(\mathbb{E}[\hat{\omega}' \hat{r}_v | \hat{\omega}])^2}{\text{var}(\hat{\omega}' \hat{r}_v | \hat{\omega})} \approx \left(\frac{T - \tau}{\sigma^2}\right) \frac{(\mu' \mu)^2}{\mu' \mu + \frac{N}{\tau}\sigma^2}. \tag{3.10}
```

In this case, with a diagonal covariance matrix, the squared Sharpe ratio is approximately proportional to the squared expected return of the portfolio in (3.9). So we can focus our discussion for now just on the expected return in (3.9).

Comparing (3.9) with (3.7), we see that, just like the OOS R², the expected portfolio return is negatively affected by higher estimation error: the expected return is increasing in the training data set size τ. The reason is that when the training data set is smaller and hence estimation error is

³The mean-variance efficient portfolio has weights proportional to Σ⁻¹ μ. If one rescales the weights such that their sum of squares is unity, the weights are \frac{1}{\sqrt{\mu' Σ⁻² μ}} Σ⁻¹ μ. This portfolio achieves the maximum Sharpe ratio, i.e., the maximum ratio of expected portfolio excess return to portfolio return standard deviation. We will come back to this special portfolio repeatedly throughout this book.
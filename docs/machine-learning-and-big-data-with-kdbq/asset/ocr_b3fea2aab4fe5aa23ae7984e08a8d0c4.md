# 248 DATA SCIENCE

. The subsequent section considers a more appropriate tool to decide whether adding variables have a significant impact on the variance improvement.

We provide a function that implements the adjusted $R^2$ defined in the previous display as:

```
.quant.ols.rSquaredAdj[y;yHat;p]
// y -- the underlying data
// yHat -- the model
// p -- the number of explanatory variables excluding constant
// adjusted Total Sum of Squares
adjTSS:(1.0%(count[y]-1))*sum t*y-avg[y]
// Adjusted Sum of Squares
adjRSS:(1.0%(count[y]-1-p))*sum t*y-yHat
// adjusted R squared
:(adjTSS-adjRSS)%
;
```

The example under consideration shows very high adjusted $R^2:

```
.quant.ols.rSquaredAdj[y; sum beta+x; count[beta]]
```

0.998931

The adjusted value is close to the unadjusted value and very high. The estimated model explains much of the variance; the unexplained variance is white noise without any pattern.

# 13.7 RELATIONSHIP WITH MAXIMUM LIKELIHOOD ESTIMATION AND AIC WITH SMALL SAMPLE CORRECTION

Us link the OLS procedure to the maximum likelihood estimation. This is interesting theoretically well as useful from a practical perspective. It allows us to define additional criteria to assess the quality of the fit. If $\epsilon_1, \dots, \epsilon_n \sim N(0, \sigma^2)$. Then, taking $\mathbf{x}_1, \dots, \mathbf{x}_n$ as data, the observations have density functions $\varphi(y_i; \beta, \sigma^2)$, and the likelihood of $\beta$ and $\sigma$, based on the sample,

$$\mathcal{L} = \prod_{i=1}^n \varphi(y_i; \mathbf{x}_i^T, \beta, \sigma^2) = (2\pi\sigma^2)^{-n/2} \exp \left\{-\frac{1}{2\sigma^2}(\mathbf{y}-\mathbf{X}\beta)^T(\mathbf{y}-\mathbf{X}\beta)\right\}$. (13.59)

It is convenient to take the logarithms and we obtain the log-likelihood

```
$$\ln(\mathcal{L}) = -\frac{n}{2}\ln(2\pi) - \frac{n}{2}\ln(\sigma^2) - \frac{1}{2\sigma^2}(\mathbf{y}-\mathbf{X}\beta)^T(\mathbf{y}-\mathbf{X}\beta)$ (13.60)
```

```
$=-\frac{n}{2}\ln(2\pi) - \frac{n}{2}\ln(\sigma^2) - \frac{1}{2\sigma^2}RSS.$ (13.61)
```
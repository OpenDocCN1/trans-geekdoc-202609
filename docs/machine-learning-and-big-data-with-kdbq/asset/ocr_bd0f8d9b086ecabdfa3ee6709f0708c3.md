# Time Series Econometrics

The OLS estimator of the parameters $\Phi = (\hat{\Phi}_1, \hat{\Phi}_2, \dots, \hat{\Phi}_p)'$ solves:

```
$\Phi = (Y'Y)^{-1}Y'X, \quad (14.6)$
```

and the variance as:

```
$\hat{\sigma}^2 = \frac{1}{n-p} \sum_{t=p+1}^n (X_t - \hat{c} - \Phi_1 X_{t-1} - \dots - \Phi_p X_{t-p})^2, \quad (14.7)$
```

A quant. the OLS estimator of $AR(p)$ models is given by the function .quantQ.tsestARP[data;p] explained in the second part of the chapter.

# 14.1.2.4 Example

To empirically verify the convergence of the implementation of the OLS estimator, we estimate 100,000 simulated values of an $AR(2)$ model:

```
$X_t = 0.4X_{t-1} + 0.3X_{t-2} + \epsilon_t,$
```

with $\epsilon_t \sim N(0, 1)$:

```
simData.quantQ.tsimAR(0.4;0.3;100000).quantQ.sim.genBoxMuller[]; .quantQ.tsestARP[simData;2]
```

The estimated parameters $\Phi = (\hat{\Phi}_1, \hat{\Phi}_2)$

```
$0.002898714 . 0.3967857 . 0.3017881$
```

are close to $c = 0, \Phi_1 = 0.4$ and $\Phi_2 = 0.3$.

# 14.1.2.5 Maximum Likelihood Estimator

Assuming the innovation $\epsilon_t \sim N(0, \sigma^2)$ are independent, the likelihood function is:

```
$l = -\frac{n}{2\sigma^2} \sum_{t=p+1}^n (X_t - \Phi_1 X_{t-1} - \dots - \Phi_p X_{t-p})^2$
```

Maximising $l$ means minimising $\sum_{t=p+1}^n (X_t - \Phi_1 X_{t-1} - \dots - \Phi_p X_{t-p})^2$ and the method is equivalent to the least squares estimator (14.6).

# 14.1.2.6 Yule-Walker Technique

Starting with the $AR(p)$ process $X_t = \Phi_1 X_{t-1} + \dots + \Phi_p X_{t-p} + \epsilon_t$, we multiply both sides of the equation by $X_{t-h}, h > 0$ and take expectation

```
$E[X_t X_{t-h}] = \Phi_1 E[X_{t-1} X_{t-h}] + \Phi_2 E[X_{t-2} X_{t-h}] + \dots + \Phi_p E[X_{t-p} X_{t-h}] + E[\epsilon_t X_{t-h}]. \quad (14.8)$
```
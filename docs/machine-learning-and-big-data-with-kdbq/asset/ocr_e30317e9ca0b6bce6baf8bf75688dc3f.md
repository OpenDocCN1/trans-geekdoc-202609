# 270 DATA SCIENCE

Let us denote the autocovariance of h $E[X_t X_{t-h}]$ as $\gamma(h)$. The equation (14.8) can be rewritten as:

$\gamma(h) = \Phi_1\gamma(h-1) + \dots + \Phi_p\gamma(h-p).$

Dividing both by the variance $\gamma(0)$ and denoting the autocorrelation of h $\rho(h)$ we get:

$\rho(h) = \Phi_1\rho(h-1) + \dots + \Phi_p\rho(h-p). \quad (14.9)$

Since $\gamma(h) = \frac{E[X_t X_{t-h}]}{E[X_t^2]} = \gamma(-h)\frac{E[X_t X_{t+h}]}{E[X_t^2]}, h = 1, \dots, p:$

```
$$\begin{cases} \rho(1) = \Phi_1\rho(0) + \dots + \Phi_p\rho(0) \ \dots \ \rho(p) = \Phi_1\rho(p-1) + \dots + \Phi_p\rho(0) \end{cases} \quad (14.10)$
```

are called the Yule-Walker equations. If $\rho(h), h=1, \dots, p$ are known, $\Phi = [\Phi_1, \dots, \Phi_p]^T$ are obtained by solving the system of equations $p$. Let $E[X_t]=0, \gamma(0)=\Phi_1\gamma(1) + \dots + \Phi_p\gamma(p) + \sigma^2$, hence:

$\sigma^2 = \gamma(0) - \Phi_1\gamma(1) - \dots - \Phi_p\gamma(p). \quad (14.11)$

In general, $\rho(h)$ are unknown and need to be estimated from the sample. Denoting the sample autocorrelation $\hat{ho}(h) = \frac{\hat{\gamma}(h)}{\hat{\gamma}(0)}$ where $\hat{\gamma}(h) = \frac{1}{n}\sum_{t=1}^n(X_t-\ar{X})(X_{t-h}-\bar{X}),$

```
$$\begin{cases} \hat{ho}(1) & \hat{ho}(0) & \hat{ho}(0) & \hat{ho}(p-1) & \Phi_1 \ \hat{ho}(2) & \hat{ho}(1) & \hat{ho}(0) & \hat{ho}(p-2) & \Phi_2 \ \dots & \dots & \dots & \dots & \dots \ \hat{ho}(p) & \hat{ho}(p-1) & \hat{ho}(p-2) & \hat{ho}(0) & \Phi_p \end{cases} \quad (14.12)$
```

The estimator of $\Phi = [\Phi_1, \dots, \Phi_p]^T$ is $\Phi_p^{-1}r_p$. As $R$ is a Toeplitz matrix with non-diagonal $\rho(0)=1$, the Durbin-Levinson algorithm is used. Let us rewrite the AR(p) process with a double suffix:

$\X_t = \Phi_1 X_{t-1} + \Phi_{2,p}X_{t-2} + \dots + \Phi_{p,p}X_{t-p} + \epsilon_t.$

Starting recursively with $p=1, 2, \dots ,$ we have:

For $p=1, \Phi_{1,1} = \frac{\hat{\gamma}(1)}{\hat{\gamma}(0)}(1-\\hat{\sigma}_{1,1}^2).$

For $p=2, \Phi_{2,2} = \frac{\hat{\gamma}(2)-\Phi_{1,1}\hat{\gamma}(1)}{\hat{\gamma}(0)}$ and $\Phi_{2,1} = \Phi_{1,1}-\Phi_{2,2}$ with $\hat{\sigma}_{2,2}^2 = \hat{\sigma}_{1,1}^2(1-\\hat{\sigma}_{2,2}^2),$

For any $p, \Phi_{p,p} = \frac{\hat{\gamma}(p)-\sum_{j=1}^{p-1}\Phi_{p,j}\hat{\gamma}(p-j)}{\hat{\gamma}(0)}$ and

```
$$\begin{cases} \Phi_{p,1} & \Phi_{p-1,1} \ \dots \ \Phi_{p,p} & \Phi_{p-1,p-1} \end{cases} = \Phi_{p,p} \begin{bmatrix} \Phi_{p-1,1} \ \dots \ \Phi_{p-1,p-1} \end{bmatrix} \dots \end{bmatrix}$
```

$\hat{\sigma}_{p,p}^2 = \hat{\sigma}_{p-1}^2(1-\\hat{\sigma}_{p,p}^2),$
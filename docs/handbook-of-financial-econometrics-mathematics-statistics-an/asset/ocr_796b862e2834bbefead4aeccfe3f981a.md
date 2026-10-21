The estimation of $(\alpha, \delta), \hat{\beta}$, is

$$\hat{\beta} = (x_h' x_h)^{-1} x_h' y_h, \quad \text{var}(\hat{\beta}) = (x_h' x_h)^{-1} \sigma_v^2 (1 - \rho^2)$$

The posterior of $(\alpha, \delta)$ is

$$\begin{pmatrix} \alpha \\ \delta \end{pmatrix} \mid \hat{\beta}, d, \rho, \sigma_v \sim N(\tilde{\beta}, \tilde{V})$$

where $\tilde{V} = \text{var}(\hat{\beta})^{-1} + (\sigma_{\beta_0}^2)^{-1}$ and $\tilde{\beta} = \tilde{V}\big(\text{var}(\hat{\beta})^{-1} \hat{\beta} + (\sigma_{\beta_0}^2)^{-1} \beta_0\big)$.

The posterior distribution of $d$ can be derived in a similar fashion. From the relation between $u_t$ and $\varepsilon_t$, we have

$$\varepsilon_t = \frac{\rho}{\sigma_v} u_t + b_{1t},$$

where $u_t$ and $b_{1t}$ are independent and $b_{1t} \sim N(0, 1 - \rho^2)$.

Since we have $\tilde{r}_t = d + \sqrt{h_{t-1}} \varepsilon_t$, we plug in the relation of $u_t$ and $\varepsilon_t$. The equation can be written as

$$\left( \frac{\tilde{r}_t}{\sqrt{h_{t-1}}} - \frac{\rho}{\sigma_v} u_t \right) = \frac{1}{\sqrt{h_{t-1}}} d + b_{1t}.$$

Let

$$y_r = \frac{\tilde{r}_t}{\sqrt{h_{t-1}}} - \frac{\rho}{\sigma_v} u_t \quad \text{and} \quad x_r = \frac{1}{\sqrt{h_{t-1}}}$$

then $\hat{d} = (x_r' x_r)^{-1} x_r' y_r$, $\text{var}(\hat{d}) = (x_r' x_r)^{-1} (1 - \rho^2)$.

Assuming a normal prior for $d$ with mean $d_0$ and variance $\sigma_{d_0}^2$, then we have a posterior distribution $d \sim N(\tilde{d}, \tilde{V}_d)$, where $\tilde{V}_d = \text{var}(\hat{d})^{-1} + (\sigma_{d_0}^2)^{-1}$ and $\tilde{d} = \tilde{V}_d\big(\text{var}(\hat{d})^{-1} \hat{d} + (\sigma_{d_0}^2)^{-1} d_0\big)$.

We use a single move sampler to update $h_t$. That is, given other state variables and parameters at time $t$, the posterior of volatility $h_t$ is derived. As time shifts forward, we continue to update the remaining volatility state variables. The random walk Metropolis algorithm is used to sample the posterior of $h_t$. Note that there is a jump component in the state equation, and we are updating $h_t$ while taking the jump size as given. We rewrite equation (52.4) as follows:

$$\tilde{r}_t \equiv r_t - \xi_t^r J_t^r = d + \sqrt{h_{t-1}} \varepsilon_t$$

$$\tilde{h}_t \equiv h_t - \xi_t^v J_t^v = \alpha + \delta h_{t-1} + \sqrt{h_{t-1}} u_t,$$

where $\tilde{h}_t \equiv h_t - \xi_t^v J_t^v$ is the non-jump-related part of $h_t$.
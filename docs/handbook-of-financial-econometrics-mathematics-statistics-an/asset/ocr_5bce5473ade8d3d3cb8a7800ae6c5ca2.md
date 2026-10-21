where $u_t = (h_t - \alpha - \delta h_{t-1} - \xi_t^v J_t^v)/\sqrt{h_{t-1}}$. $J_t^r$ follows a Bernoulli distribution with the probability of $p_t^r$ equaling one. It is easy to see that $\frac{p_t^r}{1-p_t^r}=O_t^r$, so $p_t^r = \frac{O_t^r}{1+O_t^r}$.

We choose Beta as the prior of $\lambda_r$; that is, $\text{prior}(\lambda_r)=\text{Beta}(a,b)\propto \lambda_r^{a-1}(1-\lambda_r)^{b-1}$. The posterior is $p(\lambda_r|J_r)\propto p(J_r|\lambda_r)\text{prior}(\lambda_r)\propto[\lambda_r^{\sum_{t=1}^T J_t}(1-\lambda_r)^{T-\sum_{t=1}^T J_t}]\lambda_r^{a-1}(1-\lambda_r)^{b-1}\propto\lambda_r^{a^*}(1-\lambda_r)^{b^*}$, where $a^*=a+\sum_{t=1}^T J_t-1$, $b^*=b+T-\sum_{t=1}^T J_t-1$.

The posteriors of $u_r$ and $\sigma_r^2$ can be derived by following the standard regression theory, and therefore is omitted. The posterior of a jump in the state equation can be derived with a similar method.

The prior of $u_v$ is assumed to follow $IG(\varphi_v,\lambda_v)$. The posterior can thus be written as

$p(u_v|\xi_{t|t=1}^v)\propto p(\xi_{t|t=1}^v|u_v)\text{prior}(u_v)$

$\propto u_v^{I}\exp\!\left(-\frac{1}{u_v}(\xi_{i1}^v+\xi_{i2}^v+\cdots+\xi_{iI}^v)\right)u_v^{-(\varphi_v+1)}\exp\!\left(-\frac{\lambda_v}{u_v}\right)$

$\propto u_v^{-(\varphi_v+I+1)}\exp\!\left(-\frac{\lambda_v+\sum_{t=1}^I\xi_{it}^v}{u_v}\right)$.

Thus, the posterior of $u_v$ follows the inverse gamma distribution, $IG(\varphi_v+I,\lambda_v+\sum_{t=1}^I\xi_{it}^v)$.

# 52.3 Empirical Results

Our dataset is the daily change rates of the Thai baht from January 10, 1996 to October 12, 2003, totaling 1,877 observations. Our sample periods cover the Asian financial crisis, which allows us to exploit various jump models to study episodes of market crashes. Figure 52.1 plots the daily change rate of the Thai baht; the volatility of different periods is dramatically different. For example, periods before May 1997 seldom have daily change rates of more than 1%, but this becomes very common in later periods. Extreme values also play an important role in our time series; some data points are significantly larger than others.

We begin our empirical investigation of the Thai baht jump behavior with Merton’s (1976a, 1976b) independent jump model.

$r_{t+1}=u+\sigma\varepsilon_{t+1}+\zeta_{t+1}J_{t+1}$,

where $\varepsilon_{t+1}$ follows standard normal distribution and $\zeta_{t+1}$ is a normal random variable with mean $\zeta_0$ and variance $\sigma_\zeta^2$. Here, $\zeta_{t+1}$ represents the observations
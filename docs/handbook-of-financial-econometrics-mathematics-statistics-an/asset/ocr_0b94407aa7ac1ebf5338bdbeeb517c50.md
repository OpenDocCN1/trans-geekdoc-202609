Building on the work of Kreps and Porteus (1978), Epstein and Zin (1989, 1991) and Weil (1989) develop a more flexible version of the basic power utility model. The objective function is

$$U_t = \left\{ (1 - \delta) C_t^{\frac{1-\gamma}{\theta}} + \delta \left(E_t U_{t+1}^{1-\gamma}\right)^{\frac{1}{\theta}} \right\}^{\frac{\theta}{1-\gamma}}. \tag{122.31}$$

Here $\gamma$ is the coefficient of relative risk aversion, $\theta = (1 - \gamma)/[1 - (1/\sigma)]$, and $\sigma$ is the elasticity of intertemporal substitution. The Euler equation for asset $i$’s return, $R_{i,t+1}$ can be written as

$$1 = E_t\left[\left\{\delta \left(\frac{C_{t+1}}{C_t}\right)^{-1/\sigma}\right\}^{\theta} \left\{\frac{1}{1+R_{m,t+1}}\right\}^{1-\theta} (1+R_{i,t+1})\right]. \tag{122.32}$$

For the market portfolio itself, this takes the simpler form of

$$1 = E_t\left[\left\{\delta \left(\frac{C_{t+1}}{C_t}\right)^{-1/\sigma} R_{m,t+1}\right\}^{\theta}\right]. \tag{122.33}$$

The log version of general Euler equation (122.32) can be used for cross-sectional asset pricing. It takes the more complicated form of

$$0 = \theta \log \delta - \frac{\theta}{\sigma}E_t\Delta c_{t+1} + (\theta - 1)E_t r_{m,t+1} + E_t r_{i,t+1}$$
$$+ \frac{1}{2}\left[\left(\frac{\theta}{\sigma}\right)^2 V_{cc} + (\theta - 1)^2 V_{mm} + V_{ii} - \frac{2\theta}{\sigma}(\theta - 1)(V_{cm})\right.$$
$$\left.- \frac{2\theta}{\sigma}V_{ci} + 2(\theta - 1)V_{im}\right]. \tag{122.34}$$

When the asset under consideration is a risk-free real return $r_{f,t+1}$, this expression simplifies because some variance and covariance drop out; then

$$E_t r_{i,t+1} - r_{f,t+1} = -\frac{V_{ii}}{2} + \theta \frac{V_{ic}}{\sigma} + (1 - \theta)V_{im}. \tag{122.35}$$

After substituting, equation (122.30) comes to

$$c_t - w_t = (1 - \sigma)E_t \sum_{i=1}^{\infty} \rho^{i} (r_{m,t+i}) + \frac{\rho(k - \mu_m)}{1 - \rho}. \tag{122.36}$$

Equation (122.36) means the log consumption-wealth ratio is a constant, plus $(1 - \sigma)$ times the discounted value of expected future returns on invested
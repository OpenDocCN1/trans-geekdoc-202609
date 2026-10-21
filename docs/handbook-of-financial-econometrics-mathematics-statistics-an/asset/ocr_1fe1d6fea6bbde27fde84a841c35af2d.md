Let $y = (\hat{\beta} - \beta)/\sigma_{\hat{\beta}}$. The Jacobian of the transformation is $|d\hat{\beta}/dy| = \sigma_{\hat{\beta}}$. Thus, equation (68B.2) becomes

$$E\left(\frac{1}{\beta}\right) = \frac{1}{k\sqrt{2\pi}} \int_{a'}^{b'} \left(\frac{1}{y\sigma_{\hat{\beta}}}\right) e^{-\gamma^2/2} dy, \qquad (68B.3)$$

where $a' = (a - \beta)/\sigma_{\hat{\beta}}$ and $b' = (b - \beta)/\sigma_{\hat{\beta}}^{17}$ (here, $\alpha < \beta$). To integrand in (68B.3), it is necessary to express the function, $g(y) = 1/(y\sigma_{\hat{\beta}} + \beta)$, in terms of an infinite series. Since $1/(y\sigma_{\hat{\beta}} + \beta)$ is defined for all values of $y$ in the interval $(a', b')$. The Taylor's series expansion of $g(y)$ at a positive point, say $m^* = (a' + b')$, is

$$g(y) = \frac{1}{y\sigma_{\hat{\beta}} + \beta} = \frac{1}{(m^*\sigma_{\hat{\beta}} + \beta)} \cdot \sum_{i=0}^{\infty} \left[ -\frac{\sigma_{\hat{\beta}}(y - m^*)}{(m^*\sigma_{\hat{\beta}} + \beta)} \right]^i, \qquad (68B.4)$$

where $a' \le 0 \le b'$. It can be shown that $\left[ -\sigma_{\hat{\beta}}(y - m^*)/(m^*\sigma_{\hat{\beta}} + \beta) \right] < 1$ as follows:

$$\frac{-\sigma_{\hat{\beta}}(y - m^*)}{m^*\sigma_{\hat{\beta}} + \beta} = \frac{-\sigma_{\hat{\beta}}y + m^*\sigma_{\hat{\beta}}}{m^*\sigma_{\hat{\beta}} + \beta} = \frac{(m^*\sigma_{\hat{\beta}} + \beta) - \hat{\beta}}{m^*\sigma_{\hat{\beta}} + \beta} < 1,$$

since $\sigma_{\hat{\beta}}y = \hat{\beta} - \beta < 1$ $\hat{\beta} > 0$ and $-\hat{\beta} < 0$ (it is the truncated $\hat{\beta}$). Also, $\frac{-\sigma_{\hat{\beta}}(y - m^*)}{m^*\sigma_{\hat{\beta}} + \beta} > \frac{-\sigma_{\hat{\beta}}y}{m^*\sigma_{\hat{\beta}} + \beta} = \frac{-\hat{\beta} + \beta}{(a + b) - \beta}$, since $m^*\sigma_{\hat{\beta}} + \beta = (a + b) - \beta > 0$ $> \frac{-\hat{\beta}}{(a + b) - \beta} > \frac{-\hat{\beta}}{(a + b)} < -1$

¹⁷ $b$ is chosen such that $m^* > 0$, i.e., $(a + b) > 2\beta$.
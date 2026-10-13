
$$
\ln p(\mathbf{y},\mathbf{\theta},\mathbf{\alpha},\beta) = \ln\frac{\beta^{N/2}}{(2\pi)^{N/2}} - \frac{\beta}{2}\|\mathbf{y} - \Phi\mathbf{\theta}\|^{2} - \frac{1}{2}\sum_{k = 0}^{K - 1}a_{k}\theta_{k}^{2} + \sum_{k = 0}^{K - 1}\ln\sqrt{\frac{\alpha_{k}}{2\pi}} + \ln p(\mathbf{\alpha}) + \ln p(\beta)
$$

![Equation](images/B9780443292385000196/si90.png)

或

$$
\ln p(\mathbf{y},\mathbf{\theta},\mathbf{\alpha},\beta) = - \frac{\beta}{2}\|\mathbf{y} - \Phi\mathbf{\theta}\|^{2} - \frac{1}{2}\sum_{k = 0}^{K - 1}a_{k}\theta_{k}^{2} + \text{constant}
$$

![Equation](images/B9780443292385000196/si91.png) (13.29)

其中“constant”（常数）包含所有不依赖于 `θ` 的项，因为在此步骤中我们的目标是估计 `θ` 的函数。展开公式 [(13.29)](#Chp013_635-716_B9780443292385000196.xhtml#deq37) 并关于 `β` 和 `α` 取期望，考虑到 `q[β]^{(j)}(β)` 和 `q[α]^{(j)}(α)` 已知，我们得到

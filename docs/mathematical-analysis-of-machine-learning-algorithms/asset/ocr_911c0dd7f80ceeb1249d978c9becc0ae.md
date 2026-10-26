By summing over $t = 1$ to $t = T$, we obtain

$\eta_T^{-1}\lVert w_T-w\rVert_2^2 \le \eta_0^{-1}\lVert w_0-w\rVert_2^2 + 2\sum_{t=1}^{T}[\ell_t(w)-\ell_t(w_{t-1})] + G^2\sum_{t=1}^{T}\frac{1}{\lambda t}$

Using $\sum_{t=1}^{T}(1/t) \le 1+\ln T$, we obtain the desired bound. $\square$

It is possible to remove the $\ln T$ factor if we use weighted regret, as shown in the following theorem.

# **Theorem 14.12**  *Consider convex loss functions $\ell_t(w): \Omega \to \mathbb{R}$, which are $G$-Lipschitz (i.e. $\lVert\nabla\ell_t(w)\rVert_2 \le G$) and $\lambda$ strongly convex. If we let $\eta_t = 2/(\lambda(t+1)) > 0$ in Algorithm 14.3, then all $w \in \Omega$, we have*

$\sum_{t=1}^{T}\frac{2(t+1)}{T(T+3)}\ell_t(w_{t-1}) \le \sum_{t=1}^{T}\frac{2(t+1)}{T(T+3)}\ell_t(w) + \frac{2G^2}{\lambda(T+3)}$

*Proof*  As in the proof of Theorem 14.11, we have

$\lVert w_t-w\rVert_2^2 \le (1-\eta_t\lambda)\lVert w_{t-1}-w\rVert_2^2 + 2\eta_t[\ell_t(w)-\ell_t(w_{t-1})] + G^2\eta_t^2.$

This implies that $\eta_t^{-2}(1-\eta_t\lambda) \le \eta_{t-1}^{-2}$, where we set $\eta_0^{-2}=0$:

$\eta_t^{-2}\lVert w_t-w\rVert_2^2 \le \eta_{t-1}^{-2}\lVert w_{t-1}-w\rVert_2^2 + 2\eta_t^{-1}[\ell_t(w)-\ell_t(w_{t-1})] + G^2.$

By summing over $t = 1$ to $t = T$, we obtain

$\eta_T^{-2}\lVert w_T-w\rVert_2^2 \le \eta_0^{-2}\lVert w_0-w\rVert_2^2 + 2\sum_{t=1}^{T}\eta_t^{-1}[\ell_t(w)-\ell_t(w_{t-1})] + G^2T.$

This leads to the bound. $\square$

Using batch to online conversion, we can obtain the following expected oracle inequality as a straightforward result of Theorem 14.11 and Theorem 14.12.

# **Corollary 14.13**  *Consider the regularized loss function (14.8) with $w_0 = 0$, where $\phi(w,z)$ is convex in $w$, and $G$-Lipschitz in $w$. Moreover assume that $d(\Omega)=\sup\{\lVert w\rVert_2:w\in\Omega\}$. If $Z_1,\ldots,Z_T\sim D$ are independent samples, then we can obtain the following expected oracle inequality for Algorithm 14.3 if we take the learning rate in Theorem 14.11:*

$\mathbb{E}_{S_T}\mathbb{E}_D\phi(\hat w,Z)+\frac{\lambda}{2}\lVert\hat w\rVert_2^2 \le \inf_{w\in\Omega}\left[\mathbb{E}_D\phi(w,Z)+\frac{\lambda}{2}\lVert w\rVert_2^2\right]+\frac{\ln(eT)}{2\lambda T}[G+\lambda d(\Omega)]^2.$

We can also obtain the following expected oracle inequality for Algorithm 14.3 if we take the learning rate in Theorem 14.12 with
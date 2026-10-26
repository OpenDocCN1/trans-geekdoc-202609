be the reward of expert w. Then the expected reward of Algorithm 17.1 satisfies

$$\mathbb{E}\sum_{t=1}^{T} r_t(a_t) \ge (1-\gamma)\max_q\left[\mathbb{E}_{w\sim q}R_T(w)-\frac{1}{\eta}\mathrm{KL}(q\|p_0)\right]$$
$$\qquad -c(\eta,b)\eta\sum_{t=1}^{T}\sum_{a=1}^{K}|r_t(a)-b|,$$

where the expectation is with respect to the randomization of the algorithm,

$$c(\eta,b)=\phi(z_0)\max(b,1-b),\qquad z_0=\max(0,\eta(1-b)K/\gamma),$$

and φ(z) = (eᶻ − 1 − z) / z².

**Proof**  The proof is similar to that of Theorem 16.17. By the definition of π̃ₜ(aₜ), we have

$$\tilde{\rho}_t(a_t)=\mathbb{E}_{w\sim p_{t-1}(w)}\hat{q}_t(a_t\mid w,x_t)/\hat{\pi}_t(a_t)\le 1/(1-\gamma). \tag{17.4}$$

Therefore,

$$\mathbb{E}_{w\sim p_{t-1}(w)}\hat{r}_t(w,x_t,a_t)=\mathbb{E}_{w\sim p_{t-1}(w)}\hat{q}_t(a_t\mid w,x_t)[r_t(a_t)-b]/\hat{\pi}_t(a_t)$$
$$\le \frac{1}{1-\gamma}r_t(a_t)-\tilde{\rho}_t(a_t)b. \tag{17.5}$$

The first equation used the definition of r̂. The inequality used (17.4). Moreover,

$$\mathbb{E}_{w\sim p_{t-1}(w)}\hat{r}_t(w,x_t,a_t)^2$$
$$=\mathbb{E}_{w\sim p_{t-1}(w)}\hat{q}_t(a_t\mid w,x_t)^2\left((r_t(a_t)-b)/\hat{\pi}_t(a_t)\right)^2$$
$$\le \max(b,1-b)\mathbb{E}_{w\sim p_{t-1}(w)}\hat{q}_t(a_t\mid w,x_t)[|r_t(a_t)-b|/\hat{\pi}_t(a_t)^2]$$
$$\le \frac{\max(b,1-b)}{1-\gamma}\left(|r_t(a_t)-b|/\hat{\pi}_t(a_t)\right). \tag{17.6}$$

The first equation used the definition of r̂. The first inequality used |rₜ(aₜ) − b| ≤ max(b, 1 − b). The second inequality used (17.4).

If we let

$$W_t=\mathbb{E}_{w\sim p_0(w)}u_t(w),$$

then

$$\ln\frac{W_t}{W_{t-1}}=\ln\mathbb{E}_{w\sim p_0(w)}\frac{u_t(w)}{W_{t-1}}$$
$$=\ln\mathbb{E}_{w\sim p_{t-1}(w)}\exp(\eta\hat{r}_t(w,x_t,a_t))$$
$$\le \ln\mathbb{E}_{w\sim p_{t-1}(w)}\left[1+\eta\hat{r}_t(w,x_t,a_t)+\phi(z_0)(\eta\hat{r}_t(w,x_t,a_t))^2\right]$$
$$\le \mathbb{E}_{w\sim p_{t-1}(w)}(\eta\hat{r}_t(w,x_t,a_t)) + \phi(z_0)\mathbb{E}_{w\sim p_{t-1}(w)}(\eta\hat{r}_t(w,x_t,a_t))^2$$
$$\le \frac{\eta}{1-\gamma}r_t(a_t)-\eta\tilde{\rho}_t(a_t)b+\frac{c(\eta,b)\eta^2|r_t(a_t)-b|}{(1-\gamma)\hat{\pi}_t(a_t)}.$$

The second equality used the definition of uₜ. The first inequality used exp(z) ≤ 1 + z + φ(z₀)z² when z = ηr̂ₜ(w, xₜ, aₜ) ≤ z₀; the second inequality used ln(1 + z) ≤ z; and the third inequality used (17.5) and (17.6).
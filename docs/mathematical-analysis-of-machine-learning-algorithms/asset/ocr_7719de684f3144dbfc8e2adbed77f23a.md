$\hat r_t(a),\ \hat r_t(a,a_t)$ is an unbiased estimator of the full information reward vector $[r_t(a):a\in\{1,\ldots,K\}]$:

$$r_t(a)=\mathbb{E}_{a_t\sim\hat\pi_t(\cdot)}\hat r_t(a,a_t).$$

The following regret bound holds for the EXP3 algorithm.

# **Theorem 16.17**  *Consider Algorithm 16.5.* Let $G_* = \max_a\sum_{t=1}^T r_t(a)$. We have the following bound for the adversarial regret (16.1):

$$\mathrm{REG}_T\le (e-1)\gamma G_*+\frac{K\ln K}{\gamma}.$$

*Proof*  We have

$$\sum_{a=1}^{K}\hat\pi_t(a)\hat r_t(a,a_t)=r_t(a_t), \tag{16.9}$$

$$\sum_{a=1}^{K}\hat\pi_t(a)\hat r_t(a,a_t)^2=\hat r_t(a_t,a_t)r_t(a_t)\le \hat r_t(a_t,a_t). \tag{16.10}$$

It follows that for all $t\ge 1$,

$$\begin{aligned}
\frac{w_t}{w_{t-1}}
&=\sum_{a=1}^{K}\frac{w_t(a)}{w_{t-1}}
=\sum_{a=1}^{K}\frac{w_{t-1}(a)}{w_{t-1}}\exp\left(\gamma\hat r_t(a,a_t)/K\right)\\
&=\sum_{a=1}^{K}\frac{\hat\pi_t(a)-\gamma/K}{1-\gamma}\exp\left(\gamma\hat r_t(a,a_t)/K\right)\qquad\text{(definition of $\hat\pi_t(a)$)}\\
&\le^{(a)}\sum_{a=1}^{K}\frac{\hat\pi_t(a)-\gamma/K}{1-\gamma}\left[1+\gamma\hat r_t(a,a_t)/K+(e-2)(\gamma\hat r_t(a,a_t)/K)^2\right]\\
&\le 1+\frac{1}{1-\gamma}\left[\sum_{a=1}^{K}\hat\pi_t(a)\gamma\hat r_t(a,a_t)/K+\sum_{a=1}^{K}\hat\pi_t(a)(e-2)(\gamma\hat r_t(a,a_t)/K)^2\right]\\
&\le^{(b)}1+\frac{\gamma/K}{1-\gamma}r_t(a_t)+\frac{(e-2)(\gamma/K)^2}{1-\gamma}\hat r_t(a_t,a_t).
\end{aligned}$$

In (a), we used $\exp(z)\le 1+z+(e-2)z^2$ when $z\le 1$, and $\gamma\hat r_t(a,a_t)/K\le 1$. In (b), we used (16.9) and (16.10).

Therefore,

$$\begin{aligned}
\ln\frac{w_t}{w_{t-1}}&\le \ln\left(1+\frac{\gamma/K}{1-\gamma}r_t(a_t)+\frac{(e-2)(\gamma/K)^2}{1-\gamma}\hat r_t(a_t,a_t)\right)\\
&\le \frac{\gamma/K}{1-\gamma}r_t(a_t)+\frac{(e-2)(\gamma/K)^2}{1-\gamma}\hat r_t(a_t,a_t).
\end{aligned}$$

The second inequality follows from $\ln(1+z)\le z$.

Now, by summing over $t$, and letting

$$G_T=\sum_{t=1}^{T}r_t(a_t),$$
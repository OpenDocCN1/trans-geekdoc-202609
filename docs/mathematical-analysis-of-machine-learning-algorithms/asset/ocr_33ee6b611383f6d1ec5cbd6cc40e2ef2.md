Theorem 13.11 by taking conditional expectation with respect to each trajectory. With probability at least $1 - \delta/2$, for all $f_e \in \mathcal{F}_e$, $g_e \in \mathcal{G}_e$ and $t \ge 0$, 

$$\left|\underbrace{\sum_{s=1}^t \Delta_s^{h_s}(f_e,g_e)\epsilon_s^{h_s}(f_e)}_{A}\right| \le \frac{1}{\lambda}\sum_{s=1}^t \ln \mathbb{E}_{h_s}\mathbb{E}_{x_s^{h_s},a_s^{h_s}} \exp\left(\frac{\lambda^2\Delta_s^{h_s}(f_e,g_e)^2}{8}\right) + \frac{\ln(4M_1M_2/\delta)}{\lambda},$$

where we choose $\lambda = 0.9$. Let $\xi = \lambda^2\Delta_s^{h_s}(f_e,g_e)^2/8$, then $\xi \le 0.9^2/8 \le 0.102$, and thus

$$\frac{1}{\lambda}\ln\mathbb{E}\exp(\xi) \le \frac{1}{\lambda}[\mathbb{E}\exp(\xi)-1] \le \frac{\exp(0.102)}{\lambda}\mathbb{E}\xi.$$

By combining the previous two inequalities, and using $\exp(0.102)\lambda \le 1$, and $1/\lambda \le 1.2$, we obtain

$$A \le \sum_{s=1}^t \frac{1}{H}\sum_{h=1}^H \mathbb{E}_{x_s^{h}\sim\pi_s, a_s^{h}\sim\tilde{\pi}(\cdot|x_s^{h})}\frac{\Delta_s^{h}(f_e,g_e)^2}{8} + 1.2\ln(4M_1M_2/\delta).$$

This inequality can replace $(18.4)$ in the proof of Theorem 18.14. The same argument leads to the following inequalities as counterparts of $(18.5)$ and $(18.6)$. With probability at least $1 - \delta$, for all $f \in \mathcal{F}$, $g \in \mathcal{G}$, and $t \ge 0$, 

$$\left|\sum_{s=1}^t \Delta_s^{h_s}(f,g)\epsilon_s^{h_s}(f)\right| \le \frac{1}{4H}\sum_{s=1}^t\sum_{h=1}^H \mathbb{E}_{x_s\sim\pi_s, a_s\sim\tilde{\pi}(\cdot|x_s)}\Delta_s^{h}(f,g)^2 + \epsilon t(4+\epsilon) + 1.2\ln(4M_1M_2/\delta),$$

$$\left|\sum_{s=1}^t \Delta_s^{h_s}(f,f)\epsilon_s^{h_s}(f)\right| \le \frac{1}{4H}\sum_{s=1}^t\sum_{h=1}^H \mathbb{E}_{x_s\sim\pi_s, a_s\sim\tilde{\pi}(\cdot|x_s)}\Delta_s^{h}(f,f)^2 + \epsilon t(4+\epsilon) + 1.2\ln(4M_1/\delta).$$

We can set

$$0.5\beta_t^2 \ge [\epsilon t(4+\epsilon) + 1.2\ln(4M_1M_2/\delta)] + [\epsilon t(4+\epsilon) + 1.2\ln(4M_1/\delta)]$$

as in the proof of Theorem 18.14, and obtain $Q_* \in \mathcal{F}_t$, and

$$\frac{1}{H}\sum_{s=1}^t\sum_{h=1}^H \bar{\mathcal{E}}^h(f,\pi_s\tilde{\pi})^2 \le 4\beta_t^2,$$

where $\bar{\mathcal{E}}^h$ is defined in Proposition 18.33. The result now follows directly from Proposition 18.33 and the same derivation of Theorem 18.21. $\square$

It is worth pointing out that while Algorithm 18.3 returns a policy $\pi_t$ with good average regret, the online algorithm itself does not achieve such a regret, because the algorithm needs to employ a one-step pure exploration policy $\tilde{\pi}$ that is different from $\pi_t$. The purpose of this policy is to cover all possible actions
At time $t + 1$, we have

$$\tilde r_{t+1} \equiv r_{t+1} - \xi_{t+1}^r J_{t+1}^r = d + \sqrt{\tilde h_t + \xi_t^v J_t^v}\, \varepsilon_t$$

$$\tilde h_{t+1} \equiv h_{t+1} - \xi_{t+1}^v J_{t+1}^v = \alpha + \delta(\tilde h_t + \xi_t^v J_t^v) + \sqrt{\tilde h_t + \xi_t^v J_t^v}\, u_t,$$

since

$$p(\tilde h_t|h_{t-1},\tilde h_{t+1},\xi_t^v J_t^v,\xi_{t+1}^v J_{t+1}^v)=\frac{p(\tilde h_t,h_{t-1},\tilde h_{t+1},\xi_t^v J_t^v)}{p(h_{t-1},\tilde h_{t+1},\xi_t^v J_t^v,\xi_{t+1}^v J_{t+1}^v)}$$

$$=\frac{p(\tilde h_{t+1}|\tilde h_t,\bullet)p(\tilde h_t|h_{t-1},\bullet)p(h_{t-1})}{p(\tilde h_{t+1}|h_{t-1},\bullet)p(h_{t-1})}$$

$$\propto p(\tilde h_{t+1}|\tilde h_t,\bullet)p(\tilde h_t|h_{t-1},\bullet)$$

Thus, we have the posterior of $\tilde h_t$

$$p(\tilde h_t|h_{t-1},\tilde h_{t+1},\xi_t^v J_t^v,\xi_{t+1}^v J_{t+1}^v)$$

$$\propto (\tilde h_t + \xi_t^v J_t^v)^{-1} \exp\left\{ -\frac12 \left[ \operatorname{tr}\left( \sum^{*-1} \tilde e_t \tilde e_t' \right) + \operatorname{tr}\left( \sum^{*-1} \tilde e_{t+1} \tilde e_{t+1}' \right) \right] \right\}$$

$$\propto (\tilde h_t + \xi_t^v J_t^v)^{-1} \exp\left\{ -\frac{[\tilde h_t - (\alpha + \delta h_{t-1} + \psi(\tilde r_t - d))]^2}{2\Omega h_{t-1}} - \frac{(\tilde r_{t+1} - d)^2}{2(\tilde h_t + \xi_t^v J_t^v)} \right.$$

$$\left. - \frac{\delta^2}{2\Omega(\tilde h_t + \xi_t^v J_t^v)} \left[ \tilde h_t + \xi_t^v J_t^v - \frac{1}{\delta}[\tilde h_{t+1} - \alpha] \right]^2 + \frac{\psi}{\Omega} \frac{(\tilde h_{t+1} - \alpha)\tilde r_{t+1}}{\tilde h_t + \xi_t^v J_t^v} \right\}.$$

(52.6)

The posterior of $\xi_t^v$ can be derived from the following relation:

$$p(\xi_t^v|\xi_t^r, r_t, h_t, J_t = 1)$$

$$\propto p(r_t, h_t|\xi_t^v, \xi_t^r, J_t = 1) p(\xi_t^v|u_v, J_t = 1).$$

We know that $p(r_t, h_t|\theta, h_{t-1}, \xi_t^v, \xi_t^r) \propto h_{t-1}^{-1} |\Sigma|^{-1/2} e^{-\frac12 tr(\Sigma^{-1} e_t e_t')}, e_t = (\varepsilon_t, u_t)'$. As a result,

$$p(\xi_t^v|\xi_t^r, r_t, h_t, J_t = 1)$$

$$\propto p(r_t, h_t|\xi_t^v, \xi_t^r, J_t = 1) p(\xi_t^v|u_v, J_t = 1)$$

$$\propto \left\{ e^{-\frac12 tr(\Sigma^{-1} e_t e_t')} \right\} \left\{ e^{-\frac{\xi_t^v}{u_v}} \right\}$$
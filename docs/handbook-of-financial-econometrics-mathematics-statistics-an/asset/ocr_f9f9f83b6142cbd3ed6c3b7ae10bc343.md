where $\boldsymbol{Y} = (Y_1,\dots,Y_T)'$ are log-returns and $\boldsymbol{g} = (g_1,\dots,g_T)'$ are random time-changes, $\boldsymbol{\Theta} = (\theta,\sigma,\nu_1,\alpha)'$ denote the vector of unknown drift parameter $\theta$, the volatility $\sigma$, the initial shape parameter $\nu_1$, the NGARCH parameters $\alpha = (a_0,a,b,c)$ in (70.11), respectively. Note the constant $C = -T\log\sqrt{2\pi}$. Define

$$\varpi = \frac{\theta^2}{2\sigma^2} + 1 \quad \text{and}\quad \delta_t = \frac{(Y_t - \bar{Y} - \varphi_t)^2}{2\sigma^2}.$$

Then the joint likelihood $L(\boldsymbol{\Theta}|\boldsymbol{g},\boldsymbol{Y})$ can be rewritten as

$$\begin{aligned}
 -T\ln\sigma - \sum_{t=1}^{T} \delta_t/g_t - \sum_{t=1}^{T} \varpi g_t + \sum_{t=1}^{T} \left\{\frac{\theta(Y_t - m - \varphi_t)}{\sigma^2}\right\}
\ + \sum_{t=1}^{T} \{ (\nu_t - 1.5)\log(g_t) - \log(\Gamma(\nu_t)) \} + C.
\end{aligned}$$

Since the posterior distribution

$$p(\boldsymbol{g}|\boldsymbol{Y};\boldsymbol{\Theta}) = \frac{\exp(\mathcal{L}(\boldsymbol{\Theta}|\boldsymbol{g},\boldsymbol{Y}))}{\int \exp(\mathcal{L}(\boldsymbol{\Theta}|\boldsymbol{g},\boldsymbol{Y})) d\boldsymbol{g}}. \qquad (70B.2)$$

Note any term in the joint likelihood $L(\boldsymbol{\Theta}|\boldsymbol{g},\boldsymbol{Y})$ that do not involve the random time-changes $\boldsymbol{g} = (g_1,\dots,g_T)'$ will be canceled out in (70B.2). One has the posterior distribution

$$p(\boldsymbol{g}|\boldsymbol{Y};\boldsymbol{\Theta}) \propto \prod_{t=1}^{T} \exp\big(-\varpi g_t - \delta_t/g_t + (\nu_t - 1.5)\log(g_t)\big)$$

and the lemma is proved.
# 6.2.1 Loss Function Growth Under Distributed Momentum

We analyze, in Lemma 6.4, the difference between the current loss $\mathcal{L}_H(\boldsymbol{\theta}_t)$ and the previous loss $\mathcal{L}_H(\boldsymbol{\theta}_{t-1})$ for an arbitrary iteration $t > 1$ of Robust DMHB, i.e., Algorithm 6. As expected, the loss function growth depends upon both the aggregation error $\boldsymbol{\delta}_{t-1}$ and the deviation $\boldsymbol{\xi}_{t-1}$.

**Lemma 6.4** *Suppose Assumption 3.1. Consider Algorithm 6 with batch-size $b \in [1, m)$. Then, for any iteration $t > 1$, the following holds true:*

$\mathcal{L}_H(\boldsymbol{\theta}_t) - \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) \le -\gamma_{t-1}\left(\frac{1}{2} - 2\gamma_{t-1}L\right) \|\nabla\mathcal{L}_H(\boldsymbol{\theta}_{t-1})\|^2 + \gamma_{t-1}(1 + 2\gamma_{t-1}L)\|\boldsymbol{\xi}_{t-1}\|^2 + \gamma_{t-1}(1 + \gamma_{t-1}L)\|\boldsymbol{\delta}_{t-1}\|^2$

*Proof* Consider an arbitrary iteration $t > 1$. Since $\mathcal{L}_H$ is Lipschitz smooth function with coefficient $L$, owing to Assumption 3.1, we have

$\mathcal{L}_H(\boldsymbol{\theta}_t) - \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) \le \langle \boldsymbol{\theta}_t - \boldsymbol{\theta}_{t-1}, \nabla\mathcal{L}_H(\boldsymbol{\theta}_{t-1}) \rangle + \frac{L}{2} \|\boldsymbol{\theta}_t - \boldsymbol{\theta}_{t-1}\|^2$

For details on the derivation of the above, see Lemma A.1 in Appendix A.1. Substituting from (6.4), $\boldsymbol{\theta}_t = \boldsymbol{\theta}_{t-1} - \gamma_{t-1} \mathbf{m}^\mathrm{H}_{t-1} - \gamma_{t-1} \boldsymbol{\delta}_{t-1}$, we obtain that

$\mathcal{L}_H(\boldsymbol{\theta}_t) - \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) \le -\gamma_{t-1}\langle \mathbf{m}^\mathrm{H}_{t-1}, \nabla\mathcal{L}_H(\boldsymbol{\theta}_{t-1}) \rangle - \gamma_{t-1}\langle \boldsymbol{\delta}_{t-1}, \nabla\mathcal{L}_H(\boldsymbol{\theta}_{t-1}) \rangle + \gamma_{t-1}^2 \frac{L}{2} \|\mathbf{m}^\mathrm{H}_{t-1} + \boldsymbol{\delta}_{t-1}\|^2$

Substituting from (6.17), $\mathbf{m}^\mathrm{H}_{t-1} = \nabla\mathcal{L}_H(\boldsymbol{\theta}_{t-1}) + \boldsymbol{\xi}_{t-1}$, we obtain that

$\mathcal{L}_H(\boldsymbol{\theta}_t) - \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) \le -\gamma_{t-1} \|\nabla\mathcal{L}_H(\boldsymbol{\theta}_{t-1})\|^2 - \gamma_{t-1}\langle \boldsymbol{\xi}_{t-1}, \nabla\mathcal{L}_H(\boldsymbol{\theta}_{t-1}) \rangle - \gamma_{t-1}\langle \boldsymbol{\delta}_{t-1}, \nabla\mathcal{L}_H(\boldsymbol{\theta}_{t-1}) \rangle + \gamma_{t-1}^2 \frac{L}{2} \|\mathbf{m}^\mathrm{H}_{t-1} + \boldsymbol{\delta}_{t-1}\|^2 \tag{6.20}$

Next, we separately analyze the last three terms on the right-hand side.
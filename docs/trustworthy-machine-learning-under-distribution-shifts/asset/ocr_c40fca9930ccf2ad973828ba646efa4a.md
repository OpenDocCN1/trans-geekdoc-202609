# 7.1.1 Update Rule

Before our theoretical analyses, we need to make the update rule for each variable explicit.
We have to pay attention to the fact that our algorithm is stochastic that we can not directly get the real value of the gradient $\nabla L(\theta, \omega)$, rather we estimate it by batches of samples $g_{\theta}(	heta, \omega) = \frac{1}{M} \sum_{i=1}^M \frac{\partial \mathcal{L}}{\partial \theta}(	heta; \omega; (x_i, y_i))$ and $g_{\omega}(	heta, \omega) = \frac{1}{M} \sum_{i=1}^M \frac{\partial \mathcal{L}}{\partial \omega}(\theta; \omega; (x_i, y_i))$, which hold some properties we might use in Assumption 8. So the optimization iteration is executed as follows in reality:

```
$$\theta_{t+1} = \theta_t - \eta_{\theta}g_{\theta}(\theta_t + \rho g_{\omega}(\theta_t, \omega_t), \omega_t);$
$\omega_{t+1} = \omega_t + \eta_{\omega}g_{\omega}(\theta_t, \omega_t)$.$
```

We further give a notation for brief that $\theta_{t+1/2} \overset{\	ext{=}}{=} \theta_t + \rho g_{\omega}(\theta_t, \omega_t)$, so the update for $\theta$ can be simplified as: $\theta_{t+1} = \theta_t - \eta_{\theta}g_{\theta}(\theta_{t+1/2}, \omega_t)$.

# 7.1.2 Assumptions

We also have to make some necessary assumptions on our problem setting for this convergence proof:

ASSUMPTION 8 (Bounded variance). The unbiased estimation about the gradient of the loss function also has bounded variance:

```
$$\mathbb{E}_{(x,y)\simQ}[\frac{\partial \mathcal{L}}{\partial \theta}(\theta; \omega; (x, y))] = \nabla_{\theta}L(\theta, \omega), \mathbb{E}_{(x,y)\simQ}[\frac{\partial \mathcal{L}}{\partial \theta}(\theta; \omega; (x, y)) - \nabla_{\theta}L(\theta, \omega)\|^2 \le \sigma^2;$\n$\$\mathbb{E}_{(x,y)\simQ}[\frac{\partial \mathcal{L}}{\partial \omega}(\theta; \omega; (x, y))] = \nabla_{\omega}L(\theta, \omega), \mathbb{E}_{(x,y)\simQ}[\frac{\partial \mathcal{L}}{\partial \omega}(\theta; \omega; (x, y)) - \nabla_{\omega}L(\theta, \omega)\|^2 \le \sigma^2;$
```

REMARK 9. Since $g_{\theta}$ and $g_{\omega}$ are the averaged samples that: $g_{\theta} = \frac{1}{M} \sum_{i=1}^M \frac{\partial \mathcal{L}}{\partial \theta}(\theta; \omega; (x_i, y_i))$ and $g_{\omega} = \frac{1}{M} \sum_{i=1}^M \frac{\partial \mathcal{L}}{\partial \omega}(\theta; \omega; (x_i, y_i))$ respectively, they also have the unbiased property and have bounded variance:

```
$$\mathbb{E}_{(x,y)\simQ}[g_{\theta}(\theta; \omega; (x, y))] = \nabla_{\theta}L(\theta, \omega), \mathbb{E}_{(x,y)\simQ}[g_{\theta}(\theta; \omega; (x, y)) - \nabla_{\theta}L(\theta, \omega)\|^2 \le \frac{\sigma^2}{M};$\n$\mathbb{E}_{(x,y)\simQ}[g_{\omega}(\theta; \omega; (x, y))] = \nabla_{\omega}L(\theta, \omega), \mathbb{E}_{(x,y)\simQ}[g_{\omega}(\theta; \omega; (x, y)) - \nabla_{\omega}L(\theta, \omega)\|^2 \le \frac{\sigma^2}{M};$
```
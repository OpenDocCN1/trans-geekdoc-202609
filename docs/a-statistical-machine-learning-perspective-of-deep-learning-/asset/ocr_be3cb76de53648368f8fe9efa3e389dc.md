![](bbox=[0.021, 0.039, 0.069, 0.155])

# # ADA: new formulation

+   - New formulation

$$\max_{\phi}\mathcal{L}_{\phi}=\mathbb{E}_{p_{\theta}(x\mid y)p(y)}\left[\log q_{\phi}(y\mid x)\right]$$

$$\max_{\theta}\mathcal{L}_{\theta}=\mathbb{E}_{p_{\theta}(x\mid y)p(y)}\left[\log q_{\phi}^{r}(y\mid x)\right]$$

+   - The only **difference** between optimizing $\theta$ and $\phi$: $q$ vs. $q^{r}$

+   - This is where the **adversarial** mechanism comes about
# Mutual exchanges of ideas: augment the loss functions

| | GANs (InfoGAN) | VAEs |
|---|---|---|
| KLD to minimize | $\min_{\theta} \text{KL}\left(p_{\theta}(\boldsymbol{x}|y) \|\| q^{r}(\boldsymbol{x}|\mathbf{z},y)\right)$  $\sim \min_{\theta}\text{KL}(P_{\theta} \|\| Q)$ | $\min_{\theta}\text{KL}\left(q_{\eta}(\mathbf{z}|\boldsymbol{x},y)q_{*}^{r}(y|\boldsymbol{x}) \|\| p_{\theta}(\mathbf{z},y|\boldsymbol{x})\right)$  $\sim \min_{\theta}\text{KL}(Q \|\| P_{\theta})$ |

+   - Asymmetry of KLDs inspires combination of GANs and VAEs
+     - GANs: $\min_{\theta}\text{KL}(P_{\theta}||Q)$ tends to missing mode
+     - VAEs: $\min_{\theta}\text{KL}(Q||P_{\theta})$ tends to cover regions with small values of $p_{data}$

![](bbox=[0.27, 0.71, 0.58, 0.95])

Mode covering
Mode missing

[Figure courtesy: PRML]
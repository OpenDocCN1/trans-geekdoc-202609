![](bbox=[0.02, 0.03, 0.08, 0.17])

# Recap: conventional formulation of VAEs

+   - Objective:
+     $\max_{\theta,\eta} \mathcal{L}^{\text{vae}}_{\theta,\eta} = \mathbb{E}_{p_{data}(x)} \big[ \mathbb{E}_{\tilde{q}_\eta(z|x)} [\log \tilde{p}_\theta(x|z)] - \text{KL}(\tilde{q}_\eta(z|x) \| \tilde{p}(z)) \big]$
+     - $\tilde{p}(z)$: prior over $z$
+     - $\tilde{p}_\theta(x|z)$: generative model
+     - $\tilde{q}_\eta(z|x)$: inference model
+     - Only uses real examples from $p_{data}(x)$, lacks adversarial mechanism
+   - To align with GANs, let's introduce the real/fake indicator $y$ and adversarial discriminator
# Wake Sleep Algorithm

+   - Free energy:
+     $$F(\boldsymbol{\theta}, \boldsymbol{\phi}; \boldsymbol{x}) = -\log p(\boldsymbol{x}) + KL(q_{\phi}(\boldsymbol{z}|\boldsymbol{x}) \|\| p_{\theta}(\boldsymbol{z}|\boldsymbol{x}))$$
+   - Minimize the free energy wrt. $\boldsymbol{\theta}$ of $p_{\theta}$ $\rightarrow$ *wake phase*
+     $$\max_{\boldsymbol{\theta}} \mathbb{E}_{q_{\phi}(\boldsymbol{z}|\boldsymbol{x})} [\log p_{\boldsymbol{\theta}}(\boldsymbol{x}, \boldsymbol{z})]$$
+     - Get samples from $q_{\phi}(z|x)$ through inference on hidden variables
+     - Use the samples as targets for updating the generative model $p_{\theta}(\boldsymbol{z}|\boldsymbol{x})$
+     - Correspond to the variational M step

![](bbox=[0.73, 0.02, 0.92, 0.3])
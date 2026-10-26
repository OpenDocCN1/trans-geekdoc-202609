# Generative Adversarial Nets (GANs)

+   - [Goodfellow et al., 2014]
+   - Generative model $x = G_\theta(z),\ z \sim p(z)$
+     - Map noise variable $z$ to data space $x$
+     - Define an *implicit distribution* over $x$: $p_{g_\theta}(x)$
+       - a stochastic process to simulate data $x$
+       - Intractable to evaluate likelihood
+   - Discriminator $D_\phi(x)$
+     - Output the probability that $x$ came from the data rather than the generator
+   - No explicit inference model
+   - No obvious connection to previous models with inference networks like VAEs
+     - We will build formal connections between GANs and VAEs later
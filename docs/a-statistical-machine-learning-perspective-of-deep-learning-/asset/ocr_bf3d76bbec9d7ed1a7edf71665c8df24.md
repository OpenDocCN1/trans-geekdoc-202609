![](bbox=[0.021, 0.039, 0.069, 0.156])

# GANs: a variant of ADA

+   - Implicit distribution over $x \sim p_\theta(x\mid y)$

$$p_\theta(x\mid y)=\begin{cases}p_{g_\theta}(x) & y=0 \quad \text{(distribution of generated images)}\\p_{data}(x) & y=1. \quad \text{(distribution of real images)}\end{cases}$$

+   - $x \sim p_{g_\theta}(x) \Longleftrightarrow x=G_\theta(z),\ z\sim p(z\mid y=0)$
+   - $x \sim p_{data}(x)$
+     - the code space of $z$ is degenerated
+     - sample directly from data
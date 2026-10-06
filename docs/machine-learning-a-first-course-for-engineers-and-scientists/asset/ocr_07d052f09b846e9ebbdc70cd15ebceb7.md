# 10.3 Deep generative models

Moving to the third step of the procedure, we wish to update the mapping $f_{	heta}(z)$, defining the generative model, to make the generated samples as difficult as possible for the critic to reject as fake. In is some sense the most important step of the procedure, this is where we learn the generative model. This is done in a competition with the auxiliary classifier, where the objective for the generative model is to maximize the classification loss (10.27) over $	heta$.

```
$$\max_{\	heta} \mathbb{E}[L(1, g_{\theta}(f(x)))] + \mathbb{E}[L(-1, g_{\theta}(x_i))]$$
```

This results in a so-called minimax problem, where two adversaries compete for the same objective, one tries to minimize it and the other tries to maximize it. Typically, the problem is approached by alternating updating $\theta$ and $\eta$ using stochastic gradient optimization. We provide pseudo-code for one such algorithm in Method 10.4.

# Learn a generative adversarial network

+   **Data:** $T = \{x_i\}_{i=1}^n$ initial parameters $\theta$ and $\eta$, learning rate and batch size $n_b$.

+   **Result:** Generative model $f_{	heta}(z)$

+   repeat
  for $t = 0, \dots, T_{critic}$ do
    Sample mini-batch $\{x_i\}_{i=1}^{n_b}$ from training data
    Sample mini-batch $\{z_i\}_{i=1}^{n_b}$ independently from $\mathcal{N}(0, I)$
    Compute gradient $\hat{g}_{critic} = \sum_{i=1}^{n_b} \nabla_{\eta} L(1, g_{\eta}(f_{	heta}(z_i))) + L(-1, g_{\eta}(x_i))$
    Update critic: $\eta \leftarrow \eta - \gamma\hat{g}_{critic}$
  end
  Sample mini-batch $\{x_i\}_{i=1}^{n_b}$ independently from $\mathcal{N}(0, I)$
  Compute gradient $\hat{g}_{gen} = \sum_{i=1}^{n_b} \nabla_{\theta} L(1, g_{\eta}(f_{	heta}(z_i)))$
  Update generator: $\theta \leftarrow \theta + \gamma\hat{g}_{gen}$
until convergence

# Sample from a generative adversarial network

+   **Data:** Generative model $f_{	heta}(z)$

+   **Result:** Synthetic sample $x'$

+   1 Sample $z' \sim \\mathcal{N}(0, I)$

+   2 Output $x' = f_{	heta}(z')$

# Method 10.4: Learning of a generative adversarial network.

From an optimization point-of-view, the minimax problem is more challenging than solving a pure minimization problem, because the competing forces can result in oscillatory behavior. Many modifications and variations of the procedure outlined above have been developed, among others to stabilize the optimization and obtain efficient learning algorithms. Still, this is one of the drawbacks of using generative adversarial networks for instance, normalizing flows that can be learned by direct likelihood relationship. Related to this is the generative model $f_{	heta}(z)$, which implicitly implies defining the distribution $p(\mathbf{x}|\theta)$, it can still be used to evaluate the likelihood $p(\mathbf{x}|\theta)$ for some newly observed data point $\mathbf{x}$. Having access to such an explicit likelihood can be useful in certain applications, for instance to reason about the plausibility of the observed $\mathbf{x}$, under the learnt model of $p(\mathbf{x})$.

> Although, using the probability density function to reason about plausibility can be challenging and potentially misleading in very high-dimensional spaces.
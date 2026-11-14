![](bbox=[0.22, 0.1, 0.8, 0.26])

Figure 6.3: Illustration of the Gumbel-softmax (concrete) distribution with $K = 7$ states at different temperatures $\tau$. The top row shows $\mathbb{E}[\boldsymbol{z}]$, and the bottom row shows samples $\boldsymbol{z} \sim \text{GumbelSoftmax}(\boldsymbol{\alpha}, \tau)$. The left column shows a discrete (categorical) distribution, which always produces one-hot samples. From Figure 1 of [JGP17]. Used with kind permission of Ben Poole.

where $\epsilon_k \sim \text{Gumbel}(0, 1)$ is sampled from the **Gumbel distribution** [Gum54]. We can draw such samples by first sampling $u_k \sim \text{Unif}(0, 1)$ and then computing $\epsilon_k = -\log(-\log(u_k))$. This is called the **Gumbel-max trick** [MTM14], and gives us a reparameterizable representation for the categorical distribution.

Unfortunately, the derivative of the argmax is 0 everywhere except at the boundary of transitions from one label to another, where the derivative is undefined. However, suppose we replace the argmax with a softmax, and replace the discrete one-hot vector $\boldsymbol{d}$ with a continuous relaxation $\boldsymbol{x} \in \Delta^{K-1}$, where $\Delta^{K-1} = \{ \boldsymbol{x} \in \mathbb{R}^K : x_k \in [0, 1], \sum_{k=1}^K x_k = 1 \}$ is the $K$-dimensional simplex. Then we can write

```
\(x_k = \frac{\exp((\log \alpha_k + \epsilon_k)/\tau)}{\sum_{k'=1}^K \exp((\log \alpha_{k'} + \epsilon_{k'})/\tau)}\) (6.79)
```

where $\tau > 0$ is a temperature parameter. This is called the **Gumbel-softmax distribution** [JGP17] or the **concrete distribution** [MMT17]. This smoothly approaches the discrete distribution as $\tau \to 0$, as illustrated in Figure 6.3.
We can now replace \(f(\boldsymbol{d})\) with \(f(\boldsymbol{x})\), which allows us to take reparameterized gradients wrt \(\boldsymbol{x}\).

# 6.3.7 Stochastic computation graphs

We can represent an arbitrary function containing both deterministic and stochastic components as a **stochastic computation graph**. We can then generalize the AD algorithm (Section 6.2) to leverage score function estimation (Section 6.3.4) and reparameterization (Section 6.3.5) to compute Monte Carlo gradients for complex nested functions. For details, see [Sch+15a; Gaj+19].
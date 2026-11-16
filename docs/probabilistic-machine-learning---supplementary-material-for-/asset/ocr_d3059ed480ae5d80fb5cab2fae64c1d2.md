In this section, we will consider a convex outer approximation, $\mathbb{L}(G)$, based on pseudo marginals, as in Section 9.1.3.1. We also need to approximate the entropy (which was not needed when performing MAP estimation, discussed in Section 9.1.3). We discuss this entropy approximation in Section 10.1.3.1, and then show how we can use this to approximate log $Z$. Finally we show that loopy belief propagation attempts to optimize this approximation.

# 10.1.3.1 Bethe free energy

From Equation (9.17), we know that a joint distribution over a tree-structured graphical model can be represented exactly by the following:

$p_{\boldsymbol{\mu}}(\boldsymbol{x}) = \prod_{s \in V} \mu_s(x_s) \prod_{(s,t) \in E} \frac{\mu_{st}(x_s, x_t)}{\mu_s(x_s)\mu_t(x_t)}$ (10.11)

This satisfies the normalization and pairwise marginalization constraints of the outer approximation by construction.

From Equation 10.11, we can write the exact entropy of any tree structured distribution $\boldsymbol{\mu} \in \mathbb{M}(T)$ as follows:

$\mathbb{H}(\boldsymbol{\mu}) = \sum_{s \in V} H_s(\mu_s) - \sum_{(s,t) \in E} I_{st}(\mu_{st})$ (10.12)

$H_s(\mu_s) = - \sum_{x_s \in \mathcal{X}_s} \mu_s(x_s) \log \mu_s(x_s)$ (10.13)

$I_{st}(\mu_{st}) = \sum_{(x_s, x_t) \in \mathcal{X}_s \times \mathcal{X}_t} \mu_{st}(x_s, x_t) \log \frac{\mu_{st}(x_s, x_t)}{\mu_s(x_s)\mu_t(x_t)}$ (10.14)

Note that we can rewrite the mutual information term in the form $I_{st}(\mu_{st}) = H_s(\mu_s) + H_t(\mu_t) - H_{st}(\mu_{st})$, and hence we get the following alternative but equivalent expression:

$\mathbb{H}(\boldsymbol{\mu}) = - \sum_{s \in V} (d_s - 1) H_s(\mu_s) + \sum_{(s,t) \in E} H_{st}(\mu_{st})$ (10.15)

where $d_s$ is the degree (number of neighbors) for node $s$.

The Bethe$^1$ approximation to the entropy is simply the use of Equation 10.12 even when we don't have a tree:

$\mathbb{H}_{\text{Bethe}}(\boldsymbol{\tau}) = \sum_{s \in V} H_s(\tau_s) - \sum_{(s,t) \in E} I_{st}(\tau_{st})$ (10.16)

We define the Bethe free energy as the expected energy minus approximate entropy:

$\mathcal{F}_{\text{Bethe}}(\boldsymbol{\tau}) \triangleq - [\boldsymbol{\theta}^T \boldsymbol{\tau} + \mathbb{H}_{\text{Bethe}}(\boldsymbol{\tau})] \approx - \log Z$ (10.17)

Thus our final objective becomes

$\max_{\boldsymbol{\tau} \in \mathbb{L}(G)} \boldsymbol{\theta}^T \boldsymbol{\tau} + \mathbb{H}_{\text{Bethe}}(\boldsymbol{\tau})$ (10.18)

We call this the Bethe variational problem or BVP. The space we are optimizing over is a convex set, but the objective itself is not concave (since $\mathbb{H}_{\text{Bethe}}$ is not concave). Thus there can be multiple local optima. Also, the entropy approximation is not a bound (either upper or lower) on the true entropy. Thus the value obtained by the BVP is just an approximation to $\log Z(\boldsymbol{\theta})$. However, in the case of trees, the approximation is exact. Also, in the case of models with attractive potentials, the resulting value turns out to be an upper bound [SWW08]. In Section 10.1.5, we discuss how to modify the algorithm so it always minimizes an upper bound for any model.
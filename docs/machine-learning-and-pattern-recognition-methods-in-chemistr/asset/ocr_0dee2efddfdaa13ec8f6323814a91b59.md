# Autoencoders in generative modeling 129

KL divergence is non-negative so the ELBO is a lower bound on the likelihood of the data.

```
$\mathcal{L}_{\theta,\phi} = \log p_{\theta}(\mathbf{x}) - D_{KL}(q_{\phi}(\mathbf{z}|\mathbf{x})||p_{\theta}(\mathbf{z}|\mathbf{x})) \leq \log p_{\theta}(\mathbf{x}) \quad (6.21)$
```

So, the KL divergence $D_{KL}(q_{\phi}(\mathbf{z}|\mathbf{x})||p_{\theta}(\mathbf{x}))$ determines two distances:

+   1. The KL divergence of the approximate posterior from the true posterior;
2. The gap between the ELBO and the marginal likelihood $\log p_{\theta}(\mathbf{x})$; the better $q_{\phi}(\mathbf{z}|\mathbf{x})$ approximates the $p_{\theta}(\mathbf{z}|\mathbf{x})$, the smaller the gap. Equations about maximization of the ELBO w.r.t. the parameters $\theta$ and $\phi$ will concurrently optimize the two things we are about:
1. It will approximately maximize the marginal likelihood $p_{\theta}(\mathbf{x})$. This means that the generative model will become better.
2. It will minimize the KL divergence of the approximation $q_{\phi}(\mathbf{z}|\mathbf{x})$ from the true posterior, so the inference model becomes better. We can start out with random initial values of $\phi$ and $\theta$, and optimize their values until convergence. Given a dataset with i.i.d. data, the ELBO objective is the sum of individual-datoint ELBOs:

```
$\mathcal{L}_{\theta,\phi}(\mathbf{D}) = \sum_{\mathbf{x} \in \mathbf{D}} \mathcal{L}_{\theta,\phi}(\mathbf{x}) \quad (6.22)$
```

The individual-datoint ELBO, and its gradient $\nabla_{\theta,\phi}\mathcal{L}_{\theta,\phi}(\mathbf{x})$, is general, intractable. However, good unbiased estimators $\tilde{\nabla}_{\theta,\phi}\mathcal{L}_{\theta,\phi}(\mathbf{x})$ exist, such that we can still perform minibatch SGD.

Gradients of the ELBO w.r.t. are:

```
$\nabla_{\theta,\phi}\mathcal{L}_{\theta,\phi}(\mathbf{x}) = \nabla_{\theta} \mathbb{E}_{q_{\phi}(\mathbf{z}|\mathbf{x})} [\log p_{\theta}(\mathbf{x}, \mathbf{z}) - \log q_{\phi}(\mathbf{z}|\mathbf{x})]$
```

```
= \mathbb{E}_{q_{\phi}(\mathbf{z}|\mathbf{x})} [\nabla_{\theta} (\log p_{\theta}(\mathbf{x}, \mathbf{z}) - \log q_{\phi}(\mathbf{z}|\mathbf{x}))] \quad (6.23)$
```

```
$\nabla_{\theta,\phi}\mathcal{L}_{\theta,\phi}(\mathbf{x}) \approx \nabla_{\phi} (\log p_{\theta}(\mathbf{x}, \mathbf{z}) - \log q_{\phi}(\mathbf{z}|\mathbf{x})) = \nabla_{\phi} (\log p_{\theta}(\mathbf{x}, \mathbf{z})) \quad (6.24)$
```

The last line is a simple Monte Carlo estimator, where $z$ is a random sample from $q_{\phi}(\mathbf{z}|\mathbf{x})$. Computing gradients w.r.t. the variational parameters, $\phi$, are tricky:

```
$\nabla_{\phi}\mathcal{L}_{\theta,\phi}(\mathbf{x}) = \nabla_{\phi} \mathbb{E}_{q_{\phi}(\mathbf{z}|\mathbf{x})} [\log p_{\theta}(\mathbf{x}, \mathbf{z}) - \log q_{\phi}(\mathbf{z}|\mathbf{x})]$
```

```
= \mathbb{E}_{q_{\phi}(\mathbf{z}|\mathbf{x})} [\nabla_{\phi} (\log p_{\theta}(\mathbf{x}, \mathbf{z}) - \log q_{\phi}(\mathbf{z}|\mathbf{x}))] \quad (6.25)$
```
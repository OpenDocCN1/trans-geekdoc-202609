![](bbox=[0.27, 0.1, 0.735, 0.37])

Figure 10.4: Illustration of the reparameterization trick. The objective f depends on the variational parameters \(\phi\), the observed data \(x\), and the latent random variable \(z \sim q_\phi(z|x)\). On the left, we show the standard form of the computation graph. On the right, we show a reparameterized form, in which we move the stochasticity into the noise source \(\epsilon\), and compute \(z\) deterministically, \(z = g(\phi, x, \epsilon)\). The rest of the graph is deterministic, so we can backpropagate the gradient of the scalar \(f\) wrt \(\phi\) through \(z\) and into \(\phi\). From Figure 2.3 of [KW19a]. Used with kind permission of Durk Kingma.

The gradient wrt the generative parameters \(\theta\) is easy to compute, since we can push gradients inside the expectation, and use a single Monte Carlo sample:

```
\(\nabla_\theta \mathbf{L}(\theta, \phi | x) = \nabla_\theta \mathbb{E}_{q_\phi(z|x)} [\log p_\theta(x, z) - \log q_\phi(z|x)]\)
\(= \mathbb{E}_{q_\phi(z|x)} [\nabla_\theta \{ \log p_\theta(x, z) - \log q_\phi(z|x) \}]\)
\(\approx \nabla_\theta \log p_\theta(x, z^s)\)
```

where \(z^s \sim q_\phi(z|x)\). This is an unbiased estimate of the gradient, so can be used with SGD.

The gradient wrt the inference parameters \(\phi\) is harder to compute since

```
\(\nabla_\phi \mathbf{L}(\theta, \phi | x) = \nabla_\phi \mathbb{E}_{q_\phi(z|x)} [\log p_\theta(x, z) - \log q_\phi(z|x)]\)
\(\neq \mathbb{E}_{q_\phi(z|x)} [\nabla_\phi \{ \log p_\theta(x, z) - \log q_\phi(z|x) \}]\)
```

However, we can often use the reparameterization trick, which we discuss in Section 10.2.1. If not, we can use blackbox VI, which we discuss in Section 10.2.3.

# 10.2.1 Reparameterized VI

In this section, we discuss the **reparameterization trick** for taking gradients wrt distributions over continuous latent variables \(z \sim q_\phi(z|x)\). We explain this in detail in Section 6.3.5, but we summarize the basic idea here.
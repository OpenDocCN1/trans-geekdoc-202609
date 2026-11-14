![](bbox=[0.22, 0.13, 0.79, 0.285])

Figure 6.5: Changing the mean of a Gaussian by a fixed amount (from solid to dotted curve) can have more impact when the (shared) variance is small (as in a) compared to when the variance is large (as in b). Hence the impact (in terms of prediction accuracy) of a change to $\mu$ depends on where the optimizer is in $(\mu, \sigma)$ space. From Figure 3 of [Hon+10], reproduced from [Val00]. Used with kind permission of Antti Honkela.

For example, consider comparing two Gaussians, $p_\theta = p(y|\mu, \sigma)$ and $p_{\theta'} = p(y|\mu', \sigma')$. The (squared) Euclidean distance between the parameter vectors decomposes as $\|\theta - \theta'\|^2 = (\mu - \mu')^2 + (\sigma - \sigma')^2$. However, the predictive distribution has the form $\exp(-\frac{1}{2\sigma^2} (y - \mu)^2)$, so changes in $\mu$ need to be measured relative to $\sigma$. This is illustrated in Figure 6.5(a-b), which shows two univariate Gaussian distributions (dotted and solid lines) whose means differ by $\delta$. In Figure 6.5(a), they share the same small variance $\sigma^2$, whereas in Figure 6.5(b), they share the same large variance. It is clear that the value of $\delta$ matters much more (in terms of the effect on the distribution) when the variance is small. Thus we see that the two parameters interact with each other, which the Euclidean distance cannot capture. This problem gets much worse when we consider more complex models, such as deep neural networks. By modeling such correlations, NGD can converge much faster than other gradient methods.

# 6.4.1 Defining the natural gradient

The key to NGD is to measure the notion of distance between two probability distributions in terms of the KL divergence. As we show in Section 5.1.9, this can be approximated in terms of the Fisher information matrix (FIM). In particular, for any given input $x$, we have

```
$D_{KL}(p_\theta(y|x) \| p_{\theta+\delta}(y|x)) \approx \frac{1}{2} \delta^T F_x \delta$
```

where $F_x$ is the FIM

```
$F_x(\theta) = -E_{p_\theta(y|x)}[\nabla^2 \log p_\theta(y|x)] = E_{p_\theta(y|x)}[(\nabla \log p_\theta(y|x))(\nabla \log p_\theta(y|x))^T]$
```

We can compute the average KL between the current and updated distributions using $\frac{1}{2} \delta^T F \delta$, where $F$ is the averaged FIM:

```
$F(\theta) = E_{p_D(x)}[F_x(\theta)]$
```
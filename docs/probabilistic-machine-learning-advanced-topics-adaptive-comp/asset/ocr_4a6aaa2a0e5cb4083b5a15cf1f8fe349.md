![](bbox=[0.14, 0.09, 0.86, 0.38])

# 5.6.2 Variational IB

In this section, we derive a variational upper bound on Equation (5.165), leveraging ideas from Section 5.3.6. This is called the variational IB or VIB method [Ale+16]. The key trick will be to use the non-negativity of the KL divergence to write

```
\int dx p(\boldsymbol{x}) \log p(\boldsymbol{x}) \ge \int dx p(\boldsymbol{x}) \log q(\boldsymbol{x}) \qquad (5.167)
```

for any distribution q. (Note that both p and q may be conditioned on other variables.)

To explain the method in more detail, let us define the following notation. Let $e(\boldsymbol{z}|\boldsymbol{x}) = p(\boldsymbol{z}|\boldsymbol{x})$ represent the encoder, $b(\boldsymbol{z}|\boldsymbol{y}) \approx p(\boldsymbol{z}|\boldsymbol{y})$ represent the backwards encoder, $d(\boldsymbol{y}|\boldsymbol{z}) \approx p(\boldsymbol{y}|\boldsymbol{z})$ represent the classifier (decoder), and $m(\boldsymbol{z}) \approx p(\boldsymbol{z})$ represent the marginal. (Note that we get to choose $p(\boldsymbol{z}|\boldsymbol{x})$, but the other distributions are derived by approximations of the corresponding marginals and conditionals of the exact joint $p(\boldsymbol{x}, \boldsymbol{y}, \boldsymbol{z})$.). Also, let $\langle \cdot \rangle$ represent expectations wrt the relevant terms from the $p(\boldsymbol{x}, \boldsymbol{y}, \boldsymbol{z})$ joint.

With this notation, we can derive a lower bound on $\mathbb{I}(\boldsymbol{z}; \boldsymbol{y})$ as follows:

```
\mathbb{I}(\boldsymbol{z}; \boldsymbol{y}) = \int dy dz p(\boldsymbol{y}, \boldsymbol{z}) \log \frac{p(\boldsymbol{y}, \boldsymbol{z})}{p(\boldsymbol{y}) p(\boldsymbol{z})} \qquad (5.168)
= \int dy dz p(\boldsymbol{y}, \boldsymbol{z}) \log p(\boldsymbol{y}|\boldsymbol{z}) - \int dy dz p(\boldsymbol{y}, \boldsymbol{z}) \log p(\boldsymbol{y}) \qquad (5.169)
= \int dy dz p(\boldsymbol{z}) p(\boldsymbol{y}|\boldsymbol{z}) \log p(\boldsymbol{y}|\boldsymbol{z}) - \text{const} \qquad (5.170)
\ge \int dy dz p(\boldsymbol{y}, \boldsymbol{z}) \log d(\boldsymbol{y}|\boldsymbol{z}) \qquad (5.171)
= \langle \log d(\boldsymbol{y}|\boldsymbol{z}) \rangle \qquad (5.172)
```

where we exploited the fact that $\mathbb{H}(p(\boldsymbol{y}))$ is a constant that is independent of our representation.
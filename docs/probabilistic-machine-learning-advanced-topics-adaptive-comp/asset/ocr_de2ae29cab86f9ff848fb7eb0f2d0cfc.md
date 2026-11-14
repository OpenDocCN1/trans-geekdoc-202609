Note that we can approximate the expectations by sampling from

$$p(\mathbf{y}, \mathbf{z}) = \int d\mathbf{x} \, p(\mathbf{x})p(\mathbf{y}|\mathbf{x})p(\mathbf{z}|\mathbf{x}) = \int d\mathbf{x} \, p(\mathbf{x}, \mathbf{y})e(\mathbf{z}|\mathbf{x})$$

This is just the empirical distribution “pushed through” the encoder.
Similarly, we can derive an upper bound on $\mathbb{I}(\mathbf{z}; \mathbf{x})$ as follows:

$$\mathbb{I}(\mathbf{z}; \mathbf{x}) = \int d\mathbf{z} d\mathbf{x} \, p(\mathbf{x}, \mathbf{z}) \log \frac{p(\mathbf{z}, \mathbf{x})}{p(\mathbf{x})p(\mathbf{z})}$$ (5.174)

$$= \int d\mathbf{z} d\mathbf{x} \, p(\mathbf{x}, \mathbf{z}) \log p(\mathbf{z}|\mathbf{x}) - \int d\mathbf{z} \, p(\mathbf{z}) \log p(\mathbf{z})$$ (5.175)

$$\le \int d\mathbf{z} d\mathbf{x} \, p(\mathbf{x}, \mathbf{z}) \log p(\mathbf{z}|\mathbf{x}) - \int d\mathbf{z} \, p(\mathbf{z}) \log m(\mathbf{z})$$ (5.176)

$$= \int d\mathbf{z} d\mathbf{x} \, p(\mathbf{x}, \mathbf{z}) \log \frac{e(\mathbf{z}|\mathbf{x})}{m(\mathbf{z})}$$ (5.177)

$$= \langle \log e(\mathbf{z}|\mathbf{x}) \rangle - \langle \log m(\mathbf{z}) \rangle$$ (5.178)

Note that we can approximate the expectations by sampling from $p(\mathbf{x}, \mathbf{z}) = p(\mathbf{x})p(\mathbf{z}|\mathbf{x})$. Putting it altogether, we get the following upper bound on the IB objective:

$$\beta \mathbb{I}(\mathbf{x}; \mathbf{z}) - \mathbb{I}(\mathbf{z}; \mathbf{y}) \le \beta (\langle \log e(\mathbf{z}|\mathbf{x}) \rangle - \langle \log m(\mathbf{z}) \rangle) - \langle \log d(\mathbf{y}|\mathbf{z}) \rangle$$ (5.179)

Thus the VIB objective is

$$\mathcal{L}_{\text{VIB}} = \beta (\mathbb{E}_{p_D(\mathbf{x})e(\mathbf{z}|\mathbf{x})} [\log e(\mathbf{z}|\mathbf{x}) - \log m(\mathbf{z})]) - \mathbb{E}_{p_D(\mathbf{x})e(\mathbf{z}|\mathbf{x})d(\mathbf{y}|\mathbf{z})} [\log d(\mathbf{y}|\mathbf{z})]$$ (5.180)

$$= -\mathbb{E}_{p_D(\mathbf{x})e(\mathbf{z}|\mathbf{x})d(\mathbf{y}|\mathbf{z})} [\log d(\mathbf{y}|\mathbf{z})] + \beta \mathbb{E}_{p_D(\mathbf{x})} [D_{\text{KL}}(e(\mathbf{z}|\mathbf{x}) \| m(\mathbf{z}))]$$ (5.181)

We can now take stochastic gradients of this objective and minimize it (wrt the parameters of the encoder, decoder, and marginal using SGD. (We assume the distributions are reparameterizable, as discussed in Section 6.3.5.) For the encoder $e(\mathbf{z}|\mathbf{x})$, we often use a conditional Gaussian, and for the decoder $d(\mathbf{y}|\mathbf{z})$, we often use a softmax classifier. For the marginal, $m(\mathbf{z})$, we should use a flexible model, such as a mixture of Gaussians, since it needs to approximate the **aggregated posterior** $p(\mathbf{z}) = \int d\mathbf{z} p(\mathbf{x}) e(\mathbf{z}|\mathbf{x})$, which is a mixture of $N$ Gaussians (assuming $p(\mathbf{x})$ is an empirical distribution with $N$ samples, and $e(\mathbf{z}|\mathbf{x})$ is a Gaussian).

We illustrate this in Figure 5.13, where we fit the an MLP model to MNIST. We use a 2d bottleneck layer before passing to the softmax. In panel a, we show the embedding learned by a deterministic encoder. We see that each image gets mapped to a point, and there is little overlap between classes, or between instances. In panels b-c, we show the embedding learned by a stochastic encoder. Each image gets mapped to a Gaussian distribution, we show the mean and the covariance separately. The classes are still well separated, but individual instances of a class are no longer distinguishable, since such information is not relevant for prediction purposes.

# 5.6.3 Conditional entropy bottleneck

The IB tries to maximize $\mathbb{I}(Z; Y)$ while minimizing $\mathbb{I}(Z; X)$. We can write this objective as

$$\min \mathbb{I}(\mathbf{x}; \mathbf{z}) - \lambda \mathbb{I}(\mathbf{y}; \mathbf{z})$$ (5.182)
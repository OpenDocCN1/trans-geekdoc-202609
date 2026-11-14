floor. In such cases, one can get faster convergence by scaling the gradient vector by a **conditioning matrix** $\mathbf{C}_t$ as follows:

```
$\boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t - \eta_t \mathbf{C}_t \mathbf{g}_t$ (6.48)
```

This is called **preconditioned SGD**. For more details, see [Mur22, Sec 8.4.6].

# 6.3.2 SGD for optimizing a finite-sum objective

In the simplest case, the distribution used to compute the expectation, $q_{\theta}(z)$, does not depend on the parameters being optimized, $\theta$. In this case, we can push gradients inside the expectation operator, and then use Monte Carlo sampling for $\mathbf{z}$ to approximate the gradient:

```
$\nabla_{\boldsymbol{\theta}} \mathcal{L}(\boldsymbol{\theta}) = \nabla_{\boldsymbol{\theta}} \mathbb{E}_{q(\mathbf{z})} \left[ \tilde{\mathcal{L}}(\boldsymbol{\theta}, \mathbf{z}) \right] = \mathbb{E}_{q(\mathbf{z})} \left[ \nabla_{\boldsymbol{\theta}} \tilde{\mathcal{L}}(\boldsymbol{\theta}, \mathbf{z}) \right] \approx \frac{1}{S} \sum_{s=1}^S \nabla_{\boldsymbol{\theta}} \tilde{\mathcal{L}}(\boldsymbol{\theta}, \mathbf{z}_s)$ (6.49)
```

For example, consider the problem of **empirical risk minimization** or **ERM**, which requires minimizing

```
$\mathcal{L}(\boldsymbol{\theta}) = \frac{1}{N} \sum_{n=1}^N \tilde{\mathcal{L}}(\boldsymbol{\theta}, \mathbf{z}_n) = \frac{1}{N} \sum_{n=1}^N \ell(\mathbf{y}_n, f(\mathbf{x}_n; \boldsymbol{\theta}))$ (6.50)
```

where $\mathbf{z}_n = (\mathbf{x}_n, \mathbf{y}_n)$ is the $n$'th labeled example, and $f$ is a prediction function. This kind of objective is called a **finite sum objective**. We can write this as an expected loss wrt the empirical distribution $p_{\mathcal{D}}(\mathbf{x}, \mathbf{y})$:

```
$\mathcal{L}(\boldsymbol{\theta}) = \mathbb{E}_{p_{\mathcal{D}}(\mathbf{x}, \mathbf{y})} \left[ \tilde{\mathcal{L}}(\boldsymbol{\theta}, \mathbf{z}) \right]$ (6.51)
```

Since the expectation depends on the data, and not on the parameters, we can approximate the gradient by using a **minibatch** of $B = |\mathcal{B}|$ datapoints from the full dataset $\mathcal{D}$ at each iteration:

```
$\mathbf{g}_t = \nabla \mathcal{L}(\boldsymbol{\theta}_t) = \frac{1}{B} \sum_{n \in B} \nabla \ell(\mathbf{y}_n, f(\mathbf{x}_n; \boldsymbol{\theta}))$ (6.52)
```

These noisy gradients can then be passed to SGD. When the dataset is large, this method is much faster than **full batch** gradient descent, since it does not require evaluating the loss on all $N$ examples before updating the model [BB08; BB11].

# 6.3.3 SGD for optimizing the parameters of a distribution

Now suppose the stochasticity depends on the parameters we are optimizing. For example, $\mathbf{z}$ could be an action sampled from a stochastic policy $q_{\boldsymbol{\theta}}$, as in RL (Section 35.3.2), or $\mathbf{z}$ could be a latent variable sampled from an inference network $q_{\boldsymbol{\theta}}$, as in stochastic variational inference (see Section 10.2).

In this case, the gradient is given by

```
$\nabla_{\boldsymbol{\theta}} \mathbb{E}_{q_{\boldsymbol{\theta}}(\mathbf{z})} \left[ \tilde{\mathcal{L}}(\boldsymbol{\theta}, \mathbf{z}) \right] = \nabla_{\boldsymbol{\theta}} \int \tilde{\mathcal{L}}(\boldsymbol{\theta}, \mathbf{z}) q_{\boldsymbol{\theta}}(\mathbf{z}) d\mathbf{z}$ (6.53)
```

```
$= \int \left[ \nabla_{\boldsymbol{\theta}} \tilde{\mathcal{L}}(\boldsymbol{\theta}, \mathbf{z}) \right] q_{\boldsymbol{\theta}}(\mathbf{z}) d\mathbf{z} + \int \tilde{\mathcal{L}}(\boldsymbol{\theta}, \mathbf{z}) \left[ \nabla_{\boldsymbol{\theta}} q_{\boldsymbol{\theta}}(\mathbf{z}) \right] d\mathbf{z}$ (6.54)
```
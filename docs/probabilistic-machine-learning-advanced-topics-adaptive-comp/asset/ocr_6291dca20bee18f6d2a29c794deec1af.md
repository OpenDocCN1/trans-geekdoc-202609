added noise. If we approximate the gradient with a stochastic gradient, we get a method known as **SGLD**, or **stochastic gradient Langevin descent** (see Section 12.7.1 for details).

Now suppose \(\boldsymbol{\Sigma} = \mathbf{I}\), and we set \(\eta = \sqrt{2}\). In continuous time, we get the following stochastic differential equation (SDE), known as **Langevin diffusion**:

\(d\boldsymbol{\theta}_t = -\nabla \mathcal{E}(\boldsymbol{\theta}_t)dt + \sqrt{2}d\mathbf{B}_t\) (12.83)

where \(\mathbf{B}_t\) represents \(D\)-dimensional Brownian motion. If we use this to generate the samples, the method is known as the **anadjusted Langevin algorithm** or **ULA** [Par81; RT96].

# 12.5.7 Connection between SGD and Langevin sampling

In this section, we discuss a deep connection between stochastic gradient descent (SGD) and Langevin sampling, following the presentation of [BZ20, Sec 10.2.3].

Consider the minimization of the additive loss

\(\mathcal{L}(\boldsymbol{\theta}) = \sum_{n=1}^N \mathcal{L}_n(\boldsymbol{\theta})\) (12.84)

For example, we may define \(\mathcal{L}_n(\boldsymbol{\theta}) = -\log p(y_n|\mathbf{x}_n, \boldsymbol{\theta})\). We will use a minibatch approximation to the gradients:

\(\nabla_B \mathcal{L}(\boldsymbol{\theta}) = \frac{1}{B} \sum_{n \in S} \nabla \mathcal{L}_n(\boldsymbol{\theta})\) (12.85)

where \(\mathcal{S} = \{i_1, \dots, i_B\}\) is a randomly chosen set of indices of size \(B\). For simplicity of analysis, we assume the indices are chosen with replacement from \(\{1, \dots, N\}\).

Let us define the (scaled) error (due to minibatching) in the estimated gradient by

\(\boldsymbol{v}_t \triangleq \sqrt{\eta} (\nabla \mathcal{L}(\boldsymbol{\theta}_t) - \nabla_B \mathcal{L}(\boldsymbol{\theta}_t))\) (12.86)

This is called the **diffusion term**. Then we can rewrite the SGD update as

\(\boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t - \eta \nabla_B \mathcal{L}(\boldsymbol{\theta}_t) = \boldsymbol{\theta}_t - \eta \nabla \mathcal{L}(\boldsymbol{\theta}_t) + \sqrt{\eta} \boldsymbol{v}_t\) (12.87)

The diffusion term \(\boldsymbol{v}_t\) has mean 0, since

\(\mathbb{E}[\nabla_B \mathcal{L}(\boldsymbol{\theta})] = \frac{1}{B} \sum_{j=1}^B \mathbb{E}[\nabla \mathcal{L}_{i_j}(\boldsymbol{\theta})] = \frac{1}{B} \sum_{j=1}^B \nabla \mathcal{L}(\boldsymbol{\theta}) = \nabla \mathcal{L}(\boldsymbol{\theta})\) (12.88)

To compute the variance of the diffusion term, note that

\(\mathbb{V}[\nabla_B \mathcal{L}(\boldsymbol{\theta})] = \frac{1}{B^2} \sum_{j=1}^B \mathbb{V}[\nabla \mathcal{L}_{i_j}(\boldsymbol{\theta})]\) (12.89)
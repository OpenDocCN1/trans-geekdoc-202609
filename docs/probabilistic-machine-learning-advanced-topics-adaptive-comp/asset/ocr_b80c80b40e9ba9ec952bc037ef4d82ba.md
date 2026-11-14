An alternative approach is to use a hierarchical model, in which we add **auxiliary latent variables** $\mathbf{a}$, which are used to increase the flexibility of the variational posterior. In particular, we can still assume $q_\phi(\mathbf{z}|\mathbf{x}, \mathbf{a})$ is conditionally factorized, but when we marginalize out $\mathbf{a}$, we induce dependencies between the elements of $\mathbf{z}$, i.e.,

$q_\phi(\mathbf{z}|\mathbf{x}) = \int q_\phi(\mathbf{z}|\mathbf{x}, \mathbf{a}) q_\phi(\mathbf{a}|\mathbf{x}) d\mathbf{a} \neq \prod_k q_\phi(z_k|\mathbf{x})$ (10.164)

This is called a **hierarchical variational model** [Ran16], or an **auxiliary variable deep generative model** [Maa+16].

In [TRB16], they model $q_\phi(\mathbf{z}|\mathbf{x}, \mathbf{a})$ as a Gaussian process, which is a flexible nonparametric distribution (see Chapter 18), where $\mathbf{a}$ are the inducing points. This combination is called a **variational GP**.

# 10.4.3 **Normalizing flow posteriors**

Normalizing flows are a class of probability models which work by passing a simple source distribution, such as a diagonal Gaussian, through a series of nonlinear, but invertible, mappings $f$ to create a more complex distribution. This can be used to get more accurate posterior approximations than standard Gaussian VI, as we discuss in Section 23.1.2.2.

# 10.4.4 **Implicit** posteriors

In Chapter 26, we discuss implicit probability distributions, which are models which we can sample from, but which we cannot evaluate pointwise. For example, consider passing a Gaussian noise term, $\mathbf{z}_0 \sim \mathcal{N}(\mathbf{0}, \mathbf{I})$, through a nonlinear, *non-invertible* mapping $f$ to create $\mathbf{z} = f(\mathbf{z}_0)$; it is easy to sample from $q(\mathbf{z})$, but it is intractable to evaluate the density $q(\mathbf{z})$ (unlike with flows). This makes it hard to evaluate the log density ratio $\log p_\theta(\mathbf{z})/q_\phi(\mathbf{z}|\mathbf{x})$, which is needed to compute the ELBO. However, we can use the same method as is used in GANs (generative adversarial networks, Chapter 26), in which we train a classifier that discriminates prior samples from samples from the variational posterior by evaluating $T(\mathbf{x}, \mathbf{z}) = \log q_\psi(\mathbf{z}|\mathbf{x}) - \log p_\theta(\mathbf{z})$. See e.g., [TR19] for details.

# 10.4.5 **Combining VI with MCMC inference**

There are various ways to combine variational inference with MCMC to get an improved approximate posterior. In [SKW15], they propose **Hamiltonian variational inference**, in which they train an inference network to initialize an HMC sampler (Section 12.5). The gradient of the log posterior (wrt the latents), which is needed by HMC, is given by

$\nabla_{\mathbf{z}} \log p_\theta(\mathbf{z}|\mathbf{x}) = \nabla_{\mathbf{z}} \log [p_\theta(\mathbf{x}, \mathbf{z}) - \log p_\theta(\mathbf{x})] = \nabla_{\mathbf{z}} \log p_\theta(\mathbf{x}, \mathbf{z})$ (10.165)

This is easy to compute. They use the final sample to approximate the posterior $q_\phi(\mathbf{z}|\mathbf{x})$. To compute the entropy of this distribution, they also learn an auxiliary inverse inference network to reverse the HMC Markov chain.

A simpler approach is proposed in [Hof17]. Here they train an inference network to initialize an HMC sampler, using the standard ELBO for $\phi$, but they optimize the generative parameters $\theta$ using
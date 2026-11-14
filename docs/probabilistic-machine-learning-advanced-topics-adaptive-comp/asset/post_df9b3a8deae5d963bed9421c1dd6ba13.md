
normalizing flows in latent space for language modeling.

#### 23.3.3 Inference

Normalizing flows have been used for probabilistic inference. Rezende and Mohamed [RM15] popularized normalizing flows in machine learning, and showed how they can be used for modeling variational posterior distributions in latent variable models. Various extensions such as Householder flows [TW16], inverse autoregressive flows [Kim+16], multiplicative normalizing flows [LW17], and Sylvester flows [Ber+18] have been proposed for modeling the variational posterior for latent variable models, as well as posteriors for Bayesian neural networks.

Flows have been used as complex proposal distributions for importance sampling; examples include neural importance sampling [Mül+19b] and Boltzmann generators [Noé+19]. Hoffman et al. [Hof+19] used flows to improve the performance of Hamiltonian Monte Carlo (Section 12.5) by defining bijective transformations to transform random variables to simpler distributions and performing HMC in that space instead.

Finally, flows can be used in the context of simulation-based inference, where the likelihood function of the parameters is not available, but simulating data from the model is possible. The main idea is to train a flow on data simulated from the model in order to approximate the posterior distribution or the likelihood function. The flow model can also be used to guide simulations in order to make inference more efficient [PSM19; GNM19]. This approach has been used for inference of simulation models in cosmology [Als+19] and computational neuroscience [Gon+20].

## 24 Energy-based models

*This chapter is co-authored with Yang Song and Durk Kingma.*

### 24.1 Introduction

We have now seen several ways of defining deep generative models, including VAEs (Chapter 21), autoregressive models (Chapter 22), and normalizing flows (Chapter 23). All of the above models can be formulated in terms of directed graphical models (Chapter 4), where we generate the data one step at a time, using locally normalized distributions. In some cases, it is easier to specify a distribution in terms of a set of constraints that valid samples must satisfy, rather than a generative process. This can be done using an undirected graphical model (Chapter 4).

**Energy-based models** or **EBM** can be written as a Gibbs distribution as follows:

$$p_{\boldsymbol{\theta}}(\mathbf{x}) = \frac{\exp(-\mathcal{E}_{\boldsymbol{\theta}}(\mathbf{x}))}{Z_{\boldsymbol{\theta}}}$$ (24.1)

where $\mathcal{E}_{\boldsymbol{\theta}}(\mathbf{x}) \ge 0$ is known as the **energy function** with parameters $\boldsymbol{\theta}$, and $Z_{\boldsymbol{\theta}}$ is the **partition function**:

$$Z_{\boldsymbol{\theta}} = \int \exp(-\mathcal{E}_{\boldsymbol{\theta}}(\mathbf{x})) \, \mathrm{d}\mathbf{x}$$ (24.2)

This is constant wrt $\mathbf{x}$ but is a function of $\boldsymbol{\theta}$. Since EBMs do not usually make any Markov assumptions (unlike graphical models), evaluating this integral is usually intractable. Consequently we usually need to use approximate methods, such as annealed importance sampling, discussed in Section 11.5.4.1.

The advantage of an EBM over other generative models is that the energy function can be any kind of function that returns a non-negative scalar; it does not need to integrate to 1. This allows one to use a variety of neural network architectures for defining the energy. As such, EBMs have found wide applications in many fields of machine learning, including image generation [Ngi+11; Xie+16; DM19b], discriminative learning [Gra+20b], natural processing [Mik+13; Den+20], density estimation [Wen+19a; Son+19], and reinforcement learning [Haa+17; Haa+18a], to list a few. (More examples can be found at https://github.com/yataobian/awesome-ebm.)

![](img/ca72c1626f4850f058a9edc138c1ac73_871_0.png)

Figure 24.1: Combining two energy functions in 2d by summation, which is equivalent to multiplying the corresponding probability densities. We also illustrate some sampled trajectories towards high probability (low energy) regions. From Figure 14 of [DM19a]. Used with kind permission of Yilun Du.

#### 24.1.1 Example: products of experts (PoE)

As an example of why energy based models are useful, suppose we want to create a generative model of proteins that are thermally stable at room temperature, and which bind to the COVID-19 spike receptor. Suppose \(p_1(\boldsymbol{x})\) can generate stable proteins and \(p_2(\boldsymbol{x})\) can generate proteins that bind. (For example, both of these models could be autoregressive sequence models, trained on different datasets.) We can view each of these models as “experts” about a particular aspect of the data. On their own, they are not an adequate model of the data that we have (or want to have), but we can then combine them, to represent the **conjunction of features**, by computing a **product of experts** (**PoE**) [Hin02]:

$$p_{12}(\boldsymbol{x}) = \frac{1}{Z_{12}} p_1(\boldsymbol{x}) p_2(\boldsymbol{x})$$

This will assign high probability to proteins that are stable and which bind, and low probability to all others. By contrast, a **mixture of experts** would either generate from \(p_1\) or from \(p_2\), but would not combine features from both.

If the experts are represented as energy based models (EBM), then the PoE model is also an EBM, with an energy given by

$$\mathcal{E}_{12}(\boldsymbol{x}) = \mathcal{E}_1(\boldsymbol{x}) + \mathcal{E}_2(\boldsymbol{x})$$

Intuitively, we can think of each component of energy as a “soft constraint” on the data. This idea is illustrated in Figure 24.1.

#### 24.1.2 Computational difficulties

Although the flexibility of EBMs can provide significant modeling advantages, computation of the likelihood and drawing samples from the model are generally intractable. In this chapter, we will discuss a variety of approximate methods to solve these problems.

### 24.2 Maximum likelihood training

The de facto standard for learning probabilistic models from iid data is maximum likelihood estimation (MLE). Let $p_{\theta}(\mathbf{x})$ be a probabilistic model parameterized by $\theta$, and $p_{\mathcal{D}}(\mathbf{x})$ be the underlying data distribution of a dataset. We can fit $p_{\theta}(\mathbf{x})$ to $p_{\mathcal{D}}(\mathbf{x})$ by maximizing the expected log-likelihood function over the data distribution, defined by

\[
\ell(\theta) = \mathbb{E}_{\mathbf{x} \sim p_{\mathcal{D}}(\mathbf{x})}[\log p_{\theta}(\mathbf{x})] \tag{24.5}
\]

as a function of $\theta$. Here the expectation can be easily estimated with samples from the dataset. Maximizing likelihood is equivalent to minimizing the KL divergence between $p_{\mathcal{D}}(\mathbf{x})$ and $p_{\theta}(\mathbf{x})$, because

\[
\ell(\theta) = -D_{\text{KL}}(p_{\mathcal{D}}(\mathbf{x}) \parallel p_{\theta}(\mathbf{x})) + \text{const} \tag{24.6}
\]

where the constant is equal to \(\mathbb{E}_{\mathbf{x} \sim p_{\mathcal{D}}(\mathbf{x})}[\log p_{\mathcal{D}}(\mathbf{x})]\) which does not depend on $\theta$.

We cannot usually compute the likelihood of an EBM because the normalizing constant $Z_{\theta}$ is often intractable. Nevertheless, we can still estimate the gradient of the log-likelihood with MCMC approaches, allowing for likelihood maximization with stochastic gradient ascent [You99]. In particular, the gradient of the log-probability of an EBM decomposes as a sum of two terms:

\[
\nabla_{\theta} \log p_{\theta}(\mathbf{x}) = -\nabla_{\theta} \mathcal{E}_{\theta}(\mathbf{x}) - \nabla_{\theta} \log Z_{\theta}. \tag{24.7}
\]

The first gradient term, $-\nabla_{\theta} \mathcal{E}_{\theta}(\mathbf{x})$, is straightforward to evaluate with automatic differentiation. The challenge is in approximating the second gradient term, $\nabla_{\theta} \log Z_{\theta}$, which is intractable to compute exactly. This gradient term can be rewritten as the following expectation:

\[
\begin{align}
\nabla_{\theta} \log Z_{\theta} &= \nabla_{\theta} \log \int \exp(-\mathcal{E}_{\theta}(\mathbf{x})) d\mathbf{x} \tag{24.8} \\
\overset{(i)}{=} \left( \int \exp(-\mathcal{E}_{\theta}(\mathbf{x})) d\mathbf{x} \right)^{-1} \nabla_{\theta} \int \exp(-\mathcal{E}_{\theta}(\mathbf{x})) d\mathbf{x} \tag{24.9} \\
&= \left( \int \exp(-\mathcal{E}_{\theta}(\mathbf{x})) d\mathbf{x} \right)^{-1} \int \nabla_{\theta} \exp(-\mathcal{E}_{\theta}(\mathbf{x})) d\mathbf{x} \tag{24.10} \\
\overset{(ii)}{=} \left( \int \exp(-\mathcal{E}_{\theta}(\mathbf{x})) d\mathbf{x} \right)^{-1} \int \exp(-\mathcal{E}_{\theta}(\mathbf{x})) (-\nabla_{\theta} \mathcal{E}_{\theta}(\mathbf{x})) d\mathbf{x} \tag{24.11} \\
&= \int \left( \int \exp(-\mathcal{E}_{\theta}(\mathbf{x})) d\mathbf{x} \right)^{-1} \exp(-\mathcal{E}_{\theta}(\mathbf{x})) (-\nabla_{\theta} \mathcal{E}_{\theta}(\mathbf{x})) d\mathbf{x} \tag{24.12} \\
\overset{(iii)}{=} \int \frac{1}{Z_{\theta}} \exp(-\mathcal{E}_{\theta}(\mathbf{x})) (-\nabla_{\theta} \mathcal{E}_{\theta}(\mathbf{x})) d\mathbf{x} \tag{24.13} \\
\overset{(iv)}{=} \int p_{\theta}(\mathbf{x}) (-\nabla_{\theta} \mathcal{E}_{\theta}(\mathbf{x})) d\mathbf{x} \tag{24.14} \\
&= \mathbb{E}_{\mathbf{x} \sim p_{\theta}(\mathbf{x})} [ -\nabla_{\theta} \mathcal{E}_{\theta}(\mathbf{x}) ] , \tag{24.15}
\end{align}
\]

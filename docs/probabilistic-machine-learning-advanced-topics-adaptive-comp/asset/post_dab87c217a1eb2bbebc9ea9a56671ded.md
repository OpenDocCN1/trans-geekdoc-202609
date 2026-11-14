
![](img/ca72c1626f4850f058a9edc138c1ac73_190_0.png)

Figure 4.10: A DPGM representing the joint distribution p(z_{1:N}, x_{1:N}, \theta_z, \theta_x). The local variables z_n are hidden, whereas x_n are observed. This is typical for learning unsupervised latent variable models.

However, we notice there are a lot of zeros in the sufficient statistics, due to the small sample size, resulting in extreme estimates for some of the probabilities \hat{\theta}_{ijk}. We discuss a (Bayesian) solution to this in Section 4.2.7.3.

### 4.2.7.3 Example: computing the posterior for CPTs

In Section 4.2.7.2 we discussed how to compute the MLE for the CPTs in a discrete Bayes net. We also observed that this can suffer from the zero-count problem. In this section, we show how a Bayesian approach can solve this problem.

Let us put a separate Dirichlet prior on each row of each CPT, i.e., \theta_{ij} ~ Dir(\alpha_{ij}). Then we can compute the posterior by simply adding the pseudocounts to the empirical counts to get \theta_{ij} | D ~ Dir(N_{ij} + \alpha_{ij}), where N_{ij} = {N_{ijk} : k = 1 : K_i}, and N_{ijk} is the number of times that node i is in state k while its parents are in state j. Hence the posterior mean estimate is given by

```
\bar{\theta}_{ijk} = \frac{N_{ijk} + \alpha_{ijk}}{\sum_{k'}(N_{ijk'} + \alpha_{ijk'})} (4.48)
```

The MAP estimate has the same form, except we use \alpha_{ijk} - 1 instead of \alpha_{ijk}.

In Table 4.3, we illustrate this approach applied to the G node in the student network, where we use a uniform Dirichlet prior, \alpha_{ijk} = 1.

### 4.2.7.4 Learning from incomplete data

In Section 4.2.7.1, we explained that when we have complete data, the likelihood (and posterior) factorizes over CPDs, so we can estimate each CPD independently. Unfortunately, this is no longer the case when we have incomplete or missing data. To see this, consider Figure 4.10. The likelihood of the observed data can be written as follows:

```
p(\mathcal{D}|\theta) = \sum_{z_{1:N}} [\prod_{n=1}^N p(z_n|\theta_z)p(x_n|z_n, \theta_x)] (4.49)
```

```
= \prod_{n=1}^N \sum_{z_n} p(z_n|\theta_z)p(x_n|z_n, \theta_x) (4.50)
```

Thus the log likelihood is given by

```
\ell(\boldsymbol{\theta}) = \sum_{n} \log \sum_{\boldsymbol{z}_n} p(\boldsymbol{z}_n | \boldsymbol{\theta}_z) p(\boldsymbol{x}_n | \boldsymbol{z}_n, \boldsymbol{\theta}_x)
```

The log function does not distribute over the \sum_{\boldsymbol{z}_n} operation, so the objective does not decompose over nodes.^2 Consequently, we can no longer compute the MLE or the posterior by solving separate problems per node.

To solve this, we will resort to optimization methods. (We focus on the MLE case, and leave discussion of Bayesian inference for latent variable models to Part II.) In the sections below, we discuss how to use EM and SGD to find a local optimum of the (non convex) log likelihood objective.

### 4.2.7.5 Using EM to fit CPTs in the incomplete data case

A popular method for estimating the parameters of a DPGM in the presence of missing data is to use the expectation maximization (EM) algorithm, as proposed in [Lau95]. We describe EM in detail in Section 6.5.3, but the basic idea is to alternate between inferring the latent variables \boldsymbol{z}_n (the E or expectation step), and estimating the parameters given this completed dataset (the M or maximization step). Rather than returning the full posterior p(\boldsymbol{z}_n | \boldsymbol{x}_n, \boldsymbol{\theta}^{(t)}) in the E step, we instead return the expected sufficient statistics (ESS), which takes much less space. In the M step, we maximize the expected value of the log likelihood of the fully observed data using these ESS.

As an example, suppose all the CPDs are tabular, as in the example in Section 4.2.7.2. The log-likelihood of the complete data is given by

```
\log p(\mathcal{D} | \boldsymbol{\theta}) = \sum_{i=1}^{N_G} \sum_{j=1}^{J_i} \sum_{k=1}^{K_i} N_{ijk} \log \theta_{ijk}
```

and hence the expected complete data log-likelihood has the form

```
\mathbb{E} [\log p(\mathcal{D} | \boldsymbol{\theta})] = \sum_{i} \sum_{j} \sum_{k} \overline{N}_{ijk} \log \theta_{ijk}
```

where

```
\overline{N}_{ijk} = \sum_{n=1}^{N} \mathbb{E} [\mathbb{I} [ (x_{ni} = k, \boldsymbol{x}_{n, \text{pa}(i)} = j) ] ] = \sum_{n=1}^{N} p(x_{ni} = k, \boldsymbol{x}_{n, \text{pa}(i)} = j | \mathcal{D}_n, \boldsymbol{\theta}^{old})
```

where \mathcal{D}_n are all the visible variables in case n, and \boldsymbol{\theta}^{old} are the parameters from the previous iteration. The quantity p(x_{ni}, \boldsymbol{x}_{n, \text{pa}(i)} | \mathcal{D}_n, \boldsymbol{\theta}^{old}) is known as a family marginal, and can be computed using any GM inference algorithm. The \overline{N}_{ijk} are the expected sufficient statistics (ESS), and constitute the output of the E step.

2. We can also see this from the graphical model: \boldsymbol{\theta}_x is no longer independent of \boldsymbol{\theta}_z, because there is a path that connects them via the hidden nodes \boldsymbol{z}_n. (See Section 4.2.4 for an explanation of how to “read off” such CI properties from a DPGM.)

Given these ESS, the M step has the simple form

$$\hat{\theta}_{ijk} = \frac{N_{ijk}}{\sum_{k'} N_{ijk'}}$$ (4.55)

We can modify this to perform MAP estimation with a Dirichlet prior by simply adding pseudocounts to the expected counts.

The famous Baum-Welch algorithm is a special case of the above equations which arises when the DPGM is an HMM (see Section 29.4.1 for details).

### 4.2.7.6 Using SGD to fit CPTs in the incomplete data case

The EM algorithm is a batch algorithm. To scale up to large datasets, it is more common to use stochastic gradient descent or SGD (see e.g., [BC94; Bin+97]). To apply this, we need to compute the marginal likelihood of the observed data for each example:

$$p(\boldsymbol{x}_n|\boldsymbol{\theta}) = \sum_{\boldsymbol{z}_n} p(\boldsymbol{z}_n|\boldsymbol{\theta}_z)p(\boldsymbol{x}_n|\boldsymbol{z}_n, \boldsymbol{\theta}_x)$$ (4.56)

where $\boldsymbol{\theta} = (\boldsymbol{\theta}_z, \boldsymbol{\theta}_x).$ (We say that we have “collapsed” the model by marginalizing out $\boldsymbol{z}_n$.) We can then compute the log likelihood using

$$\ell(\boldsymbol{\theta}) = \log p(\mathcal{D}|\boldsymbol{\theta}) = \log \prod_{n=1}^N p(\boldsymbol{x}_n|\boldsymbol{\theta}) = \sum_{n=1}^N \log p(\boldsymbol{x}_n|\boldsymbol{\theta})$$ (4.57)

The gradient of this objective can be computed as follows:

$$\nabla_\theta \ell(\theta) = \sum_n \nabla_\theta \log p(\boldsymbol{x}_n|\boldsymbol{\theta})$$ (4.58)
$$= \sum_n \frac{1}{p(\boldsymbol{x}_n|\boldsymbol{\theta})} \nabla_\theta p(\boldsymbol{x}_n|\boldsymbol{\theta})$$ (4.59)
$$= \sum_n \frac{1}{p(\boldsymbol{x}_n|\boldsymbol{\theta})} \nabla_\theta \mathbb{E}_\theta \left[ \sum_{\boldsymbol{z}_n} p(\boldsymbol{z}_n, \boldsymbol{x}_n|\boldsymbol{\theta}) \right]$$ (4.60)
$$= \sum_n \sum_{\boldsymbol{z}_n} \frac{p(\boldsymbol{z}_n, \boldsymbol{x}_n|\boldsymbol{\theta})}{p(\boldsymbol{x}_n|\boldsymbol{\theta})} \nabla_\theta \log p(\boldsymbol{z}_n, \boldsymbol{x}_n|\boldsymbol{\theta})$$ (4.61)
$$= \sum_n \sum_{\boldsymbol{z}_n} p(\boldsymbol{z}_n|\boldsymbol{x}_n, \boldsymbol{\theta}) \nabla_\theta \log p(\boldsymbol{z}_n, \boldsymbol{x}_n|\boldsymbol{\theta})$$ (4.62)

We can now apply a minibatch approximation to this in the usual way.

## 4.2.8 Plate notation

To make the parameters of a PGM explicit, we can add them as nodes to the graph, and treat them as hidden variables to be inferred. Figure 4.11(a) shows a simple example, in which we have N iid

![](img/ca72c1626f4850f058a9edc138c1ac73_193_0.png)

Figure 4.11: Left: datapoints $\mathbf{x}_n$ are conditionally independent given $\theta$. Right: Same model, using plate notation. This represents the same model as the one on the left, except the repeated $\mathbf{x}_n$ nodes are inside a box, known as a plate; the number in the lower right hand corner, $N$, specifies the number of repetitions of the $\mathbf{x}_n$ node.

random variables, $\mathbf{x}_n$, all drawn from the same distribution with common parameter $\theta$. We denote this by

```
$$\mathbf{x}_n \sim p(\mathbf{x}|\theta)$$
```

The corresponding joint distribution over the parameters and data $\mathcal{D} = \{\mathbf{x}_1, \dots, \mathbf{x}_N\}$ has the form

```
$$p(\mathcal{D}, \theta) = p(\theta)p(\mathcal{D}|\theta)$$
```

where $p(\theta)$ is the prior distribution for the parameters, and $p(\mathcal{D}|\theta)$ is the likelihood. By virtue of the iid assumption, the likelihood can be rewritten as follows:

```
$$p(\mathcal{D}|\theta) = \prod_{n=1}^N p(\mathbf{x}_n|\theta)$$
```

Notice that the order of the data vectors is not important for defining this model, i.e., we can permute the leaves of the DPGM. When this property holds, we say that the data is **exchangeable**.

In Figure 4.11(a), we see that the $\mathbf{x}$ nodes are repeated $N$ times. (The **shaded** nodes represent observed values, whereas the unshaded (hollow) nodes represent latent variables or parameters.) To avoid visual clutter, it is common to use a form of syntactic sugar called **plates**. This is a notational convention in which we draw a little box around the repeated variables, with the understanding that nodes within the box will get repeated when the model is **unrolled**. We often write the number of copies or repetitions in the bottom right corner of the box. This is illustrated in Figure 4.11(b).

### 4.2.8.1 Example: factor analysis

In Section 28.3.1, we discuss the factor analysis model, which has the form

```
$$p(\mathbf{z}) = \mathcal{N}(\mathbf{z}|\mu_0, \mathbf{\Sigma}_0)$$
```

```
$$p(\mathbf{x}|\mathbf{z}) = \mathcal{N}(\mathbf{x}|\mathbf{W}\mathbf{z} + \mu, \mathbf{\Psi})$$
```

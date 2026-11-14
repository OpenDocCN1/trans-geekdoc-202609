
## 6.9.11 Structured norms and loss functions

Convex norms are used ubiquitously in machine learning, often as complexity penalizing regularizers (e.g., the ubiquitous p-norms for p >= 1) and also sometimes as losses (e.g., squared error). Identifying new useful structured and possibly learnable sparse norms is an interesting and useful endeavor, and submodularity can help here as well. Firstly, recall the l0 or counting norm ||x||_0 simply counts the number of nonzero entries in x. When we wish for a sparse solution, we may wish to regularize using ||x||_0 but it both leads to an intractable combinatorial optimization problem, and it leads to an object that is not differentiable. The usual approach is to find the closest convex relaxation of this norm and that is the 1-norm or ||x||_1. This is convex in x and has a sub-gradient structure and hence can be combined with a loss function to produce an optimizable machine learning objective, for example it is the lasso. On the other hand, ||x||_1 has no structure, as each element of x is penalized based on its absolute value irrespective of the state of any of the other elements. There have thus been efforts to develop group norms that penalize groups or subsets of elements of x together, such as group lasso [HTW15].

It turns out that there is a way to utilize a submodular function as the regularizer. Penalizing x via ||x||_0 is identical to penalizing it via |V(x)| and note that m(A) = |A| is a modular function. Instead, we could penalize x via f(V(x)) for a submodular function f. Here, any element of x being non-zero would allow for a diminishing penalty of other elements of x being zero all according to the submodular function, and such cooperative penalties can be obtained via a submodular parameterization. Like when using the zero-norm ||x||_0, this leads to the same combinatorial problem due to continuous optimization of x with a penalty term of the form f(V(x)). To address this, we can use the Lovász extension \(\breve{f}(x)\) on a vector x. This function is convex, but it is not a norm, but if we consider the construct defined as ||x||_f = \(\breve{f}(|x|)\), it can be shown that this satisfies all the properties of a norm for all non-trivial submodular functions [PG98; Bac+13] (i.e., those normalized submodular functions for which f(v) > 0 for all v). In fact, the group lasso mentioned above is a special case for a particularly simple feature-based submodular function (a sum of min-truncated cardinality functions). But in principle, the same submodular design strategies mentioned in Section 6.9.6 can be used to produce a submodular function to instantiate an appropriate convex structured norm for a given machine learning problem.

## 6.9.12 Conclusions

We have only barely touched the surface of submodularity and how it applies to and can benefit machine learning. For more details, see [Bil22] and the many references contained therein. Considering once again the innocuous looking submodular inequality, then very much like the definition of convexity, we observe something that belies much of its complexity while opening the gates to wide and worthwhile avenues for machine learning exploration.

## PART II

### Inference

## 7 Inference algorithms: an overview

### 7.1 Introduction

In the probabilistic approach to machine learning, all unknown quantities — be they predictions about the future, hidden states of a system, or parameters of a model — are treated as random variables, and endowed with probability distributions. The process of **inference** corresponds to computing the posterior distribution over these quantities, conditioning on whatever data is available.

In more detail, let $\theta$ represent the unknown variables, and $\mathcal{D}$ represent the known variables. Given a likelihood $p(\mathcal{D}|\theta)$ and a prior $p(\theta)$, we can compute the posterior $p(\theta|\mathcal{D})$ using Bayes’ rule:

\( p(\theta|\mathcal{D}) = \frac{p(\theta)p(\mathcal{D}|\theta)}{p(\mathcal{D})} \) (7.1)

The main computational bottleneck is computing the normalization constant in the denominator, which requires solving the following high dimensional integral:

\( p(\mathcal{D}) = \int p(\mathcal{D}|\theta)p(\theta)d\theta \) (7.2)

This is needed to convert the unnormalized joint probability of some parameter value, $p(\theta, \mathcal{D})$, to a normalized probability, $p(\theta|\mathcal{D})$, which takes into account all the other plausible values that $\theta$ could have.

Once we have the posterior, we can use it to compute posterior expectations of some function of the unknown variables, i.e.,

\( \mathbb{E} [g(\theta)|\mathcal{D}] = \int g(\theta)p(\theta|\mathcal{D})d\theta \) (7.3)

By defining $g$ in the appropriate way, we can compute many quantities of interest, such as the following:

- mean: $g(\theta) = \theta$ (7.4)
- covariance: $g(\theta) = (\theta - \mathbb{E} [\theta|\mathcal{D}])(\theta - \mathbb{E} [\theta|\mathcal{D}])^\top$ (7.5)
- marginals: $g(\theta) = p(\theta_1 = \theta_1^*|\theta_{2:D})$ (7.6)
- predictive: $g(\theta) = p(y_{N+1}|\theta)$ (7.7)
- expected loss: $g(\theta) = \ell(\theta, a)$ (7.8)

![](img/ca72c1626f4850f058a9edc138c1ac73_371_0.png)

Figure 7.1: Graphical models with (a) global hidden variables for representing the Bayesian discriminative model \( p(y_{1:N}, \theta_y | x_{1:N}) = p(\theta_y) \prod_{n=1}^N p(y_n | x_n, \theta_y) \); (b) local hidden variables for representing the generative model \( p(x_{1:N}, z_{1:N} | \theta) = \prod_{n=1}^N p(z_n | \theta_z) p(x_n | z_n, \theta_x) \); (c) local and global hidden variables for representing the Bayesian generative model \( p(x_{1:N}, z_{1:N}, \theta) = p(\theta_z) p(\theta_x) \prod_{n=1}^N p(z_n | \theta_z) p(x_n | z_n, \theta_x) \). Shaded nodes are assumed to be known (observed), unshaded nodes are hidden.

where \(\boldsymbol{y}_{N+1}\) is the next observation after seeing the \( N \) examples in \( \mathcal{D} \), and the posterior expected loss is computed using loss function \( \ell \) and action \( a \) (see Section 34.1.3). Finally, if we define \( g(\theta) = p(\mathcal{D} | \theta, M) \) for model \( M \), we can also phrase the marginal likelihood (Section 3.8.3) as an expectation wrt the prior:

\( \mathbb{E}[g(\theta) | \mathcal{D}] = \int g(\theta) p(\theta | M) d\theta = \int p(\mathcal{D} | \theta, M) p(\theta | M) d\theta = p(\mathcal{D} | M) \) (7.9)

Thus we see that integration (and computing expectations) is at the heart of Bayesian inference, whereas differentiation is at the heart of optimization.

In this chapter, we give a high level summary of algorithmic techniques for computing (approximate) posteriors, and/or their corresponding expectations. We will give more details in the following chapters. Note that most of these methods are independent of the specific model. This allows problem solvers to focus on creating the best model possible for the task, and then relying on some inference engine to do the rest of the work — this latter process is sometimes called “turning the Bayesian crank”. For more details on Bayesian computation, see e.g., [Gel+14a; MKL21; MFR20].

### 7.2 Common inference patterns

There are kinds of posterior we may want to compute, but we can identify 3 main patterns, as we discuss below. These give rise to different types of inference algorithm, as we will see in later chapters.

### 7.2.1 Global latents

The first pattern arises when we need to perform inference in models which have **global latent variables**, such as parameters of a model \( \theta \), which are shared across all \( N \) observed training cases. This is shown in Figure 7.1a, and corresponds to the usual setting for supervised or discriminative learning, where the joint distribution has the form

$$ p(\boldsymbol{y}_{1:N}, \boldsymbol{\theta}|\boldsymbol{x}_{1:N}) = p(\boldsymbol{\theta}) \left[ \prod_{n=1}^N p(\boldsymbol{y}_n|\boldsymbol{x}_n, \boldsymbol{\theta}) \right] $$
(7.10)

The goal is to compute the posterior \(p(\boldsymbol{\theta}|\boldsymbol{x}_{1:N}, \boldsymbol{y}_{1:N})\). Most of the Bayesian supervised learning models discussed in Part III follow this pattern.

### 7.2.2 Local latents

The second pattern arises when we need to perform inference in models which have **local latent variables**, such as hidden states \(\boldsymbol{z}_{1:N}\); we assume the model parameters \(\boldsymbol{\theta}\) are known. This is shown in Figure 7.1b. Now the joint distribution has the form

$$ p(\boldsymbol{x}_{1:N}, \boldsymbol{z}_{1:N}|\boldsymbol{\theta}) = \left[ \prod_{n=1}^N p(\boldsymbol{x}_n|\boldsymbol{z}_n, \boldsymbol{\theta}_x)p(\boldsymbol{z}_n|\boldsymbol{\theta}_z) \right] $$
(7.11)

The goal is to compute \(p(\boldsymbol{z}_n|\boldsymbol{x}_n, \boldsymbol{\theta})\) for each \(n\). This is the setting we consider for most of the PGM inference methods in Chapter 9.

If the parameters are not known (which is the case for most latent variable models, such as mixture models), we may choose to estimate them by some method (e.g., maximum likelihood), and then plug in this point estimate. The advantage of this approach is that, conditional on \(\boldsymbol{\theta}\), all the latent variables are conditionally independent, so we can perform inference in parallel across the data. This lets us use methods such as expectation maximization (Section 6.5.3), in which we infer \(p(\boldsymbol{z}_n|\boldsymbol{x}_n, \boldsymbol{\theta}_t)\) in the E step for all \(n\) simultaneously, and then update \(\boldsymbol{\theta}_t\) in the M step. If the inference of \(\boldsymbol{z}_n\) cannot be done exactly, we can use variational inference, a combination known as variational EM (Section 6.5.6.1).

Alternatively, we can use a minibatch approximation to the likelihood, marginalizing out \(\boldsymbol{z}_n\) for each example in the minibatch to get

$$ \log p(\mathcal{D}_t|\boldsymbol{\theta}_t) = \sum_{n \in \mathcal{D}_t} \log \left[ \sum_{\boldsymbol{z}_n} p(\boldsymbol{x}_n, \boldsymbol{z}_n|\boldsymbol{\theta}_t) \right] $$
(7.12)

where \(\mathcal{D}_t\) is the minibatch at step \(t\). If the marginalization cannot be done exactly, we can use variational inference, a combination known as stochastic variational inference or SVI (Section 10.1.4). We can also learn an inference network \(q_\phi(\boldsymbol{z}|\boldsymbol{x}; \boldsymbol{\theta})\) to perform the inference for us, rather than running an inference engine for each example \(n\) in each batch \(t\); the cost of learning \(\boldsymbol{\phi}\) can be amortized across the batches. This is called amortized SVI (see Section 10.1.5).

### 7.2.3 Global and local latents

The third pattern arises when we need to perform inference in models which have **local and global latent variables**. This is shown in Figure 7.1c, and corresponds to the following joint distribution:

$$ p(\boldsymbol{x}_{1:N}, \boldsymbol{z}_{1:N}, \boldsymbol{\theta}) = p(\boldsymbol{\theta}_x)p(\boldsymbol{\theta}_z) \left[ \prod_{n=1}^N p(\boldsymbol{x}_n|\boldsymbol{z}_n, \boldsymbol{\theta}_x)p(\boldsymbol{z}_n|\boldsymbol{\theta}_z) \right] $$
(7.13)

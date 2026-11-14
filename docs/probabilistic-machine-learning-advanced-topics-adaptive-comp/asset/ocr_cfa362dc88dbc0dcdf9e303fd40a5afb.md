in Figure 15.2a. We can fix this problem by using **polynomial regression**. For example, consider a quadratic expansion of the standardized features \(x_i\):

\(\mu_i = \alpha + \beta_1 x_i + \beta_2 x_i^2 \quad \text{(15.85)}\)

If we use a log-Gaussian prior for \(\beta_2\), we find that the model is too constrained, and it underfits. This is illustrated in Figure 15.2b. The reason is that we need to use an inverted quadratic with a negative coefficient, but since this is disallowed by the prior, the model ends up not using this degree of freedom (we find \(\mathbb{E}[\beta_2|\mathcal{D}] \approx 0.08\)). If we use a Gaussian prior on \(\beta_2\), we avoid this problem, illustrated in Figure 15.2c.

This example shows that it can be useful to think about the functional form of the mapping from inputs to outputs in order to specify sensible priors.

# ## 15.2.5 Spike and slab prior

It is often useful to be able to select a subset of the input features when performing prediction, either to reduce overfitting, or to improve interpretability of the model. This can be achieved if we ensure that the weight vector \(\boldsymbol{w}\) is **sparse** (i.e., has many zero elements), since if \(w_d = 0\), then \(x_d\) plays no role in the inner product \(\boldsymbol{w}^\top \boldsymbol{x}\).

The canonical way to achieve sparsity when using Bayesian inference is to use a **spike-and-slab (SS) prior** [MB88], which has the form of a 2 component mixture model, with one component being a “spike” at 0, and the other being a uniform “slab” between \(-a\) and \(a\):

\(p(\boldsymbol{w}) = \prod_{d=1}^D (1 - \pi)\delta(w_d) + \pi \text{Unif}(w_d \mid -a, a) \quad \text{(15.86)}\)

where \(\pi\) is the prior probability that each coefficient is non-zero. The corresponding log prior on the coefficients is thus

\(\log p(\boldsymbol{w}) = ||\boldsymbol{w}||_0 \log(1 - \pi) + (D - ||\boldsymbol{w}||_0) \log \pi = -\lambda ||\boldsymbol{w}||_0 + \text{const} \quad \text{(15.87)}\)

where \(\lambda = \log \frac{\pi}{1 - \pi}\) controls the sparsity of the model, and \(||\boldsymbol{w}||_0 = \sum_{d=1}^D \mathbb{I}(w_d \neq 0)\) is the \(\ell_0\) **norm** of the weights. Thus MAP estimation with a spike and slab prior is equivalent \(\ell_0\) **regularization**; this penalizes the number of non-zero coefficients. Interestingly, posterior samples will also be sparse. By contrast, consider using a Laplace prior. The **lasso** estimator uses MAP estimation, which results in a sparse estimate. However, posterior samples are not sparse. Interestingly, [EY09] show theoretically (and [SPZ09] confirm experimentally) that using the posterior mean with a spike-and-slab prior also results in better prediction accuracy than using the posterior mode with a Laplace prior.

In practice, we often approximate the uniform slab with a broad Gaussian distribution,

\(p(\boldsymbol{w}) = \prod_d (1 - \pi)\delta(w_d) + \pi \mathcal{N}(w_d \mid 0, \sigma_w^2) \quad \text{(15.88)}\)

As \(\sigma_w^2 \rightarrow \infty\), the second term approaches a uniform distribution over \([-\infty, +\infty]\). We can implement the mixture model by associating a binary random variable, \(s_d \sim \text{Ber}(\pi)\), with each coefficient, to indicate if the coefficient is “on” or “off”.
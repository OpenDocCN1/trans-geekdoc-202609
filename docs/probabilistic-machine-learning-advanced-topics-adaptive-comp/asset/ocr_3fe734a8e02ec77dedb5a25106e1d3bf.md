the space of possible values into a finite set of regions, call them \(\boldsymbol{r}_1, \dots, \boldsymbol{r}_K\), each representing a region of parameter space of volume \(\Delta\) centered on \(\boldsymbol{\theta}_k\). This is called a **grid approximation**. The probability of being in each region is given by \(p(\boldsymbol{\theta} \in \boldsymbol{r}_k | \mathcal{D}) \approx p_k \Delta\), where

\(p_k = \frac{\tilde{p}_k}{\sum_{k'=1}^K \tilde{p}_{k'}}\) (7.20)
\(\tilde{p}_k = p(\mathcal{D}|\boldsymbol{\theta}_k)p(\boldsymbol{\theta}_k)\) (7.21)

As \(K\) increases, we decrease the size of each grid cell. Thus the denominator is just a simple numerical approximation of the integral

\(p(\mathcal{D}) = \int p(\mathcal{D}|\boldsymbol{\theta})p(\boldsymbol{\theta})d\boldsymbol{\theta} \approx \sum_{k=1}^K \Delta \tilde{p}_k\) (7.22)

As a simple example, we will use the problem of approximating the posterior of a beta-Bernoulli model. Specifically, the goal is to approximate

\(p(\boldsymbol{\theta}|\mathcal{D}) \propto \left[ \prod_{n=1}^N \text{Ber}(y_n|\boldsymbol{\theta}) \right] \text{Beta}(1,1)\) (7.23)

where \(\mathcal{D}\) consists of 10 heads and 1 tail (so the total number of observations is \(N=11\)), with a uniform prior. Although we can compute this posterior exactly using the method discussed in Section 3.4.1, this serves as a useful pedagogical example since we can compare the approximation to the exact answer. Also, since the target distribution is just 1d, it is easy to visualize the results.

In Figure 7.3a, we illustrate the grid approximation applied to our 1d problem. We see that it is easily able to capture the skewed posterior (due to the use of an imbalanced sample of 10 heads and 1 tail). Unfortunately, this approach does not scale to problems in more than 2 or 3 dimensions, because the number of grid points grows exponentially with the number of dimensions.

# 7.4.3 Laplace (quadratic) approximation

In this section, we discuss a simple way to approximate the posterior using a multivariate Gaussian; this known as a **Laplace approximation** or **quadratic approximation** (see e.g., [TK86; RMC09]).

Suppose we write the posterior as follows:

\(p(\boldsymbol{\theta}|\mathcal{D}) = \frac{1}{Z} e^{-\mathcal{E}(\boldsymbol{\theta})}\) (7.24)

where \(\mathcal{E}(\boldsymbol{\theta}) = -\log p(\boldsymbol{\theta},\mathcal{D})\) is called an energy function, and \(Z = p(\mathcal{D})\) is the normalization constant. Performing a Taylor series expansion around the mode \(\hat{\boldsymbol{\theta}}\) (i.e., the lowest energy state) we get

\(\mathcal{E}(\boldsymbol{\theta}) \approx \mathcal{E}(\hat{\boldsymbol{\theta}}) + (\boldsymbol{\theta}-\hat{\boldsymbol{\theta}})^\mathsf{T} \boldsymbol{g} + \frac{1}{2}(\boldsymbol{\theta}-\hat{\boldsymbol{\theta}})^\mathsf{T} \mathbf{H} (\boldsymbol{\theta}-\hat{\boldsymbol{\theta}})\) (7.25)

where \(\boldsymbol{g}\) is the gradient at the mode, and \(\mathbf{H}\) is the Hessian. Since \(\hat{\boldsymbol{\theta}}\) is the mode, the gradient term is
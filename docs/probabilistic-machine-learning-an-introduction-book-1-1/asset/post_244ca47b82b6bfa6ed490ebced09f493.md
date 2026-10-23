
Various approaches have been proposed for setting $g$, including cross validation, empirical Bayes [Min00a; GF00], hierarchical Bayes [Lia+08], etc.

## 11.6.4 Sparsity-promoting priors

In this section, we discuss Bayesian inference for the parameters of linear regression models using sparsity-promoting priors.

### 11.6.4.1 Spike and slab prior

The canonical way to achieve sparsity when using Bayesian inference is to use a **spike-and-slab** (SS) prior [MB88], which has the form of a 2 component mixture model, with one component being a “spike” at 0, and the other being a uniform “slab” between $-a$ and $a$:

$p(\mathbf{w}) = \prod_{d=1}^{D} (1 - \pi)\delta(w_d) + \pi \text{Unif}(w_d | -a, a)$  (11.160)

where $\pi$ is the prior probability that each coefficient is non-zero. The corresponding log prior on the coefficients is thus

$\log p(\mathbf{w}) = \|\mathbf{w}\|_0 \log(1 - \pi) + (D - \|\mathbf{w}\|_0) \log \pi = -\lambda \|\mathbf{w}\|_0 + \text{const}$  (11.161)

where $\lambda = \log \frac{\pi}{1-\pi}$ controls the sparsity of the model, and $\|\mathbf{w}\|_0 = \sum_{d=1}^{D} \mathbb{I}(w_d \neq 0)$ is the $\ell_0$ **norm** of the weights. Thus MAP estimation with a spike and slab prior is equivalent to $\ell_0$ **regularization**; this penalizes the number of non-zero coefficients. However, posterior samples will also be sparse, which is not the case under a Laplace prior discussed in Sec. 11.5. Interestingly, [EY09] show theoretically (and [SPZ09] confirm experimentally) that using the posterior mean with a spike-and-slab prior also results in better prediction accuracy than using the posterior mode with a Laplace prior.

In practice, we often approximate the uniform slab with a broad Gaussian distribution,

$p(\mathbf{w}) = \prod_{d} (1 - \pi)\delta(w_d) + \pi \mathcal{N}(w_d | 0, \sigma_w^2)$  (11.162)

As $\sigma_w^2 \to \infty$, the second term approaches a uniform distribution over $[-\infty, +\infty]$. We can implement the mixture model by associating a binary random variable, $s_d \sim \text{Ber}(\pi)$, with each coefficient, to indicate if the coefficient is “on” or “off”.

Unfortunately, MAP estimation (not to mention full Bayesian inference) with such discrete mixture priors is computationally difficult. Various approximate inference methods have been proposed, including greedy search (see e.g., [SPZ09]) or MCMC (see e.g., [HS09]).

### 11.6.4.2 Laplace prior

A computationally cheap way to achieve sparsity is to perform MAP estimation with a Laplace prior, as in the lasso (Sec. 11.5). In this section, we discuss posterior inference with this prior; this is known as the **Bayesian lasso**. In particular, we assume the following prior:

$p(\mathbf{w} | \sigma^2) = \prod_{j} \frac{\lambda}{2\sqrt{\sigma^2}} e^{-\lambda |w_j| / \sqrt{\sigma^2}}$  (11.163)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_391_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_391_1.png)

*Figure 11.20: (a) Representing lasso using a Gaussian scale mixture prior. (b) Graphical model for group lasso with 2 groups, the first has size G₁ = 2, the second has size G₂ = 3.*

(Note that conditioning the prior on σ² is important to ensure that the full posterior is unimodal.)

To simplify inference, we will represent the Laplace prior as a Gaussian scale mixture, which we discussed in Sec. 3.7.3.2. In particular, one can show that the Laplace distribution is an infinite weighted sum of Gaussians, where the precision comes from a Gamma distribution:

Lap(w|0, λ) = ∫ N(w|0, τ²) Ga(τ²|1, λ²/2) dτ²  (11.164)

We can therefore represent the Bayesian lasso model as a hierarchical latent variable model, as shown in Fig. 11.20a. The corresponding joint distribution has the following form:

p(y, w, τ, σ²|X) = N(y|Xw, σ²I_N) [∏_j N(w_j|0, σ²τ_j²) Ga(τ_j²|1, λ²/2)] p(σ²)  (11.165)

We can also create a GSM to match the group lasso prior in Sec. 11.5.7. In particular, one can show (Exercise 11.10) that the group lasso prior is equivalent to the following:

w_g|σ², τ_g² ~ N(0, σ²τ_g² I_{d_g})  (11.166)
τ_g² ~ Ga((d_g + 1)/2, λ²/2)  (11.167)

where d_g is the size of group g. So we see that there is one variance term per group, each of which comes from a Gamma prior, whose shape parameter depends on the group size, and whose rate parameter is controlled by γ.

Fig. 11.20b gives an example, where we have 2 groups, one of size 2 and one of size 3. This picture makes it clearer why there should be a grouping effect. For example, suppose w₁,₁ is small; then τ₁² will be estimated to be small, which will force w₁,₂ to be small, due to shrinkage (c.f., Sec. 7.4). Conversely, suppose w₁,₁ is large; then τ₁² will be estimated to be large, which will allow w₁,₂ to be become large as well.

Given these hierarchical models, we can easily derive a Gibbs sampling algorithm (Sec. 7.7.4) to sample from the posterior (see e.g., [PC08]). Unfortunately, these posterior samples are not sparse,

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_392_0.png)

even though the MAP estimate is sparse. This is because the prior puts infinitesimal probability on the event that each coefficient is zero.

The Laplace prior is not suitable for sparse Bayesian models, because posterior samples are not sparse. Furthermore, the spike and slab prior is often too slow to use. Fortunately, it is possible to devise continuous priors (without discrete latent variables) that are both sparse and efficient. One popular prior of this type is the horseshoe prior [CPS10]. so-named because of the shape of its density function.

```
w_j ~ N(0, λ_j² τ²) (11.168)
λ_j ~ C_+(0,1) (11.169)
```

where C_+(0,1) is the half-Cauchy distribution (Sec. 3.4.2), λ_j is a local shrinkage factor, and τ² a global shrinkage factor. The Cauchy distribution has very fat tails, so λ_j is likely to be either 0 or very far from 0, which emulates the spike and slab prior. For more details, see e.g., [Bha+19].

In this section, we consider a hierarchical Bayesian model for multiple related linear regressions. We apply it to a simplified version of the radon example from [Gel+14, Sec 9.4].

Radon is known to be the highest cause of lung cancer in non-smokers, so reducing it where possible is desirable. To help with this, we fit a regression model, that predicts the (log) radon level as a function of the location of the house, as represented by a categorical feature indicating its county, and

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_393_0.png)

Figure 11.22: Posterior marginals for α_c and β_c for each county in the radon model. Generated by linreg_hierarchical_pymc3.ipynb.

a binary feature representing whether the house has a basement or not. We use a dataset consisting of C = 85 counties in Minnesota; each county has between 2 and 80 measurements.

We assume the following likelihood:

$y_n|x_n = (c, f), \theta \sim \mathcal{N}(\alpha_c + \beta_c f, \sigma_y^2)$ (11.170)

where $c \in \{1, \dots, C\}$ is the county for house $n$, and $f \in \{0,1\}$ indicates if the floor is at level 0 (i.e., in the basement) or level 1 (i.e., above ground). Intuitively we expect the radon levels to be lower in houses without basements, since they are more insulated from the earth where the radon lives. Thus we want to compute $p(\beta|\mathcal{D})$, so we can test this hypothesis.

Since some counties have very few data points, we use a hierarchical prior in which we assume $\alpha_c \sim \mathcal{N}(\mu_\alpha, \sigma_\alpha^2)$ and $\beta_c \sim \mathcal{N}(\mu_\beta, \sigma_\beta^2)$. We use weak priors for the parameters: $\mu_\alpha \sim \mathcal{N}(0,1)$, $\mu_\beta \sim \mathcal{N}(0,1)$, $\sigma_\alpha \sim \mathcal{C}_+(1)$, $\sigma_\beta \sim \mathcal{C}_+(1)$, $\sigma_y \sim \mathcal{C}_+(1)$. See Fig. 11.21 for the graphical model.

We can perform posterior inference in this model using a variety of algorithms. In this section, we discuss the results of using HMC (Sec. 7.7.4), as implemented in the PyMC3 package.

Fig. 11.22 shows the posterior marginals for $\mu_\alpha$, $\mu_\beta$, $\alpha_c$ and $\beta_c$. We see that $\mu_\beta$ is close to -0.6 with high probability, which confirms our suspicion that having $f = 1$ (i.e., no basement) decreases the amount of radon in the house. We also see that the distribution of the $\alpha_c$ parameters is quite variable, due to different base rates across the counties.

Fig. 11.23 shows predictions from the hierarchical and non-hierarchical model for 3 different counties. We see that the predictions from the hierarchical model are more consistent across counties, and work well even if there are no examples of certain feature combinations for a given county (e.g., there are no houses without basements in the sample from Cass county). If we sample data from the posterior predictive distribution, and compare it to the real data, we find that the RMSE is 0.13 for the non-hierarchical model and 0.08 for the hierarchical model, indicating that the latter fits better.

One problem that frequently arises in hierarchical models is that the parameters become very

7. We use the code from Thomas Wiecki and Danne Elbers at https://twiecki.io/blog/2014/03/17/bayesian-glms-3/.

Then we update it with the new likelihood to get the posterior

$$\hat{p}(\theta_t) = \frac{1}{Z_t} p(\mathcal{D}_t|\theta_t) q_{t|t-1}(\theta_t) \tag{7.237}$$

where

$$Z_t = \int p(\mathcal{D}_t|\theta_t) q_{t|t-1}(\theta_t) d\theta \tag{7.238}$$

is the normalization constant. If the prior is from a suitably restricted family, this process is usually tractable. However, we often find that the resulting posterior is no longer in our tractable family, $\hat{p}(\theta_t) \notin \mathcal{Q}$. So after updating we seek the best tractable approximation by computing

$$q(\theta_t) = \argmin_{q \in \mathcal{Q}} \mathbb{KL}(\hat{p}(\theta_t) \| q(\theta_t)) \tag{7.239}$$

This minimizes the the Kullback-Leibler divergence (Sec. 6.2) from the approximation $q(\theta_t)$ to the (one-step) exact posterior $\hat{p}(\theta_t)$, and can be thought of as **projecting** $\hat{p}$ onto the space of tractable distributions, as sketched in Fig. 7.31. Thus the overall algorithm consists of three steps: predict, update, and project. (See also Sec. 11.6.7, where we discuss a similar algorithm for online Bayesian linear regression.)

If $q$ is in the exponential family, one can show that this KL minimization can be done by moment matching (Sec. 4.5). In the Gaussian case, this means that need to find the parameters of $q$ such that the means and variances match those of $p$. We give a concrete example of this in Sec. 10.6.5, where we apply the method to a Bayesian logistic regression model. See [GDFY16] for an application to Bayesian neural networks.

# 7.8 Exercises

**Exercise 7.1** [Gaussian posterior credible interval]

(Source: DeGroot.) Let $X \sim \mathcal{N}(\mu, \sigma^2 = 4)$ where $\mu$ is unknown but has prior $\mu \sim \mathcal{N}(\mu_0, \sigma_0^2 = 9)$. The posterior after seeing $n$ samples is $\mu \sim \mathcal{N}(\mu_n, \sigma_n^2)$. (This is called a credible interval, and is the Bayesian analog of a confidence interval.) How big does $n$ have to be to ensure

$$p(\ell \le \mu_n \le u | D) \ge 0.95 \tag{7.240}$$

where $(\ell, u)$ is an interval (centered on $\mu_n$) of width 1 and $D$ is the data? Hint: recall that 95% of the probability mass of a Gaussian is within $\pm1.96\sigma$ of the mean.

**Exercise 7.2** [BIC for Gaussians]

(Source: Jaakkola.)

The Bayesian information criterion (BIC) is a penalized log-likelihood function that can be used for model selection. It is defined as

$$BIC = \log p(\mathcal{D}|\hat{\theta}_{ML}) - \frac{d}{2} \log(N) \tag{7.241}$$

where $d$ is the number of free parameters in the model and $N$ is the number of samples. In this question, we will see how to use this to choose between a full covariance Gaussian and a Gaussian with a diagonal covariance. Obviously a full covariance Gaussian has higher likelihood, but it may not be "worth" the extra
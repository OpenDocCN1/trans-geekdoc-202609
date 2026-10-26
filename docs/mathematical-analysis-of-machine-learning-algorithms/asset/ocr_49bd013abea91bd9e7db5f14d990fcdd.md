# Theorem 8.7 Consider the model selection algorithm in (8.3), with

$$\tilde R(\theta, f, \mathcal{S}_n) = \tilde R(\theta) \ge 2R_n(\mathcal{F}(\theta), \mathcal{D}) + M(\theta)\sqrt{\frac{\ln(1/q(\theta))}{2n}},$$

where $M(\theta) = \sup_{f,z,z'} |\phi(f,z) - \phi(f,z')|$, and $q(\theta)$ satisfies (8.1). Then with probability at least $1-\delta$, for all $\theta$ and $f \in \mathcal{F}(\theta)$,

$$\phi(f, \mathcal{D}) \le \phi(f, \mathcal{S}_n) + \tilde R(\theta) + M(\theta)\sqrt{\frac{\ln(1/\delta)}{2n}}.$$

Moreover, we have the following oracle inequality. With probability of at least $1-\delta$,

$$\phi(\hat f, \mathcal{D}) \le \inf_{\theta, f \in \mathcal{F}(\theta)} \left[ \phi(f, \mathcal{D}) + \tilde R(\theta) + 2M(\theta)\sqrt{\frac{\ln(2/\delta)}{2n}} \right] + \tilde \epsilon.$$

Proof Note that from Corollary 6.19, we obtain for any $\theta$ with $h = 0$, with probability $1-\delta$, the following uniform convergence result holds for all $f \in \mathcal{F}(\theta)$:

$$\phi(f, \mathcal{D}) \le \phi(f, \mathcal{S}_n) + 2R_n(\mathcal{F}(\theta), \mathcal{D}) + M(\theta)\sqrt{\frac{\ln(1/\delta)}{2n}}.$$

The choice of $\tilde R$ satisfies the condition of Theorem 8.5 with $c_0 = 1$ and $\beta = 0.5$. It implies the desired uniform convergence result.

Given fixed $\theta$ and $f \in \mathcal{F}(\theta)$, we know that

$$\big|\big[\phi(f, \mathcal{S}_n) + \tilde R(\theta)\big] - \big[\phi(f, \mathcal{S}'_n) + \tilde R(\theta)\big]\big| \le M(\theta)$$

when $\mathcal{S}_n$ and $\mathcal{S}'_n$ differ by one element. From McDiarmid's inequality, we know that with probability at least $1-\delta$, 

$$\phi(f, \mathcal{S}_n) + \tilde R(\theta) \le \phi(f, \mathcal{D}) + \tilde R(\theta) + M(\theta)\sqrt{\frac{\ln(1/\delta)}{2n}}.$$ 

It follows that we can take

$$\epsilon'(\theta, f, \delta) = M(\theta)\sqrt{\frac{\ln(1/\delta)}{2n}}$$

in Theorem 8.5, and obtain the desired oracle inequality.

Compared to Corollary 8.3, Theorem 8.7 achieves similar results using sample-dependent uniform convergence bounds. The resulting model selection algorithm (8.3) avoids partitioning data into training and validation parts, and can be used to design integrated algorithms that simultaneously estimate the model parameter and hyperparameter on the training data. However, the algorithm in (8.3) requires knowing the specific generalization bound for each model class, which may not be practical in some real applications.
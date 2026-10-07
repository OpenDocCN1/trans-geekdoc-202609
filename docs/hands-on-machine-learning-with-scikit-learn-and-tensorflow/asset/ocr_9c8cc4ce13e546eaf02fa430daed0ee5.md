In practice, there are different techniques to maximize the ELBO. In mean field variational inference, it is necessary to pick the family of distributions q(z; λ) and the prior p(z) very carefully to ensure that the equation for the ELBO simplifies to a form that can actually be computed. Unfortunately, there is no general way to do this, it depends on the task and requires mathematical skills. For example, the distributions and lower bound used in Scikit-Learn's BayesianGaussianMixture class are presented in the documentation. From these equations it is possible to derive updates for the cluster parameters and assignment variables: these are used much like in the Expectation-Maximization algorithm. In fact, the computational complexity of the BayesianMixture class is similar to that of the GaussianMixture class (but significantly slower). A simpler approach to maximizing the ELBO is called black box stochastic variational inference (BBSVI); at each iteration, a few samples are drawn from q and they are used to estimate the gradients of the ELBO with regards to the variational parameters λ, which are then used in a gradient ascent step. This approach makes it possible to use Bayesian inference with any kind of model (provided it is differentiable), even deep neural networks: this is called Bayesian learning.

If you want to dive deeper into Bayesian statistics, check out the Bayesian Data Analysis book by Andrew Gelman, John Carlin, Hal Stern, David Dunson, Aki Vehtari, and Donald Rubin.

![](bbox=[0.17, 0.437, 0.24, 0.503])

Gaussian mixture models work on clusters on ellipsoidal shapes, but if you try to fit a dataset with different shapes, you may have bad surprises. For example, let's see what happens if we use a Bayesian Gaussian mixture model to cluster the moons (see Figure 9-24):

![](bbox=[0.147, 0.622, 0.853, 0.756])

Figure 9-24. moons_vs_bgm_diagram

Oops, the algorithm desperately searched for ellipsoids, so it found 8 different clusters instead of 2. The density estimation is not too bad, so this model could be used for anomaly detection, but it failed to identify the two moons. Let's now look at a few clustering algorithms capable of dealing with arbitrarily shaped clusters.

Gaussian Mixtures | 273

WOW! eBook
www.wowebook.org
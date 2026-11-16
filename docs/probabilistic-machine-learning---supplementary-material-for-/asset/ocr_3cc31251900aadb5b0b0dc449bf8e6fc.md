![](bbox=[0.335, 0.095, 0.665, 0.27])

Figure 6.10: Illustration of the CMA-ES method applied to a simple 2d function. The dots represent members of the population, and the dashed orange ellipse represents the multivariate Gaussian. From https://en.wikipedia.org/wiki/CMA-ES. Used with kind permission of Wikipedia author Sentewolf.

# 6.3.5 Natural evolutionary strategies

Evolution strategies [Wie+14] are a form of distribution-based optimization in which the distribution over the population is represented by a Gaussian, p(x|theta_t) (see e.g., [Sal+17]). Unlike CEM, the parameters are updated using gradient ascent applied to the expected value of the objective using MLE on a set of elite samples. More precisely, consider the smoothed objective L(theta) = E_{p(x|theta)} [f(x)]. We can use the REINFORCE estimator (??) to compute the gradient of this objective as follows:

nabla_theta L(theta) = E_{p(x|theta)} [f(x) nabla_theta log p(x|theta)] (6.74)

This can be approximated by drawing Monte Carlo samples. If the probability model is in the exponential family, we can compute the natural gradient (??), rather than the "vanilla" gradient; such methods are called natural evolution strategies [Wie+14].

# 6.3.5.1 CMA-ES

The CMA-ES method of [Han16], which stands for "covariance matrix adaptation evolution strategy" is a kind of NES. It is very similar to CEM except it updates the parameters in a special way. In particular, instead of computing the new mean and covariance using unweighted MLE on the elite set, we attach weights to the elite samples based on their rank. We then set the new mean to the weighted MLE of the elite set.

The update equations for the covariance are more complex. In particular, "evolutionary paths" are also used to accumulate the search directions across successive generations, and these are used to update the covariance. It can be show that the resulting updates approximate the natural gradient of L(theta) without explicitly modeling the Fisher information matrix [Oll+17].

Figure 6.10 illustrates the method in action.

# 6.4 Dynamic programming

Dynamic programming is a way to efficiently find the globally optimal solution to certain kinds of optimization problems. The key requirement is that the optimal solution be expressed in terms of the optimal solution to smaller subproblems, which can be reused many times. Note that DP is more of an algorithm "family" rather than a specific algorithm. We give some examples below.
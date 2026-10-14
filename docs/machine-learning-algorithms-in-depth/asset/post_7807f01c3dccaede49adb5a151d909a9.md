
In other words, if we perform a random walk across the parameter space, the fraction of time we spend in a particular state $\theta$ is proportional to $p(\theta|x)$.

We begin by introducing MCMC in the following section. We'll proceed with three warm-up Monte Carlo examples (estimating pi, binomial tree model, and self-avoiding random walk) before looking at three popular sampling algorithms (Gibbs sampling, Metropolis-Hastings, and importance sampling). The warm-up algorithms in this chapter are selected to give the reader an appropriate introduction to MCMC, and the sampling algorithms are selected for their wide application in sampling from probabilistic graphical models (PGMs).

## 2.1 Introduction to Markov chain Monte Carlo

Let’s start by understanding high dimensional parameter spaces based on a simple example of classifying irises. An iris is a species of flowers consisting of three types: setosa, versicolor, and virginica. The flowers are characterized by their petal and sepal length and width, which can be used as features to determine the iris type. Figure 2.1 shows the iris pairplot.

![](img/325742126d3ff007c6c385f4ffb5c3be_35_0.png)

Figure 2.1 Iris pairplot: pairwise scatterplots color coded by iris species

A pairplot is a matrix of plots where off-diagonal entries contain a scatter plot of every feature (e.g., petal length) against every other feature, while the main diagonal entries contain plots of every feature against itself color-coded by the three iris species. The pairplot captures pairwise relationships in the iris dataset. Let's focus on the main diagonal entries and try to model the data we see. Since we have three types of Iris flowers, we can model the data as a mixture of three Gaussian distributions. A Gaussian mixture is a weighted sum of Gaussian probability distributions. Equation 2.1 captures this in mathematical terms.

Sum of K Gaussians

$$p(x|\theta) = \sum_{k=1}^K N(x; \mu_k, \sigma_k^2) \pi_k \tag{2.1}$$

| Gaussian mixture | Gaussian RV | Mixture proportions |
| --- | --- | --- |

A mixture of Gaussians consists of K Gaussian RVs scaled by mixture proportions $\pi_k$ that are positive and add up to 1: $\sum \pi_k = 1, \pi_k > 0$. This is a high dimensional parameter problem because to fit the Gaussian mixture model, we need to find the values for the means $\mu_k$, covariances $\sigma_k^2$, and mixture proportions $\pi_k$. In case of the iris dataset, we have $K = 3$, which means the number of parameters for the Gaussian mixture is equal to $9 - 1 = 8$ (i.e., we have 9 parameters in $\theta = \{\mu_k, \sigma_k^2, \pi_k\}_{k=1}^3$, and we subtract 1 because of the sum-to-one constraint for $\pi_k$). In a later chapter, we'll look at how to find the Gaussian mixture parameters via the expectation-maximization (EM) algorithm. Now that we have an idea about parameter spaces, let's review our understanding of posterior distribution, using coin flips as an example.

### 2.1.1 Posterior distribution of coin flips

With MCMC algorithms, we attempt to approximate the posterior distribution through samples. In fact, most of the Bayesian inference is designed to efficiently approximate the posterior distribution. Let's understand what a posterior distribution is in a little more detail. Posterior arises when we have a model with parameters $\theta$ we are trying to fit to observed data $x$. Namely, it's the probability of parameters given the data $p(\theta|x)$. Consider an example of a sequence of coin flips where every coin is heads with probability $\theta$ and tails with probability $1 - \theta$, as shown in figure 2.2.

![](img/325742126d3ff007c6c385f4ffb5c3be_36_0.png)

Figure 2.2 Bernoulli random variable

Figure 2.2 shows the probability mass function (PMF) of a Bernoulli RV modeling the coin flip. If $\theta = 1/2$, we have a fair coin with an equal chance of heads (1) or tails (0); otherwise, we say that the coin is biased, with a bias equal to $\theta$. We can write down the PMF of a Bernoulli RV as follows.

$$p_x(x|\theta) = \theta^x (1 - \theta)^{1-x}, \ x \in \{0, 1\}\tag{2.2}$$

The mean of the Bernoulli RV is equal to $E[X] = \sum_x x p_x(x|\theta) = 0(1 - \theta) + 1(\theta) = \theta$, while the variance is equal to $VAR(x) = E[x^2] - E[x]^2 = \theta - \theta^2 = \theta(1 - \theta)$. Let’s go back to our coin-tossing example. Let $D = \{x_1,\ldots,x_n\}$ be a sequence of independent and identically distributed (iid) coin flips. Then, we can compute the likelihood as follows.

$$p_x(D|\theta) = p_x(x_1,\ldots,x_n|\theta)\\ = \prod_{i=1}^{n} p(x_i|\theta) = \prod_{i=1}^{n} \theta^{x_i} (1 - \theta)^{1 - x_i}\\ = \theta^{N_1} (1 - \theta)^{N_0}\tag{2.3}$$

Here, we assume $N_1 = \sum_{i=1}^n x_i$, or the total number of counts for which the coin landed heads, and $N_0 = n - N_1$, or the total number of counts for which the coin landed tails.

Equations 2.2 and 2.3 have the form $p(x|\theta)$, which is, by definition, the likelihood of data $x$, given the parameter $\theta$. What if we have some prior information about the parameter $\theta$; in other words, what if we know something about $p(\theta)$, such as the number of heads and tails we obtained in another experiment with the same coins? We can capture this prior information as follows.

$$\text{Beta}(\theta|a, b) \propto \theta^{a-1} (1 - \theta)^{b-1}\tag{2.4}$$

Here, $a$ is the number of heads and $b$ is the number of tails in our previous experiment. When computing the posterior distribution, we are interested in computing $p(\theta|x)$. We can use the Bayes rule from chapter 1 to express the posterior distribution as proportional to the product of the likelihood and prior.

$$p(\theta|D) \propto p(D|\theta)p(\theta)\\ = \theta^{N_1} (1 - \theta)^{N_0} \theta^{a-1} (1 - \theta)^{b-1} = \theta^{N_1 + a -1} (1 - \theta)^{N_0 + b -1}\\ \propto \text{Beta}(\theta|N_1 + a, N_0 + b)\tag{2.5}$$

Equation 2.5 computes the posterior distribution $p(\theta|D)$, which tells us the probability of heads for a sequence of coin flips. We can see that the posterior is distributed as a Beta random variable. Remember that our prior was also a Beta random variable; we say that the prior is “conjugate to the posterior.” In other words, the posterior can be computed in closed form by updating the prior counts with observed data.

### 2.1.2 Markov chain for page rank

Before we dive into MCMC algorithms, we need to introduce the concept of a Markov chain. A *Markov chain* is a sequence of possible events, in which the probability of the current event depends only on the previous event. A first-order Markov chain can be written as shown in equation 2.6. Let $x_1,\ldots,x_t$ be the samples from our posterior distribution; then, we can write the joint as follows.

$$p(x_1,\ldots,x_t)=p(x_1)p(x_2\mid x_1)p(x_3\mid x_2)\cdots p(x_t\mid x_{t-1})$$

$$=p(x_1)\prod_{i=2}^{t}p(x_i\mid x_{i-1}) \tag{2.6}$$

Notice how the joint factors as a product of conditional distributions, where the current state is conditioned only on the previous state. A Markov chain is characterized by the initial distribution over the states $p(x_1=i)$ and a state transition matrix $A_{ij}=p(x_t=j\mid x_{t-1}=i)$ from state $i$ to state $j$.

Let’s motivate Markov chains via a Google page rank example. Google uses a page rank algorithm to rank billions of web pages. We can formulate a collection of $n$ web pages as a graph $G=(V,E)$. Let every node $v\in V$ represent a web page and every edge $e\in E$ represent a link from one page to another. Knowing how the pages are linked allows us to construct a giant, sparse transition matrix $A$, where $A_{ij}$ is the probability of following a link from page $i$ to page $j$, as shown in figure 2.3.

![](img/325742126d3ff007c6c385f4ffb5c3be_38_0.png)

Note that every row in the matrix $A$ sums to 1 (i.e., $\sum_j A_{ij}=1$). A matrix with this property is known as a *stochastic matrix*. Note that $A_{ij}$ corresponds to transition probability from state $i$ to state $j$. As we will see in a later chapter, page rank is a stationary distribution over the states of the Markov chain. To make it scale to billions of web pages, we’ll

$$I = \int_{-r}^{r} \int_{-r}^{r} 1[x^2 + y^2 \le r^2] dx dy = E_{x,y}[w(x,y)] \tag{2.10}$$

Here, $1[x^2 + y^2 \le r^2]$ is an indicator function equal to 1 when a point is inside the circle of radius $r$ and equal to 0 otherwise. Therefore, $\pi = I / r^2$. To compute $I$, note the following equation.

$$w(x,y) = (b_x - a_x)(b_y - a_y) 1[x^2 + y^2 \le r^2]\\ = (2r)(2r) 1[x^2 + y^2 \le r^2]\\ = 4r^2 1[x^2 + y^2 \le r^2] \tag{2.11}$$

We can summarize the pi estimation algorithm in the pseudo-code shown in figure 2.4.

```text
1: function pi_est(R, N):
2: for i = 1 to N:
3: X[i] ~ Unif(-R, R) → Uniform RVs
4: Y[i] ~ Unif(-R, R)
5: IN[i] = X[i]^2 + Y[i]^2 ≤ R^2
6: S[i] = (2R) × (2R) × IN[i]
7: end for
8: Î = 1/N Σ_{i=1}^N S[i]
9: π̂ = Î / R^2 ← Pi estimate
10: π̂_se = σ_S / √N ← Pi standard deviation
11: return π̂ ± π̂_se
```

Figure 2.4 Pi estimator pseudo-code

We generate N samples from a uniform distribution with support from −R to R and compute a Boolean expression of whether our sample is inside or outside the circle. If the sample is inside, it factors into the integral computation. Once we have an estimate of the integral, we divide the result by R^2 to compute our estimate of pi. We are now ready to implement our pi estimator!

### Listing 2.1 Pi estimator

```python
import numpy as np
import matplotlib.pyplot as plt
np.random.seed(42)  # Fixes a seed for reproducible results

def pi_est(radius=1, num_iter=int(1e4)):  # Experiments with a different number of samples N
    X = np.random.uniform(-radius,+radius,num_iter)
    Y = np.random.uniform(-radius,+radius,num_iter)
```

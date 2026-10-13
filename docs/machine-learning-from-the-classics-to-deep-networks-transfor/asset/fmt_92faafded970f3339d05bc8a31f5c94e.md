
## 17.3 Kalman and particle filtering

Particle filtering is an instance of the sequential Monte Carlo methods. It is a technique born in the 1990s and it was first introduced in [19] as an attempt to solve estimation tasks in the context of state-space modeling for the more general nonlinear and non-Gaussian scenarios. The term “particle filtering” was coined in [3], although the term “particle” had been used in [27].

Hidden Markov models (HMMs), which are treated in Section 16.4, and Kalman filters, introduced in Chapter 4, are special types of state-space (state-observation) modeling. The former address the case of discrete state (latent) variables and the latter the continuous case, albeit in the very special case of linear and Gaussian scenario. In particle filtering, the interest shifts to models of the following form:

![](images/B9780443292385000238/fx003.jpg)

where `f_n` and `h_n` are, in general, nonlinear (vector) functions, `η_n` and `v_n` are noise sequences, and the dimensions of `x_n` and `y_n` can be different. The random vector `x_n` is the (latent) state vector and `y_n` corresponds to the observations. There are two inference tasks that are of interest in practice.

**Filtering**: Given the set of observations, `y_{1:n}`, in the time index set `{1, 2, …, n}`, compute

`p(x_n | y_{1:n})`.

**Smoothing**: Given the set of observations `y_{1:N}` in the time index set `{1, 2, …, N}`, compute

`p(x_n | y_{1:N}), 1 ≤ n ≤ N`.

Before we proceed to our main goal, let us review the simpler case, that of Kalman filters, this time from a Bayesian viewpoint.

### 17.3.1 Kalman filtering: a Bayesian point of view

Kalman filtering was discussed in Section 4.10 in the context of linear estimation methods and the mean-square error criterion. In the current section, the Kalman filtering algorithm will be rederived following concepts from the theory of graphical models and Bayesian networks, which are treated in Chapters 15 and 16. This probabilistic view will then be used for the subsequent nonlinear generalizations in the framework of particle filtering. For the linear case model, Eqs. (17.12) and (17.13) become

```
x_n = F_n x_{n-1} + η_n,
``` (17.14)

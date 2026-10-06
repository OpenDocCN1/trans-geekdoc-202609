
# Blackbox Hyperparameter Optimization

## Methods:

- Grid-Search
- Random-Search
- Bayesian Optimization

![](img/f01928df50903c99ce023dd3c527a33d_952_0.png)

- The blackbox function is expensive to evaluate $\Rightarrow$ sample efficiency is important

## Grid Search and Random Search

- Both completely uninformed
- Random search handles unimportant dimensions better
- Random search is a useful baseline

![](img/f01928df50903c99ce023dd3c527a33d_953_0.png)

Image source: Bergstra & Bengio, JMLR 2012

## Bayesian Optimization

## Learning Outcome for today...

In this lecture, we will..

- Introduce Bayesian Optimization (BO) as active learning framework ...
- which is a data-efficient black-box optimization framework
- BO uses more directed exploration for sample generation

## Why Bayesian Optimization?

- Most data-efficient black-box optimizer we know
- Principled treatment of exploration
- Used a lot in auto ML: automatic hyper-parameter tuning
- Limited scalability (10-20 parameters)
- Computationally very expensive

![](img/f01928df50903c99ce023dd3c527a33d_955_0.png)

## Bayesian Optimization (BO)

- Sequentially gather observations at different locations in the input space
- Exploit the underlying structure of the input space $\Rightarrow$ Kernel regression
- Bayesian view: Model expectation and uncertainty $\Rightarrow$ Gaussian Processes
- Once the budget is over, recommend the best location

![](img/f01928df50903c99ce023dd3c527a33d_956_0.png)

## Recall: Gaussian Processes

- Distribution over functions
- Tractable Bayesian modeling of functions even with infinite feature spaces
- Input space (the search space) $\mathcal{X}$
- Kernel function $k: \mathcal{X} \times \mathcal{X} \to \mathbb{R}$

Every finite set of N points $\{x_1, \dots, x_N\}$ induces a N-dimensional Gaussian distribution, which is the posterior distribution on $\{f(x_1), \dots, f(x_N)\}$

![](img/f01928df50903c99ce023dd3c527a33d_957_0.png)

## Gaussian Processes

A Gaussian Process (GP) $f(\boldsymbol{x}) \sim \mathcal{GP}(m(\boldsymbol{x}), k(\boldsymbol{x}, \boldsymbol{x}'))$ is a mean function covariance function is a probability distribution over functions $f(\boldsymbol{x})$, such that any finite set of function values $t_i = f(\boldsymbol{x}_i)$ evaluated at inputs $\boldsymbol{x}_1, \dots, \boldsymbol{x}_n$ is jointly Gaussian distributed

-- Mean function evaluates our prior belief about the function
  $\mathbb{E}[f(\boldsymbol{x})] = m(\boldsymbol{x})$
  - For simplicity, we will use $m(\boldsymbol{x}) = 0$

- Covariance function evaluates how similar/correlated two function evaluations at inputs $\boldsymbol{x}, \boldsymbol{x}'$ are
  $\mathbb{E}[f(\boldsymbol{x})f(\boldsymbol{x}')] = k(\boldsymbol{x}, \boldsymbol{x}')$
  - Covariance function needs to be a positive definite function (similar to a kernel function)

## Example: Gaussian Kernel

The Gaussian kernel is defined by:

```
$k(\boldsymbol{x}, \boldsymbol{y}) = \exp\left(-\frac{\|\boldsymbol{x} - \boldsymbol{y}\|^2}{2\sigma^2}\right)$
```

- where $\sigma$ is the bandwidth parameter

![](img/f01928df50903c99ce023dd3c527a33d_959_0.png)

Often also called:

- Radial basis function kernel (RBF)
- Squared exponential kernel

It is the **most used kernel** for kernel methods

## Gaussian Process Prior

$\mathcal{GP}$ : a distribution over functions from $\mathcal{X}$ to $\mathbb{R}$

Prior $\mathcal{GP}$

![](img/f01928df50903c99ce023dd3c527a33d_960_0.png)

## Gaussian Process Posterior

$\mathcal{GP}$ : a distribution over functions from $\mathcal{X}$ to $\mathbb{R}$

Observations

![](img/f01928df50903c99ce023dd3c527a33d_961_0.png)

## Gaussian Process Posterior

$\mathcal{GP} :$ a distribution over functions from $\mathcal{X}$ to $\mathbb{R}$

Posterior $\mathcal{GP}$ given observations

![](img/f01928df50903c99ce023dd3c527a33d_962_0.png)

## Predictive distribution of a GP

Given: inputs $x_i$, noisy outputs $y_i$

- Kernel matrix: $[K]_{x_i x_j} = k(x_i, x_j)$
- Kernel vector: $k(x^*) = [k(x_1, x^*), \dots, k(x_N, x^*)]^T$

## GP posterior distribution:

- We can evaluate mean and variance for unseen data-point $x'$

$\mu(x') = k_{x'}^T(K + \sigma_y^2 I)^{-1}y$
$\sigma^2(x') = k(x', x') + \sigma_y^2 - k_{x'}^T(K + \sigma_y^2 I)^{-1}k_{x'}$

## Observations:

- The mean corresponds to Kernel Ridge Regression
- Can represent aleatoric and epistemic uncertainty

![](img/f01928df50903c99ce023dd3c527a33d_963_0.png)

Example of Sinusoidal Data (green: true function; blue: noisy data; red: GPR predictive mean; shaded: $\pm\sigma$)

## Template for BO using Acquisition Functions

For each round $t$:

1. Select an action $\theta_t \in \mathcal{X}$ that maximizes an acquisition function $\text{acq}_t(\theta)$
2. Observe reward $r_t = g(\theta_t) + \epsilon_t$

After $T$ rounds: recommend solution $\theta_T^*$

## Acquisition functions

- Pure exploration: Only final results
- Probability of improvement (PI)
- Expected improvement (EI)
- Exploration/Exploitation trade-off: Also intermediate results should be good
- Gaussian Process Upper Bounds (GP-UCB)
There is no winner, but many exist in the literature...
- Current SOTA: Predictive Entropy Search

## Probability of Improvement (PI)

**Pure exploration:** only interested in final result
- Let $g^*_{t-1} = \max(g(\theta_1), \dots, g(\theta_{t-1}))$ be the so far maximum
- Probability of improvement at location $x$: $PI_t(\theta) = \text{Pr}[g(\theta) \geq g_{t}^*]$

**Properties:**
- Can be computed quite easily for GPs
- Does not consider the magnitude of improvement
- Assumes noise-free setting

## Illustration

Examples:

![](img/f01928df50903c99ce023dd3c527a33d_967_0.png)
![](img/f01928df50903c99ce023dd3c527a33d_967_1.png)
![](img/f01928df50903c99ce023dd3c527a33d_967_2.png)
![](img/f01928df50903c99ce023dd3c527a33d_967_3.png)

## Expected Improvement

- Also considers magnitude of improvement
- Improvement at location $x$ using function $g$: $I_t(g, \theta) = \max(g(\theta) - g_{t-1}^*, 0)$
As $g$ is unknown, we can estimate the expected improvement:
$EI_t(\theta) = \mathbb{E}_{g \sim GP(\mathcal{D})}[I_t(\theta)|\mathcal{D}]$, where $\mathcal{D} = [\theta_1, g_1, \dots, \theta_{t-1}, g_{t-1}]$

- Can again be estimated for GPs, works better than probability of improvement (PI)
- Has a hyper-parameter $\xi$ that can scale exploration
- $\xi$ is always added to $g_{t-1}^*$ to pretend we have found a higher maximum
- Enforces exploration

## Gaussian-Process Upper Confidence Bounds

- Optimism in the face of uncertainty
- $UCB_t(\theta) = \mu_{t-1}(\theta) + \sqrt{\beta_t}\sigma_{t-1}(\theta)$
- Want to achieve high mean and high uncertainty
- $\beta_t$ time-dependent scaling of standard deviation
- Theory exists for selecting $\beta_t$ optimally

![](img/f01928df50903c99ce023dd3c527a33d_970_0.png)

- See RL lecture

## GP-UCB

![](img/f01928df50903c99ce023dd3c527a33d_971_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_972_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_973_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_974_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_975_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_976_0.png)

## GP-UCB

![](img/f01928df50903c99ce023dd3c527a33d_977_0.png)

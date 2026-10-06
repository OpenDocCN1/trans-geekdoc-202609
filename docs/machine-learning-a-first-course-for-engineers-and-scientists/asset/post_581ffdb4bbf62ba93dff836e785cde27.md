
## 9.2 Bayesian linear regression

From (9.10) we can also derive the posterior predictive for $f(x\star)$ by Corollary 9.2 in Appendix 9,A.

```
$p(f(x\star) | y) = N(f(x\star); m_*\star, s_*\star), \qquad (9.11a)$
m_*\star = x_*\star^T\mu_n, \qquad (9.11b)$
s_*\star = x_*\star^T\Sigma_n x_*\star. \qquad (9.11c)$
```

We have so far derived the posterior predictive for $f(x\star)$. Since we have $y\star = f(x\star) + \epsilon$ correction to the linear regression model (9.10), where $\epsilon$ is assumed to be independent of variance $\sigma^2$, we can compute the posterior predictive for $y\star$

```
$p(y\star | y) = N(y\star; m_*\star, s_*\star + \sigma^2). \qquad (9.11d)$
```

Note, that only difference from $p(f(x\star) | y)$ is that we add the variance of the measurement noise $\sigma^2$ which reflects the additional uncertainty we expect to get from the data output. But in $p(f(x\star) | y)$ and $p(y\star | y)$ the measurement noise of the training data output is reflected via the posterior.

We now have all pieces of Bayesian linear regression. The main difference to linear regression is that we compute a posterior distribution $p(\theta | y)$ (instead of a single value $\theta$) and a posterior predictive $p(y\star | y)$ of a prediction $\theta$. We summarize it as Method 9.1 and illustrate it with Example 9.1.

## Learn Bayesian linear regression

- **Data:** Training data $T = \{x_i, y_i\}_{i=1}^n$
- **Result:** Posterior $p(\theta | y) = N(\mu_n, \Sigma_n)$
- **1** Compute $\mu_n$ and $\Sigma_n$ as (9.10).

## Predict Bayesian linear regression

- **Data:** Posterior $p(\theta | y) = N(\mu_n, \Sigma_n)$ and test input $x\star$
- **Result:** Posterior predictive $p(f(x\star) | y) = N(f(x\star); m_*\star, s_*\star)$
- **1** Compute $m_*\star$ and $s_*\star$ as (9.11).

## Method 9.1: Bayesian linear regression.

We have so far assumed that the noise variance $\sigma^2$ is fixed. However one also is the parameter user to decide, by maximizing the marginal likelihood. Corollary 9.2 gives us the marginal likelihood

```
$p(y\star) = N(y\star; X\mu_n, \sigma^2 I + X\Sigma_n X^T). \qquad (9.12)$
```

It is also possible to choose the prior variance $\sigma^2$ by maximizing (9.12).

Just as linear regression it is also possible to use nonlinear transformations, such as polynomials, in Bayesian linear regression. We give an example of that in Example 9.2, where we return to the running regression example of car stopping distances. We can, however, go one step further and use the kernel trick from Chapter 8. That will lead us to the Gaussian process, which is the topic of Section 9.3.

## 9 The Bayesian approach and Gaussian processes

## Example 9.1: Bayesian linear regression

To illustrate the inner workings of Bayesian linear regression, we consider a one-dimensional example with $y = \theta_1 + \theta_2x + \varepsilon$. In the first row of Figure 9.1, the left panel shows the prior $p(\theta)$ (blue surface: a two-dimensional Gaussian distribution over $\theta_1$ and $\theta_2$) from which 10 samples are drawn (blue dots). Each of these samples correspond to a straight line in the right (blue lines).

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_183_0.png)

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_183_1.png)

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_183_2.png)

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_183_3.png)

Fig. 9.1

In the second row of Figure 9.1 ($n=1$) data point $(x_1, y_1)$ is introduced. Its value is shown in the right panel (black dot), and the posterior for $\theta$ in the left panel (a Gaussian: blue surface). In addition ten samples are drawn from the posterior (blue dots), each corresponding to a straight line in the right panel (blue lines). In the Bayesian framework the formulated samples can be thought of as equally likely posterior hypotheses about $f(x_n)$. This is repeated with $n=3$ and $n=30$ data points in Figure 9.1. We can particular how the posterior contracts (“less uncertainty”) as more data arrives, in terms of the blue surface being peaked as the blue lines more concentrated.

## Example 9.2: Car stopping distances

We consider the car stopping problem from Example 9.2 and apply linear regression with $y = 1 + \theta_1x + \epsilon$ and $y = 1 + \theta_1x + \theta_2x^2$ respectively. We use $\sigma^2$ and $\sigma_0^2$ by maximizing the marginal likelihood, which gives us $\sigma^2 = 0.4^2$ and $\sigma_0^2 = 0.1$ for the linear model, and $\sigma^2 = 0.1^2$ and $\sigma_0^2 = 0.3^2$ for the quadratic model.

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_184_0.png)

In Figure 9.2 we utilize $p(f|y)$ and $p(y|y)$ (9.11) using the darker line for the mean (which both have the same mean) and the shaded areas to visualize the standard deviations of $p(f|y)$ and $p(y|y)$ in the case $\sigma^2$ is fixed. The only difference from $p(f|y)$ is that we add the variance of the measurement noise $\sigma^2$.

## Connection to linear regression

The main feature of the Bayesian approach is that it provides a full distribution $p(\theta)$ over parameters $\theta$, rather than a single point estimate $\hat{\theta}$. There is also an interesting connection between the Bayesian approach and regression. We will make this concrete by considering the posterior $p(\theta|y)$ and the point estimate $\hat{\theta}$ from $L^2$-regularized regression. The MAP estimate is the value of $\theta$ for which the posterior reaches its maximum,

```
$\hat{\theta}_{MAP} = \arg\max p(\theta|y) = \arg\max p(y|\theta)p(\theta) = \arg\max [ln p(y|\theta) + ln p(\theta)] \quad (9.13)$
```

where the second equality follows from the fact that $p(\theta) \propto e^{-\lambda||\theta||^2}$ and $p(y)$ does not depend on $\theta$. Here $L^2$-regularized linear regression can be understood using the cost function,

```
$\hat{\theta} = \arg\max [ln p(y|\theta) + \lambda||\theta||^2] \quad (9.14)$
```

with regularization parameter $\lambda$. When comparing (9.14) to (9.13), see that if $p(\theta) \propto e^{-\lambda||\theta||^2}$, the MAP estimate is indeed the case for some value of $\theta$. If, for example, we chose to use a Laplace prior, the MAP estimate would be identical to $L^1$ regularization. In general there are many methods that can be interpreted as choosing a prior. This connection to regularization explains why the Bayesian approach is prone to overfitting. It is important to note that the connection between the Bayesian approach and the use of regularization does not imply that the two approaches are equivalent. The main point with the Bayesian approach is still to provide a distribution for $\theta$, not just a point estimate $\hat{\theta}$.

## 9.3 The Gaussian process

We introduced the Bayesian approach as the idea of considering unknown parameters $\theta$ as random variables, and consequently learning a posterior distribution $p(\theta|y)$ instead of a single value $\theta$. However the Bayesian idea not only apply to models with parameters, but also to nonparametric models. We will now introduce the Gaussian process, instead of considering parameters $\theta$ being random variables we effectively consider an entire function $f(x)$ as a stochastic process, and compute the posterior $p(f|y)$. The Gaussian process is an interesting and commonly used Bayesian nonparametric model. In nutshell it is the Bayesian approach applied to kernel regression (Chapter 8). We will present the Gaussian process as a method for handling regression problems, but it is possible to use it for classification problems (similar to how linear regression can be modified to logistic regression). In this section we will introduce the fundamentals of the Gaussian process and in Section 9.4 describe how it can be used as a supervised learning method. We will first discuss what a Gaussian process is and thereafter how we can construct a Gaussian process that connects to kernel regression from Section 8.2.

## What is a Gaussian process?

A Gaussian process is a specific type of stochastic process. A stochastic process, in turn, is a generalization of a random variable. Most commonly we think about a stochastic process as some random quantity that evolves over time. Mathematically this corresponds to a collection of random variables $\{z(t) : t \in \mathbb{R}\}$ indexed by time $t$. That is, for each point $t$, the value of the process $z(t)$ is a random variable. Furthermore, often we assume that at different times, $z(t)$ and $z(t')$ are correlated and the correlation depends on the time difference. More abstractly, we can view $z(t)$ as a random function, where the function is to the index $t$. With this interpretation it is possible to generalize the concept of stochastic process to random functions with arbitrary inputs, $f(x)$ where $x \in \mathcal{X}$ denotes the input variable in the input space. Similarly, this means that the value $f(x)$ for any $x$ is a random variable, and that the function $f(x)$ and $f(x')$ for inputs $x$ and $x'$ are dependent. As we will see later, the dependencies can be used to control certain properties of the function. For instance, if we want the function to smooth (slowly), then the function values $f(x)$ and $f(x')$ be highly correlated if $x$ is close to $x'$. The Gaussian generalization opens up using random functions for unknown functions (such as a regression function) in a Bayesian setting. To introduce the Gaussian process as a random function, we will start by making the simplifying assumption that the input variable $x$ is discrete and can take only few different values, $x_1,\dots , x_q$. Hence, the function $f(x)$ is completely characterized by the $q$-dimensional vector $f = [f_1 \dots , f_q]^T = [f(x_1)\dots , f(x_q)]^T$.

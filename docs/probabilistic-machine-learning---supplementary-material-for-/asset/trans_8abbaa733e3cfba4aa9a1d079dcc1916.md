

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_64_0.png)

图 6.10: 将 CMA-ES 方法应用于简单 2d 函数的示意图。点表示种群成员，虚线橙色椭圆表示多元高斯分布。来自 https://en.wikipedia.org/wiki/CMA-ES。经 Wikipedia 作者 Sentewolf 许可使用。

## 6.3.5 Natural evolutionary strategies

Evolution strategies [Wie+14] are a form of distribution-based optimization in which the distribution over the population is represented by a Gaussian, p(x|theta_t) (see e.g., [Sal+17]). Unlike CEM, the parameters are updated using gradient ascent applied to the expected value of the objective using MLE on a set of elite samples. More precisely, consider the smoothed objective L(theta) = E_{p(x|theta)} [f(x)]. We can use the REINFORCE estimator (??) to compute the gradient of this objective as follows:

nabla_theta L(theta) = E_{p(x|theta)} [f(x) nabla_theta log p(x|theta)] (6.74)

This can be approximated by drawing Monte Carlo samples. If the probability model is in the exponential family, we can compute the natural gradient (??), rather than the "vanilla" gradient; such methods are called natural evolution strategies [Wie+14].

### 6.3.5.1 CMA-ES

The CMA-ES method of [Han16], which stands for "covariance matrix adaptation evolution strategy" is a kind of NES. It is very similar to CEM except it updates the parameters in a special way. In particular, instead of computing the new mean and covariance using unweighted MLE on the elite set, we attach weights to the elite samples based on their rank. We then set the new mean to the weighted MLE of the elite set.

The update equations for the covariance are more complex. In particular, "evolutionary paths" are also used to accumulate the search directions across successive generations, and these are used to update the covariance. It can be shown that the resulting updates approximate the natural gradient of L(theta) without explicitly modeling the Fisher information matrix [Oll+17].

Figure 6.10 illustrates the method in action.

## 6.4 Dynamic programming

Dynamic programming is a way to efficiently find the globally optimal solution to certain kinds of optimization problems. The key requirement is that the optimal solution be expressed in terms of the optimal solution to smaller subproblems, which can be reused many times. Note that DP is more of an algorithm "family" rather than a specific algorithm. We give some examples below.

### 6.4.1 Example: computing Fibonacci numbers

Consider the problem of computing **Fibonacci numbers**, defined via the recursive equation

$F_i = F_{i-1} + F_{i-2}$ (6.75)

with base cases $F_0 = F_1 = 1$. Thus we have that $F_2 = 2, F_3 = 3, F_4 = 5, F_5 = 8$, etc. A simple **recursive** algorithm to compute the first $n$ Fibonacci numbers is shown in Algorithm 2. Unfortunately, this takes exponential time. For example, evaluating fib(5) proceeds as follows:

$F_5 = F_4 + F_3$ (6.76)
$= (F_3 + F_2) + (F_2 + F_1)$ (6.77)
$= ((F_2 + F_1) + (F_1 + F_0)) + ((F_1 + F_0) + F_1)$ (6.78)
$= (((F_1 + F_0) + F_1) + (F_1 + F_0))(F_1 + F_0) + F_1)$ (6.79)

We see that there is a lot of repeated computation. For example, fib(2) is computed 3 times. One way to improve the efficiency is to use **memoization**, which means memorizing each function value that is computed. This will result in a linear time algorithm. However, the overhead involved can be high.

It is usually preferable to try to solve the problem **bottom up**, solving small subproblems first, and then using their results to help solve larger problems later. A simple way to do this is shown in Algorithm 3.

```
Algorithm 2: Fibonacci numbers, top down
1 function fib(n);
2 if n = 0 or n = 1 then
3 | return 1
4 else
5 | return (fib(n - 1) + fib(n - 2))
```

```
Algorithm 3: Fibonacci numbers, bottom up
1 function fib(n);
2 F_0 := 1, F_1 := 1 ;
3 For i = 2, ..., n do
4 | F_i := F_{i-1} + F_{i-2}
5 return F_n
```

### 6.4.2 ML examples

There are many applications of DP to ML problems, which we discuss elsewhere in this book. These include the forwards-backwards algorithm for inference in HMMs (**??**), the Viterbi algorithm for MAP sequence estimation in HMMs (**??**), inference in more general graphical models (**??**), reinforcement learning (**??**), etc.

## 6.5 Conjugate duality

In this section, we briefly discuss **conjugate duality**, which is a useful way to construct linear lower bounds on non-convex functions. We follow the presentation of [Bis06, Sec. 10.5].

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_66_0.png)

Figure 6.11: Illustration of a conjugate function. Red line is original function f(x), and the blue line is a linear lower bound \(\lambda x\). To make the bound tight, we find the x where \(\nabla f(x)\) is parallel to \(\lambda\), and slide the line up to touch there; the amount we slide up is given by \(f^*(\lambda)\). Adapted from Figure 10.11 of [Bis06].

### 6.5.1 Introduction

Consider an arbitrary continuous function \(f(\mathbf{x})\), and suppose we create a linear lower bound on it of the form

\(\mathcal{L}(\mathbf{x}, \boldsymbol{\lambda}) \triangleq \boldsymbol{\lambda}^\top \mathbf{x} - f^*(\boldsymbol{\lambda}) \le f(\mathbf{x})\) (6.80)

where \(\boldsymbol{\lambda}\) is the slope, which we choose, and \(f^*(\boldsymbol{\lambda})\) is the intercept, which we solve for below. See Figure 6.11(a) for an illustration.

For a fixed \(\lambda\), we can find the point \(\mathbf{x}_\lambda\) where the lower bound is tight by “sliding” the line upwards until it touches the curve at \(\mathbf{x}_\lambda\), as shown in Figure 6.11(b). At \(\mathbf{x}_\lambda\), we minimize the distance between the function and the lower bound:

\(\mathbf{x}_\lambda \triangleq \underset{x}{\text{argmin}} f(x) - \mathcal{L}(\mathbf{x}, \boldsymbol{\lambda}) = \underset{x}{\text{argmin}} f(x) - \boldsymbol{\lambda}^\top \mathbf{x}\) (6.81)

Since the bound is tight at this point, we have

\(f(\mathbf{x}_\lambda) = \mathcal{L}(\mathbf{x}_\lambda, \boldsymbol{\lambda}) = \boldsymbol{\lambda}^\top \mathbf{x}_\lambda - f^*(\boldsymbol{\lambda})\) (6.82)

and hence

\(f^*(\boldsymbol{\lambda}) = \boldsymbol{\lambda}^\top \mathbf{x}_\lambda - f(\mathbf{x}_\lambda) = \underset{x}{\max} \boldsymbol{\lambda}^\top \mathbf{x} - f(\mathbf{x})\) (6.83)

The function \(f^*\) is called the **conjugate** of \(f\), also known as the **Fenchel transform** of \(f\). For the special case of differentiable \(f\), \(f^*\) is called the **Legendre transform** of \(f\).

One reason conjugate functions are useful is that they can be used to create convex lower bounds to non-convex functions. That is, we have \(\mathcal{L}(\mathbf{x}, \boldsymbol{\lambda}) \le f(\mathbf{x})\), with equality at \(\mathbf{x} = \mathbf{x}_\lambda\), for any function \(f : \mathbb{R}^D \to \mathbb{R}\). For any given \(\mathbf{x}\), we can optimize over \(\boldsymbol{\lambda}\) to make the bound as tight as possible, giving us a fixed function \(\mathcal{L}(\mathbf{x})\); this is called a **variational approximation**. We can then try to maximize this lower bound wrt \(\mathbf{x}\) instead of maximizing \(f(\mathbf{x})\). This method is used extensively in approximate Bayesian inference, as we discuss in **??**.

### 6.5.2 Example: exponential function

Let us consider an example. Suppose \(f(x) = e^{-x}\), which is convex. Consider a linear lower bound of the form

\(\mathcal{L}(x, \lambda) = \lambda x - f^\dagger(\lambda)\) (6.84)

where the conjugate function is given by

\(f^\dagger(\lambda) = \underset{x}{\max} \lambda x - f(x) = -\lambda \log(-\lambda) + \lambda\) (6.85)

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_67_0.png)

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_67_1.png)

Figure 6.12: (a) The red curve is f(x) = e^{-x} and the colored lines are linear lower bounds. Each lower bound of slope \lambda is tangent to the curve at the point x_\lambda = -log(-\lambda), where f(x_\lambda) = e^{log(-\lambda)} = -\lambda. For the blue curve, this occurs at x_\lambda = \xi. Adapted from Figure 10.10 of [Bis06]. Generated by opt_lower_bound.py. (b) For a convex function f^*(x), its epigraph can be represented as the intersection of half-spaces defined by linear lower bounds of the form f^*(\lambda). Adapted from Figure 13 of [JJ99].

as illustrated in Figure 6.12(a).

To see this, define

$$J(x, \lambda) = \lambda x - f(x)$$

We have

$$\frac{\partial J}{\partial x} = \lambda - f'(x) = \lambda + e^{-x}$$

Setting the derivative to zero gives

$$x_\lambda = \arg \max_x J(x, \lambda) = -\log(-\lambda)$$

Hence

$$f^\dagger(\lambda) = J(x_\lambda, \lambda) = \lambda(-\log(-\lambda)) - e^{\log(-\lambda)} = -\lambda \log(-\lambda) + \lambda$$

### 6.5.3 Conjugate of a conjugate

It is interesting to see what happens if we take the conjugate of the conjugate:

$$f^{**}(x) = \max_\lambda \lambda^T x - f^\dagger(\lambda)$$

If f is convex, then f^{**} = f, so f and f^\dagger are called conjugate duals. To see why, note that

$$f^{**}(x) = \max_\lambda \mathcal{L}(x, \lambda) \le f(x)$$

Since we are free to modify \lambda for each x, we can make the lower bound tight at each x. This perfectly characterizes f, since the epigraph of a convex function is an intersection of half-planes defined by linear lower bounds, as shown in Figure 6.12(b). Let us demonstrate this using the example from Section 6.5.2. We have

$$f^{**}(x) = \max_\lambda \lambda x - f^\dagger(\lambda) = \max_\lambda \lambda x + \lambda \log(-\lambda) - \lambda$$

Define

$$J^*(x, \lambda) = \lambda x - f^\dagger(x) = \lambda x + \lambda \log(-\lambda) - \lambda$$


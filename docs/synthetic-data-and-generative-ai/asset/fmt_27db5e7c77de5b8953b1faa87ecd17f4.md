
In this chapter, I discuss an unusual optimization algorithm. Why would anyone be interested in an algorithm that never converges to the solution you are looking for? This version of the `fixed-point iteration`, when approaching a zero or an optimum, emits a strong signal and allows you to detect a small interval likely to contain the solution: the zero or global optimum in question. It may approach the optimum quite well, but subsequent iterations do not lead to convergence: the algorithm eventually moves away from the optimum, or oscillates around the optimum without ever reaching it.

The `fixed-point iteration` [[Wiki](https://en.wikipedia.org/wiki/Fixed-point_iteration)] is the mother of all optimization and root-finding algorithms. In particular, all `gradient-based` optimization techniques [[Wiki](https://en.wikipedia.org/wiki/Gradient_descent)] are a particular version of this generic method. In this chapter, I use it in a very challenging setting. The target function may not be differentiable or may have a very large number of local minima and maxima. All the standard techniques fail to detect the global optima. In this case, even the `fixed-point method` diverges. However, somehow, it can tell you the location of a global optimum with a rather decent precision. Once an approximation is obtained, the method can be applied again, this time focusing around a narrow interval containing the solution to achieve higher precision. Also, this method is a lot faster than brute force such as `grid search`.

I first illustrate the method on a specific problem. Then, generating synthetic data that emulates and generalizes the setting of the initial problem, I illustrate how the method performs on different functions or data sets. The purpose is to show how synthetic data can be used to test and benchmark algorithms, or to understand when they work, and when they do not. This, combined with the intuitive aspects of my `fixed-point iteration`, illustrates a particular facet of explainable AI. Finally, I use a smoothing technique to visualize the highly chaotic functions involved here. It highlights the features of the functions that we are interested in, while removing the massive noise that makes these functions almost impossible to visualize in any meaningful way.

## Keywords

fixed-point algorithm; factorization; divergent algorithm; synthetic function; root finding; smoothing; discrete optimization

## 13.1 Introduction

While the technique discussed here is a last resort solution when all else fails, it is actually more powerful than it seems at first glance. First, it also works in standard cases with “nice” functions. However, there are better methods when the function behaves nicely, taking advantage of the differentiability of the function in question, such as the `Newton algorithm` [[Wiki](https://en.wikipedia.org/wiki/Newton%27s_method)] (itself a `fixed-point iteration`). It can be generalized to higher dimensions, though I focus on univariate functions here.

Perhaps the attractive features are the fact that it is simple and intuitive, and quickly leads to a solution despite the absence of convergence. However, it is an empirical method and may require working with different parameter sets to actually find a solution. Still, it can be turned into a black-box solution by automatically testing different parameter configurations. In that respect, I compare it to the empirical `elbow rule` to detect the number of clusters in unsupervised clustering problems. I discuss the elbow rule and its automation in Section [18.6](#Chp018_361-386_B9780443218576000229.xhtml). Another `fixed-point algorithm` leading to explainable AI in the context of linear regression is discussed in Section [7.1](#Chp007_113-129_B9780443218576000114.xhtml).

### 13.1.1 The problem, with illustration

The method can solve two types of problems: finding the zeros of a function, or its optima (maxima or minima). Optima correspond to a zero of the derivative, so finding them is a root-finding problem. In my example, the functions typically have multiple global minima that we want to detect. The initial problem is to find a factor `b` of a large integer number `a`. Here `a` is fixed, and the function is denoted as `f(b)`![Image](images/B9780443218576000175/si1.png) with `f(b)=0`![Image](images/B9780443218576000175/si2.png) if and only if `b` is such a factor (integer number) different from 1 and `a`. If `b` is not a factor, then `f(b)>0`![Image](images/B9780443218576000175/si3.png). Initially, the interest was to factor a number that is a product of two large primes, as this has implications in cryptography. However, the technique led to a much larger class of applications where it has much more value than for factoring integers.

The first step was to change the problem setting: extending the function `f(b)`![Image](images/B9780443218576000175/si1.png) which accepts an integer argument `b`, into a continuous function where `b` is a real number. Here `f(b)=a mod b`![Image](images/B9780443218576000175/si4.png). So to get a continuous extension, one has to define the modulo operator for arguments `b` that are not integer numbers. Finally, it led to

```latex
f(b) = a - \lfloor b + \epsilon\rfloor\lfloor \epsilon + \frac{a}{\lfloor b + \epsilon\rfloor} \rfloor,\quad b > 0.
```

![Image](images/B9780443218576000175/si5.png)(13.1)

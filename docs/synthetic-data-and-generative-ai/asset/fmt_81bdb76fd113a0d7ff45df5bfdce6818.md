
Again, `s` and `λ` should be estimated first. The statistic `T(λ, s)`![Image](images/B9780443218576000205/si170.png) is the **interarrival time** or distance between a point and its closest neighbor the right (in one dimension). However, a simultaneous estimation of `λ`, `s`, `F`![Image](images/B9780443218576000205/si312.png) is feasible and consists of finding the parameters `λ`, `s`, `F`![Image](images/B9780443218576000205/si312.png) minimizing `γ(F)`![Image](images/B9780443218576000205/si313.png), now denoted as `γ(λ, s, F)`![Image](images/B9780443218576000205/si314.png). See Section [16.3.1](#Chp016_293-327_B9780443218576000205.xhtml#s0085) to estimate `λ` and `s` separately: this stepwise procedure is simpler and less prone to **overfitting** \[[Wiki](https://en.wikipedia.org/wiki/Overfitting)\].

The estimation technique introduced here, especially formula [(16.18)](#Chp016_293-327_B9780443218576000205.xhtml#deq25), is sometimes referred to as **minimum contrast estimation**. See slides 114–116 in the presentation entitled “Introduction to Spatial Point Processes and Simulation-Based Inference”, by Jesper Møller [\[31\]](#Chp016_293-327_B9780443218576000205.xhtml#br0155).

#### 16.4.4.1 Theoretical values obtained by simulations

This section highlights some simulation results obtained with [`PB_main.py`](https://github.com/VincentGranville/Point-Processes/blob/main/Source%20Code/PB_main.py) to compute moments `E[T^r]`![Image](images/B9780443218576000205/si315.png) of the interarrival times `T = T(λ, s)`![Image](images/B9780443218576000205/si242.png) for various `λ`, `s`![Image](images/B9780443218576000205/si316.png), as well as statistics related to the point count (random variable) `N(B)`![Image](images/B9780443218576000205/si19.png), where `B = [a, b]`![Image](images/B9780443218576000205/si317.png) is an interval. The goal is to:

- Show that except if `F` has a finite support or `s` is very small, the choice of `F` has very little impact;
- Show how fast the Poisson–binomial process converges to a stationary Poisson process as `s` increases;
- Show that any point of the process can be used to compute the *theoretical distribution* of `T`, thus choosing `X[0]`![Image](images/B9780443218576000205/si318.png) or any `X[k]`![Image](images/B9780443218576000205/si29.png), or averaging over many points, yields the same theoretical distribution;
- Show that you can use one realization of the process with many points, or many realizations of the process, each with few points, to compute the theoretical distribution of `T`.

The last fact illustrates the **ergodicity** of `T`.

[Table 16.2](#Chp016_293-327_B9780443218576000205.xhtml#t0015) shows simulation results based on `λ = 1`![Image](images/B9780443218576000205/si49.png), `r = 1/2`![Image](images/B9780443218576000205/si321.png) and `B = [a, b]`![Image](images/B9780443218576000205/si317.png) with `a = -0.75`![Image](images/B9780443218576000205/si322.png) and `b = 0.75`![Image](images/B9780443218576000205/si323.png). Three different `F` were tested: uniform, logistic, and Cauchy. The notation `μ(B)`![Image](images/B9780443218576000205/si324.png) stands for `b - a`![Image](images/B9780443218576000205/si325.png). In two dimensions, it represents the area of the set `B` (typically, a square or a circle). In one dimension, when `s = ∞`![Image](images/B9780443218576000205/si106.png), `N(B)`![Image](images/B9780443218576000205/si19.png) has a Poisson distribution of expectation `λμ(B)`![Image](images/B9780443218576000205/si326.png), and `T` has an exponential distribution of expectation `1/λ`![Image](images/B9780443218576000205/si38.png). The limiting process is a stationary Poisson process of intensity `λ`. The exact formula for `` `E[√T]` ``![Image](images/B9780443218576000205/si319.png), when `s = ∞`![Image](images/B9780443218576000205/si106.png), was obtained with the online version of Mathematica: you can check the computation, [here](https://bit.ly/30t354T). In general, convergence to the Poisson process, when `s → ∞`![Image](images/B9780443218576000205/si8.png), is slower and more bumpy if `F` is uniform, compared to using a logistic or Cauchy distribution for `F`.

| Statistic | Formula | Value | Uniform | Logistic | Cauchy |
| --- | --- | --- | --- | --- | --- |
| `E[N(B)]` | `λμ(B)` | `3/2` | `1.5019` | `1.5000` | `1.4962` |
| `Var[N(B)]` | `λμ(B)` | `3/2` | `1.4738` | `1.4906` | `1.4872` |
| `P[N(B)=0]` | `e^(-λμ(B))` | `0.2231` | `0.2196` | `0.2221` | `0.2230` |
| `E[T]` | `1/λ` | `1` | `1.0003` | `0.9999` | `1.0010` |
| `Var[T]` | `1/λ²` | `1` | `0.9680` | `0.9888` | `1.0029` |
| `E[√T]` | `(1/2)√(π/λ)` | `0.8862` | `0.8865` | `0.8862` | `0.8873` |

![Image](images/B9780443218576000205/t0015.png)

#### 16.4.4.2 Retrieving `F` from the interarrival times distribution

I assume here that `F` has a density `f`, and we are dealing with a one-dimensional Poisson–binomial process. The random variable `T(λ, s)`![Image](images/B9780443218576000205/si170.png) measuring the distance between a point and the closest neighbor to the right on the X axis is called the interarrival time. Given the limit distribution of the standardized interarrival times, the purpose is to retrieve the distribution of `F`. If you are familiar with the concept of **characteristic function** \[[Wiki](https://en.wikipedia.org/wiki/Characteristic_function_\(probability_theory\))\], this exercise is easy. If not, you should first get familiar with this concept. The theorems referred to are from my book “Stochastic Processes and Simulation: A Machine Learning Approach”.

The **standardized interarrival times** is defined as `` `(1/s)[T(λ,s) - 1/λ]` ``![Image](images/B9780443218576000205/si327.png) and has zero expectation by virtue of Theorem 4.3. By virtue of Theorem 4.2, it can be rewritten as `` `(1/(λ s))[T(1, λ s) - 1]` ``![Image](images/B9780443218576000205/si328.png). Its limit, as `s → 0`![Image](images/B9780443218576000205/si329.png), is denoted as `T^*`![Image](images/B9780443218576000205/si330.png). One of the simplest cases, besides Gaussian and Cauchy, is the following: If `T^*`![Image](images/B9780443218576000205/si330.png) has a standard **Laplace distribution** \[[Wiki](https://en.wikipedia.org/wiki/Laplace_distribution)\] (that is, symmetric centered at zero, and with variance `π²/3`![Image](images/B9780443218576000205/si135.png)), show that `F` is a **modified Bessel distribution** of the second kind [\[35\]](#Chp016_293-327_B9780443218576000205.xhtml#br0175). Note that as a consequence of L'Hôpital's rule \[[Wiki](https://bit.ly/3sQXEbL)\], `T^*`![Image](images/B9780443218576000205/si330.png) is the derivative of `T(λ, s)`![Image](images/B9780443218576000205/si170.png) with respect to `s`, evaluated at `s = 0`![Image](images/B9780443218576000205/si10.png).

By virtue of Theorem 4.4, we have

`` `P(T^* < y) = ∫_{-∞}^∞ F(y - x) f(x) dx` ``

![Image](images/B9780443218576000205/si331.png)

which is a **convolution** of `F` with itself. Thus `T^*`![Image](images/B9780443218576000205/si330.png) has the distribution of the sum of two independent random variables, say `Z[1]`, `Z[2]`![Image](images/B9780443218576000205/si332.png), of distribution `F`. Its characteristic function is therefore

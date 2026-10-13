
**θ**[*n*] = **θ**[*n* − 1] + *μ* csgn[*e*[*n*]^*] **x**[*n*]

where the complex sign of a complex number, *z* = *x* + *jy*, is defined as

csgn(*z*) = sgn(*x*) + *j* sgn(*y*).

If in addition *μ* is chosen to be a power of two, then the recursion becomes *multiplication-free*, and *l* multiplications are only needed for the computation of the error. It turns out that the algorithm minimizes, in the stochastic approximation sense, the following cost function:

*J*(**θ**) = 𝔼 [|*y* − **θ**^(*H*) **x**|]

and stability is guaranteed for sufficiently small values of *μ* [83].

### The least-mean-fourth (LMF) algorithm

The scheme minimizes the following cost function:

*J*(**θ**) = 𝔼 [|*y* − **θ**^(*H*) **x**|⁴]

and the corresponding update recursion is given by

**θ**[*n*] = **θ**[*n* − 1] + *μ* |*e*[*n*]|² **x**[*n*] *e*[*n*]^*.

It has been shown [101] that minimization of the fourth power of the error may lead to an online scheme with better compromise between convergence rate and excess MSE than the LMS if the noise source is sub-Gaussian. In a sub-Gaussian distribution, the tails of the PDF graph are decaying faster compared to the Gaussian one. The LMF could be seen as a version of the LMS with time-varying step size, equal to *μ* |*e*[*n*]|². Hence, when the error is large, the step size increases, which helps the LMF to converge faster. On the other hand, when the error is small, the equivalent step size is reduced, leading to lower values of the excess MSE. This idea turns out to work well when the noise is sub-Gaussian. However, the LMF tends to become unstable in the presence of outliers. This is also understood, because for very large error values the equivalent step size becomes very large, leading to instability. This is, for example, the case when the noise follows a distribution with high tails; that is, when the corresponding PDF curve decays at lower rates compared to the Gaussian, such as in the case of super-Gaussian distributions. Results concerning the analysis of the LMF can be found in [69, 70, 83]. Robustness and stability of the algorithm are guaranteed for sufficiently small values of *μ* [83].

### Transform-domain LMS

We have already commented that the convergence speed of the LMS heavily depends on the condition number $\left( \frac{\lambda_{\max}}{\lambda_{\min}} \right)$ of the covariance matrix; this will soon be demonstrated in the examples below.

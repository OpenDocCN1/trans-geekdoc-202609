![](bbox=[0.36, 0.1, 0.66, 0.37])

Figure 6.10: Illustration of sequential Bayesian optimization over three iterations. The rows correspond to a training set of size t = 2, 3, 4. The dotted black line is the true, but unknown, function f(x). The solid black line is the posterior mean, μ(x). The shaded blue intervals are the 95% credible interval derived from μ(x) and σ(x). The solid black dots correspond to points whose function value has already been computed, i.e., xn for which f(xn) is known. The green curve at the bottom is the acquisition function. The red dot is the proposed next point to query, which is the maximum of the acquisition function. From Figure 1 of [Sha+16]. Used with kind permission of Nando de Freitas.

p(f(x)|Dn) = N(f|μn(x), σn^2(x)), where μn(x) and σn(x) are functions that can be derived from the training data Dn = {(xi, yi) : i = 1 : n} using a simple closed-form equation. The GP requires specifying a kernel function Kθ(x, x'), which measures similarities between input points x, x'. The intuition is that if two inputs are similar, so Kθ(x, x') is large, then the corresponding function values are also likely to be similar, so f(x) and f(x') should be positively correlated. This allows us to interpolate the function between the labeled training points; in some cases, it also lets us extrapolate beyond them.

GPs work well when we have little training data, and they support closed form Bayesian updating. However, exact updating takes O(N^3) for N samples, which becomes too slow if we perform many function evaluations. There are various methods (Section 18.5.3) for reducing this to O(NM^2) time, where M is a parameter we choose, but this sacrifices some of the accuracy.

In addition, the performance of GPs depends heavily on having a good kernel. We can estimate the kernel parameters θ by maximizing the marginal likelihood, as discussed in Section 18.6.1. However, since the sample size is small (by assumption), we can often get better performance by marginalizing out θ using approximate Bayesian inference methods, as discussed in Section 18.6.2. See e.g., [WF16] for further details.

# 6.6.2.2 Bayesian neural networks

A natural alternative to GPs is to use a parametric model. If we use linear regression, we can efficiently perform exact Bayesian inference, as shown in Section 15.2. If we use a nonlinear model,
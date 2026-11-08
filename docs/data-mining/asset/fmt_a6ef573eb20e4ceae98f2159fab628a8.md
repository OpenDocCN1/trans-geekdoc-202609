
# Generalized Linear Models

In this context the data can be thought of in terms of response variables `y[i]` and explanatory variables organized as `p`-dimensional vectors `x_i`, `i` = 1, …, `n`. Response variables can be expressed in different ways, ranging from binary to categorical or ordinal data. A model is then defined where the expected value `E[y]` of the distribution used for the response variable consists of an initial linear prediction `η[i] = β^(T) x[i]` using a parameter vector `β`, which is then subjected to a smooth, invertible, and potentially nonlinear transformation using the mean function `g^(-1)`:

`μ[i] = E[y[i]] = g^(-1)(β^(T) x[i])`.

The mean function is the inverse of the link function `g`. In generalized linear modeling the entire set of explanatory variables for all the observations is arranged as an `n × p` matrix `X` so that a vector of linear predictions for the entire data set is `η = X β`. The variance of the underlying distribution can also be modeled, typically as a function of the mean. Different distributions, link functions, and corresponding mean functions give a great deal of flexibility in defining probabilistic models; [Table 14.2](#Ch015_516-570_B9780443158889000157_b.xhtml#t0015) shows some examples.

### Table 14.2
Link Functions, Mean Functions, and Distributions Used in Generalized Linear Models

| Link Name | Link Function `η = β^(T) x = g(μ)` | Mean Function `μ = g^(-1)(β^(T) x) = g^(-1)(η)` | Typical Distribution |
|---|---|---|---|
| Identity | `η = μ` | `μ = η` | Gaussian |
| Inverse | `η = μ^(-1)` | `μ = η^(-1)` | Exponential |
| Log | `η = log_e μ` | `μ = exp(η)` | Poisson |
| Log-log | `η = - log(- log_e μ)` | `μ = exp(- exp(- η))` | Bernoulli |


The goal of this example is to obtain the values in the conditional probability table in a general Bayesian network, which consists of `l` discrete random nodes/variables, `x[1], x[2], …, x[l]`. We assume that all the involved variables can be observed and we have a training set of `N` observations. The maximum likelihood method will be employed. Let `x[i](n)` (`n = 1, 2, …, N`) denote the `n`th observation of the `i`th variable.

The joint PDF under the Bayesian network assumption is given by

```
P(x_1,...,x_l) = ∏_{i=1}^{l} P(x_i | Pa_i; θ_i),
```

and the respective log-likelihood is

```
L(X; θ) = ∑_{n=1}^{N} ∑_{i=1}^{l} ln P( x_i(n) | Pa_i(n); θ_i ).
```

Assuming `θ[i]` to be disjoint with `θ[j]` (`i ≠ j`), optimization over each `θ[i]` (`i = 1, 2, …, l`) can take place separately. This property is referred to as the *global decomposition* of the likelihood function. Thus, it suffices to perform the optimization locally on each node, that is,

```
l(θ_i) = ∑_{n=1}^{N} ln P( x_i(n) | Pa_i(n); θ_i ),  i = 1,2,...,l.  (16.64)
```

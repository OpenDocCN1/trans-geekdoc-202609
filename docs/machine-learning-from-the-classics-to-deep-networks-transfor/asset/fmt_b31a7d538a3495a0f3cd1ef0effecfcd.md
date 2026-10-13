
Thus, our goal is to estimate `θ` subject to the nonnegativity as well as the sparsity constraints, given the spectral measurements, `y`, and the endmember matrix, `X`. Obviously, there are different paths to achieve this goal. Because we are currently exploring the Bayesian world, we will employ the Bayesian framework. To this end, an appropriate prior model that expresses our prior belief on the parameters of interest will first be adopted, and we will then perform Bayesian inference using the variational Bayes methodology, as has been previously discussed.

### 13.13.1 Hierarchical Bayesian modeling

The presence of Gaussian noise in Eq. [(13.143)](#Chp013_635-716_B9780443292385000196.xhtml#deq240) dictates that

```
p(y|θ,β) = N(y|Xθ,β^{-1}I_M) = (2π)^{-M/2}β^{M/2}exp(-β/2||y - Xθ||^2).
```

![Equation](images/B9780443292385000196/si708.png)(13.145)

We now turn our attention to selecting suitable priors for the model parameters, which are treated as random variables, `θ`, `β`. As a prior for the nonnegative noise precision `β` we adopt a Gamma distribution (Section [13.3](#Chp013_635-716_B9780443292385000196.xhtml#s0030), Eq. [(13.25)](#Chp013_635-716_B9780443292385000196.xhtml#deq32)), expressed as

```
p(β) = Gamma(β|c,d) = d^c/Γ(c) β^{c-1}exp(-dβ),
```

![Equation](images/B9780443292385000196/si710.png)(13.146)

where `c` and `d` are the respective parameters (set equal to 10^{-6} in the experiments).

For the abundance vector `θ`, we define a two-level hierarchical prior that is expressed in a conjugate form and imposes sparsity as well as nonnegativity on the abundance coefficients. Inspired by [70], a nonnegatively truncated Gaussian prior is selected, i.e.,

```
p(θ|α) = N[R_+^(l)](θ|0,A^{-1}),
```

![Equation](images/B9780443292385000196/si712.png)(13.147)

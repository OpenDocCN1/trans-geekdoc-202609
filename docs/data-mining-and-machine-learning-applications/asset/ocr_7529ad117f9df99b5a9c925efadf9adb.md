# 15.3.7.1 Gibbs Sampling

Gibbs Sampling is a Markov Chain Monte Carlo (MCMC) method used to get the observations in sequential from the multivariate probability distribution of information. It can also be used to approximate the joint probability distribution. Gibbs sampling generates the samples which are related to Markov Chains which are similar to the other samples which are generated.

Algorithm 15.1 described below shows how the Gibbs Sampling works on our proposed methodology. Gibbs Sampling is preferred for our methodology as it helps us to make accurate results while performing the training further [33].

```
Algorithm 15.1 Gibbs Sampling
Begin Gibbs-Sampler(y, Φ, P (0) (y), z )
// y—Sampling of the set of variables
// Φ—Number of factors which defines PΦ
// P (0) (y)—Distribution of the initial state
//z—Time steps calculation
...............................................
1. Sample y(0) from P (0)(y)
2. for z=1, ..., z
3. y(z)—y(z-1)
4. for each yi y
5. Sample yi(z) from PΦ(yi|y-i)
6. // Change yi in y(z)
7. return y(0), ..., y(T)
```

# 15.3.7.2 Contrastive Divergence (CD)

Contrastive Uniqueness is a Monte Carlo Markov Chain (MCMC) gradient descent learning method especially appropriate for learning products of experts (PoE) and energy-based model parameters. A general algorithm for contrastive divergence is described below, which is used in our proposed methodology [34]. Although contrastive divergence algorithm is
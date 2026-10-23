# 7.2. Conjugate priors

When performing inference for the parameters of a specific model, we can ignore this term, since it is constant wrt θ. However, this quantity plays a vital role when choosing between different models, as we discuss in Sec. 7.6.1. It is also useful for estimating the hyperparameters from data (an approach known as empirical Bayes), as we discuss in Sec. 7.5.

In general, computing the marginal likelihood can be hard. However, in the case of the beta-Bernoulli model, the marginal likelihood is proportional to the ratio of the posterior normalizer to the prior normalizer. To see this, recall that the posterior for the beta-binomial models is given by p(θ|D) = Beta(θ|a', b'), where a' = a + N1 and b' = b + N0. We know the normalization constant of the posterior is B(a', b'). Hence

p(θ|D) = p(D|θ)p(θ)/p(D) = 1/p(D) [1/B(a,b) θ^{a-1}(1-θ)^{b-1}] [(N choose N1) θ^{N1}(1-θ)^{N0}] = (N choose N1) 1/p(D) 1/B(a,b) [θ^{a+N1-1}(1-θ)^{b+N0-1}]

So 1/B(a+N1, b+N0) = (N choose N1) 1/p(D) 1/B(a,b)

p(D) = (N choose N1) B(a+N1, b+N0)/B(a,b)

The marginal likelihood for the beta-Bernoulli model is the same as above, except it is missing the (N choose N1) term.

# 7.2.1.6 Mixtures of conjugate priors

The beta distribution is a conjugate prior for the binomial likelihood, which enables us to easily compute the posterior in closed form, as we have seen. However, this prior is rather restrictive. For example, suppose we want to predict the outcome of a coin toss at a casino, and we believe that the coin may be fair, but may equally likely be biased towards heads. This prior cannot be represented by a beta distribution. Fortunately, it can be represented as a mixture of beta distributions.

For example, we might use p(θ) = 0.5 Beta(θ|20, 20) + 0.5 Beta(θ|30, 10)

If θ comes from the first distribution, the coin is fair, but if it comes from the second, it is biased towards heads.

We can represent a mixture by introducing a latent indicator variable h, where h = k means that θ comes from mixture component k. The prior has the form

p(θ) = sum_k p(h = k) p(θ|h = k)

Do not distribute without permission from Kevin P. Murphy and MIT Press.
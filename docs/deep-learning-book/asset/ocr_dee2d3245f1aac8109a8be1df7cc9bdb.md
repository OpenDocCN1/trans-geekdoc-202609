the partition function Z because Z is not a function of x and therefore ∇ₓ Z = 0. Initially, score matching appears to have a new difficulty: computing the score of the data distribution requires knowledge of the true distribution generating the training data, p_data. Fortunately, minimizing the expected value of L(x, θ) is equivalent to minimizing the expected value of

$$\tilde{L}(\mathbf{x},\boldsymbol{\theta}) = \sum_{j=1}^{n} \left( \frac{\partial^{2}}{\partial x_{j}^{2}} \log p_{\text{model}}(\mathbf{x};\boldsymbol{\theta}) + \frac{1}{2} \left( \frac{\partial}{\partial x_{j}} \log p_{\text{model}}(\mathbf{x};\boldsymbol{\theta}) \right)^{2} \right), \quad (18.25)$$

where n is the dimensionality of x.

Because score matching requires taking derivatives with respect to x, it is not applicable to models of discrete data but the latent variables in the model may be discrete.

Like pseudolikelihood, score matching only works when we are able to evaluate log \tilde{p}(x) and its derivatives directly. It is not compatible with methods that provide only a lower bound on log \tilde{p}(x), because score matching requires the derivatives and second derivatives of log \tilde{p}(x), and a lower bound conveys no information about its derivatives. This means that score matching cannot be applied to estimating models with complicated interactions between the hidden units, such as sparse coding models or deep Boltzmann machines. While score matching can be used to pretrain the first hidden layer of a larger model, it has not been applied as a pretraining strategy for the deeper layers of a larger model. This is probably because the hidden layers of such models usually contain some discrete variables.

While score matching does not explicitly have a negative phase, it can be viewed as a version of contrastive divergence using a specific kind of Markov chain (Hyvärinen, 2007a). The Markov chain in this case is not Gibbs sampling, but rather a different approach that makes local moves guided by the gradient. Score matching is equivalent to CD with this type of Markov chain when the size of the local moves approaches zero.

Lyu (2009) generalized score matching to the discrete case (but made an error in the derivation that was corrected by Marlin et al. [2010]). Marlin et al. (2010) found that **generalized score matching** (GSM) does not work in high-dimensional discrete spaces where the observed probability of many events is 0.

A more successful approach to extending the basic ideas of score matching to discrete data is **ratio matching** (Hyvärinen, 2007b). Ratio matching applies specifically to binary data. Ratio matching consists of minimizing the average over
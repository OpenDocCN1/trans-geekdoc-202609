# ## 3.5.3.3 Learning invariant priors

Whenever we have knowledge of some kind of invariance we want our model to satisfy, we can use this to encode a corresponding prior. Sometimes this is done analytically (see e.g., [Rob07, Ch.9]). When this is intractable, it may be possible to learn invariant priors by solving a variational optimization problem (see e.g., [NS18]).

# ## 3.5.4 Reference priors

One way to define a noninformative prior is as a distribution which is maximally far from all possible posteriors, when averaged over datasets. This is the basic idea behind a **reference prior** [Ber05; BBS09]. More precisely, we say that \( p(\theta) \) is a reference prior if it maximizes the expected KL divergence between posterior and prior:

```
$$ p^*(\theta) = \underset{p(\theta)}{\text{argmax}} \int_{\mathcal{D}} p(\mathcal{D}) D_{\text{KL}} (p(\theta|\mathcal{D}) \| p(\theta)) d\mathcal{D} \quad (3.243) $$
```

where \( p(\mathcal{D}) = \int p(\mathcal{D}|\theta)p(\theta)d\theta \). This is the same as maximizing the mutual information \( \mathbb{I}(\theta, \mathcal{D}) \). We can eliminate the integral over datasets by noting that

```
$$ \int p(\mathcal{D}) \int p(\theta|\mathcal{D}) \log \frac{p(\theta|\mathcal{D})}{p(\theta)} = \int p(\theta) \int p(\mathcal{D}|\theta) \log \frac{p(\mathcal{D}|\theta)}{p(\mathcal{D})} = \mathbb{E}_{\theta} [D_{\text{KL}} (p(\mathcal{D}|\theta) \| p(\mathcal{D}))] \quad (3.244) $$
```

where we used the fact that \( \frac{p(\theta|\mathcal{D})}{p(\theta)} = \frac{p(\mathcal{D}|\theta)}{p(\mathcal{D})} \).

One can show that, in 1d, the corresponding prior is equivalent to the Jeffreys prior. In higher dimensions, we can compute the reference prior for one parameter at a time, using the chain rule. However, this can become computationally intractable. See [NS17] for a tractable approximation based on variational inference (Section 10.1).

# ## 3.6 Hierarchical priors

Bayesian models require specifying a prior \( p(\theta) \) for the parameters. The parameters of the prior are called **hyperparameters**, and will be denoted by \( \xi \). If these are unknown, we can put a prior on them; this defines a **hierarchical Bayesian model**, or **multi-level model**, which can visualize like this: \( \xi \to \theta \to \mathcal{D} \). We assume the prior on the hyper-parameters is fixed (e.g., we may use some kind of minimally informative prior), so the joint distribution has the form

```
$$ p(\xi, \theta, \mathcal{D}) = p(\xi)p(\theta|\xi)p(\mathcal{D}|\theta) \quad (3.245) $$
```

The hope is that we can learn the hyperparameters by treating the parameters themselves as datapoints.

A common setting in which such an approach makes sense is when we have \( J > 1 \) related datasets, \( \mathcal{D}_j \), each with their own parameters \( \theta_j \). Inferring \( p(\theta_j|\mathcal{D}_j) \) independently for each group \( j \) can give poor results if \( \mathcal{D}_j \) is a small dataset (e.g., if condition \( j \) corresponds to a rare combination of features, or a sparsely population region). We could of course pool all the data to compute a single model, \( p(\theta|\mathcal{D}) \), but that would not let us model the subpopulations. A hierarchical Bayesian model lets us
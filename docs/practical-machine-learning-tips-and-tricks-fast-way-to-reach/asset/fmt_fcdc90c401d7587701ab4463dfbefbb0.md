
# EM Algorithm and Latent Variable Models

## 11.4 EM Algorithm

The EM algorithm can be interpreted as F function's maximization-maximization algorithm:

```
{ z } EM algorithm can be interpreted as F function's = arg max ∑P(z|D,θ−1)log[P(D,z|θ)] maximization-maximization algorithm, based on this in = θ z{
arg max Ez|D,θt−1 log[P(D,z|θ)]} terpretation there are many variations and generalization,(11.32) e.g., generalized EM Algorithm(GEM).θ≜
arg maxQ(θ,θt−1) (11.33)
θ
```

### 11.4.11.1 F Function's Maximization-Maximization Algorithm

**Definition 11.1.** Given the probability distribution of the hidden variable Z is `˜(Z)`, define F function as the following:

```
˜ ˜ F(P,θ) = E ˜[logP(X,Z|θ)] + H(P) (11.34)
```

Where `H(P) = −E ˜[log ˜P(Z)]`, which is `˜P(Z)`'s entropy.

Assume `θt−1` is the estimation of `θ` in the (t−1)-th iteration, `˜t−1` is the estimation of `˜P` in the (t−1)-th iteration. Then in the t-th iteration two steps are:
1. For fixed `θt−1`, find `˜t` that maximizes `F(˜P, θt−1)`;
2. For fixed `˜t`, find `θt` that maximizes `F(˜Pt, θ)`.

**Lemma 11.1.** For a fixed `θ`, there is only one distribution `˜Pθ` which maximizes `F(˜P, θ)`:

```
˜Pθ(Z) = P(Z|X,θ) (11.35)
```

**Proof.** Given a fixed `θ`, we can get `˜θ` which maximizes `F(˜P, θ)`. We construct the Lagrangian:

```
˜ log ˜Pθ(Z)
L(˜P, θ) = E ˜[logP(X,Z|θ)] − E ˜[P] + λ(1 − ∑P(Z))
Z
```

Take partial derivative with respect to `˜Pθ(Z)` then we get:

```
∂L/∂˜Pθ(Z) = logP(X,Z|θ) − log ˜Pθ(Z) − 1 − λ
```

Let it equal to 0, we can get `λ = logP(X,Z|θ) − log ˜θ(Z) − 1`.

Then we can derive that `˜Pθ(Z)` is proportional to `P(X,Z|θ)`:

```
P(X,Z|θ) = e1+λ ˜Pθ(Z)
˜Pθ(Z) = P(X,Z|θ) / e1+λ
∑P(X,Z|θ) = 1
Z
⇒ e1+λ = ∑P(X,Z|θ) = P(X|θ)
Z
⇒ ˜Pθ(Z) = P(X,Z|θ) / P(X|θ) = P(Z|X,θ)
```

**Lemma 11.2.** If `˜Pθ(Z) = P(Z|X,θ)`, then:

```
˜F(P, θ) = logP(X|θ) (11.37)
```

**Theorem 11.2.** One iteration of EM algorithm can be implemented as F function's maximization-maximization.

**Proof.**
(1) According to Lemma 11.1, we can get `˜Pt(Z) = P(Z|X,θt−1)`.
(2) According above, we can get:

```
˜F(Pt, θ) = E ˜t[logP(X,Z|θ)] + H(Pt)
= ∑P(Z|X,θt−1)logP(X,Z|θ) + H(Pt)
Z
= Q(θ, θt−1) + H(Pt)
```

And `˜Pθ` is continuous w.r.t. `θ`. Then `θt` which maximizes `F(˜Pt, θ)`:

```
θt = arg max F(Pt, θ) = arg max Q(θ, θt−1)
θ θ
```

### 11.4.11.2 The Generalized EM Algorithm (GEM)

In the formulation of the EM algorithm described above, `θt` was chosen as the value of `θ` for which `Q(θ, θt−1)` was maximized. While this ensures the greatest increase in `ℓ(θ)`, it is however possible to relax the requirement of maximization to one of simply increasing `Q(θ, θt−1)` so that `Q(θt, θt−1) ≥ Q(θt−1, θt−1)`. This approach, to simply increase and not necessarily maximize `Q(θt, θt−1)` is known as the **Generalized Expectation Maximization (GEM)** algorithm and is often useful in cases where the maximization is difficult. The convergence of the GEM algorithm is similar to the EM algorithm.

### 11.4.12 Online EM

### 11.4.13 Other EM Variants

## 11.5 Model Selection for Latent Variable Models

When using LVMs, we must specify the number of latent variables, which controls the model complexity. In particular, in the case of mixture models, we must specify K, the number of clusters. Choosing these parameters is an example of model selection. We discuss some approaches below.

### 11.5.1 Model Selection for Probabilistic Models

The optimal Bayesian approach, discussed in Section 5.3, is to pick the model with the largest marginal likelihood, `K = arg maxk p(D|k)`. There are two problems with this. First, evaluating the marginal likelihood for LVMs is quite difficult. In practice, simple approximations, such as BIC, can be used (see e.g., (Fraley and Raftery 2002)). Alternatively, we can use the cross-validated likelihood as a performance measure, although this can be slow, since it requires fitting each model F times, where F is the number of CV folds. The second issue is the need to search over a potentially large number of models. The usual approach is to perform exhaustive search over all candidate values of K. However, sometimes we can set the model to its maximal size, and then rely on the power of the Bayesian Occam's razor to kill off unwanted components. An example of this will be shown in Section TODO 21.6.1.6, when we discuss variational Bayes. An alternative approach is to perform stochastic sampling in the space of models. Traditional approaches, such as (Green 1998, 2003; Lunn et al. 2009), are based on reversible jump MCMC, and use birth moves to propose new centers, and death moves to kill off old centers. However, this can be slow and difficult to implement. A simpler approach is to use a Dirichlet process mixture model, which can be fit using Gibbs sampling, but still allows for an unbounded number of mixture components; see Section TODO 25.2 for details. Perhaps surprisingly, these sampling-based methods can be faster than the simple approach of evaluating the quality of each K separately. The reason is that fitting the model for each K is often slow. By contrast, the sampling methods can often quickly determine that a certain value of K is poor, and thus they need not waste time in that part of the posterior.

### 11.5.2 Model Selection for Non-probabilistic Methods

What if we are not using a probabilistic model? For example, how do we choose K for the K-means algorithm? Since this does not correspond to a probability model, there is no likelihood, so none of the methods described above can be used. An obvious proxy for the likelihood is the reconstruction error. Define the squared reconstruction error of a data set D, using model complexity K, as follows:

```
E(D, K) ≜ 1/N ∑|xi − x̂i|² (11.38)
|D| i=1
```

In the case of K-means, the reconstruction is given by `xi = µzi`, where `zi = arg mink ||xi − µk||²`, as explained in Section 11.4.2.6 TODO. In supervised learning, we can always use cross validation to select between non-probabilistic models of different complexity, but this is not the case with unsupervised learning. The most common approach is to plot the reconstruction error on the training set versus K, and to try to identify a knee or kink in the curve.

## 11.6 Fitting Models with Missing Data

Suppose we want to fit a joint density model by maximum likelihood, but we have holes in our data matrix, due to missing data (usually represented by NaNs). More formally, let `Oij = 1` if component j of data case i is observed, and let `Oij = 0` otherwise. Let `Xv = {xij : Oij = 1}` be the visible data, and `Xh = {xij : Oij = 0}` be the missing or hidden data. Our goal is to compute:

```
θ̂ = arg max p(Xv|θ, O) (11.39)
θ
```

Under the missing at random assumption (see Section 8.6.2), we have TODO.

### 11.6.1 EM for the MLE of an MVN with Missing Data

TODO

# Chapter 12 Latent Linear Models

## 12.1 Factor Analysis

One problem with mixture models is that they only use a single latent variable to generate the observations. In particular, each observation can only come from one of K prototypes. One can think of a mixture model as using K hidden binary variables, representing a one-hot encoding of the cluster identity. But because these variables are mutually exclusive, the model is still limited in its representational power. An alternative is to use a vector of real-valued latent variables, `zi ∈ RL`. The simplest prior to use is a Gaussian (we will consider other choices later):

From this, we see that we can set `µ0 = 0` without loss of generality, since we can always absorb `W µ0` into `µ`. Similarly, we can set `Σ0 = I` without loss of generality, because we can always emulate a correlated prior by defining a new weight matrix, `W̃ = W Σ0^(-1/2)`. So we can rewrite Equation 12.6 and 12.2 as:

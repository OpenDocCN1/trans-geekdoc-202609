
# Chapter 15 Problems

## Problem 15.4

Calculate (i) the KL divergence, (ii) the reverse KL divergence, (iii) the Jensen-Shannon divergence, and (iv) the Wasserstein distance between the distributions:

![c15-fig-5027.jpg](images/c15-fig-5027.jpg)

(15.19)

for the range `a ∈ [−3, 3]`. To get a formula for the Wasserstein distance for this special case, consider the total "earth" (i.e., probability mass) that must be moved and multiply this by the squared distance it must move.

## Problem 15.5

The KL distance and Wasserstein distances between univariate Gaussian distributions are given by:

![c15-fig-5028.jpg](images/c15-fig-5028.jpg)

(15.20)

and

![c15-fig-5029.jpg](images/c15-fig-5029.jpg)

(15.21)

respectively. Plot these distances as a function of `μ[1] − μ[2]` for the case when `σ[1] = σ[2] = 1`.

## Problem 15.6

Consider a latent variable `z` with dimension 100. Consider truncating the values of this variable to (i) `τ = 2.0`, (ii) `τ = 1.0`, (iii) `τ = 0.5`, (iv) `τ = 0.04` standard deviations. What proportion of the original probability distribution is disregarded in each case?

# Chapter 16

Normalizing flows

Chapter 15 introduced generative adversarial networks (GANs). These are generative models that pass a latent variable through a deep network to create a new sample. GANs are trained using the principle that the samples should be indistinguishable from real data. However, they don't define a distribution over data examples. Hence, assessing the probability that a new example belongs to the same dataset isn't straightforward.

In this chapter, we describe *normalizing flows*. These learn a probability model by transforming a simple distribution into a more complicated one using a deep network. Normalizing flows can both sample from this distribution and evaluate the probability of new examples. However, they require specialized architecture: each layer must be *invertible*. In other words, it must be able to transform data in both directions.

## 16.1 1D example

Normalizing flows are probabilistic generative models: they fit a probability distribution to training data (figure 14.2b). Consider modeling a 1D distribution `Pr(x)`. Normalizing flows start with a simple tractable *base* distribution `Pr(z)` over a latent variable `z` and apply a function `x = f[z, ϕ]`, where the parameters `ϕ` are chosen so that `Pr(x)` has the desired distribution ([figure 16.1](#c016.xhtml#c16-fig-0001)). Generating a new example `x*` is easy; we draw `z*` from the base density and pass this through the function so that `x* = f[z*, ϕ]`.

![Figure 16.1 Transforming probability distributions. a) The base density is a standard normal defined on a latent variable z. b) This variable is transformed by a function x = f[z, ϕ] to a new variable x, which c) has a new distribution. To sample from this model, we draw values z from the base density (green and brown arrows in panel (a) show two examples). We pass these through the function f[z, ϕ] as shown by dotted arrows in panel (b) to generate the values of x, which are indicated as arrows in panel (c).](images/c16-fig-0001.jpg)

[Figure 16.1](#c016.xhtml#c16-fig-0001a) Transforming probability distributions. a) The base density is a standard normal defined on a latent variable `z`. b) This variable is transformed by a function `x = f[z, ϕ]` to a new variable `x`, which c) has a new distribution. To sample from this model, we draw values `z` from the base density (green and brown arrows in panel (a) show two examples). We pass these through the function `f[z, ϕ]` as shown by dotted arrows in panel (b) to generate the values of `x`, which are indicated as arrows in panel (c).

### 16.1.1 Measuring probability

Measuring the probability of a data point `x` is more challenging. Consider applying a function `f[z, ϕ]` to random variable `z` with known density `Pr(z)`. The probability density will decrease in areas that are stretched by the function and increase in areas that are compressed so that the area under the new distribution remains one. The degree to which a function `f[z, ϕ]` stretches or compresses its input depends on the magnitude of its gradient. If a small change to the input causes a larger change in the output, it stretches the function. If a small change to the input causes a smaller change in the output, it compresses the function ([figure 16.2](#c016.xhtml#c16-fig-0002)).

![Figure 16.2 Transforming distributions. The base density (cyan, bottom) passes through a function (blue curve, top right) to create the model density (orange, left). Consider dividing the base density into equal intervals (gray vertical lines). The probability mass between adjacent lines must remain the same after transformation. The cyan-shaded region passes through a part of the function where the gradient is larger than one, so this region is stretched. Consequently, the height of the orange-shaded region must be lower so that it retains the same area as the cyan-shaded region. In other places (e.g., z = −2), the gradient is less than one, and the model density increases relative to the base density.](images/c16-fig-0002.jpg)

[Figure 16.2](#c016.xhtml#c16-fig-0002a) Transforming distributions. The base density (cyan, bottom) passes through a function (blue curve, top right) to create the model density (orange, left). Consider dividing the base density into equal intervals (gray vertical lines). The probability mass between adjacent lines must remain the same after transformation. The cyan-shaded region passes through a part of the function where the gradient is larger than one, so this region is stretched. Consequently, the height of the orange-shaded region must be lower so that it retains the same area as the cyan-shaded region. In other places (e.g., `z = −2`), the gradient is less than one, and the model density increases relative to the base density.

More precisely, the probability of data `x` under the transformed distribution is:

![c16-fig-5001.jpg](images/c16-fig-5001.jpg)

(16.1)

where `z = f⁻¹[x, ϕ]` is the latent variable that created `x`. The term `Pr(z)` is the original probability of this latent variable under the base density. This is moderated according to the magnitude of the derivative of the function. If this is greater than one, then the probability decreases. If it is smaller, the probability increases.

***

Notebook 16.1

1D normalizing flows

***

### 16.1.2 Forward and inverse mappings

To draw samples from the distribution, we need the forward mapping `x = f[z, ϕ]`, but to measure the likelihood, we need to compute the inverse `z = f⁻¹[x, ϕ]`. Hence, we need to choose `f[z, ϕ]` judiciously so that it is *invertible*.

***

Problems 16.1–16.2

***

The forward mapping is sometimes termed the *generative direction*. The base density is usually chosen to be a standard normal distribution. Hence, the inverse mapping is termed the *normalizing direction* since this takes the complex distribution over `x` and turns it into a normal distribution over `z` ([figure 16.3](#c016.xhtml#c16-fig-0003)).

![Figure 16.3 Inverse mapping (normalizing direction). If the function is invertible, then it's possible to transform the model density back to the original base density. The probability of a point x under the model density depends partly on the probability of the equivalent point z under the base density (see equation 16.1).](images/c16-fig-0003.jpg)

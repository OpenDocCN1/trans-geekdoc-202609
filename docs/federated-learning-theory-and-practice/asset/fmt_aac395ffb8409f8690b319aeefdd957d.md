
As *α* → ∞, RDP[*α*] converges to the standard (*ε*, 0)-DP. Both *ε* and *δ* should be positive or equal to zero. Considering *δ* → 0 with only minor relaxation, a smaller value of *ε* indicates a stronger (*ε*, 0)-differentially private guarantee. In other words, nearly equal probabilities in [(20.1)](#Chp020_353-368_B9780443190377000302.xhtml#deq1) would be given from the neighboring inputs *d* and *d*′, which makes data identity much harder to infer. Moreover, learning from post-processing features (e.g., Mel-spectrum [[6](#Chp020_353-368_B9780443190377000302.xhtml#br0030), [16]](#Chp020_353-368_B9780443190377000302.xhtml#br0080)) based on the speech data could also be differentially private, which has been shown by the theorem given in [[1](#Chp020_353-368_B9780443190377000302.xhtml#br0005), [18]](#Chp020_353-368_B9780443190377000302.xhtml#br0090). We aim to further study a performance trade-off between the additive DP-noise and robustness of neural network based models in this proposal, which remains an open problem to design high-performance DP-preserving speech models and understand their limits. As one popular deep neural network based DP-preserving baseline, we provide a review of differentially private stochastic gradient descent (DPSGD) [[65]](#Chp020_353-368_B9780443190377000302.xhtml#br0325). DPSGD is based on stochastic gradient descent (SGD) [[30]](#Chp020_353-368_B9780443190377000302.xhtml#br0150), which is an iterative optimization method for solving the convex optimization problem. SGD starts with a starting point *w*[0], and at step *t*, updates the iterate as

*w*[*t* + 1] = *w*[*t*] − *η*[*t*](*λw*[*t*] + ∇ℓ(*w*[*t*], *x*[*t*], *y*[*t*])),

(20.3)

where *η*[*t*] denotes learning rate, and the (sub)gradient ∇ℓ(*w*[*t*], *x*[*t*], *y*[*t*]) is computed based on a single input *x*[*t*] and label *y*[*t*]. To introduce DP-noises, a DPSGD update is defined as

*w*[*t* + 1] = *w*[*t*] − *η*[*t*](*λw*[*t*] + ∇ℓ(*w*[*t*], *x*[*t*], *y*[*t*]) + *Z*[*t*]),

(20.4)

where each *Z*[*t*] is a random noise vector in *R*^(*d*) drawn independently from the density of *ρ*(*z*) ∝ *e*^(−(*α*/2)∥*z*∥). DPSGD has been recently [[15]](#Chp020_353-368_B9780443190377000302.xhtml#br0075) introduced into large-scale optimization machine learning backbone to replace SGD for training a model under DP measurement. However, both direct database-level DP perturbation and DPSGD will largely degrade model performance. When ASR and voice assistant production are still performance-driven tasks, we will introduce some recent federated training methods to enhance ASR performance.

## 20.1.5 Teacher-student learning for federated ASR

How to reduce the privacy budget and deploy a performance-driven ASR system is one challenging topic. To reduce the privacy cost over the standard data-independent bound, Papernot et al. [[46]](#Chp020_353-368_B9780443190377000302.xhtml#br0230) have provided a theoretical analysis of a general data-dependent upper bound through **ensemble learning** with deep neural networks, which needs less cost of a predicting loss to achieve a targeted DP-privacy budget (*ε*). We could extend the random privacy-preserving algorithm ℳ (introduced in [(20.1)](#Chp020_353-368_B9780443190377000302.xhtml#deq1)) under *ε*-DP, where *ε* is equal to 2*γ*^()

$$
\alpha\left( l;d,d^{\prime} \right) \leqslant \log\left( (1 - \tau)\left( \frac{1 - \tau}{1 - e^{2\gamma}\tau} \right)^{l} + \tau e^{(2\gamma l)} \right).
$$

(20.5)

Bound [(20.5)](#Chp020_353-368_B9780443190377000302.xhtml#deq5) is built upon a foundation of composition theorem [[19]](#Chp020_353-368_B9780443190377000302.xhtml#br0095) over aggregation methods for *ε*-DP. We refer to Theorem 1, and Theorem 3 in [[46]](#Chp020_353-368_B9780443190377000302.xhtml#br0230) for more details.

We now describe the private aggregation of teacher ensembles (PATE) [[46](#Chp020_353-368_B9780443190377000302.xhtml#br0230), [47]](#Chp020_353-368_B9780443190377000302.xhtml#br0235) based acoustic modeling to empower *ε*-DP in the federated settings. First, an ensemble of teacher models is built by partitioning the training dataset into *I* disjoint subsets, 𝒟[1], …, 𝒟[*I*]. Next, these are used to train *I* teacher models independently, 𝒯[1], …, 𝒯[*I*]. They are employed to generate acoustic model scores [[8]](#Chp020_353-368_B9780443190377000302.xhtml#br0040) to be combined as an effective way for teacher-student learning in order to aggregate frame-level predictions of the teachers by taking a weighted average of context-dependent state posteriors from ASR models. For each frame of audio *x*, the final aggregated teacher model produces a vector of posteriors, 𝒯[*ens*](*s*|*x*), over context-dependent states *s* computed as follows:

$$
\mathcal{T}_{ens}(s|x) = \sum\limits_{i = 1}^{I}w_{i}\mathcal{T}_{i}(s|x),
$$

(20.6)

where 𝒯[*i*](*s*|*x*) is the posterior from the *i*th model, and *w*[*i*] is its weighting coefficient. The corresponding states from individual teacher models have the same dimension *J* before the output alignment (e.g., considering a special silent character before alignment).

To ensure *ε*-DP under the PATE method, a random perturbation was introduced into the individual teachers' predictions (𝒯[*i*]). We revise [(20.6)](#Chp020_353-368_B9780443190377000302.xhtml#deq6) to obtain a final ensemble from noisy teachers:

$$
\mathcal{T}_{PATE}(x,\lambda) = \sum\limits_{i = 1}^{I}w_{i}\left( \mathcal{T}_{i}(x) + Y_{j}(\lambda) \right),
$$

(20.7)

where *Y*[1], …, *Y*[*m*] are i.i.d. Laplacian or Gaussian random variables with location 0 and scale *λ*^(−1), where *λ* refers to a privacy parameter that influences (*ϵ*, *δ*)-DP guarantees and for which a bound has been proven under composition theorems applicable to model aggregation [[46](#Chp020_353-368_B9780443190377000302.xhtml#br0230), [47]](#Chp020_353-368_B9780443190377000302.xhtml#br0235).

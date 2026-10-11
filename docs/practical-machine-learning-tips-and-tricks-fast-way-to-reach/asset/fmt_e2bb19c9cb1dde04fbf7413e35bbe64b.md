
# EM Algorithm

To perform MAP estimation, we modify the M-step as follows:

**Input**: observed data `D = {x1, x2, ..., xN}`, joint distribution `P(x, z | θ)`

**Output**: model's parameters `θ`

```text
// 1. identify hidden variables z, write out the log likelihood function ℓ(x, z | θ)
θ(0) = ... // initialize

while (!convergency) do
    // 2. E-step: plug in P(x, z | θ), derive the formula of Q(θ, θ^(t-1))
    Q(θ, θ^(t-1)) = E[ℓc(θ) | D, θ^(t-1)]

    // 3. M-step: find θ that maximizes the value of Q(θ, θ^(t-1))
    θ^t = arg max Q(θ, θ^(t-1))
          θ
end
```

**Algorithm 3**: EM algorithm

Below we explain how to perform the E and M steps for several simple models, that should make things clearer.

## 11.4.3 EM for GMMs

### 11.4.3.1 Auxiliary function

```math
Q(θ, θ^(t-1)) = E_{z|D, θ^(t-1)}[ℓc(θ)]
             = E_{z|D, θ^(t-1)}[∑_{i=1}^N log p(x_i, z_i | θ)]
             = E_{z|D, θ^(t-1)}[∑_{i=1}^N log ∏_{k=1}^K (π_k p(x_i | θ_k))^{I(z_i=k)}]
             = ∑_{i=1}^N ∑_{k=1}^K E[I(z_i = k)] log[π_k p(x_i | θ_k)]
             = ∑_{i=1}^N ∑_{k=1}^K p(z_i = k | x_i, θ^(t-1)) log[π_k p(x_i | θ_k)]
             = ∑_{i=1}^N ∑_{k=1}^K r_{ik} log π_k + ∑_{i=1}^N ∑_{k=1}^K r_{ik} log p(x_i | θ_k)  (11.16)
```

where `r_{ik} ≜ E[I(z_i = k)] = p(z_i = k | x_i, θ^(t-1))` is the responsibility that cluster `k` takes for data point `i`. This is computed in the E-step, described below.

```math
θ^t = arg max Q(θ, θ^(t-1)) + log p(θ)  (11.15)
      θ
```

### 11.4.3.2 E-step

The E step remains unchanged. The E-step has the following simple form, which is the same for any mixture model:

```math
r_{ik} = p(z_i = k | x_i, θ^(t-1)) = \frac{p(z_i = k, x_i | θ^(t-1))}{p(x_i | θ^(t-1))}  (11.17)
       = \frac{π_k p(x_i | θ_k^(t-1))}{∑_{k'=1}^K π_{k'} p(x_i | θ_{k'}^(t-1))}
```

### 11.4.3.3 M-step

In the M-step, we optimize `Q` wrt `π` and `θ_k`. For `π`, grouping together only the terms that depend on `π`, we find that we need to maximize `∑_{i=1}^N ∑_{k=1}^K r_{ik} log π_k`. However, there is an additional constraint `∑_{k=1}^K π_k = 1`, since they represent the probabilities `π_k = P(z_i = k)`. To deal with the constraint we construct the Lagrangian:

```math
L(π) = ∑_{i=1}^N ∑_{k=1}^K r_{ik} log π_k + β(∑_{k=1}^K π_k - 1)
```

where `β` is the Lagrange multiplier. Taking derivatives, we find:

```math
π_k = \frac{∑_{i=1}^N r_{ik}}{N}  (11.18)
```

This is the same for any mixture model, whereas `θ_k` depends on the form of `p(x | θ_k)`.

For `θ_k`, plug in the pdf to Equation 11.16:

```math
Q(θ, θ^(t-1)) = ∑_{i=1}^N ∑_{k=1}^K r_{ik} log π_k - \frac{1}{2} ∑_{i=1}^N ∑_{k=1}^K r_{ik} [log |Σ_k| + (x_i - μ_k)^T Σ_k^{-1} (x_i - μ_k)]
```

Take partial derivatives of `Q` wrt `μ_k`, `Σ_k` and let them equal to 0, we can get:

```math
\frac{∂Q}{∂μ_k} = -\frac{1}{2} ∑_{i=1}^N r_{ik} [(Σ_k^{-1} + Σ_k^{-T})(x_i - μ_k)]
               = -[Σ_k^{-1}(x_i - μ_k)] ∑_{i=1}^N r_{ik} = 0
⇒ μ_k = \frac{∑_{i=1}^N r_{ik} x_i}{∑_{i=1}^N r_{ik}}  (11.19)
```

```math
\frac{∂Q}{∂Σ_k} = -\frac{1}{2} ∑_{i=1}^N r_{ik} [\frac{1}{Σ_k} - \frac{1}{Σ_k^2} (x_i - μ_k)(x_i - μ_k)^T] = 0
⇒ Σ_k = \frac{∑_{i=1}^N r_{ik} (x_i - μ_k)(x_i - μ_k)^T}{∑_{i=1}^N r_{ik}}  (11.20)
```

```math
= \frac{∑_{i=1}^N r_{ik} x_i x_i^T}{∑_{i=1}^N r_{ik}} - μ_k μ_k^T  (11.21)
```

### 11.4.3.4 Algorithm pseudo code

**Input**: observed data `D = {x1, x2, ..., xN}`, GMM

**Output**: GMM's parameters `π, μ, Σ`

```text
// 1. initialize
π^(0) = ...
μ^(0) = ...
Σ^(0) = ...
t = 0

while (!convergency) do
    // 2. E-step
    r̂_{ik} = \frac{π_k p(x_i | θ_k^(t-1))}{∑_{k'=1}^K π_{k'} p(x_i | μ_{k'}^(t-1), Σ_{k'}^(t-1))}

    // 3. M-step
    π̂_k = \frac{∑_{i=1}^N r̂_{ik}}{N}
    μ̂_k = \frac{∑_{i=1}^N r̂_{ik} x_i}{∑_{i=1}^N r̂_{ik}}
    Σ̂_k = \frac{∑_{i=1}^N r̂_{ik} (x_i - μ̂_k)(x_i - μ̂_k)^T}{∑_{i=1}^N r̂_{ik}}
    t++
end
```

**Algorithm 4**: EM algorithm for GMM

### 11.4.3.5 MAP estimation

As usual, the MLE may overfit. The overfitting problem is particularly severe in the case of GMMs. An easy solution to this is to perform MAP estimation. The new auxiliary function is the expected complete data log-likelihood plus the log prior:

```math
Q(θ, θ^(t-1)) = ∑_{i=1}^N ∑_{k=1}^K r_{ik} log π_k + ∑_{i=1}^N ∑_{k=1}^K r_{ik} log p(x_i | θ_k)
              + log p(π) + ∑_{k=1}^K log p(θ_k)
```

It is natural to use conjugate priors.

```math
p(π) = Dir(π | α)
p(μ_k, Σ_k) = NIW(μ_k, Σ_k | m_0, κ_0, ν_0, S_0)
```

From Equation 3.28 and Section 4.6.3, the MAP estimate is given by:

```math
π_k = \frac{∑_{i=1}^N r_{ik} + α_k - 1}{N + ∑_{k=1}^K α_k - K}  (11.23)
μ_k = \frac{∑_{i=1}^N r_{ik} x_i + κ_0 m_0}{∑_{i=1}^N r_{ik} + κ_0}  (11.24)
Σ_k = \frac{\bar{S}_0 + S_k + \frac{κ_0 r_k}{κ_0 + r_k} (\bar{x}_k - m_0)(\bar{x}_k - m_0)^T}{ν_0 + r_k + D + 2}  (11.25)
```

where `r_k ≜ ∑_{i=1}^N r_{ik}`, `\bar{x}_k ≜ \frac{∑_{i=1}^N r_{ik} x_i}{r_k}`, `\bar{S}_k ≜ \frac{∑_{i=1}^N r_{ik} (x_i - \bar{x}_k)(x_i - \bar{x}_k)^T}{r_k}`.

## 11.4.4 EM for K-means

### 11.4.4.1 Representation

```math
y_j = k \text{ if } \| x_j - μ_k \|_2^2 \text{ is minimal}  (11.26)
```

where `μ_k` is the centroid of cluster `k`.

### 11.4.4.2 Evaluation

```math
\arg \min_{μ} ∑_{j=1}^N ∑_{k=1}^K γ_{jk} \| x_j - μ_k \|_2^2  (11.27)
```

The hidden variable is `γ_{jk}`, which's meaning is:

```math
γ_{jk} = \begin{cases}
1, & \text{if } \| x_j - μ_k \|_2^2 \text{ is minimal for } μ_k \\
0, & \text{otherwise}
\end{cases}
```

### 11.4.4.3 Optimization

**E-Step**:

```math
γ_{jk}^{(i+1)} = \begin{cases}
1, & \text{if } \| x_j - μ_k^{(i)} \|_2^2 \text{ is minimal for } μ_k^{(i)} \\
0, & \text{otherwise}
\end{cases}
```

**M-Step**:

```math
μ_k^{(i+1)} = \frac{∑_{j=1}^N γ_{jk}^{(i+1)} x_j}{∑_{j=1}^N γ_{jk}^{(i+1)}}  (11.28)
```

### 11.4.4.4 Tricks

**Choosing the initial centroids (seeds)**

1. **K-means++**. The intuition that spreading out the `k` initial cluster centers is a good thing is behind this approach: the first cluster center is chosen uniformly at random from the data points that are being clustered, after which each subsequent cluster center is chosen from the remaining data points with probability proportional to its squared distance from the point's closest existing cluster center. The exact algorithm is as follows:
   a. Choose one center uniformly at random from among the data points.
   b. For each data point `x`, compute `D(x)`, the distance between `x` and the nearest center that has already been chosen.
   c. Choose one new data point at random as a new center, using a weighted probability distribution where a point `x` is chosen with probability proportional to `D(x)^2`.
   d. Repeat Steps 2 and 3 until `k` centers have been chosen.
   e. Now that the initial centers have been chosen, proceed using standard k-means clustering.

2. TODO

## 11.4.5 EM for mixture of experts

TODO

## 11.4.6 EM for DGMs with hidden variables

## 11.4.7 EM for the Student distribution

## 11.4.8 EM for probit regression

## 11.4.9 Derivation of the Q function (Jensen's inequality)

Let `f` be a convex function (see Section A.1) defined on a convex set `S`. If `x_1, x_2, ..., x_n ∈ S` and `λ_1, λ_2, ..., λ_n ≥ 0` with `∑_{i=1}^n λ_i = 1`, then:

```math
f(∑_{i=1}^n λ_i x_i) ≤ ∑_{i=1}^n λ_i f(x_i)  (11.29)
```

**Proposition 11.1**.

```math
log(∑_{i=1}^n λ_i x_i) ≥ ∑_{i=1}^n λ_i log(x_i)  (11.30)
```

Now let's prove why the Q function should look like Equation 11.13:

```math
ℓ(θ) = log P(D | θ)
     = log ∑_z P(D, z | θ)
     = log ∑_z P(D | z, θ) P(z | θ)
     = log ∑_z \frac{P(z | D, θ^(t-1)) P(D | z, θ) P(z | θ)}{P(z | D, θ^(t-1))}
     = log ∑_z P(z | D, θ^(t-1)) \frac{P(D | z, θ) P(z | θ)}{P(z | D, θ^(t-1)) P(D | θ^(t-1))} P(D | θ^(t-1))
     ≥ ∑_z P(z | D, θ^(t-1)) log \frac{P(D | z, θ) P(z | θ)}{P(z | D, θ^(t-1)) P(D | θ^(t-1))}
     = ∑_z P(z | D, θ^(t-1)) log \frac{P(D | z, θ) P(z | θ)}{P(z | D, θ^(t-1))} - log P(D | θ^(t-1))
```

![Figure 11.4: Graphical interpretation of a single iteration of the EM algorithm: The function B(θ, θ^(t-1)) is bounded above by the log likelihood function ℓ(θ). The functions are equal at θ = θ^(t-1). The EM algorithm chooses θ^t as the value of θ for which B(θ, θ^(t-1)) is a maximum. Since ℓ(θ) ≥ B(θ, θ^(t-1)), increasing B(θ, θ^(t-1)) ensures that the value of the log likelihood function ℓ(θ) is increased at each step.](image_rsrc1RT.jpg)

```math
B(θ, θ^(t-1)) ≜ ∑_z P(z | D, θ^(t-1)) log \frac{P(D | z, θ) P(z | θ)}{P(z | D, θ^(t-1)) P(D | θ^(t-1))}
```

Since the expected complete data log likelihood `Q` is derived from `B(θ, θ^(t-1))` by dropping terms which are constant w.r.t. `θ`, so it is also a lower bound to a lower bound of `ℓ(θ)`.

```math
θ^t = \arg \max_θ B(θ, θ^(t-1))
    = \arg \max_θ [ℓ(θ^(t-1)) + ∑_z P(z | D, θ^(t-1)) log \frac{P(D | z, θ) P(z | θ)}{P(z | D, θ^(t-1)) P(D | θ^(t-1))}]
    = \arg \max_θ ∑_z P(z | D, θ^(t-1)) log [P(D | z, θ) P(z | θ)]
```

## 11.4.10 Convergence of the EM Algorithm

### 11.4.10.1 Expected complete data log likelihood is a lower bound

Note that `ℓ(θ) ≥ B(θ, θ^(t-1))`, and `ℓ(θ^(t-1)) = B(θ^(t-1), θ^(t-1))`, which means `B(θ, θ^(t-1))` is a lower bound of `ℓ(θ)`. If we maximize `B(θ, θ^(t-1))`, then `ℓ(θ)` gets maximized.

### 11.4.10.2 EM monotonically increases the observed data log likelihood

Now drop terms which are constant w.r.t. `θ`:

```math
θ^t = \arg \max_θ ∑_z P(z | D, θ^(t-1)) log [P(D | z, θ) P(z | θ)]
```

## 11.4.11 Generalization of EM Algorithm

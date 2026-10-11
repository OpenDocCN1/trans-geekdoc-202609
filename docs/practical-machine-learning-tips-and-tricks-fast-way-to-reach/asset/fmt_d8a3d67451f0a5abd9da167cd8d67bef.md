
# 7.4 Ridge Regression (MAP)

## 7.3.1.1 Geometric Understanding

See Figure 7.1.

To limit the standard of the leftover, `y - ŷ`, we need the lingering vector to be symmetrical to each segment of `X`, so `x̃ⱼ(y - ŷ) = 0` for `j = 1 : D`. Hence

```
xⱼ(y - ŷ) = 0
Xᵀ(y - Xw) = 0
w = (XᵀX)⁻¹Xᵀy
```

One issue with ML assessment is that it can bring about overfitting. In this part, we talk about a method for enhancing this issue by utilizing MAP assessment with a Gaussian prior.

### 7.4.1 Basic Idea

We can urge the boundaries to be little, subsequently bringing about a smoother bend, by utilizing a zero-mean Gaussian prior:

```
p(w) = ∏ N(wⱼ | 0, τ²)
      j
```

where `1/τ²` controls the strength of the earlier. The relating MAP assessment issue becomes

```
arg max ∑ log N(yᵢ | w₀ + wᵀxᵢ, σ²) + ∑ log N(wⱼ | 0, τ²)
      w i=1       j=1
```

In spaces with bunches of information, basic techniques can function admirably (Halevy et al. 2009). In any case, there are still motivations to concentrate on more complex learning strategies, on the grounds that there will consistently be issues for which we have little information. For instance, even in such an information rich space as web search, when we need to begin customizing the outcomes, the measure of information accessible for some random client begins to look little once more (comparative with the intricacy of the problem).

It is a basic exercise to show that this is identical to limiting the following

```
J(w) = (1/Nσ²) ∑ (yᵢ - (w₀ + wᵀxᵢ))² + λ ||w||², λ ≜ 1/τ²
        i=1
```

Here the initial term is the MSE/NLL of course, and the subsequent term, `λ ≥ 0`, is an intricacy punishment. The relating arrangement is given by

```
ŵ_ridge = (λI_D + XᵀX)⁻¹Xᵀy
```

This method is known as edge regression, or punished least squares. By and large, adding a Gaussian preceding the boundaries of a model to urge them to be little is called `ℓ₂` regularization or weight rot. Note that the offset term `w₀` isn’t regularized, since this simply influences the tallness of the capacity, not its complexity. We will think about a wide range of priors in this book. Each of these relates to an alternate type of regularization. This strategy is generally used to forestall overfitting.

### 7.4.2 Numerically Stable Computation

```
ŵ_ridge = V (ZᵀZ + λI_N)⁻¹Zᵀy
```

### 7.4.3 Connection with PCA

### 7.4.4 Regularization Impacts of Large Data

Regularization is the most well-known method for staying away from overfitting. Notwithstanding, another compelling methodology which isn’t generally accessible is to utilize heaps of information. It ought to be naturally clear that the additional preparation information we have, the better we will actually want to learn.

# Chapter 8 Logistic Regression

## 8.1 Representation

Logistic relapse can be binomial or multinomial. The binomial strategic relapse model has the following structure

```
p(y | x, w) = Ber(y | sigm(wᵀx))
```

where `w` and `x` are broadened vectors, i.e., `w = (b, w₁, w₂, · · · , w_D)`, `x = (1, x₁, x₂, · · · , x_D)`.

```
g(w) = dJ/dw = ∑ [π(xᵢ) - yᵢ]xᵢ = Xᵀ(π - y)
       i=1

H(w) = d²g/dwᵀ = d(π - y)ᵀXᵀ/dw
     = XᵀSX, S ≜ diag(π(xᵢ)(1 - π(xᵢ))xᵢ)
```

## 8.2 Optimization

### 8.2.1 MLE

```
{ N
ℓ(w) = log ∏ [π(xᵢ)]ʸⁱ [1 - π(xᵢ)]¹⁻ʸⁱ
     i=1
```

where `π(x) ≜ P(y = 1 | x, w)`.

```
N
= ∑ [yᵢ log π(xᵢ) + (1 - yᵢ) log(1 - π(xᵢ))]
i=1

N
= ∑ [yᵢ log (π(xᵢ)/(1 - π(xᵢ)))] + ∑ log(1 - π(xᵢ))
i=1   i=1

N
= ∑ [yᵢ(w·xᵢ) - log(1 + exp(w·xᵢ))]
i=1
```

```
J(w) ≜ NLL(w) = -ℓ(w)
N
= -∑ [yᵢ(w·xᵢ) - log(1 + exp(w·xᵢ))]
i=1
```

Equation 8.2 is likewise called the cross-entropy blunder work (see Equation 2.53).

Unlike direct relapse, we can presently don’t record the MLE in shut structure. All things considered, we really want to utilize an improvement calculation to register it, see Appendix A. For this, we want to determine the angle and Hessian.

For the situation of calculated relapse, one can show that the slope and Hessian of this are given by the following

### 8.2.1.1 Iteratively Reweighted Least Squares (IRLS)

### 8.2.2 MAP

Just as we incline toward edge relapse to direct relapse, so we ought to favor MAP assessment for strategic relapse to processing the MLE. `ℓ₂` regularization we can utilize `ℓ₂` regularization, similarly as with edge relapse. We note that the new unbiased, angle and Hessian have the accompanying forms:

```
J'(w) ≜ NLL(w) + λwᵀw
g'(w) = g(w) + λw
H'(w) = H(w) + λI
```

It is a basic make a difference to pass these adjusted conditions into any inclination based optimizer.

## 8.3 Multinomial Logistic Regression

### 8.3.1 Representation

Multinomial strategic relapse model is likewise called a most extreme entropy classifier, which has the accompanying form

```
p(y = c | x, W) = exp(w_cᵀx) / ∑ exp(w_cᵀx)
                   C
                  c=1
```

Let `yᵢ = (I(yᵢ = 1), I(yᵢ = 1), · · · , I(yᵢ = C))`, `µᵢ = (p(y = 1 | xᵢ, W), p(y = 2 | xᵢ, W), · · · , p(y = C | xᵢ, W))`, then, at that point, the log-probability capacity can be composed as

```
ℓ(W) = log ∏ ∏ µᵢcʸⁱᶜ
       N C
      i=1 c=1

= ∑ ∑ yᵢc w_cᵀxᵢ - log ∑ exp(w_cᵀxᵢ)
  i=1 c=1   C
           c=1
```

Define the true capacity as NLL

```
J(W) ≜ NLL(W) = -ℓ(W)
```

Define `A ⊗ B` be the kronecker result of matrices `A` and `B`. If `A` is an `m×n` matrix and `B` is a `p×q` matrix, then `A ⊗ B` is the `mp×nq` block matrix

```
⎡ a₁₁B  ···  a₁ₙB ⎤
⎢ ...    ...  ... ⎥
⎣ aₘ₁B  ···  aₘₙB ⎦
```

The inclination and Hessian are given by

```
g(W) = ∑ (µᵢ - yᵢ) ⊗ xᵢ
       i=1

H(W) = ∑ (diag(µᵢ) - µᵢµᵢᵀ) ⊗ (xᵢxᵢᵀ)
       i=1
```

where `yᵢ = (I(yᵢ = 1), I(yᵢ = 1), · · · , I(yᵢ = C-1))` and `µᵢ = (p(y = 1 | xᵢ, W), p(y = 2 | xᵢ, W), · · · , p(y = C-1 | xᵢ, W))` are section vectors of length `C-1`. Pass them to any slope based optimizer.

### 8.3.2 MLE

### 8.3.3 MAP

The new objective

```
J'(W) = NLL(w) - log p(W)
```

where `p(W) ≜ ∏ N(w_c | 0, V₀)`
                  C
                 c=1

```
= J(W) + 1/2 ∑ w_cᵀ V₀⁻¹ w_c
         C
        c=1
```

Its inclination and Hessian are given by

```
g'(w) = g(W) + V₀⁻¹ ∑ w_c
                   C
                  c=1

H'(w) = H(w) + I_C ⊗ V₀⁻¹
```

This can be passed to any slope based streamlining agent to observe the MAP gauge. Note, nonetheless, that the Hessian has size `((CD)(CD))`, which is `C` occasions more line and segments than in the double case, so restricted memory BFGS is more suitable than Newtons strategy.

## 8.4 Bayesian Strategic Regression

It is normal to need to process the full back over the boundaries, `p(w | D)`, for strategic relapse models. This can be valuable for any circumstance where we need to assoamate certainty stretches with our forecasts (e.g., this is essential when tackling relevant criminal issues, examined in Section TODO). Unfortunately, dissimilar to the straight relapse case, this is impossible precisely, since there is no helpful conjugate earlier for calculated relapse. We talk about one simple guess beneath; some different methodologies include MCMC (Section TODO), variational inference (Section TODO), expectation propagation (Kuss and Rasmussen 2005), etc. For notational simplicity, we stick to binary calculated regression.

### 8.4.1 Laplace Approximation

### 8.4.2 Derivation of the BIC

### 8.4.3 Gaussian Guess for Calculated Regression

### 8.4.4 Approximating the Back Predictive

### 8.4.5 Residual Examination (Anomaly Location)

## 8.5 Online Learning and Stochastic Optimization

Traditionally AI is performed disconnected, be that as it may, assuming we have streaming information, we really want to perform internet learning, so we can refresh our appraisals as each new information point shows up rather than delaying until the end (which may never happen). Furthermore regardless of whether we have a cluster of information, we should deal with it like a stream on the off chance that it is too enormous to even think about holding in principle memory. Beneath we examine learning strategies for this sort of scenario.

TODO

![](image_rsrc1RG.jpg)

**Fig. 8.1: Perceptron**

```
w ← 0; b ← 0; k ← 0;
while no slip-ups made inside the for circle
```

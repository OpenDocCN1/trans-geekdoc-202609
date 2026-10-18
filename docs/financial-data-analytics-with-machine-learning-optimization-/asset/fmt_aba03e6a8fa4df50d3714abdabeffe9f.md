
when the sample size `n` is large. Here, it is assumed that the data `(x₁, y₁), ..., (xₙ, yₙ)` are iid realizations of `(x, y)`. By the Law of Large Numbers again, with a sufficiently large `M << n`, the theoretical expectation `E(∇_θ ℓ(θ; y, x))` can be approximated instead by a small portion of size `M` of `S`, that is,

```
E[∇_θ ℓ(θ; y, x)] ≈ (1/M) Σ_{m=1}^M ∇_θ ℓ(θ; y_m, x_m).
```

Therefore, with a very high probability, with both large `M` and `n`,

```
∇_θ L_M(θ) ≈ (1/M) Σ_{m=1}^M ∇_θ ℓ(θ; y_m, x_m),
```

and this is the main philosophy of mini‐batch SGD: replacing the gradient of the overall loss by only a portion average of gradient individual losses.
